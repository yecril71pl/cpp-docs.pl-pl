---
title: is_trivially_copy_assignable, klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 831e7c5afdd39980876a8e8284a68fec2084a4e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630987"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable, klasa

Sprawdza, czy typ ma operator przypisania kopiowania prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* to klasa, która ma proste operatora przypisanej kopii, w przeciwnym razie przechowuje wartość false.

Konstruktor przypisania dla klasy *T* jest proste, jeśli jest niejawnie podany, klasa *T* ma żadnych funkcji wirtualnych klasy *T* ma nie baz wirtualnych klas Wszyscy członkowie danych niestatycznych typu klasy mają operatory przypisania proste, a klasy wszystkie składowe danych niestatycznych tablicy typu klasy mieć operatory przypisania prosta.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
