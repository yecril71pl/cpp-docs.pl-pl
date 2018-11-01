---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506849"
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