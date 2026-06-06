# Pythonのリスト内包表記ってなに？

## 概要

Pythonのリスト内包表記は、`for` 文を使って新しいリストを作る処理を、短く読みやすく書くための構文です。

## 詳細説明

基本の形は次のとおりです。

```python
[式 for 変数 in iterable]
```

たとえば、リストの各要素を2倍した新しいリストを作るならこう書けます。

```python
nums = [1, 2, 3]
result = [n * 2 for n in nums]

print(result)  # [2, 4, 6]
```

これは、通常の `for` 文で書く次の処理をコンパクトにしたものです。

```python
nums = [1, 2, 3]
result = []

for n in nums:
    result.append(n * 2)
```

条件を付けて、特定の要素だけを取り出すこともできます。

```python
nums = [1, 2, 3, 4, 5, 6]
evens = [n for n in nums if n % 2 == 0]

print(evens)  # [2, 4, 6]
```

便利な書き方ですが、式が複雑になりすぎると読みづらくなります。短く書けることよりも、あとから見て意味が分かりやすいかを優先して使うのがコツです。

## 参照URL

- https://docs.python.org/ja/3/tutorial/datastructures.html#list-comprehensions
- https://peps.python.org/pep-0202/
