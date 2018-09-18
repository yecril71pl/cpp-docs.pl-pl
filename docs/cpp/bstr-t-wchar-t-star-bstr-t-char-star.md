---
title: _bstr_t::wchar_t *, _bstr_t::char* | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::wchar_t*
- _bstr_t::char*
dev_langs:
- C++
helpviewer_keywords:
- operator wchar_t* [C++]
- operator char* [C++]
ms.assetid: acd9f4a7-b427-42c2-aaae-acae21cab317
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abd0b53c178e028b975e2b26d36317b773c2cfa5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102765"
---
# <a name="bstrtwchart-bstrtchar"></a>_bstr_t::wchar_t *, _bstr_t::char*

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