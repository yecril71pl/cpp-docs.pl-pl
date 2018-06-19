---
title: EventSource::Add — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 92af8746b4d2b5ba2f379cc8660b5345b2c5f175
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873241"
---
# <a name="eventsourceadd-method"></a>EventSource::Add — Metoda
Dołącza reprezentowany przez interfejs określonego delegata do zestawu obsługi zdarzeń dla bieżącego obiektu EventSource programu obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `delegateInterface`  
 Interfejs do obiektu delegowanego, który reprezentuje program obsługi zdarzeń.  
  
 `token`  
 Po zakończeniu wykonywania tej operacji, uchwyt reprezentuje zdarzenia. Użyj tego token jako parametr do [Remove()](../windows/eventsource-remove-method.md) metodę, aby odrzucić programu obsługi zdarzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)