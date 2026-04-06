# Python'da `sorted()`

Python'da ro'yxatlarni saralash uchun `sorted()` funksiyasi va `.sort()` metodi ishlatiladi.

---

## sorted() va .sort() farqi

```python
asl = [3, 1, 4, 1, 5, 9]

yangi = sorted(asl)
print(asl)    # [3, 1, 4, 1, 5, 9]  — o'zgarmadi
print(yangi)  # [1, 1, 3, 4, 5, 9]  — yangi ro'yxat

asl.sort()
print(asl)    # [1, 1, 3, 4, 5, 9]  — o'zgarib ketdi
```

- `sorted()` — aslini o'zgartirmaydi, yangi ro'yxat qaytaradi
- `.sort()` — ro'yxatni o'z ichida o'zgartiradi, `None` qaytaradi

---

## Oddiy saralash

```python
sonlar = [5, 2, 8, 1, 9, 3]
print(sorted(sonlar))
# [1, 2, 3, 5, 8, 9]

ismlar = ["Zafar", "Ali", "Malika", "Bobur"]
print(sorted(ismlar))
# ['Ali', 'Bobur', 'Malika', 'Zafar']
```

---

## Teskari tartib — reverse=True

```python
sonlar = [5, 2, 8, 1, 9, 3]
print(sorted(sonlar, reverse=True))
# [9, 8, 5, 3, 2, 1]
```

---

## key parametri

Har bir elementga funksiya qo'llab, shu natijaga qarab saralaydi.

```python
# Uzunlikka qarab
sozlar = ["olma", "o'rik", "qovun", "banan", "nok"]
print(sorted(sozlar, key=len))
# ['nok', 'olma', "o'rik", 'banan', 'qovun']

# Absolut qiymatga qarab
sonlar = [-7, 3, -1, 8, -4]
print(sorted(sonlar, key=abs))
# [-1, 3, -4, -7, 8]

# Katta-kichik harfsiz (case-insensitive)
ismlar = ["zafar", "Ali", "malika", "Bobur"]
print(sorted(ismlar, key=str.lower))
# ['Ali', 'Bobur', 'malika', 'zafar']
```

---

## Lambda bilan saralash

```python
talabalar = [
    ("Ali",     85),
    ("Vali",    92),
    ("Guli",    78),
    ("Dilnoza", 92),
]

# Ballga qarab
print(sorted(talabalar, key=lambda x: x[1]))
# [('Guli', 78), ('Ali', 85), ('Vali', 92), ('Dilnoza', 92)]

# Ball kamayish, ism o'sish
print(sorted(talabalar, key=lambda x: (-x[1], x[0])))
# [('Dilnoza', 92), ('Vali', 92), ('Ali', 85), ('Guli', 78)]
```

---

## Lug'atlarni saralash

```python
narxlar = {"olma": 3500, "banan": 8000, "anor": 15000, "nok": 6000}

# Qiymatga qarab saralash
for nom, narx in sorted(narxlar.items(), key=lambda x: x[1]):
    print(f"{nom}: {narx} so'm")

# olma: 3500 so'm
# nok: 6000 so'm
# banan: 8000 so'm
# anor: 15000 so'm
```

---

## Ko'p mezonli saralash

```python
xodimlar = [
    ("Karimov",  "Zafar", 5),
    ("Rahimov",  "Ali",   3),
    ("Karimov",  "Bobur", 7),
    ("Rahimov",  "Guli",  5),
]

# Familiya (o'sish) → Ish staji (kamayish)
natija = sorted(xodimlar, key=lambda x: (x[0], -x[2]))
for fam, ism, staj in natija:
    print(f"{fam} {ism} — {staj} yil")

# Karimov Bobur — 7 yil
# Karimov Zafar — 5 yil
# Rahimov Guli  — 5 yil
# Rahimov Ali   — 3 yil
```
