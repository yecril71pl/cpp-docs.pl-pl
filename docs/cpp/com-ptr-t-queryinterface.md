---
title: _com_ptr_t::QueryInterface | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21dffde38e58bb7c07a1a92421d3febe10cc1032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Dotyczące firmy Microsoft**  
  
 Wywołania `QueryInterface` funkcji członkowskiej klasy **IUnknown** na wskaźnik hermetyzowany interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `iid`  
 **Identyfikator IID** wskaźnika interfejsu.  
  
 `p`  
 Wskaźnik interfejsu pierwotnego.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania **IUnknown::QueryInterface** na wskaźniku zhermetyzowany interfejs z określonym **IID** i zwraca wynikowy wskaźnik interfejsu pierwotnego w `p`. Ta procedura zwraca `HRESULT` do wskazania powodzenia lub niepowodzenia.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)