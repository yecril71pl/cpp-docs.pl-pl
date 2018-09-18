---
title: _bstr_t::operator = | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35778fe3bdf75738f67b280cbbe4c8ceeb498634
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46017004"
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