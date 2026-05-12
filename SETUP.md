# セットアップ手順 📝

このリポジトリ（`dufaro/dufaro`）は **GitHub プロフィール用の特別なリポジトリ** です。
README.md がプロフィールページに自動で表示されます。

## 1. WakaTime API Key を Secrets に登録

1. [https://wakatime.com/api-key](https://wakatime.com/api-key) を開いて、**Secret API Key**（`waka_xxxx...` で始まるもの）をコピー
2. [リポジトリの Secrets 設定](https://github.com/dufaro/dufaro/settings/secrets/actions/new) を開く
3. 以下を入力して **Add secret**
   - **Name**: `WAKATIME_API_KEY`
   - **Secret**: コピーしたAPIキー

※ 古い `GH_TOKEN` Secret は不要になりました（あっても害はないので残してもOK）

## 2. WakaTime プラグインをエディタに入れる（まだなら）

実際にコーディング時間を計測するために必要です。

- **Xcode**: [WakaTime for Xcode](https://github.com/wakatime/xcode-wakatime)
- **VS Code**: 拡張機能から `WakaTime` を検索してインストール
- **JetBrains 系**: Plugins から `WakaTime`
- その他のエディタ: [公式プラグイン一覧](https://wakatime.com/plugins)

プラグインを入れると初回起動時に API Key を求められるので、上と同じキーを貼り付けます。

## 3. ワークフローを手動で動かして確認

1. [Actions タブ](https://github.com/dufaro/dufaro/actions) を開く
2. 左サイドバーから **Waka Readme** を選択
3. **Run workflow** → **Run workflow** をクリック
4. **30秒〜1分程度**で README が自動更新されます

以降は毎日 **JST 朝7時** に自動更新されます ⏰

## 4. 表示されるもの

WakaTime セクションには **過去7日間** の以下が表示されます：

```text
Swift        4 hrs 30 mins  ████████████░░░░░░░  60.00 %
TypeScript   2 hrs 15 mins  ██████░░░░░░░░░░░░░  30.00 %
JavaScript   45 mins        ██░░░░░░░░░░░░░░░░░  10.00 %
```

README にはこの他にも：
- 🧑‍💻 自己紹介セクション
- 🛠 使用技術バッジ
- 📊 GitHub Stats カード（コミット数・スター数など）
- 🏆 Top Languages（使用言語ランキング）
- 🔥 Streak Stats（連続コミット日数）
- 👀 プロフィール閲覧数カウンター

## トラブルシューティング

- **WakaTime の部分が更新されない** → Secrets の名前が `WAKATIME_API_KEY` か再確認
- **データが少ない / 出ない** → エディタにプラグインを入れて数日コーディングすればデータが溜まります
- **Stats カードが表示されない** → `github-readme-stats.vercel.app` 側の一時的な不調の可能性。少し時間を置いてリロード
