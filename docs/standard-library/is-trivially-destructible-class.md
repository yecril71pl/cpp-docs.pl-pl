---
title: Klasa is_trivially_destructible | Dokumentacja firmy Microsoft
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
- type_traits/std::is_trivially_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10f83d6ace116d48e9c117724b5b408721de625c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallydestructible-class"></a>is_trivially_destructible — klasa

Sprawdza, czy typ jest trivially które można zniszczyć.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Parametry

`T` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest które można zniszczyć typu, a destruktor jest znana kompilatora do użycia ma nieuproszczone operacji. Przechowuje w przeciwnym razie wartość false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
