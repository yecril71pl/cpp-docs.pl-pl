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
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187573"
---
# <a name="_variant_t-relational-operators"></a>_variant_t — Operatory relacyjne

**Specyficzne dla firmy Microsoft**

Porównaj dwa `_variant_t` obiekty pod kątem równości lub nierówności.

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
`VARIANT` do porównania z obiektem `_variant_t`.

*pSrc*<br/>
Wskaźnik do `VARIANT`, który ma zostać porównany z obiektem `_variant_t`.

## <a name="return-value"></a>Wartość zwracana

Zwraca **wartość PRAWDA** , jeśli porównanie ma wartość **Fałsz** , jeśli nie.

## <a name="remarks"></a>Uwagi

Porównuje obiekt `_variant_t` z `VARIANT`, testowania pod kątem równości lub nierówności.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_variant_t, klasa](../cpp/variant-t-class.md)
