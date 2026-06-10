# verify-sender-trust

`verify-sender-trust` は、チラシ、広告、メール、ダイレクトメール、SMS、SNS 広告、案内状、寄付依頼、求人、イベント告知などについて、送り主や関係団体が信頼できるかを確認するための Agent Skill です。

この Skill は、案内の見た目や送り主の自己申告だけで判断せず、案内内の手がかりを公式情報・公的情報・一次情報へ接続していくことを重視します。

特に、次の 2 つを分けて扱います。

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

Agent Skills CLI を使う場合:

```bash
npx skills add selchy24x/verify-sender-trust-skill --skill verify-sender-trust
```

Claude Code にユーザースコープで入れる例:

```bash
npx skills add selchy24x/verify-sender-trust-skill --skill verify-sender-trust --agent claude-code --global
```

Codex にユーザースコープで入れる例:

```bash
npx skills add selchy24x/verify-sender-trust-skill --skill verify-sender-trust --agent codex --global
```

### GitHub CLI

`gh skill` に対応した GitHub CLI を使う場合:

```bash
gh skill install selchy24x/verify-sender-trust-skill verify-sender-trust
```

Claude Code にユーザースコープで入れる例:

```bash
gh skill install selchy24x/verify-sender-trust-skill verify-sender-trust --agent claude-code --scope user
```

Codex にユーザースコープで入れる例:

```bash
gh skill install selchy24x/verify-sender-trust-skill verify-sender-trust --agent codex --scope user
```

`gh skills` は、対応している GitHub CLI では `gh skill` の別名として利用できます。

その他の Agent AI ツールでの導入方法は、各ツールの Agent Skills 対応方法に従ってください。

インストール後、新しい Skill が自動認識されない場合は、利用中の Agent AI ツールを再起動してください。

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

## 注意

この Skill は調査手順を改善するためのものです。安全性を保証するものではありません。

医療、法律、金融、税金、移民、雇用、行政給付などの高リスク領域では、案内内の連絡先ではなく、公式サイトや公的機関から独立して確認した連絡経路で必ず確認してください。
