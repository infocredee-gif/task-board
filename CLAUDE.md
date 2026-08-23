# CLAUDE.md

このファイルは、このリポジトリで作業する際の Claude Code (claude.ai/code) 向けガイダンスです。

## プロジェクト概要

**プロジェクト名**: task-board

タスク管理アプリ(カンバンボード形式などを想定)を新規開発するプロジェクト。

## GitHubリポジトリ

https://github.com/infocredee-gif/task-board.git

## デプロイ先

https://infocredee-gif.github.io/task-board/

`main` ブランチへの push をトリガーに GitHub Actions
([.github/workflows/deploy.yml](.github/workflows/deploy.yml)) が
ビルドして GitHub Pages に自動デプロイする。

## 技術スタック

- React 18 (関数コンポーネント + Hooks。クラスコンポーネントは使わない)
- Vite 5 (ビルド・開発サーバー。`@vitejs/plugin-react` を使用)
- 素の CSS(コンポーネント単位のファイル分割。CSS Modules やCSS-in-JSは使わない)
- 状態管理ライブラリは使わず、`useState` / `useEffect` の範囲で完結させる
- データ永続化は `localStorage`(バックエンド API は現時点では無し)
- ルーティングライブラリは未導入(単一画面のため)

## コンポーネントの命名規約

- コンポーネントファイルは `PascalCase.jsx`(例: `App.jsx`)。
- コンポーネント名(関数名)はファイル名と一致させる。
- 1ファイル1コンポーネントを基本とする。
- スタイルはコンポーネントと同名の CSS ファイルを同じディレクトリに置く
  (例: `App.jsx` ↔ `App.css`)。アプリ全体に関わるグローバルなスタイルのみ
  `index.css` に置く。
- エントリーポイントは `main.jsx` に固定する。

## 対応方針

- 回答は必ず日本語で行う。

## Git 運用ルール

- このプロジェクトは Git で管理する。作業前に `.git` が存在しない場合は `git init` を行い、
  GitHub 上にリモートリポジトリを作成・接続する。
- **コードを変更するたびに、コミットして GitHub にプッシュする。**
  - 1つの変更(機能追加・修正・リファクタリングなど)が完了したら、都度コミットを作成する。
  - コミット後は必ず `git push` を実行し、リモート(GitHub)に反映する。
  - 変更を溜め込んでからまとめてプッシュするのではなく、意味のある単位ごとに
    こまめにコミット・プッシュを行う。
- コミットメッセージは変更内容が分かるよう簡潔に記述する。
- force push など破壊的な操作は、明示的な指示がない限り行わない。
