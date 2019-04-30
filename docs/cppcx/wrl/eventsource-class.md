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
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398514"
---
# <a name="eventsource-class"></a>EventSource — Klasa

Reprezentuje zdarzenie agile. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń. Dla zdarzeń agile, należy użyć [AgileEventSource](agileeventsource-class.md).

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
| [EventSource::EventSource](#eventsource) | Inicjuje nowe wystąpienie klasy `EventSource` klasy. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                 | Opis                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | Dołącza program obsługi zdarzeń, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego `EventSource` obiektu.                     |
| [EventSource::GetSize](#getsize)     | Pobiera liczbę programów obsługi zdarzeń skojarzonych z bieżącym `EventSource` obiektu.                                                                         |
| [EventSource::InvokeAll](#invokeall) | Wywołuje każdy program obsługi zdarzeń skojarzonych z bieżącym `EventSource` przy użyciu określone typy argumentów i argumenty.                                      |
| [EventSource::Remove](#remove)       | Usuwa program obsługi zdarzeń, reprezentowane przez tokenu rejestracji określonego zdarzenia z zestawu programów obsługi zdarzeń skojarzonych z bieżącym `EventSource` obiektu. |

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

| Nazwa                                                    | Opis                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | Synchronizuje dostęp do [targets_ — element](#targets) tablicy podczas dodawania, usuwania lub wywoływania procedury obsługi zdarzeń.                          |
| [EventSource::targets_](#targets)                       | Tablica procedury obsługi zdarzeń.                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | Synchronizuje dostęp do danych wewnętrznych elementów członkowskich, nawet wtedy, gdy programy obsługi zdarzeń dla tego źródła zdarzeń są dodawane, usuwane lub wywołana. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="add"></a>EventSource::Add

Dołącza program obsługi zdarzeń, reprezentowane przez interfejs określonego delegata do zestawu programów obsługi zdarzeń dla bieżącego `EventSource` obiektu.

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
Po zakończeniu tej operacji, uchwyt, który reprezentuje zdarzenie. Używanie tego tokenu jako parametr do [Remove()](#remove) metodę, aby odrzucić programu obsługi zdarzeń.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="addremovelock"></a>EventSource::addRemoveLock_

Synchronizuje dostęp do [targets_ — element](#targets) tablicy podczas dodawania, usuwania lub wywoływania procedury obsługi zdarzeń.

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource

Inicjuje nowe wystąpienie klasy `EventSource` klasy.

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource::GetSize

Pobiera liczbę programów obsługi zdarzeń skojarzonych z bieżącym `EventSource` obiektu.

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczby programami obsługi zdarzeń w [targets_ — element](#targets).

## <a name="invokeall"></a>EventSource::InvokeAll

Wywołuje każdy program obsługi zdarzeń skojarzonych z bieżącym `EventSource` przy użyciu określone typy argumentów i argumenty.

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
Typ argumentu procedury obsługi zdarzeń zerowego.

*T1*<br/>
Typ pierwszego argumentu procedury obsługi zdarzeń.

*T2*<br/>
Typ drugiego argumentu procedury obsługi zdarzeń.

*T3*<br/>
Typ trzeciego argumentu procedury obsługi zdarzeń.

*T4*<br/>
Typ czwartego argumentu procedury obsługi zdarzeń.

*T5*<br/>
Typ piątego argumentu procedury obsługi zdarzeń.

*T6*<br/>
Typ szóstego argumentu procedury obsługi zdarzeń.

*T7*<br/>
Typ siódmego argumentu procedury obsługi zdarzeń.

*T8*<br/>
Typ ósmego argumentu procedury obsługi zdarzeń.

*T9*<br/>
Typ dziewiątego argumentu procedury obsługi zdarzeń.

*arg0*<br/>
Argument procedury obsługi zdarzeń zerowego.

*arg1*<br/>
Pierwszy argument procedury obsługi zdarzeń.

*arg2*<br/>
Drugi argument procedury obsługi zdarzeń.

*arg3*<br/>
Trzeci argument procedury obsługi zdarzeń.

*arg4*<br/>
Czwarty argument procedury obsługi zdarzeń.

*arg5*<br/>
Piąty argument procedury obsługi zdarzeń.

*arg6*<br/>
Szósty argument procedury obsługi zdarzeń.

*arg7*<br/>
Siódmego argumentu procedury obsługi zdarzeń.

*arg8*<br/>
Identyfikator ósmego argumentu procedury obsługi zdarzenia.

*arg9*<br/>
Dziewiątego argumentu procedury obsługi zdarzeń.

## <a name="remove"></a>EventSource::Remove

Usuwa program obsługi zdarzeń, reprezentowane przez tokenu rejestracji określonego zdarzenia z zestawu programów obsługi zdarzeń skojarzonych z bieżącym `EventSource` obiektu.

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>Parametry

*token*<br/>
Uchwyt, który reprezentuje program obsługi zdarzeń. Token ten został zwrócony podczas obsługi zdarzeń było zarejestrowane przez [Add()](#add) metody.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat `EventRegistrationToken` struktury, zobacz **struktury typem Windows::Foundation:: eventregistrationtoken** tematu w **Windows Runtime** dokumentację referencyjną.

## <a name="targets"></a>EventSource::targets_

Tablica procedury obsługi zdarzeń.

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>Uwagi

Gdy zdarzenia, który jest reprezentowany przez bieżącą `EventSource` obiekt występuje, są wywoływane programy obsługi zdarzeń.

## <a name="targetspointerlock"></a>EventSource::targetsPointerLock_

Synchronizuje dostęp do elementów członkowskich danych wewnętrznych, nawet w trakcie procedury obsługi zdarzeń dla tego `EventSource` są dodawane, usunięte lub wywołana.

```cpp
Wrappers::SRWLock targetsPointerLock_;
```
