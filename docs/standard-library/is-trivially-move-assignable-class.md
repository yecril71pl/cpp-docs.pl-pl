---
title: is_trivially_move_assignable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19346075d0b52be7820adfe60e77e0f76113bc98
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44099912"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable, klasa

Sprawdza, czy typ ma operator przypisania przenoszenia prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *Ty* to klasa, która ma proste operator przypisania przenoszenia, w przeciwnym razie przechowuje wartość false.

Operator przypisania przenoszenia dla klasy *Ty* jest proste jeśli:

Domyślnie jest ona udostępniana

Klasa *Ty* ma żadnych funkcji wirtualnych

Klasa *Ty* ma nie baz wirtualnych

klasy wszystkie składowe danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania

klasy wszystkie składowe danych niestatycznych typu tablicowego klasy mają trivial przenoszące operatory przypisania

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
