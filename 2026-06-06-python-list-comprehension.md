# Pythonのリスト内包表記

## 概要
for文でリストを作る処理を1行で書ける書き方。

## 基本の形
```python
[式 for 変数 in iterable]
```

## 例
```python
nums = [1, 2, 3]
result = [n * 2 for n in nums]  # [2, 4, 6]
```

## 条件付き
```python
evens = [n for n in nums if n % 2 == 0]  # 偶数だけ
```

## 参照
- https://docs.python.org/ja/3/tutorial/datastructures.html#list-comprehensions
