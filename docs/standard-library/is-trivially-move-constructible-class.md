---
title: is_trivially_move_constructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316ffdee4905ff8a35baef7137ff7f28a2846786
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958195"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible, klasa

Konstruktor przenoszący sprawdza, czy typ ma proste.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty* typ do zapytania.

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
