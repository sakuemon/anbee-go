# Copilot用指示 — anbee-go

目的: このリポジトリで動作するCopilot形式のアシスタント向けの実務的な指示。

# 前提条件
- 回答は必ず日本語ですること。
- コードを変更するときは許可を得ること。

## すぐ使えるコマンド（プロジェクト固有）
- ビルド（全パッケージ）:
  - go build ./...
- テスト（全体）:
  - go test ./... -v
- 単一テストを実行（パッケージ内）:
  - cd <pkg-dir> && go test -run '^TestName$' -v -race
- テスト名で絞ってパッケージ横断実行:
  - go test ./... -run 'TestName' -v

## 高水準アーキテクチャ（現状）
- モジュール名: "anbee-go"（go.mod）、Goバージョン: go.modを参照。
- 現時点ではモジュールメタデータのみで、Goソースはコミットされていません。
- リポジトリを素早く把握するための検索:
  - `go list ./...` でパッケージ一覧を得る

## キーとなる慣習・ルール
- ビルド/テストはGoツールチェーンを使用。go.modに記載されているバージョンを前提にする。
- CI/workflow ファイルは未検出。GitHub Actions を追加する場合は `.github/workflows/` 配下に置く。
- 自動化やCopilot支援でコミットを作る場合、コミットメッセージに以下のトレーラを含めること:
  - `Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>`

## チェックすべきAIアシスタント関連ファイル
- 存在すれば取り込むべきファイル例: CLAUDE.md, .cursorrules, .cursor/rules/, AGENTS.md, .windsurfrules, CONVENTIONS.md, AIDER_CONVENTIONS.md, .clinerules
- 現在これらは存在しません（リポジトリスキャンで改めて確認してください）。

## 将来のCopilotセッション向けメモ
- 現状リポジトリは最小限なので、作業前に必ず最新スキャンを行うこと。
- 実装場所を特定するには具体的な検索（glob/grep/view）を優先し、存在しないレイアウトを前提にしないこと。
