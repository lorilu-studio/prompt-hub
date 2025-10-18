---
title: 代码审查助手
category: 编程
subcategory: 代码审查
tags: [coding, review, debugging, intermediate]
difficulty: intermediate
target_model: gpt-4, claude
language: multilingual
author: Prompt Repository
date: 2025-06-18
description: 全面的代码审查提示词，帮助发现潜在问题和改进点
version: 1.0
---

# 代码审查助手

## 提示词内容

请对以下代码进行全面审查，并提供详细的反馈和建议：

**代码：**
```
[在这里粘贴需要审查的代码]
```

**编程语言：** [指定编程语言]

**项目背景：** [简要描述代码的功能和项目背景]

请从以下几个方面进行审查：

1. **代码质量**
   - 代码结构和组织
   - 命名规范
   - 代码简洁性
   - 重复代码

2. **性能考虑**
   - 时间复杂度
   - 空间复杂度
   - 潜在性能瓶颈
   - 优化建议

3. **安全性**
   - 输入验证
   - 数据泄露风险
   - 注入攻击防护
   - 权限控制

4. **错误处理**
   - 异常捕获
   - 错误信息
   - 边界条件处理
   - 资源释放

5. **可维护性**
   - 代码注释
   - 文档完整性
   - 模块化程度
   - 测试友好性

6. **最佳实践**
   - 语言特定最佳实践
   - 设计模式应用
   - 代码风格一致性

请提供：
- 发现的问题清单（按优先级排序）
- 具体的改进建议
- 重构后的代码示例（如适用）
- 总体评价和评分（1-10分）

## 使用指南

### 使用场景
- 代码提交前的自我审查
- 团队代码审查流程
- 学习代码质量评估标准
- 提升代码质量技能

### 输入要求
- 需要审查的代码（必需）
- 编程语言（必需）
- 项目背景（可选，但建议提供）

### 预期输出
- 结构化的代码审查报告
- 具体问题和改进建议
- 代码示例（如适用）
- 总体评价

### 使用技巧
- 提供尽可能完整的项目背景，以获得更准确的审查
- 对于大型代码文件，可以分部分进行审查
- 重点关注您最关心的审查方面

## 示例

### 示例1
**输入：**
```
代码：
function calculatePrice(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += items[i].price * items[i].quantity;
  }
  return total;
}

编程语言：JavaScript
项目背景：电商网站的购物车价格计算功能
```

**输出：**
```
# 代码审查报告

## 发现的问题清单（按优先级排序）

### 高优先级
1. **缺少输入验证**：函数没有验证输入参数的有效性
2. **潜在精度问题**：浮点数计算可能导致精度误差

### 中优先级
3. **性能可优化**：可以使用reduce方法简化代码
4. **缺少错误处理**：没有处理items为null或undefined的情况

### 低优先级
5. **缺少注释**：函数缺少文档注释

## 具体的改进建议

1. **添加输入验证**：
   ```javascript
   function calculatePrice(items) {
     if (!Array.isArray(items)) {
       throw new Error('Invalid input: items must be an array');
     }
     // ...
   }
   ```

2. **处理精度问题**：
   ```javascript
   // 使用toFixed或专门的数学库处理浮点数精度
   return Number(total.toFixed(2));
   ```

3. **优化代码结构**：
   ```javascript
   function calculatePrice(items) {
     if (!Array.isArray(items)) {
       throw new Error('Invalid input: items must be an array');
     }
     
     return items.reduce((total, item) => {
       if (!item || typeof item.price !== 'number' || typeof item.quantity !== 'number') {
         throw new Error('Invalid item format');
       }
       return total + (item.price * item.quantity);
     }, 0);
   }
   ```

## 重构后的代码示例

```javascript
/**
 * 计算购物车中所有商品的总价格
 * @param {Array} items - 商品数组，每个商品应包含price和quantity属性
 * @returns {number} 总价格（保留两位小数）
 * @throws {Error} 当输入无效时抛出错误
 */
function calculatePrice(items) {
  // 输入验证
  if (!Array.isArray(items)) {
    throw new Error('Invalid input: items must be an array');
  }
  
  if (items.length === 0) {
    return 0;
  }
  
  // 计算总价
  const total = items.reduce((sum, item) => {
    // 验证每个商品的有效性
    if (!item || typeof item.price !== 'number' || typeof item.quantity !== 'number') {
      throw new Error('Invalid item format: each item must have price and quantity properties');
    }
    
    if (item.price < 0 || item.quantity < 0) {
      throw new Error('Invalid item values: price and quantity must be non-negative');
    }
    
    return sum + (item.price * item.quantity);
  }, 0);
  
  // 处理浮点数精度问题
  return Number(total.toFixed(2));
}
```

## 总体评价和评分

**评分：6/10**

**优点：**
- 基本功能实现正确
- 逻辑简单明了

**主要问题：**
- 缺少输入验证和错误处理
- 没有考虑边界情况
- 代码可读性和可维护性有待提升

**总结：** 代码实现了基本功能，但在健壮性和可维护性方面需要改进。
```

## 变体与扩展

### 变体1：特定关注点审查
在提示词中添加："请特别关注[特定方面，如安全性/性能]"

### 变体2：对比审查
提供两个版本的代码，要求："请比较这两个版本的代码，并推荐更好的实现"

### 变体3：重构请求
在提示词中添加："请直接提供重构后的完整代码，不需要详细解释"

## 相关提示词

- [代码优化助手](../coding/code-optimization.md)
- [调试助手](../coding/debugging-assistant.md)
- [单元测试生成器](../coding/unit-test-generator.md)

## 注意事项

1. 对于复杂或大型代码，建议分部分进行审查
2. 审查结果应结合实际项目需求和约束条件
3. 某些建议可能需要权衡性能、可读性和开发时间

## 反馈与改进

如果您有任何改进建议或使用反馈，请提交Issue或Pull Request。

---

*最后更新：2025-06-18*