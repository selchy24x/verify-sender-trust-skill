# verify-sender-trust

![verify-sender-trust eyecatch](assets/verify-sender-trust-eyecatch.jpg)

`verify-sender-trust` は、チラシ、広告、メール、ダイレクトメール、SMS、SNS 広告、案内状、寄付依頼、求人、イベント告知などについて、送り主や関係団体が信頼できるかを確認するための Agent Skill です。

基本的な方針としては、コンテンツから信頼性チェックに活用できるヒントを抽出し、web調査で

- 公式情報・公的情報・信頼できる一次情報での言及
- ドメインの信頼性

などをチェックします。

つまり、調査対象の団体/個人から伸びた「信頼の鎖」が信用の置ける団体やソースまで繋がっていて、かつその案内・送信元・リンク・支払い先・依頼行動まで確認できればOK、という考え方です。

その他にも信頼性チェックのために有用と思われるweb調査を行います。

次の2つは分けて扱います。

- その団体が実在し、信頼できそうか
- その案内、送信元、リンク、支払い先、担当者、依頼行動が本当にその団体と結びついているか

開発者: Selchy

## できること

- 団体名、送信元ドメイン、電話番号、住所、イベント名、QR/リンク先、支払い先などの手がかりを抽出する。
- 団体の実在確認と、案内そのものの真正性確認を分けて扱う。
- 公式サイト、公的登録、規制当局、学校、病院、自治体、親会社、会場、提携先などの情報源を優先する。
- `Verified`、`Partially verified`、`Not verified`、`High risk` の保守的な結論に整理する。
- 支払い、ログイン、寄付、応募、ダウンロード、返信、個人情報提出など、利用者に求められている行動のリスクを確認する。

## できないこと

- 証拠なしに詐欺だと断定すること。
- 送信者へ自動で問い合わせること。
- フォーム入力、支払い、ログイン、個人情報入力によって正当性を試すこと。
- 古い情報や未確認情報だけで、安全だと判断すること。

## リポジトリ構成

```text
.
├── README.md
├── LICENSE
├── skills/
│   └── verify-sender-trust/
│       └── SKILL.md
```

## インストール

### npx skills

```bash
npx skills add selchy24x/verify-sender-trust-skill --skill verify-sender-trust
```

### GitHub CLI

```bash
gh skill install selchy24x/verify-sender-trust-skill verify-sender-trust
```

## 利用例

```text
Use $verify-sender-trust to check whether this email asking me to pay a registration fee is really connected to the named university.
```

```text
Use $verify-sender-trust to verify whether this flyer for a city-sponsored seminar is actually connected to the city or an official contractor.
```

```text
Use $verify-sender-trust to investigate whether this donation request from a nonprofit-looking organization is trustworthy.
```

## 注意点
このSkillは簡易的な調査をAIに行わせる目的で作成されたものです。

高いリスクを伴う判断には使わない方が良いと思います。

調査結果は、各利用者の責任において活用してください。
