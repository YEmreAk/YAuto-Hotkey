---
description: AutoHotkey ile dizi işlemleri
---

# 🚄 Diziler

## ✨ Tanımlama

* Dizilerin tanımlanması `<name> := [<var>, <var2> ...]` şeklinde yapılır
* Dizilerin ilk elemanı 1'den başlar
* Dizi elemanlarına `<array>[<index>]` şeklinde erişilir

## 🔤 String Dizileri

```haskell
array := ["one", "two", "three"]

; Iterate from 1 to the end of the array:
Loop % array.Length()
    MsgBox % array[A_Index]

; Enumerate the array's contents:
For index, value in array
    MsgBox % "Item " index " is '" value "'"
```



