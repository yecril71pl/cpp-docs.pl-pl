---
title: make_signed — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::make_signed
dev_langs:
- C++
helpviewer_keywords:
- make_signed class
- make_signed
ms.assetid: 686247c0-247c-496b-9b1b-ba9dcd633621
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d25973d12c223200a6904416efd8544b1e17712
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="makesigned-class"></a>make_signed — Klasa

Wpisz sprawia, że lub najmniejszą podpisem wpisz większa niż lub równa o rozmiarze do typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct make_signed;

template <class T>
using make_signed_t = typename make_signed<T>::type;
```

### <a name="parameters"></a>Parametry

`T` Typ do zmodyfikowania.

## <a name="remarks"></a>Uwagi

Wystąpienie modyfikator typu przechowuje zmodyfikowane — typ danych `T` Jeśli `is_signed<T>` jest spełniony. W przeciwnym razie jest najmniejszą typu bez znaku `UT` dla którego `sizeof (T) <= sizeof (UT)`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
