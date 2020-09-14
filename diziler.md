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

## 🔍 Eleman Varlığı Kontrolü

* 😅 AHK içerisinde diziler için hazır gelen bir varlık kontrolü yok
* 🤹 Yeni bir `HasVal` fonksiyonu oluşturmamız gerekmekte

```haskell
HasVal(haystack, needle) {
    for index, value in haystack
        if (value = needle)
            return index
    if !(IsObject(haystack))
        throw Exception("Bad haystack!", -1, haystack)
    return 0
}


arr := ["a", "b", "", "d"]
MsgBox % HasVal(arr, "a") "`n"           ; -> 1
       . HasVal(arr, "c") "`n"           ; -> 0
       . HasVal(arr, "d")                ; -> 4


arr := {keyA: "A", keyB: "B"}
MsgBox % HasVal(arr, "B") "`n"           ; -> keyB
       . HasVal(arr, "C")                ; -> 0


arr := {keyA: "A", 1: 0, keyC: "C"}
MsgBox % HasVal(arr, 0)   "`n"           ; -> 1
       . HasVal(arr, "C") "`n"           ; -> keyC


str := "A"
MsgBox % HasVal(str, "A")                ; -> fails -1


; İçerisinde yoksa ekleme
If !HasVal(IDlist, myID) {
    IDlist.Push(myID)
}
```

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [👨‍💻 AHK\_Scripts](https://github.com/jNizM/AHK_Scripts/blob/master/src/arrays/HasVal.ahk) alanına bakabilirsin.
{% endhint %}

## 🧐 Dizi Kontrolü

* Elemanın dizi olup olmadığını uzunluk özelliği ile kontrol ederiz
* Dizi değilse uzunluk özelliği `null` değerini döndürecektir

```csharp
names := ["yunus", "emre"]
name_count := names.Length()
if name_count
    MsgBox Dizi
    
full_name := "yunus emre"
full_name_count := full_name .Length()
if !full_name_count 
    MsgBox Dizi değil
```

## ➕ Dizileri Birleştirme

* Dizileri birleştirmek için bir önceki dizinin elemanını çıkarırız
* Diğer dizinin sonuna ekleriz

```haskell
array1 := [1,2,3,4,5]
array2 := [2,4,6]

loop % array2.length() 
    array1.push(array2.pop())
```

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [👪 merging 2 array](https://www.autohotkey.com/boards/viewtopic.php?t=40106) alanına bakabilirsin.
{% endhint %}

