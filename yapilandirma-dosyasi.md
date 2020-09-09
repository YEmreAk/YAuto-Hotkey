---
description: >-
  AutoHotkey (AHK) ile temel yapılandırma dosyası işlemleri ve yapılandırma
  dosyası yönetimi
---

# ⚙️ Yapılandırma Dosyası

## ✍ Dosyaya Yazma

* 💠 IniWrite metodu ile yapılır

```c
IniWrite, this is a new value, %A_ScriptDir%\temp.ini, section2, key1
IniWrite, this is a next value, %A_ScriptDir%\temp.ini, section2, key2
```

```ocaml
[section2]
key1=this is a newvalue
key2=this is a next value
```

{% hint style="info" %}
‍🧙‍♂ Detaylar için [`IniWrite`](https://www.autohotkey.com/docs/commands/IniWrite.htm) alanına bakmanda fayda var
{% endhint %}

## 👁️ Dosyadan Okuma

| 💠 Kod | 📝 Açıklama |
| :--- | :--- |
| `IniRead, OutputVar, Filename, Section, Key, Default` | `key` değerini okuma yoksa `Default` değerini alma |
| `IniRead, OutputVar, Filename, Section, Key` | `key` okuma |
| `IniRead, OutputVarSection, Filename, Section` | `section`değerlerini okuma |
| `IniRead, OutputVarSectionNames, Filename` | Tüm dosyadaki `section` verilerini okuma |

![](.gitbook/assets/image.png)

```c
IniRead, OutputVar, %A_ScriptDir%\temp.ini, section2, key2
if (OutputVar != "ERROR") {
    MsgBox, The value is %OutputVar%.
}
```

{% hint style="info" %}
‍🧙‍♂ Detaylar için [`IniRead`](https://www.autohotkey.com/docs/commands/IniRead.htm) alanına bakmanda fayda var
{% endhint %}

## 🔗 Faydalı Kaynaklar

{% embed url="https://www.autohotkey.com/boards/viewtopic.php?t=49997" %}

