---
title: _com_ptr_t::QueryInterface | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c455ce81a869d64b3a9019088028e384c6a06217
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947743"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Microsoft Specific**  
  
 Wywołania `QueryInterface` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.  
  
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
 *IID*  
 `IID` wskaźnika interfejsu.  
  
 *p*  
 Surowego wskaźnika interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `IUnknown::QueryInterface` we wskaźniku zhermetyzowany interfejs z określonym `IID` i zwraca wynikowy surowego wskaźnika interfejsu w *p*. Ta procedura zwraca wartość HRESULT do wskazania powodzenia lub niepowodzenia.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)