---
title: Struktura to_chars_result
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: a840b8d030f0ed0d2a4afcc57e1bef1161c76ff3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212064"
---
# <a name="to_chars_result-struct"></a>Struktura to_chars_result

## <a name="syntax"></a>Składnia

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>Elementy członkowskie

|Członek|Opis|
|--|--|
|`ptr`| Jeśli `ec` jest równa `errc{}` , konwersja zakończyła się pomyślnie i `ptr` jest wskaźnikiem jednostronnym-końcowym znaków pisanych. W przeciwnym razie `ptr` ma wartość `to_chars()` parametru `last` i zawartość zakresu \[ pierwszy, ostatni) nie są określone.|
|`ec` | Kod błędu konwersji. Aby uzyskać informacje o określonych kodach błędów, zobacz [`errc`](system-error-enums.md#errc) .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<charconv>

**Przestrzeń nazw:** std

**Opcja kompilatora:** /std: c++ 17 lub nowsza, jest wymagana

## <a name="see-also"></a>Zobacz także

[to_chars](charconv-functions.md#to_chars)