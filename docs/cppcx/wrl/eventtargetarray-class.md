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
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371502"
---
# <a name="eventtargetarray-class"></a>EventTargetArray — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Uwagi

Reprezentuje tablicę programów obsługi zdarzeń.

Programy obsługi zdarzeń, które są skojarzone z [EventSource](eventsource-class.md) `EventTargetArray` obiektu są przechowywane w chronionym elementem członkowskim danych.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                           | Opis
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicjuje nowe wystąpienie klasy `EventTargetArray`.
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | Deinitializes bieżącej `EventTargetArray` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                  | Opis
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Dołącza określony program obsługi zdarzeń na końcu wewnętrznej tablicy programów obsługi zdarzeń.
[EventTargetArray::Rozpocznij](#begin)     | Pobiera adres pierwszego elementu w wewnętrznej tablicy obsługi zdarzeń.
[EventTargetArray::Koniec](#end)         | Pobiera adres ostatniego elementu w wewnętrznej tablicy obsługi zdarzeń.
[EventTargetArray::Długość](#length)   | Pobiera bieżącą liczbę elementów w wewnętrznej tablicy obsługi zdarzeń.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`EventTargetArray`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Uwagi

Deinitializes bieżącej `EventTargetArray` klasy.

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>EventTargetArray::AddTail

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parametry

*Element*<br/>
Wskaźnik do programu obsługi zdarzeń do dołączenia.

### <a name="remarks"></a>Uwagi

Dołącza określony program obsługi zdarzeń na końcu wewnętrznej tablicy programów obsługi zdarzeń.

`AddTail()`jest przeznaczony do użytku wewnętrznie `EventSource` tylko przez klasę.

## <a name="eventtargetarraybegin"></a><a name="begin"></a>EventTargetArray::Rozpocznij

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Wartość zwracana

Adres pierwszego elementu w wewnętrznej tablicy obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera adres pierwszego elementu w wewnętrznej tablicy obsługi zdarzeń.

## <a name="eventtargetarrayend"></a><a name="end"></a>EventTargetArray::Koniec

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Wartość zwracana

Adres ostatniego elementu w wewnętrznej tablicy programów obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera adres ostatniego elementu w wewnętrznej tablicy obsługi zdarzeń.

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Po tej operacji konstruktora parametr *hr* wskazuje, czy alokacja tablicy powiodła się, czy nie powiodła się. Na poniższej liście przedstawiono możliwe wartości *dla hr*.

- S_OK<br/>
  Operacja zakończyła się pomyślnie.

- E_outofmemory<br/>
  Nie można przydzielić pamięci dla tablicy.

- S_false<br/>
  *Elementy parametrów* jest mniejsza lub równa zero.

*Elementy*<br/>
Liczba elementów tablicy do przydzielenia.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `EventTargetArray`.

`EventTargetArray`służy do przechowywania tablicy programów `EventSource` obsługi zdarzeń w obiekcie.

## <a name="eventtargetarraylength"></a><a name="length"></a>EventTargetArray::Długość

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
size_t Length();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba elementów w wewnętrznej tablicy programów obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Pobiera bieżącą liczbę elementów w wewnętrznej tablicy obsługi zdarzeń.
