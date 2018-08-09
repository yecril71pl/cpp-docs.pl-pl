---
title: EventSource::Add, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Add
dev_langs:
- C++
helpviewer_keywords:
- Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 65e8576f069cce7d7aec2eae18ad577820ca93a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644745"
---
# <a name="eventsourceadd-method"></a>EventSource::Add — Metoda
Dołącza program obsługi zdarzeń, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego **EventSource** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *delegateInterface*  
 Interfejs do obiektu delegowanego, który reprezentuje program obsługi zdarzeń.  
  
 *Token*  
 Po zakończeniu tej operacji, uchwyt, który reprezentuje zdarzenie. Używanie tego tokenu jako parametr do [Remove()](../windows/eventsource-remove-method.md) metodę, aby odrzucić programu obsługi zdarzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)