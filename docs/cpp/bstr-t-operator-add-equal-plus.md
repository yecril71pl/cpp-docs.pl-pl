---
title: _bstr_t::operator += + | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a440e8b8d078c7849de2a0b29f1d50b140d70070
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044772"
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

*S1*<br/>
Element `_bstr_t` obiektu.

*S2*<br/>
Ciąg znaków wielobajtowych.

*S3*<br/>
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