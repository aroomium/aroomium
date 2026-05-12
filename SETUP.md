# セットアップ手順 📝

このリポジトリ（`dufaro/dufaro`）は **GitHub プロフィール用の特別なリポジトリ** です。
README.md がプロフィールページに自動で表示されます。

## 1. WakaTime API Key を Secrets に登録

1. [https://wakatime.com/api-key](https://wakatime.com/api-key) を開いて、**Secret API Key**（`waka_xxxx...` で始まるもの）をコピー
2. [リポジトリの Secrets 設定](https://github.com/dufaro/dufaro/settings/secrets/actions/new) を開く
3. 以下を入力して **Add secret**
   - **Name**: `WAKATIME_API_KEY`
   - **Secret**: コピーしたAPIキー

## 2. GitHub Personal Access Token (PAT) を作って Secrets に登録

`waka-readme-stats` は **コミット履歴を解析して時間帯別・曜日別グラフを作る** ため、デフォルトの `GITHUB_TOKEN` では権限が足りません。PAT が必要です。

1. [https://github.com/settings/tokens/new](https://github.com/settings/tokens/new) を開く
2. 設定値：
   - **Note**: `waka-readme-stats`
   - **Expiration**: お好みで（推奨: No expiration か 1 year）
   - **Scopes**: ✅ `repo` ✅ `read:user` にチェック
3. **Generate token** を押してトークン（`ghp_xxxx...`）をコピー
4. [リポジトリの Secrets 設定](https://github.com/dufaro/dufaro/settings/secrets/actions/new) を開く
5. 以下を入力して **Add secret**
   - **Name**: `GH_TOKEN`
   - **Secret**: コピーしたPAT

## 3. WakaTime プラグインをエディタに入れる（まだなら）

実際にコーディング時間を計測するために必要です。

- **Xcode**: [WakaTime for Xcode](https://github.com/wakatime/xcode-wakatime)
- **VS Code**: 拡張機能から `WakaTime` を検索してインストール
- **JetBrains 系**: Plugins から `WakaTime`
- その他のエディタ: [公式プラグイン一覧](https://wakatime.com/plugins)

## 4. ワークフローを手動で動かして確認

1. [Actions タブ](https://github.com/dufaro/dufaro/actions) を開く
2. 左サイドバーから **Waka Readme Stats** を選択
3. **Run workflow** → **Run workflow** をクリック
4. 数分後、README の `<!--START_SECTION:waka-->` の部分が自動で更新されます

以降は毎日 **JST 朝7時** に自動更新されます ⏰

## 5. 自動表示されるもの

WakaTime セクションには以下が **テキストベースのバーグラフ** で表示されます：

- 🌞 **時間帯別の活動分布**（朝・昼・夕方・夜のコミット比率）
- 📅 **曜日別の活動分布**（一番生産的な曜日が分かる）
- 💬 **今週使った言語**（Swift / TypeScript など、時間付きで）
- 🔥 **エディタ別の時間**（Xcode / VS Code など）
- 💻 **OS別の時間**（macOS など）
- 📊 **累計コーディング時間** と **書いたコード行数** のバッジ

## トラブルシューティング

- **WakaTime セクションが更新されない**
  → Secrets 名が **`WAKATIME_API_KEY`** と **`GH_TOKEN`** の2つ揃っているか確認
- **`Error: Resource not accessible by integration`**
  → PAT の権限不足。`repo` と `read:user` にチェックが入っているか確認
- **データが少ない / 出ない**
  → エディタに WakaTime プラグインを入れて数日コーディングするとデータが溜まります
- **Stats カードが表示されない**
  → `github-readme-stats.vercel.app` の一時的な不調の可能性。少し時間を置いてリロード
