---
title: シングル サインオンを使用する Node.js Office アドインを作成する
description: 2018/01/23
---

# <a name="create-a-nodejs-office-add-in-that-uses-single-sign-on-preview"></a>シングル サインオンを使用する Node.js Office アドインを作成する (プレビュー)

ユーザーは、このサインイン プロセスを利用してユーザーを承認する Office および Office Web アドインにサインインできます。こうして承認されたユーザーは、アドインと Microsoft Graph への 2 度目のサインオンの必要がなくなります。概要については、「[Office アドインで SSO を有効化する](sso-in-office-add-ins.md)」を参照してください。

この記事では、Node.js と Express を使用して作成したアドインで、シングル サインオン (SSO) を有効化するプロセスについて手順を追って説明します。 

> [!NOTE]
> ASP.NET ベースのアドインに関する同様の記事については、「[シングル サインオンを使用する ASP.NET Office アドインを作成する](create-sso-office-add-ins-aspnet.md)」を参照してください。

## <a name="prerequisites"></a>前提条件

* [Node および npm](https://nodejs.org/en/)、バージョン 6.9.4 以降

* [Git バッシュ](https://git-scm.com/downloads) (またはその他の Git クライアント)

* TypeScript バージョン 2.2.2 以降

* Office 2016 バージョン 1708、ビルド 8424.nnnn 以降 (「クイック実行」と呼ばれることもある Office 365 のサブスクリプション バージョン)

  このバージョンを入手するには、Office Insider への参加が必要になることがあります。詳細については、「[Office Insider](https://products.office.com/ja-jp/office-insider?tab=tab-1)」を参照してください。

## <a name="set-up-the-starter-project"></a>スタート プロジェクトをセットアップする

1. 「[Office Add-in NodeJS SSO](https://github.com/officedev/office-add-in-nodejs-sso)」にあるリポジトリを複製するかダウンロードします。 

    > [!NOTE]
    > サンプルには 2 つのバージョンがあります。  
    > * **[Before]** フォルダーはスタート プロジェクトです。SSO や承認に直接関連しない UI などの側面は、既に完了しています。この記事で後述する各セクションでは、これを完成させるための手順を順に説明します。 
    > * このサンプルの **[Completed]** バージョンは、この記事の手順を完了したときに得られるアドインと同様のものですが、完成済みのプロジェクトには、この記事のテキストと重複するコード コメントが含まれています。完成済みのバージョンを使用する場合は、この記事の手順をそのまま実行しますが、[Before] を [Completed] に置き換えて、「**クライアント側のコードを作成する**」と「**サーバー側のコードを作成する**」のセクションを省略してください。

2. **[Before]** フォルダー内で Git bash コンソールを開きます。

3. コンソールで `npm install` を入力して、package.json ファイル内のアイテム化されたすべての依存関係をインストールします。

4. コンソールで `npm run build ` を入力して、プロジェクトをビルドします。 

    > [!NOTE]
    > いくつかの使用されていない変数が宣言されているという、ビルド エラーが発生することがあります。これらのエラーは無視してください。これらは、後で追加する一部のコードが見つからないという「Before」バージョンのサンプルの副作用です。

## <a name="register-the-add-in-with-azure-ad-v20-endpoint"></a>Azure AD v2.0 エンドポイントにアドインを登録する

1. [https://apps.dev.microsoft.com](https://apps.dev.microsoft.com) に移動します。 

1. 管理者の資格情報を使用して Office 365 テナントにサインインします。たとえば、MyName@contoso.onmicrosoft.com

1. **[アプリの追加]** をクリックします。

1. ダイアログが表示されたら、アプリ名として「Office-Add-in-NodeJS-SSO」を使用して、**[アプリケーションの作成]** をクリックします。

1. アプリの構成ページが開いたら、**[アプリケーション ID]** をコピーして保存します。これは、この後の手順で使用します。 

    > [!NOTE]
    > この ID は、Office ホスト アプリケーション (たとえば、PowerPoint、Word、Excel) などの別のアプリケーションが、このアプリケーションへの承認されたアクセスを求めるときの「対象ユーザー」値になります。また、そのアプリケーションが Microsoft Graph への承認されたアクセスを求めるときには、このアプリケーションの「クライアント ID」になります。

1. **[アプリケーション シークレット]** セクションで、**[新しいパスワードを生成]** をクリックします。新しいパスワード (「アプリケーション シークレット」とも呼びます) が示されたポップアップ ダイアログが開きます。*このパスワードをすぐにコピーして、アプリケーション ID と共に保存します。*これは、この後の手順で必要になります。その後で、ダイアログを閉じます。

1. **[プラットフォーム]** セクションで、**[プラットフォームの追加]** をクリックします。 

1. 開いたダイアログで、**[Web API]** を選択します。

1. **[アプリケーション ID URI]** が、"api://{App ID GUID}" という形式で生成されています。二重スラッシュと GUID の間に文字列 "localhost:3000" を挿入します。ID 全体は、`api://localhost:3000/{App ID GUID}` のようになります。 

    > [!NOTE]
    > **[アプリケーション ID URI]** の直後の **[スコープ]** 名のドメイン部分は、一致するように自動的に変更されます。 これは `api://localhost:3000/{App ID GUID}/access_as_user` のようになります。

1. この手順と次の手順で、Office アプリケーションにアドインへのアクセス権を付与します。 **[事前承認済みアプリケーション]** セクションで、アドインの Web アプリケーションに対して承認するアプリケーションを特定します。 次のそれぞれの ID を事前承認する必要があります。 1 つの ID を入力するたびに、新しい空のテキスト ボックスが表示されます。 (GUID のみを入力してください。)

    * `d3590ed6-52b3-4102-aeff-aad2292ab01c` (Microsoft Office)
    * `57fb890c-0dab-4253-a5e0-7188c88b2bb4` (Office Online)
    * `bc59ab01-8403-45c6-8796-ac3ef710b3e3` (Office Online) 

1. それぞれの **[アプリケーション ID]** の横の **[スコープ]** ドロップダウンを開いて、`api://localhost:3000/{App ID GUID}/access_as_user` のボックスをオンにします。

1. **[プラットフォーム]** セクションの上部にある **[プラットフォームの追加]** を再度クリックして、**[Web]** を選択します。

1. **[プラットフォーム]** の下側の新しい **[Web]** セクションで、**[リダイレクト URL]** として `https://localhost:3000` を入力します。 

1. **[Microsoft Graph のアクセス許可]** セクションを下にスクロールして、**[委任されたアクセス許可]** サブセクションを表示します。**[追加]** ボタンを使用して、**[アクセス許可の選択]** ダイアログを開きます。

1. ダイアログ ボックスで、次の各アクセス許可のボックスをオンにします。 

    * Files.Read.All
    * profile

    > [!NOTE]
    > `User.Read` アクセス許可は既定でリストされている場合があります。必要でないアクセス許可は依頼しない方がよいため、このアクセス許可のボックスのチェックをオフにしておくことをお勧めします。

1. ダイアログの下側にある **[OK]** をクリックします。

1. 登録ページの下側にある **[保存]** をクリックします。

## <a name="grant-admin-consent-to-the-add-in"></a>アドインに管理者の同意を付与する

> [!NOTE]
> この手順は、アドインの開発時にのみ必要になります。 実際に運用するアドインを AppSource またはアドイン カタログに展開する場合、各ユーザーはそのアドインをインストールする際にそのアドインを個別に信頼します。

1. 次に示す文字列内のプレースホルダー "{application_ID}" は、アドインの登録時にコピーしたアプリケーション ID に置き換えます。

    `https://login.microsoftonline.com/common/adminconsent?client_id={application_ID}&state=12345`

1. その結果の URL をブラウザーのアドレス バーに貼り付けて、その場所に移動します。

1. ダイアログが表示されたら、管理者の資格情報を使用して Office 365 テナントにサインインします。

1. その後で、Microsoft Graph データにアクセスするためのアクセス許可をアドインに付与するように求めるダイアログが表示されます。**[承諾]** をクリックします。 

1. ブラウザー ウィンドウ (タブ) は、アドインの登録時に指定した **[リダイレクト URL]** にリダイレクトされ、アドインが実行中の場合は、アドインのホーム ページがブラウザーで開かれます。アドインが実行中でない場合は、localhost:3000 でリソースが見つからないか開かれていないというエラーが表示されます。*ただし、リダイレクションが試行されたということが、管理者の同意プロセスが正常に完了したことを意味します*。そのため、ホーム ページが表示されたか、このエラーが発生したかにかかわらず、次の手順に進むことができます。

2. ブラウザーのアドレスバーには、GUID 値の付いた "tenant" クエリ パラメーターが表示されます。これは、Office 365 テナントの ID です。この値をコピーして保存します。これは後の手順で使用します。

3. ウィンドウ (タブ) を閉じます。

## <a name="configure-the-add-in"></a>アドインを構成する

1. コード エディターで、src\server.ts ファイルを開きます。先頭近くに、`AuthModule` クラスのコンストラクターの呼び出しがあります。コンストラクターには、値を割り当てる必要がある、文字列のパラメーターがあります。

2. `client_id` プロパティの場合は、アドインの登録時に保存したアプリケーション ID でプレースホルダーの `{client GUID}` を置き換えます。完了すると、単一引用符で囲まれた GUID のみになります。"{}" 文字は取り去る必要があります。

3. `client_secret` プロパティの場合は、アドインの登録時に保存したアプリケーション シークレットでプレースホルダーの `{client secret}` を置き換えます。

4. `audience` プロパティの場合は、アドインの登録時に保存したアプリケーション ID でプレースホルダーの `{audience GUID}` を置き換えます。(`client_id` プロパティに割り当てた値とまったく同じになります)。
  
3. `issuer` プロパティに割り当てた文字列には、プレースホルダーの *{O365 tenant GUID}* があります。これは、前の最後の手順で保存した Office 365 テナント ID で置き換えます。何らかの理由で、まだ ID を取得していない場合は、「[Office 365 テナント ID を検索する](https://support.office.com/ja-jp/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)」に示したいずれかの方法を使用して ID を取得します。完了すると、`issuer` プロパティの値は、次に示すようなものになります。

    `https://login.microsoftonline.com/12345678-1234-1234-1234-123456789012/v2.0`

1. `AuthModule` コンストラクターのその他の値は未変更のままにしておきます。 ファイルを保存して閉じます。

1. プロジェクトのルートにある、アドイン マニフェスト ファイル「Office-Add-in-NodeJS-SSO.xml」を開きます。

1. ファイルの最後までスクロールします。

1. 最後の `</VersionOverrides>` タグの直前に、次に示すマークアップが見つかります。

    ```xml
    <WebApplicationInfo>
      <Id>{application_GUID here}</Id>
      <Resource>api://localhost:3000/{application_GUID here}</Resource>
      <Scopes>
          <Scope>Files.Read.All</Scope>
          <Scope>profile</Scope>
      </Scopes>
    </WebApplicationInfo>
    ```

1. このマークアップ内の*両方の場所の*プレースホルダー "{application_GUID here}" を、アドインの登録時にコピーしたアプリケーション ID に置き換えます (「{」と「}」は ID の一部ではないため、これらを含めないでください)。これは、web.config の ClientID と Audience に使用したものと同じ ID です。

    > [!NOTE]
    > * **[リソース]** の値は、アドインの登録に Web API プラットフォームを追加したときに設定した **[アプリケーション ID URI]** です。
    > * **[範囲]** セクションは、アドインが AppSource から販売された場合に、同意ダイアログ ボックスを生成するためにのみ使用します。

1. ファイルを保存して閉じます。

## <a name="code-the-client-side"></a>クライアント側のコードを作成する

1. **[public]** フォルダー内の program.js ファイルを開きます。これには、一部のコードが既に含まれています。

    * `Office.initialize` メソッドへの割り当てが、`getGraphAccessTokenButton` ボタン クリック イベントへのハンドラーの割り当てになります。
    * `showResult` メソッドは、作業ウィンドウの下側に Microsoft Graph から返されたデータ (またはエラー メッセージ) を表示するものです。
    * `logErrors` メソッドは、エンド ユーザーを対象としていないエラーをコンソールにログ出力するものです。

11. `Office.initialize` への割り当ての下に、次に示すコードを追加します。このコードについては、次の点に注意してください。

    * アドインのエラー処理により、アクセス トークンの取得が別のオプションのセットを使用して自動的に再試行されることがあります。 カウンター変数 `timesGetOneDriveFilesHasRun` とフラグ変数 `triedWithoutForceConsent` および `timesMSGraphErrorReceived` を使用して、失敗するトークン取得の繰り返しからユーザーが抜け出せるようにします。 
    * この後の手順では `getDataWithToken` メソッドを作成しますが、そのメソッドで `forceConsent` というオプションが `false` に設定される点に注意してください。詳細については、次の手順で説明します。

    ```javascript
    var timesGetOneDriveFilesHasRun = 0;
    var triedWithoutForceConsent = false;
    var timesMSGraphErrorReceived = false;

    function getOneDriveFiles() {
        timesGetOneDriveFilesHasRun++;
        triedWithoutForceConsent = true;
        getDataWithToken({ forceConsent: false });
    }   
    ```

1. `getOneDriveFiles` メソッドの下に、次のコードを追加します。このコードについては、次の点に注意してください。

    * `getAccessTokenAsync` は Office.js の新しい API です。これにより、アドインは Office ホスト アプリケーション (Excel、PowerPoint、Word など) に、アドインへのアクセス トークン (Office にサインインしているユーザーのトークン) を要求できるようになります。その Office ホスト アプリケーションが、Azure AD 2.0 エンドポイントにトークンを要求します。アドインの登録時に、アドインに対する Office ホストを事前認証しているため、Azure AD はトークンを送信します。
    * Office にサインインしているユーザーがいない場合、Office ホストはユーザーにサインインを求めるダイアログを表示します。
    * オプションのパラメーター `forceConsent` を `false` に設定すると、ユーザーがアドインを使用するたびに、Office ホストにアドインへのアクセス権を付与するための同意を求めるダイアログが表示されなくなります。 ユーザーが初めてアドインを実行すると、`getAccessTokenAsync` の呼び出しは失敗しますが、この後の手順で追加するエラー処理ロジックにより、`forceConsent` オプションを `true` に設定した再呼び出しが自動的に実行され、ユーザーに同意を求めるダイアログが表示されます。ただし、これは初回時のみ実行されます。
    * `handleClientSideErrors` メソッドは、この後の手順で作成します。

    ```javascript
    function getDataWithToken(options) {
    Office.context.auth.getAccessTokenAsync(options,
        function (result) {
            if (result.status === "succeeded") {
                TODO1: Use the access token to get Microsoft Graph data.
            }
            else {
                handleClientSideErrors(result);
            }
        });
    }
    ```

1. TODO1 を次に示す行に置き換えます。`getData` メソッドとサーバー側の "/api/values" ルートは、この後の手順で作成します。エンドポイントには、相対 URL を使用します。これは、その URL がアドインと同じドメインでホストされている必要があるためです。

    ```javascript
    accessToken = result.value;
    getData("/api/values", accessToken);
    ```

1. `getOneDriveFiles` メソッドの下に、以下を追加します。このコードについては、次の点に注意してください。

    * このメソッドは、特定の Web API エンドポイントを呼び出して、Office ホスト アプリケーションがアドインへのアクセスに使用したものと同じアクセス トークンを渡します。サーバー側では、このアクセス トークンが Microsoft Graph へのアクセス トークンを取得するための「代理 (on-behalf-of)」フローで使用されます。
    * `handleServerSideErrors` メソッドは、この後の手順で作成します。

    ```javascript
    function getData(relativeUrl, accessToken) {
        $.ajax({
            url: relativeUrl,
            headers: { "Authorization": "Bearer " + accessToken },
            type: "GET"
        })
        .done(function (result) {
            showResult(result);
        })
        .fail(function (result) {
            handleServerSideErrors(result);
        }); 
    }
    ```

### <a name="create-the-error-handling-methods"></a>エラー処理のメソッドを作成する

1. `getData` メソッドの下に、次のメソッドを追加します。 このメソッドは、Office ホストがアドインの Web サービスへのアクセス トークンを取得できないときに、アドインのクライアントでエラーを処理します。 こうしたエラーはエラー コードで報告されるため、このメソッドでは `switch` ステートメントを使用してエラーを識別します。

    ```javascript
    function handleClientSideErrors(result) {

        switch (result.error.code) {
    
            // TODO2: Handle the case where user is not logged in, or the user cancelled, without responding, a
            //        prompt to provide a 2nd authentication factor. 
    
            // TODO3: Handle the case where the user's sign-in or consent was aborted.
    
            // TODO4: Handle the case where the user is logged in with an account that is neither work or school, 
            //        nor Micrososoft Account.
    
            // TODO5: Handle an unspecified error from the Office host.
    
            // TODO6: Handle the case where the Office host cannot get an access token to the add-ins 
            //        web service/application.
    
            // TODO7: Handle the case where the user tiggered an operation that calls `getAccessTokenAsync` 
            //        before a previous call of it completed.
    
            // TODO8: Handle the case where the add-in does not support forcing consent.
    
            // TODO9: Log all other client errors.
        }
    }
    ```

1. `TODO2` を次のコードに置き換えます。 エラー 13001 は、ユーザーがログインしていない場合、または 2 番目の認証要素の指定を求めるダイアログに応答しないでキャンセルした場合に発生します。 どちらの場合も、このコードでは `getDataWithToken` メソッドを再実行して、サインインを求めるダイアログの表示を強制するようにオプションを設定します。

    ```javascript
    case 13001:
        getDataWithToken({ forceAddAccount: true });
        break;
    ```

1. `TODO3` を次のコードに置き換えます。 エラー 13002 は、ユーザーのサインインまたは同意が中断された場合に発生します。 ユーザーに対して 1 回だけ再試行を求めます。

    ```javascript
    case 13002:
        if (timesGetOneDriveFilesHasRun < 2) {
            showResult(['Your sign-in or consent was aborted before completion. Please try that operation again.']);
        } else {
            logError(result);
        }          
        break; 
    ```

1. `TODO4` を次のコードに置き換えます。 エラー 13003 は、ユーザーが職場または学校アカウントと、Micrososoft アカウントのどちらでもないアカウントでログインしている場合に発生します。 ユーザーに対して、サインアウトしてからサポートされているアカウントの種類で再度サインインするように求めます。

    ```javascript
    case 13003: 
        showResult(['Please sign out of Office and sign in again with a work or school account, or Microsoft Account. Other kinds of accounts, like corporate domain accounts do not work.']);
        break;   
    ```

    > [!NOTE]
    > エラー 13004 と 13005 は、開発時にのみ発生するため、このメソッドでは処理しません。 これらは、ランタイム コードで修正できるものではなく、エンド ユーザーに報告しても意味がありません。

1. `TODO5` を次のコードと置き換えます。エラー 13006 は、Office ホストで未指定のエラーがある場合に発生します。ホストが不安定な状態にあることを示している可能性があります。ユーザーに Office の再起動を求めます。

    ```javascript
    case 13006:
        showResult(['Please save your work, sign out of Office, close all Office applications, and restart this Office application.']);
        break;        
    ```

1. `TODO6` を次のコードに置き換えます。 エラー 13007 は、Office ホストの AAD との相互作用に問題があり、ホストがアドイン Web サービス/アプリケーションへのアクセス トークンを取得できない場合に発生します。 ネットワークに一時的な問題が発生している可能性があります。 しばらく待ってから再試行するようにユーザーに求めます。

    ```javascript
    case 13007:
        showResult(['That operation cannot be done at this time. Please try again later.']);
        break;      
    ```

1. `TODO7` を次のコードと置き換えます。エラー 13008 は、前回の `getAccessTokenAsync` の呼び出しが完了する前に、それを呼び出す操作をユーザーがトリガーしたときに発生します。

    ```javascript
    case 13008:
        showResult(['Please try that operation again after the current operation has finished.']);
        break;
    ```      

1. `TODO8` を次のコードに置き換えます。 エラー 13009 は、アドインが強制的な同意をサポートしていないときに、`forceConsent` オプションを `true` に設定して `getAccessTokenAsync` を呼び出した場合に発生します。 通常、この場合は、コードによって同意オプションを `false` に設定して自動的に `getAccessTokenAsync` を再実行する必要があります。 ただし、`forceConsent` を `true` に設定してメソッドを呼び出すこと自体が、そのオプションを `false` に設定したメソッドの呼び出しで発生したエラーに対する自動的な応答の場合もあります。 その場合は、コードで再試行するのではなく、ユーザーにサインアウトしてから再度サインインするように通知する必要があります。

    ```javascript
    case 13009:
        if (triedWithoutForceConsent) {
            showResult(['Please sign out of Office and sign in again with a work or school account, or Microsoft Account.']);
        } else {
            getDataWithToken({ forceConsent: false });
        }
        break;
    ```      
    
1. `TODO9` を次のコードに置き換えます。

    ```javascript
    default:
        logError(result);
        break;
    ```  

1. `handleClientSideErrors` メソッドの下に、次のメソッドを追加します。このメソッドは、代理 (on-behalf-of) フローの実行時または Microsoft Graph からのデータの取得時の問題により、アドインの Web サービスで発生したエラーを処理します。

    ```javascript
    function handleServerSideErrors(result) {
    
        // TODO10: Handle the case where AAD asks for an additional form of authentication.

        // TODO11: Handle the case where consent has not been granted, or has been revoked.

        // TODO12: Handle the case where an invalid scope (permission) was used in the on-behalf-of flow

        // TODO13: Handle the case where the token that the add-in's client-side sends to it's 
        //         server-side is not valid because it is missing `access_as_user` scope (permission).

        // TODO14: Handle the case where the token sent to Microsoft Graph in the request for 
        //         data is expired or invalid.

        // TODO15: Log all other server errors.
    }
    ```

1. `TODO10` を次のコードに置き換えます。このコードの注意点は次のとおりです。

    * ユーザーがパスワードだけで Office にサインオンできる場合でも、Microsoft Graph のいくつかのターゲット (たとえば、OneDrive) にアクセスするために、追加の認証要素を提供するようにユーザーに要求する、Azure Active Directory の構成があります。その場合、AAD は `Claims` プロパティを含むエラー 50076 で応答を送信します。 
    * Office ホストは、`authChallenge` オプションとして **Claims** 値を使用して新しいトークンを取得します。 これにより、認証のすべての必要なフォームをユーザーに表示するように AAD に指示します。 

    ```javascript
    if (result.responseJSON.error.innerError
            && result.responseJSON.error.innerError.error_codes
            && result.responseJSON.error.innerError.error_codes[0] === 50076){
        getDataWithToken({ authChallenge: result.responseJSON.error.innerError.claims });
    }
    ```

1. `TODO11` を次のコードに置き換えます (*前の手順で追加したコードの最後にある右波かっこのすぐ下*)。このコードの注意点は次のとおりです。

    * エラー 65001 は、1 つ以上のアクセス許可について Microsoft Graph にアクセスするための同意が与えられていない (または取り消されている) ことを意味します。 
    * アドインでは、`forceConsent` オプションを `true` に設定して新しいトークンを取得する必要があります。

    ```javascript
    else if (result.responseJSON.error.innerError
            && result.responseJSON.error.innerError.error_codes
            && result.responseJSON.error.innerError.error_codes[0] === 65001){
        showResult(['Please grant consent to this add-in to access your Microsoft Graph data.']);        
        /*
            THE FORCE CONSENT OPTION IS NOT AVAILABLE IN DURING PREVIEW. WHEN SSO FOR
            OFFICE ADD-INS IS RELEASED, REMOVE THE showResult LINE ABOVE AND UNCOMMENT
            THE FOLLOWING LINE.
        */
        // getDataWithToken({ forceConsent: true });
    }
    ```

1. `TODO12` を次のコードに置き換えます (*前の手順で追加したコードの最後にある右波かっこのすぐ下*)。このコードの注意点は次のとおりです。

    * エラー 70011 は、無効なスコープ (アクセス許可) が要求されたことを示します。 アドインでは、エラーを報告する必要があります。
    * コードでは、その他のエラーを AAD エラー番号と共に記録します。

    ```javascript
    else if (result.responseJSON.error.innerError
            && result.responseJSON.error.innerError.error_codes
            && result.responseJSON.error.innerError.error_codes[0] === 70011){
        showResult(['The add-in is asking for a type of permission that is not recognized.']);
    }
    ```

1. `TODO13` を次のコードに置き換えます (*前の手順で追加したコードの最後にある右波かっこのすぐ下*)。このコードの注意点は次のとおりです。

    * この後の手順で作成するサーバー側のコードでは、アドインのクライアントが AAD に送信して代理 (on-behalf-of) フローで使用されるアクセス トークンに `access_as_user` スコープ (アクセス許可) が含まれていない場合に、末尾が `... expected access_as_user` のメッセージを送信します。
    * アドインでは、エラーを報告する必要があります。

    ```javascript
    else if (result.responseJSON.error.name
            && result.responseJSON.error.name.indexOf('expected access_as_user') !== -1){
        showResult(['Microsoft Office does not have permission to get Microsoft Graph data on behalf of the current user.']);
    }
    ```

1. `TODO14` を次のコードに置き換えます (*前の手順で追加したコードの最後にある右波かっこのすぐ下*)。このコードの注意点は次のとおりです。

    * 有効期限切れのトークンや無効なトークンが Microsoft Graph に送信される可能性はほとんどありませんが、そのような事態が発生した場合は、この後の手順で作成するサーバー側のコードは、文字列 `Microsoft Graph error` で終了します。
    * この場合、アドインは `timesGetOneDriveFilesHasRun` カウンター変数と `timesGetOneDriveFilesHasRun` フラグ変数をリセットしてから、ボタン ハンドラー メソッドを再呼び出しすることで、認証プロセス全体を最初から開始する必要があります。 ただし、これは 1 回のみ実行する必要があります。 この事態が再度発生した場合は、単にエラーを記録するようにします。
    * コードでは、この事態が連続して 2 回発生した場合にエラーを記録します。

    ```javascript
    else if (result.responseJSON.error.name
            && result.responseJSON.error.name.indexOf('Microsoft Graph error') !== -1) {
        if (!timesMSGraphErrorReceived) {
            timesMSGraphErrorReceived = true;
            timesGetOneDriveFilesHasRun = 0;
            triedWithoutForceConsent = false;
            getOneDriveFiles();
        } else {
            logError(result);
        }        
    }
    ```

1. `TODO15` を次のコードに置き換えます (*前の手順で追加したコードの最後にある右波かっこのすぐ下*)。

    ```javascript
    else {
        logError(result);
    }
    ```

## <a name="code-the-server-side"></a>サーバー側のコードを作成する

変更の必要があるサーバー側のファイルは 2 つあります。 
- src\auth.js では、承認のヘルパー関数を提供します。これには、各種の承認フローで使用される汎用のメンバーが既に含まれています。これには、「代理」フローを実装するための関数を追加する必要があります。
- src\server.js ファイルには、サーバーと express ミドルウェアを実行するために必要な基本的なメンバーが含まれています。これには、ホーム ページと Microsoft Graph データを取得するための Web API を提供する関数を追加する必要があります。

### <a name="create-a-method-to-exchange-tokens"></a>トークンを交換するためのメソッドを作成する

1. \src\auth.ts ファイルを開きます。`AuthModule` クラスに、次に示すメソッドを追加します。このコードについては、次の点に注意してください。

    * `jwt` パラメーターは、アプリケーションへのアクセス トークンです。「代理 (on-behalf-of)」フローでは、これはリソースへのアクセス トークンの AAD と交換されます。
    * scopes パラメーターには既定の値がありますが、このサンプルではコード呼び出しによってオーバーライドしています。
    * resource パラメーターは省略可能です。STS が AAD V 2.0 エンドポイントの場合は使用しないでください。V 2.0 エンドポイントは scopes から resource を推測します。resource が HTTP 要求で送信されるとエラーを返します。 
    * `catch` ブロック内で例外をスローしても、即時の "500 Internal Server Error" がクライアントに送信されることは*ありません*。 server.js ファイルでコードを呼び出すことで、この例外をキャッチしてから、その例外をクライアントに送信するエラー メッセージに変換します。

    
        ```javascript
        private async exchangeForToken(jwt: string, scopes: string[] = ['openid'], resource?: string) {
            try {
                // TODO3: Construct the parameters that will be sent in the body of the 
                //        HTTP Request to the STS that starts the "on behalf of" flow.
                // TODO4: Send the request to the STS.
                // TODO5: Catch errors from the STS and relay them to the client.
                // TODO6: Process the response and persist the access token to resource.
            }
            catch (exception) {
                throw new UnauthorizedError('Unable to obtain an access token to the resource' 
                                            + JSON.stringify(exception), 
                                            exception);
            }
        }
        ```

2. `TODO3` を次のコードに置き換えます。このコードの注意点は次のとおりです。
    * 「代理」ワークフローをサポートする STS は、HTTP 要求の本文に特定のプロパティ/値ペアが含まれていることを期待します。このコードは、要求の本文になるオブジェクトを構築します。 
    * resource プロパティは、リソースがメソッドに渡された場合にのみ本文に追加されます。

        ```javascript
        const v2Params = {
                client_id: this.clientId,
                client_secret: this.clientSecret,
                grant_type: 'urn:ietf:params:oauth:grant-type:jwt-bearer',
                assertion: jwt,
                requested_token_use: 'on_behalf_of',
                scope: scopes.join(' ')
            };
            let finalParams = {};
            if (resource) {
                // In JavaScript we could just add the resource property to the v2Params
                // object, but that won't compile in TypeScript.
                let v1Params  = { resource: resource };  
                for(var key in v2Params) { v1Params[key] = v2Params[key]; }
                finalParams = v1Params;
            } else {
                finalParams = v2Params;
            } 
        ```

3. `TODO4` を次に示すコードに置き換えます。このコードでは、HTTP 要求を STS のトークン エンドポイントに送信します。

    ```javascript
    const res = await fetch(`${this.stsDomain}/${this.tenant}/${this.tokenURLsegment}`, {
        method: 'POST',
        body: form(finalParams),
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/x-www-form-urlencoded'
        }
    }); 
    ```

4. `TODO5` を次のコードに置き換えます。 例外をスローしても、即時の "500 Internal Server Error" がクライアントに送信*されない*点に注意してください。 server.js ファイルでコードを呼び出すことで、この例外をキャッチしてから、その例外をクライアントに送信するエラー メッセージに変換します。

    ```javascript
     if (res.status !== 200) {
        const exception = await res.json();
        throw exception;                
    } 
    ```

5. `TODO6` を次に示すコードに置き換えます。このコードはリソースへのアクセス トークンを永続化して、有効期限になると、そのアクセス トークンを返します。コードを呼び出すことで、期限切れになっていないリソースへのアクセス トークンが再使用されるため、STS への不要な呼び出しを回避できます。この動作のしくみは、次のセクションで説明します。

    ```javascript  
    const json = await res.json();
    const resourceToken = json['access_token'];
    ServerStorage.persist('ResourceToken', resourceToken);
    const expiresIn = json['expires_in'];  // seconds until token expires.
    const resourceTokenExpiresAt = moment().add(expiresIn, 'seconds');
    ServerStorage.persist('ResourceTokenExpiresAt', resourceTokenExpiresAt);
    return resourceToken; 
    ```

6. ファイルを閉じないで保存します。

### <a name="create-a-method-to-get-access-to-the-resource-using-the-on-behalf-of-flow"></a>「代理」ワークフローを使用してリソースにアクセスするメソッドを作成する

1. 引き続き src/auth.ts で、次に示すメソッドを `AuthModule` クラスに追加します。このコードについては、以下に注意してください。

    * `exchangeForToken` メソッドへのパラメーターに関する上記のコメントは、このメソッドのパラメーターにも当てはまります。
    * このメソッドでは、最初にリソースへの有効期限が切れていない (次の 1 分まで有効期限が続く) アクセス トークンについて永続ストレージをチェックします。これは、直前のセクションで作成した `exchangeForToken` メソッドを呼び出します (そのメソッドが必要になる場合)。

    ```javascript
    async acquireTokenOnBehalfOf(jwt: string, scopes: string[] = ['openid'], resource?: string) {
        const resourceTokenExpirationTime = ServerStorage.retrieve('ResourceTokenExpiresAt');
        if (moment().add(1, 'minute').diff(resourceTokenExpirationTime) < 1 ) {
            return ServerStorage.retrieve('ResourceToken');
        } else if (resource) {
            return this.exchangeForToken(jwt, scopes, resource);
        } else {
            return this.exchangeForToken(jwt, scopes);
        }
    } 
    ```

2. ファイルを保存して閉じます。

### <a name="create-the-endpoints-that-will-serve-the-add-ins-home-page-and-data"></a>アドインのホーム ページとデータを提供するエンドポイントを作成する

1. src\server.ts ファイルを開きます。 

2. 次に示すメソッドをファイルの末尾に追加します。このメソッドにより、アドインのホーム ページを提供します。アドイン マニフェストで、ホーム ページの URL を指定します。

    ```javascript
    app.get('/index.html', handler(async (req, res) => {
        return res.sendfile('index.html');
    })); 
    ```

3. ファイルの末尾に次のメソッドを追加します。このメソッドにより、`onedriveitems` API に対する要求を処理します。
    ```javascript
    app.get('/api/onedriveitems', handler(async (req, res) => {
        // TODO7: Initialize the AuthModule object and validate the access token 
        //        that the client-side received from the Office host.
        // TODO8: Get a token to Microsoft Graph from either persistent storage 
        //        or the "on behalf of" flow.
        // TODO9: Use the token to get data from Microsoft Graph.
        // TODO10: Relay any errors from Microsoft Graph to the client.
        // TODO11: Send to the client only the data that it actually needs.
    })); 
    ```

4. `TODO7` を次に示すコードに置き換えます。このコードでは、Office ホスト アプリケーションから受け取ったアクセス トークンを検証します。`verifyJWT` メソッドは、src\auth.ts ファイルで定義されています。これは、常に対象ユーザーと発行者を検証します。省略可能なパラメーターを使用して、アクセス トークンのスコープが `access_as_user` であることを検証する必要もあることを指定します。これは、「代理 (on-behalf-of)」フローによって Microsoft Graph へのアクセストークンを取得するために、ユーザーと Office ホストが必要とする唯一のアクセス許可です。 

    ```javascript
    await auth.initialize();
    const { jwt } = auth.verifyJWT(req, { scp: 'access_as_user' }); 
    ```

    > [!NOTE]
    > `access_as_user` スコープのみを使用して、Office アドインの代理 (on-behalf-of) フローを処理する API を承認する必要があります。サービス内の他の API は、独自のスコープ要件が必要です。これにより、Office が取得するトークンでアクセスできるものが制限されます。

5. `TODO8` を次のコードに置き換えます。このコードについては、次の点に注意してください。

    * `acquireTokenOnBehalfOf` の呼び出しには、resource パラメーターは含まれません。これは、resource プロパティをサポートしていない AAD V2.0 エンドポイントで `AuthModule` オブジェクト (`auth`) を作成したためです。
    * この呼び出しの 2 番目のパラメーターでは、OneDrive 上のユーザーのファイルとフォルダーのリストを取得するために、アドインが必要とするアクセス許可を指定します。 (`profile` アクセス許可は要求されません。これは、このアクセス許可が、Microsoft Graph へのアクセス トークン用のトークンでやり取りしているときではなく、Office ホストがアドインへのアクセス トークンを取得するときにだけ必要であるためです。)


    ```javascript
    const graphToken = await auth.acquireTokenOnBehalfOf(jwt, ['Files.Read.All']);
    ```

6. `TODO9` を次のコードに置き換えます。このコードについては、次の点に注意してください。

    * MSGraphHelper クラスは、src\msgraph-helper.ts で定義されています。 
    * 返す必要があるデータが最小になるように、name プロパティと最初の 3 つのアイテムのみが必要なことを指定しています。

    `const graphData = await MSGraphHelper.getGraphData(graphToken, "/me/drive/root/children", "?$select=name&$top=3");`

7. `TODO10` を次のコードに置き換えます。 このコードでは、Microsoft Graph からの "401 Unauthorized" エラーを処理します。このエラーは、期限切れのトークンまたは無効なトークンを表している可能性があります。 この事態は、トークンの永続化ロジックによって防止されているため、発生する可能性はほとんどありません  (前述のセクション「**「代理 (on-behalf-of) 」ワークフローを使用してリソースにアクセスするメソッドを作成する**」を参照してください)。この事態が発生した場合、このコードではエラー名に "Microsoft Graph error" を使用してクライアントにエラーを中継します  (前述の手順で program.js ファイルに作成した `handleClientSideErrors` メソッドを参照してください)。この後手順で ODataHelper.js ファイルに追加するコードは、Microsoft Graph からのエラーの処理に役立ちます。

    ```javascript
    if (graphData.code) {
        if (graphData.code === 401) {
            throw new UnauthorizedError('Microsoft Graph error', graphData);
        }
    }
    ```


1. `TODO11` を次に示すコードに置き換えます。Microsoft Graph は、`name` プロパティのみを要求した場合でも、アイテムごとに、いくつかの OData メタデータと 1 つの **eTag** プロパティを返す点に注意してください。このコードでは、アイテムの名前のみをクライアントに送信します。

    ```javascript
    const itemNames: string[] = [];
    const oneDriveItems: string[] = graphData['value'];
    for (let item of oneDriveItems){
        itemNames.push(item['name']);
    }
    return res.json(itemNames);
    ```

8. ファイルを保存して閉じます。

### <a name="add-response-handling-to-the-odatahelper"></a>ODataHelper に応答の処理を追加する

1. ファイル src\odata-helper.ts を開きます。 このファイルは、ほとんど完成しています。 要求の「終了」イベントを処理するコールバックの本文が欠落しています。 `TODO` を次のコードに置き換えます。 このコードの注意点は次のとおりです。

    * OData エンドポイントからの応答は、エラーである可能性があります。たとえば、エンドポイントがアクセス トークンを必要としていて、そのトークンが無効または有効期限切れの場合は 401 になります。 ただし、エラー メッセージは `https.get` の呼び出しでのエラーではなく*メッセージ*であるため、`https.get` の最後の行 `on('error', reject)` はトリガーされません。 そのため、コードでは、成功 (200) とエラー メッセージを区別して、要求された OData またはエラー情報のどちらかを含む JSON オブジェクトを呼び出し元に送信します。


    ```javascript
    var error;
    if (response.statusCode === 200) {
        // TODO1: Return the data to the caller and resolve the Promise.
    } else {
       // TODO2: Return an error object to the caller and resolve the Promise.
    }
    ```

1.  `TODO1` を次のコードと置き換えます。このコードでは、データが JSON として返されることを前提としています。

    ```javascript
    let parsedBody = JSON.parse(body);
    resolve(parsedBody);
    ```

1.  `TODO2` を次のコードに置き換えます。このコードの注意点は次のとおりです。

    * OData ソースからのエラー応答には、常に statusCode が含まれています。また、通常は statusMessage が含まれています。 また、一部の OData ソースは、詳細な情報 (内部のコードやメッセージ、より具体的なコードやメッセージなど) を含む error プロパティも本文に追加します。
    * Promise オブジェクトは解決されます。拒否されません。 `https.get` は、Web サービスがサーバー間の OData エンドポイントを呼び出すときに実行されます。 ただし、その呼び出しは、クライアントから Web サービスの Web API への呼び出しのコンテキストで行われます。 クライアントから Web サービスへの「外部」の要求は、「内部」の要求が拒否されると完了できなくなります。 さらに、`http.get` の呼び出し元が OData エンドポイントからクライアントにエラーを中継する必要がある場合は、カスタムの `Error` オブジェクトを含む要求も解決する必要があります。

    ```javascript
    error = new Error();
    error.code = response.statusCode;
    error.message = response.statusMessage;
    
    // The error body sometimes includes an empty space
    // before the first character, remove it or it causes an error.
    body = body.trim();
    error.bodyCode = JSON.parse(body).error.code;
    error.bodyMessage = JSON.parse(body).error.message;
    resolve(error);
    ```

1. ファイルを保存して閉じます。

## <a name="deploy-the-add-in"></a>アドインを展開する

次に、Office がアドインを検索する場所を認識できるようにする必要があります。

1. ネットワーク共有を作成するか、[フォルダーをネットワークに共有します](https://technet.microsoft.com/ja-jp/library/cc770880.aspx)。

2. プロジェクトのルートから、Office-Add-in-NodeJS-SSO.xml マニフェスト ファイルのコピーを共有フォルダーに配置します。

3. PowerPoint を起動して、ドキュメントを開きます。

4. **[ファイル]** タブを選択して、**[オプション]** を選択します。

5. [**セキュリティ センター**] を選択し、[**セキュリティ センターの設定**] ボタンを選択します。

6. **[信頼されているアドイン カタログ]** を選択します。

7. **[カタログの URL]** フィールドに、Office-Add-in-NodeJS-SSO.xml があるフォルダー共有へのネットワーク パスを入力して、**[カタログの追加]** を選択します。

8. **[メニューに表示する]** チェック ボックスをオンにして、**[OK]** を選択します。

9. これらの設定は Microsoft Office を次回起動したときに適用されることを示すメッセージが表示されます。PowerPoint を終了します。

## <a name="build-and-run-the-project"></a>プロジェクトのビルドと実行

プロジェクトのビルドと実行には 2 つの方法があり、Visual Studio Code を使用しているかどうかによって決まります。どちらの方法でも、プロジェクトをビルドして、コードに変更を加えたときには自動的に再ビルドしてから再実行します。

1. Visual Studio Code を使用していない場合: 
 1. ノード ターミナルを開いて、プロジェクトのルート フォルダーに移動します。
 2. ターミナルで、「**npm run build**」と入力します。 
 3. 2 番目のノード ターミナルを開いて、プロジェクトのルート フォルダーに移動します。
 4. ターミナルで、「**npm run start**」と入力します。

2. VS Code を使用している場合:
 1. VS Code でプロジェクトを開きます。
 2. CTRL + SHIFT + B を押して、プロジェクトをビルドします。
 3. F5 を押して、デバッグ セッションでプロジェクトを実行します。


## <a name="add-the-add-in-to-an-office-document"></a>Office ドキュメントにアドインを追加する

1. PowerPoint を再起動して、プレゼンテーションを開くか作成します。 

2. PowerPoint の **[開発]** タブで、**[個人用アドイン]** を選択します。

3. **[共有フォルダー]** タブを選択します。

4. **[SSO NodeJS Sample]** を選択して、**[OK]** を選択します。

5. **[ホーム]** リボンに、**[SSO NodeJS]** という新しいグループが表示され、**[アドインの表示]** というラベルの付いたボタンとアイコンが含まれています。 

## <a name="test-the-add-in"></a>アドインをテストする

1. 結果を確認できるように、OneDrive 内にファイルがいくつかあることを確認します。

2. **[アドインの表示]** ボタンをクリックして、アドインを開きます。

2. [ようこそ] ページでアドインが開きます。**[OneDrive からファイルを取得]** ボタンをクリックします。

2. Office にサインインしている場合は、このボタンの下に OneDrive にあるファイルとフォルダーのリストが表示されます。これは、初回実行時には 15 秒以上かかることがあります。

3. Office にサインインしていない場合は、ポップアップが表示され、サインインするように求められます。サインインが完了すると、数秒後にファイルとフォルダーが表示されます。*2 回目にボタンをクリックする必要はありません。*

> [!NOTE]
> 以前に別の ID で Office にサインオンしていて、そのときに開いたいくつかの Office アプリケーションが引き続き開いている場合、Office がその ID を確実に変更するとは限りません (PowerPoint で ID が変更済みのように表示されている場合でも)。 このような場合は、Microsoft Graph への呼び出しが失敗するか、以前の ID からのデータが返される可能性があります。 これを防止するには、必ず*他のすべての Office アプリケーションを閉じて*から、**[OneDrive からファイルを取得]** を押します。