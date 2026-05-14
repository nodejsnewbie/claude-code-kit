---
name: cc-docs
description: 更新或生成代码文档
tags: 文档, 注释, README
allowed-tools: Read, Edit, Write, Grep, Glob
---

# 文档维护

**核心原则：代码变了，文档同步。**

## 操作步骤

1. 识别变更的函数、类、模块
2. 更新 docstring，确保参数和返回值有说明
3. 如有 README 影响，同步更新
4. 确保格式一致（Google style / NumPy style）

## Docstring 模板

```python
def func(param1: str, param2: int) -> bool:
    """简短描述。

    Args:
        param1: 参数1说明
        param2: 参数2说明

    Returns:
        返回值说明

    Raises:
        ValueError: 异常说明
    """
```

## 注意事项
- 不写显而易见的注释
- 公共 API 必须有 docstring
- 私有函数按需添加
