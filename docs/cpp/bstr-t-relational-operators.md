---
title: _bstr_t — Operatory relacyjne
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: 8fc163255a5ab342938f56f8a22af3984a48e56a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216625"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t — Operatory relacyjne

**Specyficzne dla firmy Microsoft**

Porównuje dwa `_bstr_t` obiekty.

## <a name="syntax"></a>Składnia

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>Uwagi

Te operatory porównują dwa `_bstr_t` obiekty lexicographically. Operatory zwracają **`true`** , jeśli porównania są przechowywane, w przeciwnym razie zwraca **`false`** .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _bstr_t](../cpp/bstr-t-class.md)
