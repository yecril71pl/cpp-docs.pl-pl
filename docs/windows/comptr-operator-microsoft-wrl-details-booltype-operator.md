---
title: ComPtr::operator Booltype | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bb5735eeb9cd4048596588765468fbb9c5e07496
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652604"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType Operator
Wskazuje, czy **ComPtr** Zarządzanie okresem istnienia interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli interfejs jest skojarzony z tym **ComPtr**, adres [BoolStruct::Member](../windows/boolstruct-member-data-member.md) element członkowski danych; w przeciwnym razie **nullptr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)   
 [ComPtr::Get, metoda](../windows/comptr-get-method.md)