---
title: is_trivially_copyable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19bed4a455ea2b0b894ba842f349aa304e9f261d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964686"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable, klasa

Sprawdza, czy określony typ jest typem kopiowania.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* jest trywialne typu, w przeciwnym razie przechowuje wartość false. Typy trywialne mieć nie operacji kopiowania nietrywialnymi operacji przenoszenia i destruktory. Ogólnie rzecz biorąc operacja kopiowania jest uważane za trywialne, jeśli można zaimplementować jako kopię bitową. Typy wbudowane i tablic typów trywialne są kopiowania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
