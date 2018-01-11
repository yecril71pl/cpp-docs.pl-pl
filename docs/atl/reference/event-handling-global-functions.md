---
title: "Globalne funkcje obsługi zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::AtlWaitWithMessageLoop
dev_langs: C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6670ef283d24f57b407ad70693421feae427855f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-global-functions"></a>Globalne funkcje obsługi zdarzeń
Ta funkcja udostępnia program obsługi zdarzeń.  
  
> [!IMPORTANT]
>  Nie można użyć funkcji wymienionych w poniższej tabeli w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Oczekuje dla obiekt, aby zostać zgłoszony, w tym samym czasie podczas wysyłania komunikatów okien, zgodnie z potrzebami.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
 Czeka na obiekt, który ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien w razie potrzeby.  
  
> [!IMPORTANT]
>  Nie można użyć tej funkcji w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Parametry  
 `hEvent`  
 [in] Dojście oczekiwania na obiekt.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** Jeśli obiekt został sygnalizowane.  
  
### <a name="remarks"></a>Uwagi  
 Jest to przydatne, jeśli chcesz czekać na obiekt zdarzenia stanie i powiadomić go w trybie, ale zezwalaj na okna komunikatów wysyłanych podczas oczekiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
