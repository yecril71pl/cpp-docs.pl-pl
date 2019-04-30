---
title: is_trivially_move_constructible Class
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: a1aef356716fac903b4e44a358602c709572e8ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413398"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible Class

Konstruktor przenoszący sprawdza, czy typ ma proste.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma Konstruktor przenoszący prosta w przeciwnym razie przechowuje wartość false.

Konstruktor przenoszący dla klasy *Ty* jest proste jeśli:

jest niejawnie zadeklarowana

jego typy parametrów są równoważne do tych deklaracji niejawnej

Klasa *Ty* ma żadnych funkcji wirtualnych

Klasa *Ty* ma nie baz wirtualnych

Klasa nie ma danych niestatycznych elementów członkowskich

wszystkie bezpośrednio baz klasy *Ty* ma konstruktorów przenoszących prosta

klasy wszystkie składowe danych niestatycznych typu klasy ma konstruktorów przenoszących prosta

klasy wszystkie składowe danych niestatycznych typu tablicowego klasy ma konstruktorów przenoszących prosta

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
