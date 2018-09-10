---
title: is_trivially_copy_constructible, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1924b82f7c3035ea2aecb463199558c9ead45c91
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102068"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible — klasa

Sprawdza, czy typ ma konstruktora kopiującego prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu ma wartość true, jeśli typ *T* to klasa, która ma Konstruktor kopiujący prosta w przeciwnym razie przechowuje wartość false.

Konstruktor kopiujący klasy *T* jest proste, jeśli zostanie ona niejawnie zadeklarowana, klasa *T* nie ma funkcje wirtualne ani baz wirtualnych bezpośrednie podstawy klasy *T* mają Konstruktory kopiujące prosta, klasy wszystkie składowe danych niestatycznych typu klasy mają konstruktory kopiujące trivial i klasy wszystkie składowe danych niestatycznych typu tablicowego klasy mają konstruktory kopiujące trivial.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
