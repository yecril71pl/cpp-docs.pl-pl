---
title: Klasa is_trivially_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448361"
---
# <a name="istriviallymoveconstructible-class"></a>Klasa is_trivially_move_constructible

Testuje, czy typ ma Konstruktor prostego przenoszenia.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Br*\
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie predykatu typu ma wartość true, jeśli typ *ty* jest klasą, która ma prosty Konstruktor przenoszenia, w przeciwnym razie ma wartość false.

Konstruktor przenoszenia dla klasy *ty* jest prosty, jeśli:

jest on niejawnie zadeklarowany

jego typy parametrów są równoważne z niejawną deklaracją

Klasa *ty* nie ma żadnych funkcji wirtualnych

Klasa *ty* nie ma wirtualnych baz.

Klasa nie ma niestatycznych elementów członkowskich danych

wszystkie bezpośrednie bazy klasy *ty* mają konstruktorów prostego przenoszenia

klasy wszystkich niestatycznych składowych danych typu klasy mają konstruktorów prostych przenoszenia

klasy wszystkich niestatycznych składowych danych typu Array klasy mają konstruktorów prostego przenoszenia

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)
