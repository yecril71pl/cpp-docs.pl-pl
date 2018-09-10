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
ms.openlocfilehash: 9ad5631fc5d689ccb6632ac230aebdaf40f18f80
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106486"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible, klasa

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
