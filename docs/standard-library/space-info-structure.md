---
title: space_info, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b143a37c306320223ac3abe430e41c9750c8ece9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025786"
---
# <a name="spaceinfo-structure"></a>space_info — Struktura

Przechowuje informacje o woluminie.

## <a name="syntax"></a>Składnia

```cpp
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`unsigned long long available`|Reprezentuje liczbę bajtów, które są dostępne do reprezentowania danych w woluminie.|
|`unsigned long long capacity`|Reprezentuje całkowita liczba bajtów reprezentujących woluminu.|
|`unsigned long long free`|Reprezentuje liczbę bajtów, które nie są używane do reprezentowania danych w woluminie.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[miejsce](http://msdn.microsoft.com/7fce0b0e-523b-4598-b218-47245d0204ca)<br/>
[Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)<br/>
