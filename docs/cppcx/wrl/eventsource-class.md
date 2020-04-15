---
title: EventSource — Klasa
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371541"
---
# <a name="eventsource-class"></a>EventSource — Klasa

Reprezentuje zdarzenie nieaskładne. `EventSource`funkcje członkowskie dodają, usuwaj i przywołują programy obsługi zdarzeń. W przypadku zdarzeń agile należy użyć programu [AgileEventSource](agileeventsource-class.md).

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Interfejs do delegata, który reprezentuje program obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                                     | Opis                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [Źródło zdarzenia::Źródło zdarzenia](#eventsource) | Inicjuje nowe wystąpienie klasy `EventSource`. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                 | Opis                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Źródło zdarzenia::Dodaj](#add)             | Dołącza program obsługi zdarzeń reprezentowany przez określony interfejs delegata do zestawu `EventSource` programów obsługi zdarzeń dla bieżącego obiektu.                     |
| [Źródło zdarzenia::GetSize](#getsize)     | Pobiera liczbę programów obsługi zdarzeń skojarzonych `EventSource` z bieżącym obiektem.                                                                         |
| [Źródło zdarzenia::InvokeAll](#invokeall) | Wywołuje każdy program obsługi zdarzeń `EventSource` skojarzony z bieżącym obiektem przy użyciu określonych typów argumentów i argumentów.                                      |
| [Źródło zdarzenia::Usuń](#remove)       | Usuwa program obsługi zdarzeń reprezentowany przez token rejestracji określonego zdarzenia z zestawu `EventSource` programów obsługi zdarzeń skojarzonych z bieżącym obiektem. |

### <a name="protected-data-members"></a>Członkowie chronionych danych

| Nazwa                                                    | Opis                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [Źródło zdarzenia::addRemoveLock_](#addremovelock)           | Synchronizuje dostęp do tablicy [targets_](#targets) podczas dodawania, usuwania lub wywoływania programów obsługi zdarzeń.                          |
| [Źródło zdarzenia::targets_](#targets)                       | Tablica co najmniej jeden program obsługi zdarzeń.                                                                                           |
| [Źródło zdarzenia::targetsPointerLock_](#targetspointerlock) | Synchronizuje dostęp do wewnętrznych elementów członkowskich danych, nawet gdy programy obsługi zdarzeń dla tego eventsource są dodawane, usuwane lub wywoływane. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>Źródło zdarzenia::Dodaj

Dołącza program obsługi zdarzeń reprezentowany przez określony interfejs delegata do zestawu `EventSource` programów obsługi zdarzeń dla bieżącego obiektu.

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametry

*delegatInterface*<br/>
Interfejs do obiektu delegata, który reprezentuje program obsługi zdarzeń.

*Tokenu*<br/>
Po zakończeniu tej operacji dojście, który reprezentuje zdarzenie. Użyj tego tokenu jako parametru [metody Remove(),](#remove) aby odrzucić program obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>Źródło zdarzenia::addRemoveLock_

Synchronizuje dostęp do tablicy [targets_](#targets) podczas dodawania, usuwania lub wywoływania programów obsługi zdarzeń.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>Źródło zdarzenia::Źródło zdarzenia

Inicjuje nowe wystąpienie klasy `EventSource`.

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>Źródło zdarzenia::GetSize

Pobiera liczbę programów obsługi zdarzeń skojarzonych `EventSource` z bieżącym obiektem.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba programów obsługi zdarzeń w [targets_](#targets).

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>Źródło zdarzenia::InvokeAll

Wywołuje każdy program obsługi zdarzeń `EventSource` skojarzony z bieżącym obiektem przy użyciu określonych typów argumentów i argumentów.

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>Parametry

*T0*<br/>
Typ argumentu obsługi zdarzeń zeroth.

*T1*<br/>
Typ pierwszego argumentu obsługi zdarzeń.

*T2*<br/>
Typ drugiego argumentu obsługi zdarzeń.

*T3*<br/>
Typ trzeciego argumentu obsługi zdarzeń.

*T4*<br/>
Typ czwartego argumentu obsługi zdarzeń.

*T5 (włas ie*<br/>
Typ piątego argumentu obsługi zdarzeń.

*T6*<br/>
Typ szóstego argumentu obsługi zdarzeń.

*T7 (właso.*<br/>
Typ siódmego argumentu obsługi zdarzeń.

*T8 (własna)*<br/>
Typ argumentu obsługi ósmego zdarzenia.

*T9*<br/>
Typ argumentu dziewiątego programu obsługi zdarzeń.

*arg0 (arg0)*<br/>
Argument obsługi zdarzeń zeroth.

*argument1*<br/>
Pierwszy argument obsługi zdarzeń.

*argument 2*<br/>
Drugi argument obsługi zdarzeń.

*arg3 ( arg3 )*<br/>
Trzeci argument obsługi zdarzeń.

*arg4 ( arg4 )*<br/>
Czwarty argument obsługi zdarzeń.

*argument 5*<br/>
Piąty argument obsługi zdarzeń.

*arg6 (arg6)*<br/>
Szósty argument obsługi zdarzeń.

*argument 7*<br/>
Siódmy argument obsługi zdarzeń.

*arg8 (8)*<br/>
Ósmy argument obsługi zdarzeń.

*argument 9*<br/>
Dziewiąty argument obsługi zdarzeń.

## <a name="eventsourceremove"></a><a name="remove"></a>Źródło zdarzenia::Usuń

Usuwa program obsługi zdarzeń reprezentowany przez token rejestracji określonego zdarzenia z zestawu `EventSource` programów obsługi zdarzeń skojarzonych z bieżącym obiektem.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*Tokenu*<br/>
Dojście, który reprezentuje program obsługi zdarzeń. Ten token został zwrócony, gdy program obsługi zdarzeń został zarejestrowany przez [Add()](#add) metody.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej `EventRegistrationToken` informacji na temat struktury, zobacz temat **Windows::Foundation::EventRegistrationToken Structure** w dokumentacji referencyjnej **środowiska wykonawczego systemu Windows.**

## <a name="eventsourcetargets_"></a><a name="targets"></a>Źródło zdarzenia::targets_

Tablica co najmniej jeden program obsługi zdarzeń.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Uwagi

Gdy wystąpi zdarzenie reprezentowane przez `EventSource` bieżący obiekt, wywoływane są programy obsługi zdarzeń.

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>Źródło zdarzenia::targetsPointerLock_

Synchronizuje dostęp do wewnętrznych elementów członkowskich `EventSource` danych, nawet gdy programy obsługi zdarzeń są dodawane, usuwane lub wywoływane.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
