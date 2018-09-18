---
title: _bstr_t::kopiowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::copy
dev_langs:
- C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 50f9a17c93849dec49c2c9a72825a5797d8c040c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068627"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Microsoft Specific**

Tworzy kopię zhermetyzowanego `BSTR`.

## <a name="syntax"></a>Składnia

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parametry

*fCopy*<br/>
W przypadku opcji TRUE **kopiowania** zwraca kopię obiektu zamkniętego `BSTR`, w przeciwnym razie **kopiowania** zwraca rzeczywiste BSTR.

## <a name="remarks"></a>Uwagi

Zwraca nowo przydzielonego kopię zhermetyzowanego `BSTR` obiektu.

## <a name="example"></a>Przykład

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)