---
title: space_info — Struktura
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: b6998f4ac7ced2d85063186edbd47227b6d24ca5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559136"
---
# <a name="spaceinfo-structure"></a>space_info — Struktura

Przechowuje informacje o woluminie.

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
|`unsigned long long capacity`|Reprezentuje całkowita liczba bajtów reprezentujących woluminu.|
|`unsigned long long free`|Reprezentuje liczbę bajtów, które nie są używane do reprezentowania danych w woluminie.|
|`unsigned long long available`|Reprezentuje liczbę bajtów, które są dostępne do reprezentowania danych w woluminie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)<br/>
