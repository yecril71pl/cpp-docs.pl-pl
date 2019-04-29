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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350874"
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

*s1*<br/>
A `_bstr_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.

*s2*<br/>
Wielobajtowy ciąg ma być przypisane do istniejącej `_bstr_t` obiektu.

*s3*<br/>
Ciąg Unicode ma być przypisane do istniejącej `_bstr_t` obiektu.

*var*<br/>
A `_variant_t` obiekt ma być przypisane do istniejącej `_bstr_t` obiektu.

**END specyficzny dla Microsoft**

## <a name="example"></a>Przykład

Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą **operator =**.

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)