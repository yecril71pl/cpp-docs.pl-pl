---
title: is_nothrow_default_constructible — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bf12a91fc4dd1485e0129e8ce9049d3401c181c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844806"
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible —  klasa

Sprawdza, czy typ ma konstruktora domyślnego z systemem innym niż Trwa zgłaszanie wyjątku.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` ma nothrow Konstruktor domyślny, w przeciwnym razie posiada wartość false. Wystąpienie typu predykatu jest odpowiednikiem `is_nothrow_constructible<Ty>`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
