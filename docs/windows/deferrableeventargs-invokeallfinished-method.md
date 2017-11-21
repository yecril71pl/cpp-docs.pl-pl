---
title: "DeferrableEventArgs::InvokeAllFinished — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: acae8467ceeaaafea6668d4fbf6b5e2f4884b373
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished — metoda
Wywołuje się, by wskazać, że przetwarzania obsługi zdarzenia odroczone jest pełny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Uwagi  
 Tej metody należy wywołać po wywołań źródła zdarzeń [InvokeAll](../windows/eventsource-invokeall-method.md). Wywołanie tej metody uniemożliwia dalsze odroczenia podjęcie i wymusza programu obsługi zakończenia wykonywania odroczenia nie zostały pobrane.  
  
 Na przykład kod, zobacz [deferrableeventargs — klasa](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Deferrableeventargs — klasa](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll — metoda](../windows/eventsource-invokeall-method.md)