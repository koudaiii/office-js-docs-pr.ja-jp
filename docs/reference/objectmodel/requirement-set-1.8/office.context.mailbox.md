---
title: Office. メールボックス要件セット1.8
description: ''
ms.date: 10/31/2019
localization_priority: Normal
ms.openlocfilehash: 3f6d639cdf8bdff6f2df365622f58eba1c4b38e0
ms.sourcegitcommit: e989096f3d19761bf8477c585cde20b3f8e0b90d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "37902188"
---
# <a name="mailbox"></a>mailbox

### <a name="officeofficemdcontextofficecontextmdmailbox"></a>[Office](Office.md)[.context](Office.context.md).mailbox

Microsoft Outlook の Outlook アドイン オブジェクト モデルへのアクセスを提供します。

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="members-and-methods"></a>メンバーとメソッド

| メンバー | 種類 |
|--------|------|
| [ewsUrl](#ewsurl-string) | メンバー |
| [masterCategories](#mastercategories-mastercategories) | メンバー |
| [restUrl](#resturl-string) | メンバー |
| [addHandlerAsync](#addhandlerasynceventtype-handler-options-callback) | メソッド |
| [convertToEwsId](#converttoewsiditemid-restversion--string) | メソッド |
| [convertToLocalClientTime](#converttolocalclienttimetimevalue--localclienttime) | メソッド |
| [convertToRestId](#converttorestiditemid-restversion--string) | メソッド |
| [convertToUtcClientTime](#converttoutcclienttimeinput--date) | メソッド |
| [displayAppointmentForm](#displayappointmentformitemid) | メソッド |
| [displayMessageForm](#displaymessageformitemid) | メソッド |
| [displayNewAppointmentForm](#displaynewappointmentformparameters) | メソッド |
| [displayNewMessageForm](#displaynewmessageformparameters) | メソッド |
| [getCallbackTokenAsync](#getcallbacktokenasyncoptions-callback) | メソッド |
| [getCallbackTokenAsync](#getcallbacktokenasynccallback-usercontext) | メソッド |
| [getUserIdentityTokenAsync](#getuseridentitytokenasynccallback-usercontext) | メソッド |
| [makeEwsRequestAsync](#makeewsrequestasyncdata-callback-usercontext) | メソッド |
| [removeHandlerAsync](#removehandlerasynceventtype-options-callback) | メソッド |

### <a name="namespaces"></a>名前空間

[diagnostics](Office.context.mailbox.diagnostics.md):Outlook アドインに診断情報を提供します。

[item](Office.context.mailbox.item.md):Outlook アドインのメッセージや予定にアクセスするためのメソッドとプロパティを提供します。

[userProfile](Office.context.mailbox.userProfile.md):Outlook アドインのユーザーに関する情報を提供します。

### <a name="members"></a>Members

#### <a name="ewsurl-string"></a>ewsUrl: String

このメール アカウントの Exchange Web サービス (EWS) エンドポイントの URL を取得します。読み取りモードのみです。

> [!NOTE]
> このメンバーは、Outlook on iOS または Android ではサポートされていません。


  `ewsUrl` 値は、リモート サービスで、ユーザーのメールボックスに EWS 呼び出しを行うために使うことができます。たとえば、[選択したアイテムから添付ファイルを取得する](/outlook/add-ins/get-attachments-of-an-outlook-item)ためにリモート サービスを作成できます。

アプリが閲覧モードで `ewsUrl` メンバーを呼び出すには、アプリのマニフェスト内に **ReadItem** アクセス許可が指定されている必要があります。

新規作成モードでは、[`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) メソッドを呼び出してから、`ewsUrl` メンバーを使用する必要があります。アプリには、`saveAsync` メソッドを呼び出す **ReadWriteItem** アクセス許可が必要です。

##### <a name="type"></a>型

*   String

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

<br>

---
---

#### <a name="mastercategories-mastercategoriesjavascriptapioutlookofficemastercategoriesviewoutlook-js-18"></a>masterCategories: [Mastercategories](/javascript/api/outlook/office.mastercategories?view=outlook-js-1.8)

このメールボックスのカテゴリマスターリストを管理するためのメソッドを提供するオブジェクトを取得します。

> [!NOTE]
> このメンバーは、Outlook on iOS または Android ではサポートされていません。

##### <a name="type"></a>種類

*   [MasterCategories](/javascript/api/outlook/office.mastercategories?view=outlook-js-1.8)

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.8 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadWriteMailbox |
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧 |

##### <a name="example"></a>例

この例では、このメールボックスのカテゴリマスターリストを取得します。

```js
Office.context.mailbox.masterCategories.getAsync(function (asyncResult) {
  if (asyncResult.status === Office.AsyncResultStatus.Failed) {
    console.log("Action failed with error: " + asyncResult.error.message);
  } else {
    console.log("Master categories: " + JSON.stringify(asyncResult.value));
  }
});
```

<br>

---
---

#### <a name="resturl-string"></a>restUrl: String

この電子メール アカウントの REST エンドポイントの URL を取得します。

`restUrl` 値は、ユーザーのメールボックスに [REST API](/outlook/rest/) 呼び出しを行うために使用できます。

アプリが閲覧モードで `restUrl` メンバーを呼び出すには、アプリのマニフェスト内に **ReadItem** アクセス許可が指定されている必要があります。

新規作成モードでは、[`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) メソッドを呼び出してから、`restUrl` メンバーを使用する必要があります。アプリには、`saveAsync` メソッドを呼び出す **ReadWriteItem** アクセス許可が必要です。

##### <a name="type"></a>型

*   String

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

### <a name="methods"></a>メソッド

#### <a name="addhandlerasynceventtype-handler-options-callback"></a>addHandlerAsync(eventType, handler, [options], [callback])

サポートされているイベントのイベント ハンドラーを追加します。

現在、サポートされている`Office.EventType.ItemChanged`イベント`Office.EventType.OfficeThemeChanged`の種類はおよびです。

##### <a name="parameters"></a>パラメーター

| 名前 | 種類 | 属性 | 説明 |
|---|---|---|---|
| `eventType` | [Office.EventType](office.md#eventtype-string) || ハンドラーを呼び出す必要のあるイベント。 |
| `handler` | Function || イベントを処理する関数。関数は、オブジェクト リテラルである単一パラメーターを受け入れる必要があります。パラメーターの `type` プロパティは、`addHandlerAsync` に渡される `eventType` パラメーターと一致します。 |
| `options` | Object | &lt;オプション&gt; | 次のプロパティのうち 1 つ以上を含むオブジェクト リテラル。 |
| `options.asyncContext` | オブジェクト | &lt;省略可能&gt; | 開発者は、コールバック メソッドでアクセスしたい任意のオブジェクトを提供できます。 |
| `callback` | function| &lt;optional&gt;|メソッドが完了すると、`callback` パラメーターに渡された関数が、[`asyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `AsyncResult` で呼び出されます。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem |
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="example"></a>例

```js
Office.initialize = function (reason) {
  $(document).ready(function () {
    Office.context.mailbox.addHandlerAsync(Office.EventType.ItemChanged, loadNewItem, function (result) {
      if (result.status === Office.AsyncResultStatus.Failed) {
        // Handle error.
      }
    });
  });
};

function loadNewItem(eventArgs) {
  // Load the properties of the newly selected item.
  loadProps(Office.context.mailbox.item);
}
```

<br>

---
---

#### <a name="converttoewsiditemid-restversion--string"></a>convertToEwsId(itemId, restVersion) → {String}

REST 形式のアイテム ID を EWS 形式に変換します。

> [!NOTE]
> このメソッドは、Outlook on iOS または Android ではサポートされていません。

REST API ([Outlook Mail API](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) や [Microsoft Graph](https://graph.microsoft.io/) など) で取得されたアイテム ID は、Exchange Web サービス (EWS) に使用される形式とは異なる形式を使用します。`convertToEwsId` メソッドは、REST 形式の ID を EWS 用の適切な形式に変換します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`itemId`| String|Outlook REST API 形式のアイテム ID|
|`restVersion`| [Office.MailboxEnums.RestVersion](/javascript/api/outlook/office.mailboxenums.restversion?view=outlook-js-1.8)|アイテム ID の取得に使用された Outlook REST API のバージョンを示す値。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.3|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="returns"></a>戻り値:

型:String

##### <a name="example"></a>例

```js
// Get an item's ID from a REST API.
var restId = 'AAMkAGVlOTZjNTM3LW...';

// Treat restId as coming from the v2.0 version of the Outlook Mail API.
var ewsId = Office.context.mailbox.convertToEwsId(restId, Office.MailboxEnums.RestVersion.v2_0);
```

<br>

---
---

#### <a name="converttolocalclienttimetimevalue--localclienttimejavascriptapioutlookofficelocalclienttimeviewoutlook-js-18"></a>convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)}

クライアントのローカル時間で時間情報が含まれている辞書を取得します。

Outlook on the web または Outlook デスクトップのメールアプリでは、日付と時刻に異なるタイムゾーンを使用できます。Outlook デスクトップは、クライアント コンピューターのタイム ゾーンを使用します。Outlook on the web は、Exchange 管理センター (EAC) で設定されたタイム ゾーンを使用します。日付と時刻の値は、ユーザー インターフェイスに表示される値が、常にユーザーが期待するタイム ゾーンと一致するように処理する必要があります。

Outlook デスクトップ クライアントでメール アプリを実行している場合、`convertToLocalClientTime` メソッドは、クライアント コンピューターのタイム ゾーンに設定された値のディクショナリ オブジェクトを返します。Outlook on the web でメール アプリを実行している場合、`convertToLocalClientTime` メソッドは、EAC で指定したタイム ゾーンに設定された値のディクショナリ オブジェクトを返します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`timeValue`| 日付|日付オブジェクト|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="returns"></a>戻り値:

型:[LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)

<br>

---
---

#### <a name="converttorestiditemid-restversion--string"></a>convertToRestId(itemId, restVersion) → {String}

EWS 形式のアイテム ID を REST 形式に変換します。

> [!NOTE]
> このメソッドは、Outlook on iOS または Android ではサポートされていません。

EWS または `itemId` プロパティで取得されるアイテム ID は、REST API ([Outlook Mail API](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) や [Microsoft Graph](https://graph.microsoft.io/) など) に使用される形式とは異なる形式を使用します。`convertToRestId` メソッドは、EWS 形式の ID を REST 用の適切な形式に変換します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`itemId`| String|Exchange Web サービス (EWS) 形式のアイテム ID|
|`restVersion`| [Office.MailboxEnums.RestVersion](/javascript/api/outlook/office.mailboxenums.restversion?view=outlook-js-1.8)|変換後の ID を使用する Outlook REST API のバージョンを示す値。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.3|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| 制限あり|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="returns"></a>戻り値:

型:String

##### <a name="example"></a>例

```js
// Get the currently selected item's ID.
var ewsId = Office.context.mailbox.item.itemId;

// Convert to a REST ID for the v2.0 version of the Outlook Mail API.
var restId = Office.context.mailbox.convertToRestId(ewsId, Office.MailboxEnums.RestVersion.v2_0);
```

<br>

---
---

#### <a name="converttoutcclienttimeinput--date"></a>convertToUtcClientTime(input) → {Date}

時間情報が含まれているディクショナリから日付オブジェクトを取得します。

`convertToUtcClientTime` メソッドは、ローカルの日付と時刻を含むディクショナリを、ローカルの日付と時刻の正しい値を持つ日付オブジェクトに変換します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`input`| [LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)|変換するローカル時刻の値。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="returns"></a>戻り値:

時間が UTC で表現された日付オブジェクト。

型: Date

##### <a name="example"></a>例

```js
// Represents 3:37 PM PDT on Monday, August 26, 2019.
var input = {
  date: 26,
  hours: 15,
  milliseconds: 2,
  minutes: 37,
  month: 7,
  seconds: 2,
  timezoneOffset: -420,
  year: 2019
};

// result should be a Date object.
var result = Office.context.mailbox.convertToUtcClientTime(input);

// Output should be "2019-08-26T22:37:02.002Z".
console.log(result.toISOString());
```

<br>

---
---

#### <a name="displayappointmentformitemid"></a>displayAppointmentForm(itemId)

既存の予定を表示します。

> [!NOTE]
> このメソッドは、Outlook on iOS または Android ではサポートされていません。

`displayAppointmentForm` メソッドは、デスクトップ上の新しいウィンドウやモバイル デバイス上のダイアログ ボックスに既存の予定を開きます。

Outlook on Mac では、このメソッドを使用して定期的な系列に含まれない単発の予定や定期的な系列のマスター予定を表示できます。ただし、系列のインスタンスは表示できません。これは、Outlook on Mac では定期的な系列のインスタンスのプロパティ (アイテム ID を含む) にアクセスできないためです。

Outlook on the web では、このメソッドはフォームの本文が 32KB 以下の文字数の場合にのみ指定のフォームを開きます。

指定のアイテム識別子が既存の予定を表していない場合は、クライアント コンピューターまたはデバイスで空のウィンドウが開き、エラー メッセージは返されません。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`itemId`| String|既存の予定の Exchange Web サービス (EWS) 識別子。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="example"></a>例

```js
Office.context.mailbox.displayAppointmentForm(appointmentId);
```

<br>

---
---

#### <a name="displaymessageformitemid"></a>displayMessageForm(itemId)

既存のメッセージを表示します。

> [!NOTE]
> このメソッドは、Outlook on iOS または Android ではサポートされていません。

`displayMessageForm` メソッドは、デスクトップ上の新しいウィンドウやモバイル デバイス上のダイアログ ボックスに既存のメッセージを開きます。

Outlook on the web では、このメソッドはフォームの本文が 32 KB 以下の文字数の場合にのみ指定のフォームを開きます。

指定のアイテム識別子が既存のメッセージを表していない場合は、クライアント コンピューターにはメッセージは表示されず、エラー メッセージも返されません。

予定を表す `itemId` を含む `displayMessageForm` を使用しないでください。既存の予定を表示するには、`displayAppointmentForm` メソッドを使用します。新しい予定を作成するフォームを表示するには、`displayNewAppointmentForm` メソッドを使用します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 説明|
|---|---|---|
|`itemId`| String|既存のメッセージの Exchange Web サービス (EWS) 識別子。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="example"></a>例

```js
Office.context.mailbox.displayMessageForm(messageId);
```

<br>

---
---

#### <a name="displaynewappointmentformparameters"></a>displayNewAppointmentForm(parameters)

新しい予定を作成するためのフォームを表示します。

> [!NOTE]
> このメソッドは、Outlook on iOS または Android ではサポートされていません。

`displayNewAppointmentForm` メソッドを使用すると、ユーザーが新しい予定または会議を作成できるフォームが開きます。パラメーターを指定すると、予定のフォーム フィールドにパラメーターの内容が自動的に設定されます。

Outlook on the web およびモバイル デバイスでは、このメソッドは常に出席者フィールドが含まれるフォームを表示します。入力引数として出席者を指定しないと、このメソッドは **[保存]** ボタンのあるフォームを表示します。出席者を指定した場合には、フォームにその出席者と **[送信]** ボタンが表示されます。

Outlook リッチ クライアントと Outlook RT で、`requiredAttendees`、`optionalAttendees`、または `resources` パラメーターに出席者またはリソースを指定し、このメソッドを実行すると、**[送信]** ボタンがある会議フォームが表示されます。受信者を指定せずにこのメソッドを実行すると、**[保存して閉じる]** ボタンがある予定フォームが表示されます。

パラメーターのいずれかが指定のサイズ制限を超える場合、または不明なパラメーター名が指定されている場合は、例外がスローされます。

##### <a name="parameters"></a>パラメーター

> [!NOTE]
> すべてのパラメーターは省略可能です。

|名前| 型| 説明|
|---|---|---|
| `parameters` | Object | 新しい予定を記述するパラメーターのディクショナリ。 |
| `parameters.requiredAttendees` | Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt; | 予定に必要な各出席者について、メール アドレスを含む文字列の配列、または `EmailAddressDetails` オブジェクトを含む配列。配列の上限は 100 エントリです。 |
| `parameters.optionalAttendees` | Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt; | 予定の各任意出席者について、メール アドレスを含む文字列の配列、または `EmailAddressDetails` オブジェクトを含む配列。配列の上限は 100 エントリです。 |
| `parameters.start` | 日付 | 予定の開始日時を指定する `Date` オブジェクト。 |
| `parameters.end` | 日付 | 予定の終了日時を指定する `Date` オブジェクト。 |
| `parameters.location` | String | 予定の場所を含む文字列。文字列は最大 255 文字に制限されます。 |
| `parameters.resources` | Array.&lt;String&gt; | 予定に必要なリソースを含む文字列の配列。配列の上限は 100 エントリです。 |
| `parameters.subject` | String | 予定の件名を含む文字列です。文字列は最大 255 文字に制限されます。 |
| `parameters.body` | String | 予定の本文。本文の内容は、最大サイズが 32 KB に制限されます。 |

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 読み取り|

##### <a name="example"></a>例

```js
var start = new Date();
var end = new Date();
end.setHours(start.getHours() + 1);

Office.context.mailbox.displayNewAppointmentForm(
  {
    requiredAttendees: ['bob@contoso.com'],
    optionalAttendees: ['sam@contoso.com'],
    start: start,
    end: end,
    location: 'Home',
    resources: ['projector@contoso.com'],
    subject: 'meeting',
    body: 'Hello World!'
  });
```

<br>

---
---

#### <a name="displaynewmessageformparameters"></a>displayNewMessageForm(parameters)

新しいメッセージを作成するためのフォームを表示します。

The `displayNewMessageForm` method opens a form that enables the user to create a new message. If parameters are specified, the message form fields are automatically populated with the contents of the parameters.

パラメーターのいずれかが指定のサイズ制限を超える場合、または不明なパラメーター名が指定されている場合は、例外がスローされます。

##### <a name="parameters"></a>パラメーター

> [!NOTE]
> すべてのパラメーターは省略可能です。

|名前| 型| 説明|
|---|---|---|
| `parameters` | オブジェクト | 新しいメッセージを記述するパラメータの辞書。 |
| `parameters.toRecipients` | Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt; | An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the To line. The array is limited to a maximum of 100 entries. |
| `parameters.ccRecipients` | Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt; | An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the Cc line. The array is limited to a maximum of 100 entries. |
| `parameters.bccRecipients` | 配列。&lt;文字列&gt; | 配列。&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt; | An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the Bcc line. The array is limited to a maximum of 100 entries. |
| `parameters.subject` | String | A string containing the subject of the message. The string is limited to a maximum of 255 characters. |
| `parameters.htmlBody` | String | The HTML body of the message. The body content is limited to a maximum size of 32 KB. |
| `parameters.attachments` | 配列。&lt;オブジェクト&gt; | 添付ファイルまたは添付アイテムである JSON オブジェクトの配列。 |
| `parameters.attachments.type` | String | 添付ファイルの種類を示します。ファイルの添付ファイルの場合は `file`、アイテムの添付ファイルの場合は `item` です。 |
| `parameters.attachments.name` | String | 添付ファイル名を含む文字列。最大の長さは 255 文字です。|
| `parameters.attachments.url` | 文字列 | `type` が `file` に設定されている場合にのみ使用されます。ファイルの場所の URI。 |
| `parameters.attachments.isInline` | ブール値 | `type` が `file` に設定されている場合にのみ使用されます。`true` の場合、添付ファイルがインラインでメッセージ本文に表示され、添付ファイル一覧に表示されないことを示します。 |
| `parameters.attachments.itemId` | String | Only used if `type` is set to `item`. The EWS item id of the existing e-mail you want to attach to the new message. This is a string up to 100 characters. |


##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.6 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 読み取り|

##### <a name="example"></a>例

```js
Office.context.mailbox.displayNewMessageForm(
  {
    // Copy the To line from current item.
    toRecipients: Office.context.mailbox.item.to,
    ccRecipients: ['sam@contoso.com'],
    subject: 'Outlook add-ins are cool!',
    htmlBody: 'Hello <b>World</b>!<br/><img src="cid:image.png"></i>',
    attachments: [
      {
        type: 'file',
        name: 'image.png',
        url: 'http://contoso.com/image.png',
        isInline: true
      }
    ]
  });
```

<br>

---
---

#### <a name="getcallbacktokenasyncoptions-callback"></a>getCallbackTokenAsync([options], callback)

REST API または Exchange Web サービスを呼び出すために使用するトークンを含む文字列を取得します。

`getCallbackTokenAsync` メソッドは、ユーザーのメールボックスをホストする Exchange Server から不透明なトークンを取得する非同期の呼び出しを行います。コールバック トークンの有効期間は 5 分です。

> [!NOTE]
> 可能であれば、アドインでは Exchange Web サービスの代わりに REST API を使用することをお勧めします。

閲覧モードで `getCallbackTokenAsync` メソッドを呼び出すには、**ReadItem** の最小限のアクセス許可レベルが必要です。

作成モードで `getCallbackTokenAsync` を呼び出すには、アイテムを保存しておく必要があります。 [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) メソッドは、**ReadWriteItem** の最小限のアクセス許可レベルが必要です。

**REST トークン**

REST トークンが要求された場合 (`options.isRest = true`)、結果トークンは Exchange Web サービスの呼び出しを認証するためには機能しません。アドインがマニフェストで [`ReadWriteMailbox`](/outlook/add-ins/understanding-outlook-add-in-permissions#readwritemailbox-permission) アクセス許可を指定していない限り、トークンの範囲は現在のアイテムとその添付ファイルへの読み取り専用アクセスに制限されます。`ReadWriteMailbox` アクセス許可が指定されている場合は、結果トークンは、メールを送信する機能など、メール、カレンダー、連絡先への読み取り/書き込みアクセスを付与します。

アドインでは、`restUrl` プロパティを使用して、REST API 呼び出しを行うときに使用する正しい URL を決定する必要があります。

**EWS トークン**

EWS トークンが要求された場合 (`options.isRest = false`)、結果トークンは REST API 呼び出しを認証するためには機能しません。トークンの範囲は、現在のアイテムへのアクセスに制限されます。

アドインでは、`ewsUrl` プロパティを使用して、EWS 呼び出しを行うときに使用する正しい URL を決定する必要があります。

トークンと、添付ファイル識別子またはアイテム識別子の両方をサードパーティ システムに渡すことができます。 サードパーティシステムは、トークンをベアラー認証トークンとして使用して、Exchange Web サービス (EWS) の[Getattachment](/exchange/client-developer/web-service-reference/getattachment-operation)操作または[GetItem](/exchange/client-developer/web-service-reference/getitem-operation)操作を呼び出して、添付ファイルまたはアイテムを取得します。 たとえば、[選択したアイテムから添付ファイルを取得する](/outlook/add-ins/get-attachments-of-an-outlook-item)ためにリモート サービスを作成できます。

##### <a name="parameters"></a>パラメーター

|名前| 型| 属性| 説明|
|---|---|---|---|
| `options` | Object | &lt;オプション&gt; | 次のプロパティのうち 1 つ以上を含むオブジェクト リテラル。 |
| `options.isRest` | ブール値 |  &lt;optional&gt; | 提供されたトークンを Outlook REST API または Exchange Web サービスに使用するかどうかを決定します。既定値は、`false` です。 |
| `options.asyncContext` | Object |  &lt;省略可能&gt; | 非同期メソッドに渡される状態データです。 |
|`callback`| function||メソッドが完了すると、`callback` パラメーターに渡された関数が、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `asyncResult` で呼び出されます。<br/><br/>トークンは、`asyncResult.value` プロパティで文字列として提供されます。<br><br>エラーが発生した場合、 `asyncResult.error` および `asyncResult.diagnostics` のプロパティで追加情報が提供される場合があります。|

##### <a name="errors"></a>エラー

|エラー コード|説明|
|------------|-------------|
|`HTTPRequestFailure`|要求が失敗しました。 HTTP エラーコードの diagnostics オブジェクトを参照してください。|
|`InternalServerError`|Exchange サーバーがエラーを返しました。 詳細については、diagnostics オブジェクトを参照してください。|
|`NetworkError`|ユーザーはネットワークに接続されていません。 ネットワーク接続を確認し、やり直してください。|

##### <a name="requirements"></a>要件

|必要条件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成と閲覧|

##### <a name="example"></a>例

```js
function getCallbackToken() {
  var options = {
    isRest: true,
    asyncContext: { message: 'Hello World!' }
  };

  Office.context.mailbox.getCallbackTokenAsync(options, cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="getcallbacktokenasynccallback-usercontext"></a>getCallbackTokenAsync(callback, [userContext])

Exchange Server から添付ファイルやアイテムを取得するために使うトークンを含む文字列を取得します。

`getCallbackTokenAsync` メソッドは、ユーザーのメールボックスをホストする Exchange Server から不透明なトークンを取得する非同期の呼び出しを行います。コールバック トークンの有効期間は 5 分です。

トークンと、添付ファイル識別子またはアイテム識別子の両方をサードパーティ システムに渡すことができます。 サードパーティ システムは、トークンをベアラー承認トークンとして使用し、Exchange Web サービス (EWS) [GetAttachment](/exchange/client-developer/web-service-reference/getattachment-operation) 操作または [GetItem](/exchange/client-developer/web-service-reference/getitem-operation) 操作を呼び出して、添付ファイルまたはアイテムを返します。 たとえば、[選択したアイテムから添付ファイルを取得する](/outlook/add-ins/get-attachments-of-an-outlook-item)ためにリモート サービスを作成できます。

閲覧モードで `getCallbackTokenAsync` メソッドを呼び出すには、**ReadItem** の最小限のアクセス許可レベルが必要です。

作成モードで `getCallbackTokenAsync` を呼び出すには、アイテムを保存しておく必要があります。 [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) メソッドは、**ReadWriteItem** の最小限のアクセス許可レベルが必要です。

##### <a name="parameters"></a>パラメーター

|名前| 型| 属性| 説明|
|---|---|---|---|
|`callback`| 関数||メソッドが完了すると、`callback` パラメーターに渡された関数が、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `asyncResult` で呼び出されます。<br/><br/>トークンは、`asyncResult.value` プロパティで文字列として提供されます。<br><br>エラーが発生した場合、 `asyncResult.error` および `asyncResult.diagnostics` のプロパティで追加情報が提供される場合があります。|
|`userContext`| オブジェクト| &lt;省略可能&gt;|非同期メソッドに渡される状態データです。|

##### <a name="errors"></a>エラー

|エラー コード|説明|
|------------|-------------|
|`HTTPRequestFailure`|要求が失敗しました。 HTTP エラーコードの diagnostics オブジェクトを参照してください。|
|`InternalServerError`|Exchange サーバーがエラーを返しました。 詳細については、diagnostics オブジェクトを参照してください。|
|`NetworkError`|ユーザーはネットワークに接続されていません。 ネットワーク接続を確認し、やり直してください。|

##### <a name="requirements"></a>要件

|要件|||
|---|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0 | 1.3 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem | ReadItem |
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| Read | Compose |

##### <a name="example"></a>例

```js
function getCallbackToken() {
  Office.context.mailbox.getCallbackTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="getuseridentitytokenasynccallback-usercontext"></a>getUserIdentityTokenAsync(callback, [userContext])

ユーザーと Office アドインを識別するトークンを取得します。

`getUserIdentityTokenAsync` メソッドは、[アドインとユーザーをサード パーティのシステムで識別して認証](/outlook/add-ins/authentication)することのできるトークンを返します。

##### <a name="parameters"></a>パラメーター

|名前| 型| 属性| 説明|
|---|---|---|---|
|`callback`| 関数||メソッドが完了すると、`callback` パラメーターに渡された関数が、[`AsyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `asyncResult` で呼び出されます。<br/><br/>トークンは、`asyncResult.value` プロパティで文字列として提供されます。<br><br>エラーが発生した場合、 `asyncResult.error` および `asyncResult.diagnostics` のプロパティで追加情報が提供される場合があります。|
|`userContext`| オブジェクト| &lt;省略可能&gt;|非同期メソッドに渡される状態データです。|

##### <a name="errors"></a>エラー

|エラー コード|説明|
|------------|-------------|
|`HTTPRequestFailure`|要求が失敗しました。 HTTP エラーコードの diagnostics オブジェクトを参照してください。|
|`InternalServerError`|Exchange サーバーがエラーを返しました。 詳細については、diagnostics オブジェクトを参照してください。|
|`NetworkError`|ユーザーはネットワークに接続されていません。 ネットワーク接続を確認し、やり直してください。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="example"></a>例

```js
function getIdentityToken() {
  Office.context.mailbox.getUserIdentityTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="makeewsrequestasyncdata-callback-usercontext"></a>makeEwsRequestAsync(data, callback, [userContext])

ユーザーのメールボックスをホストしている Exchange サーバー上の Exchange Web サービス (EWS) のサービスに対して非同期の要求を行います。

> [!NOTE]
> このメソッドは、次のシナリオではサポートされていません。
> - Outlook on iOS または Android の場合
> - アドインが Gmail のメールボックスに読み込まれる場合
> 
> このような場合は、アドインでは [REST API を使用](/outlook/add-ins/use-rest-api)して、代わりにユーザーのメールボックスにアクセスする必要があります。

The `makeEwsRequestAsync` method sends an EWS request on behalf of the add-in to Exchange. See [Call web services from an Outlook add-in](/outlook/add-ins/web-services#ews-operations-that-add-ins-support) for a list of the supported EWS operations.

`makeEwsRequestAsync` メソッドでは、フォルダー関連アイテムを要求できません。

XML 要求では UTF-8 エンコードを指定する必要があります。

```xml
<?xml version="1.0" encoding="utf-8"?>
```

`makeEwsRequestAsync` メソッドを使用するには、アドインに **ReadWriteMailbox** アクセス許可が必要です。**ReadWriteMailbox** アクセス許可と、`makeEwsRequestAsync` メソッドで呼び出せる EWS 操作の使い方については、「[ユーザーのメールボックスへのメール アドイン アクセスのアクセス許可を指定する](/outlook/add-ins/understanding-outlook-add-in-permissions)」を参照してください。

> [!NOTE]
> サーバー管理者は、クライアント アクセス サーバーの EWS ディレクトリで `OAuthAuthentication` を true に設定して、`makeEwsRequestAsync` メソッドで EWS 要求を行うことができるようにする必要があります。

##### <a name="version-differences"></a>バージョンの相違点

バージョン 15.0.4535.1004 より前のバージョンの Outlook で実行しているメール アプリで `makeEwsRequestAsync` メソッドを使用する場合には、エンコード値を `ISO-8859-1` に設定する必要があります。

```xml
<?xml version="1.0" encoding="iso-8859-1"?>
```

Outlook on the web でメール アプリを実行している場合は、エンコード値を設定する必要はありません。 メールアプリが web 上の Outlook またはデスクトップクライアントで実行されているかどうかは、mailbox プロパティを使用して判断できます。 mailbox.diagnostics.hostVersion プロパティを使って、どのバージョンの Outlook を使って実行しているかを確認できます。

##### <a name="parameters"></a>パラメーター

|名前| 型| 属性| 説明|
|---|---|---|---|
|`data`| String||EWS 要求です。|
|`callback`| function||メソッドが完了すると、`callback` パラメーターに渡された関数が、[`asyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `AsyncResult` で呼び出されます。<br/><br/>The XML result of the EWS call is provided as a string in the `asyncResult.value` property. If the result exceeds 1 MB in size, an error message is returned instead.|
|`userContext`| Object| &lt;省略可能&gt;|非同期メソッドに渡される状態データです。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadWriteMailbox|
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|

##### <a name="example"></a>例

次の例は、`GetItem` 操作を使ってアイテムの件名を取得するため、`makeEwsRequestAsync` を呼び出します。

```js
function getSubjectRequest(id) {
  // Return a GetItem operation request for the subject of the specified item.
  var request =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"' +
    '               xmlns:xsd="http://www.w3.org/2001/XMLSchema"' +
    '               xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"' +
    '               xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types">' +
    '  <soap:Header>' +
    '    <RequestServerVersion Version="Exchange2013" xmlns="http://schemas.microsoft.com/exchange/services/2006/types" soap:mustUnderstand="0" />' +
    '  </soap:Header>' +
    '  <soap:Body>' +
    '    <GetItem xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">' +
    '      <ItemShape>' +
    '        <t:BaseShape>IdOnly</t:BaseShape>' +
    '        <t:AdditionalProperties>' +
    '            <t:FieldURI FieldURI="item:Subject"/>' +
    '        </t:AdditionalProperties>' +
    '      </ItemShape>' +
    '      <ItemIds><t:ItemId Id="' + id + '"/></ItemIds>' +
    '    </GetItem>' +
    '  </soap:Body>' +
    '</soap:Envelope>';

  return request;
}

function sendRequest() {
  // Create a local variable that contains the mailbox.
  Office.context.mailbox.makeEwsRequestAsync(
    getSubjectRequest(mailbox.item.itemId), callback);
}

function callback(asyncResult)  {
  var result = asyncResult.value;
  var context = asyncResult.asyncContext;

  // Process the returned response here.
}
```

<br>

---
---

#### <a name="removehandlerasynceventtype-options-callback"></a>removeHandlerAsync(eventType, [options], [callback])

サポートされているイベントの種類のイベント ハンドラーを削除します。

現在、サポートされている`Office.EventType.ItemChanged`イベント`Office.EventType.OfficeThemeChanged`の種類はおよびです。

##### <a name="parameters"></a>パラメーター

| 名前 | 型 | 属性 | 説明 |
|---|---|---|---|
| `eventType` | [Office.EventType](office.md#eventtype-string) || ハンドラーを取り消すイベント。 |
| `options` | オブジェクト | &lt;オプション&gt; | 次のプロパティのうち 1 つ以上を含むオブジェクト リテラル。 |
| `options.asyncContext` | Object | &lt;省略可能&gt; | 開発者は、コールバック メソッドでアクセスしたい任意のオブジェクトを提供できます。 |
| `callback` | function| &lt;optional&gt;|メソッドが完了すると、`callback` パラメーターに渡された関数が、[`asyncResult`](/javascript/api/office/office.asyncresult) オブジェクトである 1 つのパラメーター `AsyncResult` で呼び出されます。|

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最小要件セットのバージョン](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| 1.5 |
|[最小限のアクセス許可レベル](/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem |
|[適用可能な Outlook のモード](/outlook/add-ins/#extension-points)| 新規作成または閲覧|