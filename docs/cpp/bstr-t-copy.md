---
title: _bstr_t::kopiowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::copy
dev_langs: C++
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5c7a3bb2997bbec1c0e402c14985353dcf0bc768
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtcopy"></a>_bstr_t::copy
**Dotyczące firmy Microsoft**  
  
 Tworzy kopię hermetyzowany `BSTR`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      BSTR copy(  
  bool fCopy = true  
) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `fCopy`  
 Jeśli **true**, **kopiowania** zwraca kopię zamkniętego `BSTR`, w przeciwnym razie **kopiowania** zwraca rzeczywiste BSTR.  
  
## <a name="remarks"></a>Uwagi  
 Zwraca nowoprzydzielonych kopię hermetyzowany `BSTR` obiektu.  
  
## <a name="example"></a>Przykład  
  
```  
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t  
   *pVal = m_bsConStr.copy();  
}  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t — klasa](../cpp/bstr-t-class.md)