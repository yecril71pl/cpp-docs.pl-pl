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
ms.workload: cplusplus
ms.openlocfilehash: 4bbc3c33488d2925c1a7f879adf50f015f79ec8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [_bstr_t, klasa](../cpp/bstr-t-class.md)