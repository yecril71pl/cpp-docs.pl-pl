---
title: Funkcje globalne obsługi zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85babf3155fdc94dafd5d62c2e67401e5add3663
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884002"
---
# <a name="event-handling-global-functions"></a>Funkcje globalne obsługi zdarzeń
Ta funkcja udostępnia program obsługi zdarzeń.  
  
> [!IMPORTANT]
>  Nie można użyć funkcji wymienionych w poniższej tabeli w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Czeka, aż obiekt ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien, zgodnie z potrzebami.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
 Czeka na obiekt, który ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien w razie potrzeby.  
  
> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>Parametry  
 *hEvent*  
 [in] Uchwyt obiektu oczekiwania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli obiekt zostały zasygnalizowane.  
  
### <a name="remarks"></a>Uwagi  
 Jest to przydatne, jeśli chcesz czekać na obiekt zdarzenie, aby się zdarzyć i otrzymywać powiadomienia o wykonywane, ale zezwalaj na okna komunikatów wysyłanych podczas oczekiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
