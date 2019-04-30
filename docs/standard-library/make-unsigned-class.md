---
title: make_unsigned — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 42c722c5250a4989b930d8f1e6fe52f2eccc614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413050"
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
