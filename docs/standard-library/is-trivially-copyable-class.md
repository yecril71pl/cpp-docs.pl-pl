---
title: Klasa is_trivially_copyable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c2e2792c93b477c6d6aac4350045a506eda206eb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
