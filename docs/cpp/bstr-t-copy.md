---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: b6029e98e83b171d9ab9f8f3f0282fa3f46ca167
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227598"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Specyficzne dla firmy Microsoft**

Tworzy kopię hermetyzowania `BSTR` .

## <a name="syntax"></a>Składnia

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parametry

*fCopy*<br/>
Jeśli **`true`** Funkcja **copy** zwraca kopię zawartej `BSTR` , w przeciwnym razie **kopia** zwraca rzeczywistą wartość BSTR.

## <a name="remarks"></a>Uwagi

Zwraca nowo przydzieloną kopię hermetyzowanego `BSTR` obiektu.

## <a name="example"></a>Przykład

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasa _bstr_t](../cpp/bstr-t-class.md)
