---
title: Klasa underlying_type | Dokumentacja firmy Microsoft
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
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52bf41cdcb40c88f32adc6d0384bea60f5997286
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="underlyingtype-class"></a>underlying_type — klasa

Tworzy integralną typ podstawowy dla typu wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parametry

`T` Typ do zmodyfikowania.

## <a name="remarks"></a>Uwagi

`type` Typedef elementu członkowskiego szablonu klasy nazwy źródłowego typu całkowitego `T`, gdy `T` jest typ wyliczeniowy, w przeciwnym razie nie jest elementem typedef nie elementu członkowskiego `type`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
