---
title: Klasa is_trivially_copyable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 177ba6e688f6d7ed2b4c76eb0ede95cc288b1d5d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857535"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable — klasa

Sprawdza, czy typ jest typem trivially copyable.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest trivially copyable typu, w przeciwnym razie posiada wartość false. Typy trivially copyable mają nie operacje kopiowania nieuproszczony operacji przenoszenia i destruktorów. Ogólnie rzecz biorąc operacji kopiowania jest traktowany jako uproszczony, jeśli można ją wdrożyć jako kopię bitowe. Zarówno typy wbudowane, jak i tablice typów trivially copyable są trivially copyable.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
