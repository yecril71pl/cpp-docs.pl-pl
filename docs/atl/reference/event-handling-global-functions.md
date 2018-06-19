---
title: Globalne funkcje obsługi zdarzeń | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: cb2c7834e7d5475810973a42ef179ea4f5f0079f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358341"
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

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
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
