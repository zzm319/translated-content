---
title: Access-Control-Expose-Headers
slug: Web/HTTP/Headers/Access-Control-Expose-Headers
tags:
  - CORS
  - HTTP
  - Reference
  - ヘッダー
  - リファレンス
translation_of: Web/HTTP/Headers/Access-Control-Expose-Headers
---
{{HTTPSidebar}}

**`Access-Control-Expose-Headers`** レスポンスヘッダーは、レスポンスの一部としてどのヘッダーを公開するかを、その名前を列挙して示します。

既定では、公開される {{Glossary("CORS-safelisted response header", "CORS セーフリストレスポンスヘッダー")}}は 7 つだけです。

- {{HTTPHeader("Cache-Control")}}
- {{HTTPHeader("Content-Language")}}
- {{HTTPHeader("Content-Length")}}
- {{HTTPHeader("Content-Type")}}
- {{HTTPHeader("Expires")}}
- {{HTTPHeader("Last-Modified")}}
- {{HTTPHeader("Pragma")}}

クライアントが他のヘッダーにアクセスできるようにするには、 `Access-Control-Expose-Headers` ヘッダーを使用してヘッダーを列挙する必要があります。

| ヘッダー種別                                                                         | {{Glossary("Response header", "レスポンスヘッダー")}} |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| {{Glossary("Forbidden header name", "禁止ヘッダー名")}} | いいえ                                                                               |

## 構文

    Access-Control-Expose-Headers: <header-name>, <header-name>, ...
    Access-Control-Expose-Headers: *

## ディレクティブ

- \<header-name>
  - : ゼロ個以上の[ヘッダー名](/ja/docs/Web/HTTP/Headers)の一覧で、 {{Glossary("CORS-safelisted response header", "CORS セーフリストレスポンスヘッダー")}}に含まれないものであり、リソースが使用する可能性があり、公開される可能性があるものです。
- `*` (ワイルドカード)
  - : "`*`" の値は、資格情報のないリクエスト ([HTTP Cookie](/ja/docs/Web/HTTP/Cookies) や HTTP の資格情報のないリクエスト) の特殊なワイルドカード値です。資格情報付きのリクエストでは、特別な意味のない "`*`" というヘッダー名として扱われます。
    なお、 {{HTTPHeader("Authorization")}} ヘッダーはワイルドカードで表すことができず、常に明示的に列挙する必要があります。

## 例

CORS セーフリストにないレスポンスヘッダーを公開するには、次のように指定します。

    Access-Control-Expose-Headers: Content-Length

`X-Kuma-Revision` のようなカスタムヘッダーをさらに公開するには、複数のヘッダーをカンマで区切って指定することができます。

    Access-Control-Expose-Headers: Content-Length, X-Kuma-Revision

資格情報のないリクエストでは、ワイルドカード値を使うこともできます。

    Access-Control-Expose-Headers: *

但し、 {{HTTPHeader("Authorization")}} ヘッダーはワイルドカードの対象にならないので、明示的に列挙する必要があります。

    Access-Control-Expose-Headers: *, Authorization

## 仕様書

| 仕様書                                                                                                                       | 状態                     | 備考 |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ---- |
| {{SpecName('Fetch','#http-access-control-expose-headers', 'Access-Control-Expose-Headers')}} | {{Spec2("Fetch")}} |      |

## ブラウザーの互換性

{{Compat("http.headers.Access-Control-Expose-Headers")}}

## 関連情報

- {{HTTPHeader("Access-Control-Allow-Headers")}}
- {{HTTPHeader("Access-Control-Allow-Origin")}}