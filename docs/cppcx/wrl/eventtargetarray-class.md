---
title: EventTargetArray — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786811"
---
# <a name="eventtargetarray-class"></a>EventTargetArray — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Uwagi

Reprezentuje tablicę procedury obsługi zdarzeń.

Programy obsługi zdarzeń, które są skojarzone z [EventSource](eventsource-class.md) obiektu są przechowywane w chronionym `EventTargetArray` element członkowski danych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                           | Opis
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicjuje nowe wystąpienie klasy `EventTargetArray` klasy.
[EventTargetArray:: ~ EventTargetArray](#tilde-eventtargetarray) | Deinicjuje bieżące `EventTargetArray` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                  | Opis
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Dołącza określona procedura obsługi zdarzeń do końca tablicy wewnętrzne programów obsługi zdarzeń.
[EventTargetArray::Begin](#begin)     | Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.
[EventTargetArray::End](#end)         | Pobiera adres ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.
[EventTargetArray::Length](#length)   | Pobiera aktualną liczbę elementów w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventTargetArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray:: ~ EventTargetArray

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Uwagi

Deinicjuje bieżące `EventTargetArray` klasy.

## <a name="addtail"></a>EventTargetArray::AddTail

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parametry

*element*<br/>
Wskaźnik do narzędzia obsługi zdarzeń do dołączenia.

### <a name="remarks"></a>Uwagi

Dołącza określona procedura obsługi zdarzeń do końca tablicy wewnętrzne programów obsługi zdarzeń.

`AddTail()` może być używany wewnętrznie przez tylko `EventSource` klasy.

## <a name="begin"></a>EventTargetArray::Begin

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Wartość zwracana

Adres do pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera adres pierwszego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="end"></a>EventTargetArray::End

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Wartość zwracana

Adres do ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera adres ostatniego elementu w tablicy wewnętrznej procedury obsługi zdarzeń.

## <a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*godz.*<br/>
Po tej operacji konstruktora parametru *hr* wskazuje, czy przydział tablicy zakończonych powodzeniem lub niepowodzeniem. Na poniższej liście przedstawiono możliwe wartości *hr*.

+   S_OK<br/>
    Operacja zakończyła się pomyślnie.

+   E_OUTOFMEMORY<br/>
    Nie można przydzielić pamięci dla tablicy.

+   S_FALSE<br/>
    Parametr *elementów* jest mniejsza niż zero.

*Elementy*<br/>
Liczba elementów tablicy można przydzielić.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `EventTargetArray` klasy.

`EventTargetArray` jest używany do przechowywania programu obsługi zdarzeń w tablicy `EventSource` obiektu.

## <a name="length"></a>EventTargetArray::Length

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
size_t Length();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba elementów w tablicy wewnętrzne programów obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera aktualną liczbę elementów w tablicy wewnętrznej procedury obsługi zdarzeń.
