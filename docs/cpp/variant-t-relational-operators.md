---
title: _variant_t — Operatory relacyjne
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: e0d26247868440f47c73422510ac0e998f8e8dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403298"
---
# <a name="variantt-relational-operators"></a>_variant_t — Operatory relacyjne

**Microsoft Specific**

Porównanie dwóch `_variant_t` obiektów dla równości i nierówności.

## <a name="syntax"></a>Składnia

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>Parametry

*varSrc*<br/>
A `VARIANT` ma zostać porównane z `_variant_t` obiektu.

*pSrc*<br/>
Wskaźnik do `VARIANT` ma zostać porównane z `_variant_t` obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca **true** Jeśli przechowuje porównania, **false** w przeciwnym razie.

## <a name="remarks"></a>Uwagi

Porównuje `_variant_t` obiekt z `VARIANT`, testowanie dla równości i nierówności.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_variant_t, klasa](../cpp/variant-t-class.md)