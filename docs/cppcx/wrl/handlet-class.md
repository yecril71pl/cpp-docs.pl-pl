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
ms.openlocfilehash: 661d3cb92b20fc929a9bae3cad7bb55740e5e096
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213011"
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
`Traits` | Synonim dla `HandleTraits` .

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | --------------------------------------------------
[Obsługa:: obsługa](#handlet)        | Inicjuje nowe wystąpienie klasy `HandleT`.
[Obsługa:: ~ obsługa](#tilde-handlet) | Umożliwia odinicjowanie wystąpienia `HandleT` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                         | Opis
---------------------------- | ----------------------------------------------------------------------
[Uchwyt:: Attach](#attach)   | Kojarzy określone dojście z bieżącym `HandleT` obiektem.
[Obsługa:: Close](#close)     | Zamyka bieżący `HandleT` obiekt.
[Obsługa::D etach](#detach)   | Odkojarzy bieżący `HandleT` obiekt z jego bazowego uchwytu.
[Obsługa:: Get](#get)         | Pobiera wartość bazowego dojścia.
[Obsługa:: IsValid](#isvalid) | Wskazuje, czy bieżący `HandleT` obiekt reprezentuje uchwyt.

### <a name="protected-methods"></a>Metody chronione

Nazwa                                     | Opis
---------------------------------------- | ------------------------------------
[Obsługa:: InternalClose —](#internalclose) | Zamyka bieżący `HandleT` obiekt.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                   | Opis
-------------------------------------- | ----------------------------------------------------------------------------------
[Handle:: operator =](#operator-assign) | Przenosi wartość określonego `HandleT` obiektu do bieżącego `HandleT` obiektu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------------------------------
[Obsługa:: handle_](#handle) | Zawiera dojście reprezentowane przez `HandleT` obiekt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>Obsługa:: ~ obsługa

Umożliwia odinicjowanie wystąpienia `HandleT` klasy.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>Uchwyt:: Attach

Kojarzy określone dojście z bieżącym `HandleT` obiektem.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Uchwyt.

## <a name="handletclose"></a><a name="close"></a>Obsługa:: Close

Zamyka bieżący `HandleT` obiekt.

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Dojście, które jest zależne od bieżącego `HandleT` jest zamknięte, a `HandleT` jest ustawione na nieprawidłowy stan.

Jeśli uchwyt nie zostanie zamknięty prawidłowo, wyjątek jest wywoływany w wątku wywołującym.

## <a name="handletdetach"></a><a name="detach"></a>Obsługa::D etach

Odkojarzy bieżący `HandleT` obiekt z jego bazowego uchwytu.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Wartość zwracana

Podstawowy uchwyt.

### <a name="remarks"></a>Uwagi

Po zakończeniu tej operacji bieżący `HandleT` stan jest ustawiony na nieprawidłowy.

## <a name="handletget"></a><a name="get"></a>Obsługa:: Get

Pobiera wartość bazowego dojścia.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt.

## <a name="handlethandle_"></a><a name="handle"></a>Obsługa:: handle_

Zawiera dojście reprezentowane przez `HandleT` obiekt.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>Obsługa:: obsługa

Inicjuje nowe wystąpienie klasy `HandleT`.

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

*c*<br/>
Uchwyt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje `HandleT` obiekt, który nie jest prawidłowym dojściem do obiektu. Drugi Konstruktor tworzy nowy `HandleT` obiekt z parametru *h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>Obsługa:: InternalClose —

Zamyka bieżący `HandleT` obiekt.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli bieżący `HandleT` zamknięto pomyślnie; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

`InternalClose()`jest **`protected`** .

## <a name="handletisvalid"></a><a name="isvalid"></a>Obsługa:: IsValid

Wskazuje, czy bieżący `HandleT` obiekt reprezentuje uchwyt.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `HandleT` reprezentuje uchwyt; w przeciwnym razie, **`false`** .

## <a name="handletoperator"></a><a name="operator-assign"></a>Handle:: operator =

Przenosi wartość określonego `HandleT` obiektu do bieżącego `HandleT` obiektu.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Rvalue odwołanie do dojścia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `HandleT` obiektu.

### <a name="remarks"></a>Uwagi

Ta operacja unieważnia `HandleT` obiekt określony przez parametr *h*.
