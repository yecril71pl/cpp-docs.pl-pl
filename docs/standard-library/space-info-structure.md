---
title: space_info — Struktura
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: 2a9856746a8bbc796871663a81bd8911d34dcd4a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457552"
---
# <a name="spaceinfo-structure"></a>space_info — Struktura

Zawiera informacje o woluminie.

## <a name="syntax"></a>Składnia

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`unsigned long long capacity`|Reprezentuje łączną liczbę bajtów, które może reprezentować wolumin.|
|`unsigned long long free`|Reprezentuje liczbę bajtów, które nie są używane do reprezentowania danych w woluminie.|
|`unsigned long long available`|Reprezentuje liczbę bajtów, które są dostępne do reprezentowania danych w woluminie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> systemu plików

**Przestrzeń nazw:** std:: eksperymentalne:: filesystem

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Nawigacja w systemie plikówC++()](../standard-library/file-system-navigation.md)
