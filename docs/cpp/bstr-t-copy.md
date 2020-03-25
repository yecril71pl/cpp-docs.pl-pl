---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190329"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Specyficzne dla firmy Microsoft**

Tworzy kopię hermetyzowanej `BSTR`.

## <a name="syntax"></a>Składnia

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>Parametry

*fCopy*<br/>
Jeśli wartość jest równa TRUE, funkcja **copy** zwraca kopię zawartej `BSTR`, w przeciwnym razie funkcja **copy** zwraca rzeczywistą wartość BSTR.

## <a name="remarks"></a>Uwagi

Zwraca nowo przydzieloną kopię hermetyzowanego obiektu `BSTR`.

## <a name="example"></a>Przykład

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
