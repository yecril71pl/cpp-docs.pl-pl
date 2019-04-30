---
title: is_trivially_copy_constructible — klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: aa6d6b19ae2bd5d6967c57db61c5697c0c6153e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413440"
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
