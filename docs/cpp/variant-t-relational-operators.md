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
ms.openlocfilehash: 6e0296a2bf4ce97e41fdf6208c3dd1c6b91215dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226946"
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
Wartość `VARIANT` do porównania z `_variant_t` obiektem.

*pSrc*<br/>
Wskaźnik do `VARIANT` porównania z `_variant_t` obiektem.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość **`true`** , jeśli porównanie **`false`** ma być przechowywane.

## <a name="remarks"></a>Uwagi

Porównuje `_variant_t` obiekt z `VARIANT` , testowaniem pod kątem równości lub nierówności.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _variant_t](../cpp/variant-t-class.md)
