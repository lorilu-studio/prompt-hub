# 提示词分类系统

本文档定义了提示词仓库的分类系统和标签规范，以便于组织和检索提示词。

## 主分类

### 1. 写作 (Writing)
包含各种写作相关的提示词，如文章创作、编辑、润色等。

**子分类：**
- 创意写作 (Creative Writing)
- 技术写作 (Technical Writing)
- 学术写作 (Academic Writing)
- 营销文案 (Marketing Copy)
- 内容编辑 (Content Editing)

### 2. 编程 (Coding)
包含编程、开发和技术相关的提示词。

**子分类：**
- 代码生成 (Code Generation)
- 代码审查 (Code Review)
- 调试 (Debugging)
- 架构设计 (Architecture Design)
- 技术文档 (Technical Documentation)

### 3. 分析 (Analysis)
包含数据分析、研究和批判性思维相关的提示词。

**子分类：**
- 数据分析 (Data Analysis)
- 市场研究 (Market Research)
- 批判性思维 (Critical Thinking)
- 问题解决 (Problem Solving)
- 决策支持 (Decision Support)

### 4. 创意 (Creative)
包含创意生成和艺术相关的提示词。

**子分类：**
- 创意构思 (Ideation)
- 艺术创作 (Art Creation)
- 设计思维 (Design Thinking)
- 故事创作 (Storytelling)
- 创新方案 (Innovation)

### 5. 教育 (Education)
包含学习和教学相关的提示词。

**子分类：**
- 学习方法 (Learning Methods)
- 教学设计 (Teaching Design)
- 知识解释 (Knowledge Explanation)
- 技能培训 (Skill Training)
- 评估测试 (Assessment)

### 6. 商业 (Business)
包含商业应用和管理相关的提示词。

**子分类：**
- 商业策略 (Business Strategy)
- 项目管理 (Project Management)
- 市场营销 (Marketing)
- 客户服务 (Customer Service)
- 财务分析 (Financial Analysis)

## 标签系统

标签用于提供更细粒度的分类和检索功能。每个提示词可以有多个标签。

### 常用标签

#### 难度级别
- `beginner` - 初级
- `intermediate` - 中级
- `advanced` - 高级
- `expert` - 专家级

#### 应用场景
- `general-purpose` - 通用
- `specific-task` - 特定任务
- `workflow` - 工作流
- `one-shot` - 单次使用
- `iterative` - 迭代使用

#### 目标模型
- `gpt-3.5` - 适用于GPT-3.5
- `gpt-4` - 适用于GPT-4
- `claude` - 适用于Claude
- `gemini` - 适用于Gemini
- `universal` - 通用所有模型

#### 语言
- `chinese` - 中文
- `english` - 英文
- `multilingual` - 多语言

#### 特殊属性
- `template` - 模板
- `example` - 示例
- `tutorial` - 教程
- `reference` - 参考

## 文件命名规范

为了保持一致性，请遵循以下文件命名规范：

1. 使用英文文件名
2. 使用小写字母和连字符 (-) 分隔单词
3. 文件名应简明扼要地描述提示词内容
4. 使用 `.md` 扩展名

示例：
- `creative-story-starter.md`
- `code-review-checklist.md`
- `data-analysis-template.md`

## 元数据规范

每个提示词文件应包含以下元数据（YAML前置格式）：

```yaml
---
title: 提示词标题
category: 主分类
subcategory: 子分类
tags: [标签1, 标签2, 标签3]
difficulty: beginner|intermediate|advanced|expert
target_model: gpt-3.5|gpt-4|claude|gemini|universal
language: chinese|english|multilingual
author: 作者名
date: YYYY-MM-DD
description: 简短描述（不超过100字符）
version: 1.0
---
```

## 分类扩展

如果需要添加新的主分类或子分类，请遵循以下步骤：

1. 在相应的目录中创建新目录
2. 更新本文档，添加新分类的描述
3. 创建至少一个示例提示词文件
4. 提交Pull Request，说明新分类的必要性

## 标签管理

标签系统应保持简洁和有用。添加新标签时，请考虑：

1. 标签是否具有广泛的适用性
2. 是否与现有标签重复
3. 是否符合标签命名规范

如有疑问，请在Issue中讨论。