---
title: AgileEventSource, klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 095c61dcef208028bf1c0f4b3443ba10110da8ed
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025869"
---
# <a name="agileeventsource-class"></a>AgileEventSource, klasa

Przedstawia zdarzenie, który jest wywoływany przez agile składnik, który jest składnikiem, który jest możliwy z żadnym z wątków. Dziedziczy [EventSource](eventsource-class.md) i zastępuje `Add` funkcji składowej z parametrem typu dodatkowe do określania opcji sposobu wywoływania zdarzeń agile.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

*TEventSourceOptions*<br/>
[InvokeModeOptions](invokemodeoptions-structure.md) stucture, w których pole invokeMode jest równa `InvokeMode::StopOnFirstError` lub `InvokeMode::FireAll`.

## <a name="remarks"></a>Uwagi

Większość składników środowiska wykonawczego Windows są składnikami agile. Aby uzyskać więcej informacji, zobacz [wątkowość i Marshaling (C++/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventSource`

`AgileEventSource`

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

*delegateInterface*<br/>
Interfejs do obiektu delegowanego, który reprezentuje program obsługi zdarzeń.

*token*<br/>
Po zakończeniu tej operacji, uchwyt, który reprezentuje zdarzenie. Używanie tego tokenu jako parametr do `Remove()` metodę, aby odrzucić programu obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)