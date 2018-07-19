---
title: is_trivially_copy_assignable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7c4c748d7328f534aebfb2133c72635bbdc36f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953969"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable, klasa

Sprawdza, czy typ ma operator przypisania kopiowania prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T* typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* to klasa, która ma proste operatora przypisanej kopii, w przeciwnym razie przechowuje wartość false.

Konstruktor przypisania dla klasy *T* jest proste, jeśli jest niejawnie podany, klasa *T* ma żadnych funkcji wirtualnych klasy *T* ma nie baz wirtualnych klas Wszyscy członkowie danych niestatycznych typu klasy mają operatory przypisania proste, a klasy wszystkie składowe danych niestatycznych tablicy typu klasy mieć operatory przypisania prosta.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
