# 🚨 404エラー解決ガイド

## 問題の原因
GitHubリポジトリが実際には作成されていないため、GitHub Pagesで404エラーが発生しています。

## 📋 解決手順

### Step 1: 実際のGitHubリポジトリを作成

1. **GitHub.com にログイン**
   - https://github.com にアクセス
   - ログイン（アカウントがない場合は新規作成）

2. **新規リポジトリ作成**
   - 右上の「+」アイコン → 「New repository」
   - Repository name: `flashcard-web-app`
   - Description: `🧠 科学的間隔反復学習による暗記アプリ`
   - ✅ Public をチェック
   - ❌ "Add a README file" はチェックしない（既にファイルがあるため）
   - 「Create repository」をクリック

### Step 2: リモートURLの更新

作成されたリポジトリのURLを確認し、以下のコマンドで設定：

```bash
# 現在のリモート削除
git remote remove origin

# 新しいリモート追加（YOUR-USERNAMEを実際のユーザー名に変更）
git remote add origin https://github.com/YOUR-USERNAME/flashcard-web-app.git

# 確認
git remote -v
```

### Step 3: GitHubにプッシュ

```bash
# ファイルをプッシュ
git push -u origin main
```

認証が求められた場合：
- Username: GitHubのユーザー名
- Password: GitHubのPersonal Access Token（パスワードではない）

### Step 4: Personal Access Token作成（必要な場合）

1. **GitHub Settings**
   - GitHub右上のアイコン → Settings
   - 左メニュー → Developer settings → Personal access tokens → Tokens (classic)

2. **新しいトークン作成**
   - 「Generate new token」→「Generate new token (classic)」
   - Note: `flashcard-app-deploy`
   - Expiration: 90 days
   - Scopes: ✅ repo にチェック
   - 「Generate token」

3. **トークンをコピー**
   - ⚠️ このトークンは一度しか表示されません
   - 安全な場所に保存

### Step 5: GitHub Pages設定

1. **リポジトリ Settings**
   - 作成したリポジトリ → Settings タブ
   - 左メニュー → Pages

2. **Pages設定**
   ```
   Source: Deploy from a branch
   Branch: main
   Folder: / (root)
   ```
   - 「Save」をクリック

3. **デプロイ待機**
   - 約3-5分待機
   - 緑色のチェックマークが表示されるまで待つ

### Step 6: アクセス確認

**公開URL**: `https://YOUR-USERNAME.github.io/flashcard-web-app/`

---

## 🎯 具体的な手順（実例）

### 例: ユーザー名が `john-doe` の場合

1. **リポジトリ作成後のURL**: `https://github.com/john-doe/flashcard-web-app`

2. **コマンド実行**:
```bash
git remote remove origin
git remote add origin https://github.com/john-doe/flashcard-web-app.git
git push -u origin main
```

3. **最終的な公開URL**: `https://john-doe.github.io/flashcard-web-app/`

---

## 🔍 トラブルシューティング

### Q: git push でエラーが出る
**A**: Personal Access Tokenを使用
```bash
Username: john-doe
Password: ghp_xxxxxxxxxxxxxxxxxxxx（トークン）
```

### Q: Pages設定が見つからない
**A**: リポジトリがPublicか確認
- Private リポジトリではGitHub Pages は有料プランでのみ利用可能

### Q: デプロイ後も404エラー
**A**: ファイル確認
- index.html がルートディレクトリにあるか確認
- 大文字小文字の間違いがないか確認

### Q: アクセスはできるが機能しない
**A**: ブラウザ開発者ツールでエラー確認
- F12 → Console タブでエラーメッセージ確認
- ファイルパスの問題の可能性

---

## ✅ 成功確認チェックリスト

- ✅ GitHubリポジトリが作成されている
- ✅ ファイルがすべてアップロードされている  
- ✅ GitHub Pagesが有効になっている
- ✅ 公開URLでページが表示される
- ✅ アプリの基本機能が動作する
- ✅ レスポンシブデザインが機能する

---

この手順で404エラーが解決され、暗記アプリが世界中からアクセス可能になります！