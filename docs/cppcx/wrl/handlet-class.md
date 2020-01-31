---
title: HandleT — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Attach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Get
- corewrappers/Microsoft::WRL::Wrappers::HandleT::handle_
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
- corewrappers/Microsoft::WRL::Wrappers::HandleT::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
- corewrappers/Microsoft::WRL::Wrappers::HandleT::~HandleT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleT class
- Microsoft::WRL::Wrappers::HandleT::Attach method
- Microsoft::WRL::Wrappers::HandleT::Close method
- Microsoft::WRL::Wrappers::HandleT::Detach method
- Microsoft::WRL::Wrappers::HandleT::Get method
- Microsoft::WRL::Wrappers::HandleT::handle_ data member
- Microsoft::WRL::Wrappers::HandleT::HandleT, constructor
- Microsoft::WRL::Wrappers::HandleT::InternalClose method
- Microsoft::WRL::Wrappers::HandleT::IsValid method
- Microsoft::WRL::Wrappers::HandleT::operator= operator
- Microsoft::WRL::Wrappers::HandleT::~HandleT, destructor
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
ms.openlocfilehash: f66fbe23c305be15e09928242175dfa7ce8c141b
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821821"
---
# <a name="handlet-class"></a>HandleT — Klasa

Reprezentuje dojście do obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parametry

*HandleTraits*<br/>
Wystąpienie struktury [HandleTraits](handletraits-structure.md) , które definiuje typowe cechy dojścia.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa     | Opis
-------- | -----------------------------
`Traits` | Synonim dla `HandleTraits`.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | --------------------------------------------------
[Obsługa:: obsługa](#handlet)        | Inicjuje nowe wystąpienie klasy `HandleT` klasy.
[HandleT::~HandleT](#tilde-handlet) | Deinicjalizuje wystąpienie klasy `HandleT`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                         | Opis
---------------------------- | ----------------------------------------------------------------------
[Uchwyt:: Attach](#attach)   | Kojarzy określone dojście z bieżącym obiektem `HandleT`.
[Obsługa:: Close](#close)     | Zamyka bieżący obiekt `HandleT`.
[Obsługa::D etach](#detach)   | Odkojarzy bieżący obiekt `HandleT` z jego bazowego uchwytu.
[Obsługa:: Get](#get)         | Pobiera wartość bazowego dojścia.
[Obsługa:: IsValid](#isvalid) | Wskazuje, czy bieżący obiekt `HandleT` reprezentuje uchwyt.

### <a name="protected-methods"></a>Metody chronione

Nazwa                                     | Opis
---------------------------------------- | ------------------------------------
[Obsługa:: InternalClose —](#internalclose) | Zamyka bieżący obiekt `HandleT`.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                   | Opis
-------------------------------------- | ----------------------------------------------------------------------------------
[Handle:: operator =](#operator-assign) | Przenosi wartość określonego obiektu `HandleT` do bieżącego obiektu `HandleT`.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------------------------------
[Obsługa:: handle_](#handle) | Zawiera dojście reprezentowane przez obiekt `HandleT`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki

## <a name="tilde-handlet"></a>Obsługa:: ~ obsługa

Deinicjalizuje wystąpienie klasy `HandleT`.

```cpp
~HandleT();
```

## <a name="attach"></a>Uchwyt:: Attach

Kojarzy określone dojście z bieżącym obiektem `HandleT`.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Uchwyt.

## <a name="close"></a>Obsługa:: Close

Zamyka bieżący obiekt `HandleT`.

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Dojście, które jest zależne od bieżącego `HandleT` jest zamknięte, a `HandleT` jest ustawiony na nieprawidłowy stan.

Jeśli uchwyt nie zostanie zamknięty prawidłowo, wyjątek jest wywoływany w wątku wywołującym.

## <a name="detach"></a>Obsługa::D etach

Odkojarzy bieżący obiekt `HandleT` z jego bazowego uchwytu.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Wartość zwrócona

Podstawowy uchwyt.

### <a name="remarks"></a>Uwagi

Po zakończeniu tej operacji bieżący `HandleT` jest ustawiony na nieprawidłowy stan.

## <a name="get"></a>Obsługa:: Get

Pobiera wartość bazowego dojścia.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Wartość zwrócona

Uchwyt.

## <a name="handle"></a>Obsługa:: handle_

Zawiera dojście reprezentowane przez obiekt `HandleT`.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlet"></a>Obsługa:: obsługa

Inicjuje nowe wystąpienie klasy `HandleT` klasy.

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Uchwyt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje obiekt `HandleT`, który nie jest prawidłowym dojściem do obiektu. Drugi Konstruktor tworzy nowy obiekt `HandleT` z parametru *h*.

## <a name="internalclose"></a>Obsługa:: InternalClose —

Zamyka bieżący obiekt `HandleT`.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli bieżące `HandleT` zamknięte pomyślnie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`InternalClose()` jest `protected`.

## <a name="isvalid"></a>Obsługa:: IsValid

Wskazuje, czy bieżący obiekt `HandleT` reprezentuje uchwyt.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli `HandleT` reprezentuje uchwyt; w przeciwnym razie **false**.

## <a name="operator-assign"></a>Handle:: operator =

Przenosi wartość określonego obiektu `HandleT` do bieżącego obiektu `HandleT`.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Rvalue odwołanie do dojścia.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do bieżącego obiektu `HandleT`.

### <a name="remarks"></a>Uwagi

Ta operacja unieważnia obiekt `HandleT` określony przez parametr *h*.
