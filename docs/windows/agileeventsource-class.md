---
title: AgileEventSource, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 90a2c582c2740846f90270fe9f45b96871329252
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642841"
---
# <a name="agileeventsource-class"></a>AgileEventSource, klasa

Przedstawia zdarzenie, który jest wywoływany przez agile składnik, który jest składnikiem, który jest możliwy z żadnym z wątków. Dziedziczy [EventSource](eventsource-class.md) i zastępuje `Add` funkcji składowej z parametrem typu dodatkowe do określania opcji sposobu wywoływania zdarzeń agile.

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry  
 *TDelegateInterface*  
 Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

 *TEventSourceOptions*  
 [InvokeModeOptions](invokemodeoptions-structure.md) stucture, w których pole invokeMode jest równa `InvokeMode::StopOnFirstError` lub `InvokeMode::FireAll`.

## <a name="remarks"></a>Uwagi

Większość składników środowiska wykonawczego Windows są składnikami agile. Aby uzyskać więcej informacji, zobacz [wątkowość i Marshaling (C + +/ CX)](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

 `EventSource``AgileEventSource`

## <a name="requirements"></a>Wymagania

 **Nagłówek:** event.h

 **Namespace:** Microsoft::WRL

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Metoda AgileEventSource::Add](#add)|Dołącza program obsługi zdarzeń agile, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego **AgileEventSource** obiektu.|

## <a name="add"></a> Metoda AgileEventSource::Add

Dołącza program obsługi zdarzeń, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego [EventSource](eventsource-class.md) obiektu.

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

*Token*  
Po zakończeniu tej operacji, uchwyt, który reprezentuje zdarzenie. Używanie tego tokenu jako parametr do `Remove()` metodę, aby odrzucić programu obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.


## <a name="see-also"></a>Zobacz też
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)