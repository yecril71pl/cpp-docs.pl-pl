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
ms.openlocfilehash: bfc149b0f0688bed567bf202fddb4ab2c3102630
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325812"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t::wchar_t\*, _bstr_t::char\*

**Microsoft Specific**

Zwraca znaki BSTR jako tablica wąskiego lub szerokiego znaku.

## <a name="syntax"></a>Składnia

```
operator const wchar_t*( ) const throw( );
operator wchar_t*( ) const throw( );
operator const char*( ) const;
operator char*( ) const;
```

## <a name="remarks"></a>Uwagi

Te operatory może służyć do wyodrębniania danych znakowych hermetyzowaną przez `BSTR` obiektu. Przypisywanie nową wartość do zwrócony wskaźnik nie powoduje modyfikacji oryginalnych danych BSTR.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)