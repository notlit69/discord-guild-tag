# NOTE: This only applies to guilds created before `5/9/2025, 12:30:00 AM IST`

# How to get 10% rollout for `Server Tag` Instead of 0.5%?

Hash calculation
```python
hash_value = mmh3.hash(f"2025-02_skill_trees:{guild_id}", signed=False) % 10000
```

Most github repos related to this are calculating the check with ranges `(10, 20)` and `(60, 100)`, but valid ranges are `(10, 20), (60, 100), (150, 200), (600, 1000), (1500, 2000)`.

Old Validation:
```python
is_valid = (10 <= hash_value < 20) or (60 <= hash_value < 100)
```
Correct Validation:
```python
ranges = [(10, 20), (60, 100), (150, 200), (600, 1000), (1500, 2000)]
is_valid = any(start <= hash_value < end for start, end in valid_ranges)
```
