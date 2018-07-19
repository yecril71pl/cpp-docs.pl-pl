---
title: make_unsigned — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::make_unsigned
dev_langs:
- C++
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f379500f9455ed9ad9a581966e0f8ed7bfed13f7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953917"
---
# <a name="makeunsigned-class"></a>make_unsigned — Klasa

Tworzy typ lub najmniejszy niepodpisane wpisz większa lub równa rozmiarze do typu.

## <a name="syntax"></a>Składnia

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*T*|Typ do modyfikacji.|

## <a name="remarks"></a>Uwagi

Wystąpienie modyfikatora typu przechowuje zmodyfikowany typ, który jest *T* Jeśli `is_unsigned<T>` prawdziwe. W przeciwnym razie jest najmniejszą typ ze znakiem `ST` dla którego `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
