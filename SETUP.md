# セットアップ手順 📝

このリポジトリ（`dufaro/dufaro`）は **GitHub プロフィール用の特別なリポジトリ** です。
README.md がプロフィールページに自動で表示されます。

## 1. WakaTime API Key を Secrets に登録する

GitHub Actions が WakaTime の統計を取得するために必要です。

1. [https://wakatime.com/api-key](https://wakatime.com/api-key) を開いて、**Secret API Key**（`waka_xxxx...` で始まるもの）をコピー
2. このリポジトリの **Settings** → **Secrets and variables** → **Actions** を開く
3. **New repository secret** をクリック
4. 以下を入力して **Add secret**
   - **Name**: `WAKATIME_API_KEY`
   - **Secret**: コピーしたAPIキー

## 2. WakaTime プラグインをエディタに入れる（まだなら）

実際にコーディング時間を計測するために必要です。

- **Xcode**: [WakaTime for Xcode](https://github.com/wakatime/xcode-wakatime)
- **VS Code**: 拡張機能から `WakaTime` を検索してインストール
- **JetBrains 系**: Plugins から `WakaTime`
- その他のエディタ: [公式プラグイン一覧](https://wakatime.com/plugins)

プラグインを入れると初回起動時に API Key を求められるので、上と同じキーを貼り付けます。

## 3. ワークフローを手動で動かして確認

1. リポジトリの **Actions** タブを開く
2. 左サイドバーから **Waka Readme** を選択
3. **Run workflow** → **Run workflow** をクリック
4. 数分後、README の `<!--START_SECTION:waka-->` の部分が自動で更新されます

以降は毎日 **JST 朝7時** に自動で更新されます ⏰

## 4. 表示されるもの

- 🧑‍💻 自己紹介セクション
- 🛠 使用技術バッジ
- 📊 GitHub Stats カード（コミット数・スター数など）
- 🏆 Top Languages（使用言語ランキング）
- 🔥 Streak Stats（連続コミット日数）
- ⏱ WakaTime 週間コーディング統計（言語別の作業時間）
- 👀 プロフィール閲覧数カウンター

## トラブルシューティング

- **WakaTime の部分が更新されない** → Secrets の名前が `WAKATIME_API_KEY` か再確認
- **データが少ない / 出ない** → エディタにプラグインを入れて数日コーディングすればデータが溜まります
- **Stats カードが表示されない** → `github-readme-stats.vercel.app` 側の一時的な不調の可能性。少し時間を置いてリロード
