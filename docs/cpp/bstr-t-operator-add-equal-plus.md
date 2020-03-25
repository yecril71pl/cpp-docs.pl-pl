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
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181151"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Specyficzne dla firmy Microsoft**

Dołącza znaki do końca obiektu `_bstr_t` lub łączy dwa ciągi.

## <a name="syntax"></a>Składnia

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>Parametry

*S2*<br/>
Obiekt `_bstr_t`.

*S2*<br/>
Ciąg wielobajtowy.

*S3*<br/>
Ciąg Unicode.

## <a name="remarks"></a>Uwagi

Te operatory wykonują łączenie ciągów:

- **operator + = (**  *S1*  **)** Dołącza znaki w hermetyzowanej `BSTR` z *S1* do końca `BSTR`hermetyzowane tego obiektu.

- **operator + (**  *S1*  **)** Zwraca nowy `_bstr_t`, który jest tworzony przez złączenie `BSTR` tego obiektu z elementem *S1*.

- **operator + (**  *S2*  **&#124;**  *S1*  **)** Zwraca nowy `_bstr_t`, który jest tworzony przez złączenie ciągu wielobajtowego *S2*, przekonwertowane na Unicode, z `BSTR` hermetyzowane w *S1*.

- **operator + (**  *S3* **,**  *S1*  **)** Zwraca nowy `_bstr_t`, który jest tworzony przez połączenie ciągu Unicode *S3* z `BSTR` hermetyzowane w *S1*.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
