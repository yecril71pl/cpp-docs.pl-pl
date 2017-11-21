---
title: ComPtr::operator Microsoft::WRL::Details::BoolType Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 010979a0a72fc1d522a921b20df4579bc6efa159
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType Operator
Wskazuje, czy comptr — Zarządzanie okres istnienia obiektu interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli interfejs jest skojarzony z tym comptr — adres [boolstruct::Member —](../windows/boolstruct-member-data-member.md) element członkowski danych; w przeciwnym razie `nullptr`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)   
 [ComPtr::Get — metoda](../windows/comptr-get-method.md)