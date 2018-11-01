---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432581"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Microsoft Specific**

Przypisuje nową wartość do istniejącej `_bstr_t` obiektu.

## <a name="syntax"></a>Składnia

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>Parametry

*S1*<br/>
A `_bstr_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.

*S2*<br/>
Wielobajtowy ciąg ma być przypisane do istniejącej `_bstr_t` obiektu.

*S3*<br/>
Ciąg Unicode ma być przypisane do istniejącej `_bstr_t` obiektu.

*var*<br/>
A `_variant_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.

**END specyficzny dla Microsoft**

## <a name="example"></a>Przykład

Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą **operator =**.

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)