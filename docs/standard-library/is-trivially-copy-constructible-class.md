---
title: is_trivially_copy_constructible — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 01c95007f1db1bcaf549398fa8865a9e51fe23d1
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33954105"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible — klasa

Testy, jeśli typ ma konstruktora kopiującego prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest klasa, która ma trivial konstruktora kopiującego, w przeciwnym razie posiada wartość false.

Konstruktor kopiujący dla klasy `T` jest proste, jeśli jest niejawnie zadeklarowany jako, klasa `T` nie ma funkcje wirtualne ani wirtualnych typów podstawowych, bezpośrednie podstawy klasy `T` mieć konstruktorów trivial kopiowania, klas wszystkich niestatyczna elementy członkowskie danych typu klasy mają trivial kopiowanie konstruktorów i klasy wszystkich członków danych niestatycznych tablicy typu klasy trivial kopiowanie konstruktorów.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
