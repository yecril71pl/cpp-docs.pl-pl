---
title: _bstr_t::wchar_t *, _bstr_t::char*
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
ms.openlocfilehash: 5fdce29b0be7e9aabae9e3c602822045a7bccafd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190304"
---
# <a name="_bstr_twchar_t-_bstr_tchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Specyficzne dla firmy Microsoft**

Zwraca znaki BSTR jako tablicę o wąskim lub szerokim znaku.

## <a name="syntax"></a>Składnia

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Uwagi

Te operatory mogą służyć do wyodrębniania danych znakowych, które są hermetyzowane przez obiekt `BSTR`. Przypisanie nowej wartości do zwracanego wskaźnika nie powoduje modyfikacji oryginalnych danych BSTR.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
