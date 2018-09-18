---
title: _variant_t — operatory relacyjne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95cb1ac663607f26c4f168c2e98910f5b41963c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040168"
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