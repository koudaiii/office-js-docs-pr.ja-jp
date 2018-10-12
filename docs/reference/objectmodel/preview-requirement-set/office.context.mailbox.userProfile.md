
# <a name="userprofile"></a>userProfile

### [Office](Office.md)[.context](Office.context.md)[.mailbox](Office.context.mailbox.md).userProfile

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最低要件セットのバージョン](/javascript/office/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最低限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成または読み取り|

##### <a name="members-and-methods"></a>メンバーとメソッド

| メンバー | 型 |
|--------|------|
| [accountType](#accounttype-string) | メンバー |
| [displayName](#displayname-string) | メンバー |
| [emailAddress](#emailaddress-string) | メンバー |
| [timeZone](#timezone-string) | メンバー |

### <a name="members"></a>メンバー

####  <a name="accounttype-string"></a>accountType: 文字列

> [!NOTE]
> このメンバーは、現在 Outlook 2016 for Mac またはそれ以降でのみサポートされています (ビルド 16.9.1212 またはそれ以降)。

メールボックスに関連付けられているユーザーのアカウントの種類を取得します。 使用可能な値は、次の表に表示されます。

| 値 | 説明 |
|-------|-------------|
| `enterprise` | メールボックスは、オンプレミスの Exchange Server にあります。 |
| `gmail` | メールボックスは、Gmail アカウントに関連付けられます。 |
| `office365` | メールボックスは、Office 365 の職場や学校のアカウントに関連付けられます。 |
| `outlookCom` | メールボックスは、個人の Outlook.com アカウントに関連付けられます。 |

##### <a name="type"></a>型:

*   文字列

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最低要件セットのバージョン](/javascript/office/requirement-sets/outlook-api-requirement-sets)| 1.6 |
|[最低限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成または読み取り|

##### <a name="example"></a>例

```
console.log(Office.context.mailbox.userProfile.accountType);
```

####  <a name="displayname-string"></a>displayName: 文字列

ユーザーの表示名を取得します。

##### <a name="type"></a>型:

*   文字列

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最低要件セットのバージョン](/javascript/office/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最低限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成または読み取り|

##### <a name="example"></a>例

```
// Example: Allie Bellew
console.log(Office.context.mailbox.userProfile.displayName);
```

####  <a name="emailaddress-string"></a>emailAddress : 文字列

ユーザーの SMTP 電子メール アドレスを取得します。

##### <a name="type"></a>型:

*   文字列

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最低要件セットのバージョン](/javascript/office/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最低限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成または読み取り|

##### <a name="example"></a>例

```
// Example: allieb@contoso.com
console.log(Office.context.mailbox.userProfile.emailAddress);
```

####  <a name="timezone-string"></a>タイム ゾーン : 文字列

ユーザーの既定のタイム ゾーンを取得します。

##### <a name="type"></a>型:

*   文字列

##### <a name="requirements"></a>要件

|要件| 値|
|---|---|
|[メールボックスの最低要件セットのバージョン](/javascript/office/requirement-sets/outlook-api-requirement-sets)| 1.0|
|[最低限のアクセス許可レベル](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| ReadItem|
|[適用可能な Outlook のモード](https://docs.microsoft.com/outlook/add-ins/#extension-points)| 新規作成または読み取り|

##### <a name="example"></a>例

```
// Example: Pacific Standard Time
console.log(Office.context.mailbox.userProfile.timeZone);
```