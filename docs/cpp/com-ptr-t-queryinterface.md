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
ms.openlocfilehash: 20d22fac89b151a28e856ac4eaf61021faa6bfd5
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407435"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface
**Microsoft Specific**  
  
 Wywołania **QueryInterface** funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [_com_ptr_t, klasa](../cpp/com-ptr-t-class.md)