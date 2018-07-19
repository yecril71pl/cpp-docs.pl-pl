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
ms.openlocfilehash: ae0db2b789e16a39396a329a64dfb8794eef5775
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961912"
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable, klasa

Sprawdza, czy typ ma operator przypisania przenoszenia prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty* typ do zapytania.

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
