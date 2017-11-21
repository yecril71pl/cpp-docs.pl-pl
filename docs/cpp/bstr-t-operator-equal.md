---
title: _bstr_t::operator = | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::operator=
dev_langs: C++
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5005dd0aa020ee38e4a6d29237f6ec683219ce9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =
**Dotyczące firmy Microsoft**  
  
 Przypisuje nową wartość do istniejącej `_bstr_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *S1*  
 A `_bstr_t` obiektu do przypisania do istniejącej `_bstr_t` obiektu.  
  
 *S2*  
 Ciąg wielobajtowy do przypisania do istniejącej `_bstr_t` obiektu.  
  
 `s3`  
 Ciąg Unicode do przypisania do istniejącej `_bstr_t` obiektu.  
  
 `var`  
 A `_variant_t` obiektu do przypisania do istniejącej `_bstr_t` obiektu.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) przykład przy użyciu `operator=`.  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t — klasa](../cpp/bstr-t-class.md)