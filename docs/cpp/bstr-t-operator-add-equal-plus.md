---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: 0a2c374fc160a0575e0a17cc85ab51c65fa9392a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390837"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +

**Microsoft Specific**

Dołącza znaki do końca `_bstr_t` obiektu lub łączy dwa ciągi.

## <a name="syntax"></a>Składnia

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parametry

*s1*<br/>
Element `_bstr_t` obiektu.

*s2*<br/>
Ciąg znaków wielobajtowych.

*s3*<br/>
Ciąg Unicode.

## <a name="remarks"></a>Uwagi

Te operatory wykonaj ciągów:

- **+= — Operator (***s1***)** dołącza znaki w zhermetyzowany `BSTR` z *s1* na końcu tego obiektu zhermetyzowany`BSTR`.

- **Operator + (***s1***)** zwraca nową `_bstr_t` , jest tworzona przez złączenie tego obiektu `BSTR` z tymi, które *s1*.

- **Operator + (***s2***&#124;***s1***)** zwraca nowy `_bstr_t` , jest tworzona przez złączenie ciąg znaków wielobajtowych *s2*, przekonwertowane na format Unicode, za pomocą `BSTR` hermetyzowane w *s1*.

- **Operator + (***s3* **,***s1***)** zwraca nowy `_bstr_t` , jest tworzona przez złączenie ciąg Unicode *s3* z `BSTR` hermetyzowane w *s1*.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)