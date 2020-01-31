---
title: Klasa AgileEventSource
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: fa1e0a72d865b2993e149f6e4d2b57fe13463a61
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821743"
---
# <a name="agileeventsource-class"></a>Klasa AgileEventSource

Reprezentuje zdarzenie, które jest zgłaszane przez składnik Agile, który jest składnikiem, do którego można uzyskać dostęp z dowolnego wątku. Dziedziczy po elemencie [EventSource](eventsource-class.md) i przesłania funkcję składowej `Add` z dodatkowym parametrem typu w celu określenia opcji wywoływania zdarzenia Agile.

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
Interfejs do delegata, który reprezentuje procedurę obsługi zdarzeń.

*TEventSourceOptions*<br/>
Struktura [InvokeModeOptions](invokemodeoptions-structure.md) , której pole invokemode ma wartość `InvokeMode::StopOnFirstError` lub `InvokeMode::FireAll`.

## <a name="remarks"></a>Uwagi

Większość składników w środowisko wykonawcze systemu Windows są składniki Agile. Aby uzyskać więcej informacji, zobacz [wątkowość i kierowanieC++(/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Event. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[AgileEventSource:: Add — Metoda](#add)|Dołącza obsługę zdarzeń Agile reprezentowane przez określony interfejs delegata do zestawu obsługi zdarzeń dla bieżącego obiektu **AgileEventSource** .|

## <a name="add"></a>AgileEventSource:: Add — Metoda

Dołącza obsługę zdarzeń reprezentowane przez określony interfejs delegata do zestawu obsługi zdarzeń dla bieżącego obiektu [EventSource](eventsource-class.md) .

### <a name="syntax"></a>Składnia

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegateInterface*<br/>
Interfejs do obiektu delegata, który reprezentuje procedurę obsługi zdarzeń.

*klucza*<br/>
Po zakończeniu tej operacji, dojście, które reprezentuje zdarzenie. Użyj tego tokenu jako parametru do metody `Remove()`, aby odrzucić procedurę obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwrócona

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)