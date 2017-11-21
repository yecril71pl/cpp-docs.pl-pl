---
title: "EventTargetArray::Begin — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs: C++
helpviewer_keywords: Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 092aa684cace186e3aa5ad443e6f419f10d68160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
ComPtr<IUnknown>* Begin();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Eventtargetarray — klasa](../windows/eventtargetarray-class.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)