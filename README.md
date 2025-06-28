# AI Development Methodology for Cursor

A comprehensive set of Cursor rules implementing a three-step AI-driven development methodology, enhanced with Gherkin syntax for acceptance criteria and Test-Driven Development (TDD) practices.

**Note**: All rules are written in Traditional Chinese. Users can easily translate them to English or other languages as needed, given the convenience of modern translation tools.

## Overview

This project is based on the three-step AI programming method presented in [this YouTube video](https://youtu.be/fD4ktSkNCw4?si=nhYH28nSIT3PUONj), with original rules from [snarktank/ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks).

The rules have been translated to Traditional Chinese and enhanced with additional elements:
- **Gherkin syntax** for acceptance criteria
- **Test-Driven Development (TDD)** methodology
- **Structured task management** with clear validation steps

## How It Works

The methodology follows a three-step process:

1. **@create-prd** - Create a high-level Product Requirements Document (PRD)
2. **@generate-tasks** - Generate detailed task lists from the PRD
3. **@process-task-list** - Iteratively complete each task using TDD

## Usage

### Step 1: Create PRD (@create-prd)
Start by thinking about what you want to build, then use `@create-prd` to establish a high-level execution plan. The AI will:
- Ask clarifying questions to understand your requirements
- Generate a comprehensive PRD with user stories, acceptance criteria, and technical considerations
- Save the document as `prd-[feature-name].md` in the `/tasks` directory

### Step 2: Generate Tasks (@generate-tasks)
Once your PRD is complete, use `@generate-tasks` to break down the work into actionable tasks. This will:
- Analyze the PRD and create Gherkin acceptance criteria
- Generate high-level parent tasks following TDD methodology
- Break down each parent task into detailed sub-tasks
- Identify relevant files and dependencies
- Save the task list as `tasks-[prd-filename].md`

### Step 3: Process Tasks (@process-task-list)
Finally, use `@process-task-list` to iteratively complete each task. The process follows strict TDD cycles:
- **Structure Definition**: Create interfaces, classes, or function stubs
- **Test Structure**: Write test declarations without implementation
- **Test Logic (Red Phase)**: Implement full test logic and verify failures
- **Feature Implementation (Green Phase)**: Implement functionality to pass tests

## Key Features

### Enhanced TDD Workflow
- **Component-by-component development**: Complete full TDD cycles for each component before moving to the next
- **Test-first approach**: Write tests before implementation
- **Red-Green validation**: Ensure tests fail first, then implement to pass
- **Developer confirmation**: Pause for approval at key stages

### Gherkin Acceptance Criteria
- Uses Cucumber's Gherkin syntax for clear, testable acceptance criteria
- Enables direct validation through MCP (Model Context Protocol)
- Supports both UI operations and command-line validations

### Structured Task Management
- Clear parent-child task relationships
- Checkbox-based progress tracking
- File dependency mapping
- Iterative completion with user approval

## Getting Started

1. Copy the `.cursor` directory to your project root
2. Use `@create-prd` to start planning your feature
3. Follow the three-step methodology for structured development

---

# AI 開發方法論 for Cursor

一套完整的 Cursor 規則集，實現三步驟 AI 驅動開發方法論，並增強了 Gherkin 語法驗收條件和測試驅動開發 (TDD) 實踐。

**注意**：所有規則都是使用繁體中文撰寫。使用者如有需要，可以利用現代翻譯工具的便利性，輕鬆將規則翻譯成英文或其他語言。

## 概述

此專案基於[這個 YouTube 影片](https://youtu.be/fD4ktSkNCw4?si=nhYH28nSIT3PUONj)中提出的三步驟 AI 程式設計方法，原始規則來自 [snarktank/ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks)。

規則已翻譯成繁體中文並增強了額外元素：
- **Gherkin 語法**用於驗收條件
- **測試驅動開發 (TDD)** 方法論
- **結構化任務管理**具有明確的驗證步驟

## 運作方式

方法論遵循三步驟流程：

1. **@create-prd** - 建立高階產品需求文件 (PRD)
2. **@generate-tasks** - 從 PRD 生成詳細任務清單
3. **@process-task-list** - 使用 TDD 迭代完成每個任務

## 使用方法

### 步驟 1：建立 PRD (@create-prd)
首先思考您要建立什麼，然後使用 `@create-prd` 建立高階執行計畫。AI 將會：
- 詢問澄清問題以了解您的需求
- 生成包含使用者故事、驗收條件和技術考量的綜合 PRD
- 將文件儲存為 `/tasks` 目錄中的 `prd-[功能名稱].md`

### 步驟 2：生成任務 (@generate-tasks)
PRD 完成後，使用 `@generate-tasks` 將工作分解為可執行的任務。這將：
- 分析 PRD 並建立 Gherkin 驗收條件
- 遵循 TDD 方法論生成高階父任務
- 將每個父任務分解為詳細的子任務
- 識別相關檔案和依賴關係
- 將任務清單儲存為 `tasks-[prd-檔案名].md`

### 步驟 3：處理任務 (@process-task-list)
最後，使用 `@process-task-list` 迭代完成每個任務。流程遵循嚴格的 TDD 循環：
- **結構定義**：建立介面、類別或函數存根
- **測試結構**：撰寫測試宣告但不實作
- **測試邏輯（紅色階段）**：實作完整測試邏輯並驗證失敗
- **功能實作（綠色階段）**：實作功能以通過測試

## 主要特色

### 增強的 TDD 工作流程
- **逐組件開發**：在移至下一個組件前完成每個組件的完整 TDD 循環
- **測試優先方法**：在實作前撰寫測試
- **紅綠驗證**：確保測試先失敗，然後實作以通過
- **開發者確認**：在關鍵階段暫停等待批准

### Gherkin 驗收條件
- 使用 Cucumber 的 Gherkin 語法提供清晰、可測試的驗收條件
- 支援透過 MCP (Model Context Protocol) 直接驗證
- 支援 UI 操作和命令列驗證

### 結構化任務管理
- 清晰的父子任務關係
- 基於勾選框的進度追蹤
- 檔案依賴關係對應
- 需要使用者批准的迭代完成

## 開始使用

1. 將 `.cursor` 目錄複製到您的專案根目錄
2. 使用 `@create-prd` 開始規劃您的功能
3. 遵循三步驟方法論進行結構化開發