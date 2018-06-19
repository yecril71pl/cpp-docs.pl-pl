---
title: ComPtr::operator Microsoft::WRL::Details::BoolType Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5efd641e5c908e5f1c4d4a3cdb78cd146b634f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883163"
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
 [ComPtr::Get, metoda](../windows/comptr-get-method.md)