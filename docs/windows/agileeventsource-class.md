---
title: Klasa AgileEventSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 58eb96e3a0268d3ba70b60d9c315e935e19485f3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="agileeventsource-class"></a>Klasa AgileEventSource

Reprezentuje zdarzenie jest wywoływane przez składnik agile, czyli składnik, który można uzyskać z dowolnego wątku. Dziedziczy [EventSource](eventsource-class.md) i zastępuje `Add` funkcji członkowskiej z parametrem typu dodatkowe służący do określania opcji dotyczących sposobu wywołania agile zdarzeń.

## <a name="syntax"></a>Składnia

```
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry  
 `TDelegateInterface`  

 Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

 `TEventSourceOptions`  
 [InvokeModeOptions](invokemodeoptions-structure.md) stucture, których pole invokeMode ma ustawioną wartość `InvokeMode::StopOnFirstError` lub `InvokeMode::FireAll`.

## <a name="remarks"></a>Uwagi

Większość składników środowiska wykonawczego systemu Windows są składnikami elastyczne. Aby uzyskać więcej informacji, zobacz [wątków i przekazywanie (C + +/ CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

 `EventSource``AgileEventSource`

## <a name="requirements"></a>Wymagania

 **Nagłówek:** event.h

 **Namespace:** Microsoft::wrl —

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AgileEventSource::Add — metoda](#add)|Dołącza program obsługi zdarzeń agile reprezentowany przez interfejs określonego delegata do zestawu obsługi zdarzeń dla bieżącego obiektu AgileEventSource.|

## <a name="add"></a> AgileEventSource::Add — metoda

Dołącza program obsługi zdarzeń reprezentowany przez interfejs określonego delegata do obsługi zdarzeń dla bieżącego zestawu [EventSource](eventsource-class.md) obiektu.

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


## <a name="see-also"></a>Zobacz też

 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)
