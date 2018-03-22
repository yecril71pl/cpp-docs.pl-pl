---
title: Klasa AgileEventSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d025fc2be86fb5b59107d1deee39962c3c6db04
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="agileeventsource-class"></a>Klasa AgileEventSource
Reprezentuje agile zdarzenia. Dziedziczy [EventSource](eventsource-class.md) i zastępuje `Add` funkcji członkowskiej z parametrem typu dodatkowe służący do określania opcji dotyczących sposobu wywołania agile zdarzeń.
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```  
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

 `TEventSourceOptions` [InvokeModeOptions](invokemodeoptions-structure.md) stucture, których pole invokeMode ma ustawioną wartość `InvokeMode::StopOnFirstError` lub `InvokeMode::FireAll`.

## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AgileEventSource::Add — metoda](#add)|Dołącza program obsługi zdarzeń agile reprezentowany przez interfejs określonego delegata do zestawu obsługi zdarzeń dla bieżącego obiektu AgileEventSource.|  

## <a name="add"></a> AgileEventSource::Add — metoda

Dołącza reprezentowany przez interfejs określonego delegata do zestawu obsługi zdarzeń dla bieżącego obiektu EventSource programu obsługi zdarzeń.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*

Interfejs do obiektu delegowanego, który reprezentuje program obsługi zdarzeń.

*Token* po zakończeniu tej operacji, uchwyt reprezentuje zdarzenia. Użyj ten token jako parametr do metody Remove() odrzucić programu obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwracana
S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `EventSource`  
 `AgileEventSource`
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)