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
ms.openlocfilehash: bde7d7f1bd6730d96cb0f7a0d191a32eb8ed3e8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371463"
---
# <a name="handlet-class"></a>HandleT — Klasa

Reprezentuje dojście do obiektu.

## <a name="syntax"></a>Składnia

```cpp
template <typename HandleTraits>
class HandleT;
```

### <a name="parameters"></a>Parametry

*HandleTraits (HandleTraits)*<br/>
Wystąpienie [HandleTraits](handletraits-structure.md) struktury, która definiuje wspólne cechy dojścia.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa     | Opis
-------- | -----------------------------
`Traits` | Synonimem . `HandleTraits`

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | --------------------------------------------------
[Uchwyt::Uchwyt](#handlet)        | Inicjuje nowe wystąpienie klasy `HandleT`.
[Uchwyt::~Uchwyt](#tilde-handlet) | Deinitializes wystąpienia `HandleT` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                         | Opis
---------------------------- | ----------------------------------------------------------------------
[Uchwyt::Dołącz](#attach)   | Kojarzy określony dojście `HandleT` z bieżącym obiektem.
[Uchwyt::Zamknij](#close)     | Zamyka bieżący `HandleT` obiekt.
[Uchwyt: :Detach](#detach)   | Odłącza bieżący `HandleT` obiekt od jego dojścia.
[Uchwyt::Pobierz](#get)         | Pobiera wartość dojścia źródłowego.
[Uchwyt::IsValid](#isvalid) | Wskazuje, czy `HandleT` bieżący obiekt reprezentuje dojście.

### <a name="protected-methods"></a>Metody chronione

Nazwa                                     | Opis
---------------------------------------- | ------------------------------------
[Uchwyt::InternalClose](#internalclose) | Zamyka bieżący `HandleT` obiekt.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                   | Opis
-------------------------------------- | ----------------------------------------------------------------------------------
[Uchwyt::operator=](#operator-assign) | Przenosi wartość określonego `HandleT` obiektu do `HandleT` bieżącego obiektu.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------------------------------
[Uchwyt::handle_](#handle) | Zawiera dojście, który `HandleT` jest reprezentowany przez obiekt.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="handlethandlet"></a><a name="tilde-handlet"></a>Uchwyt::~Uchwyt

Deinitializes wystąpienia `HandleT` klasy.

```cpp
~HandleT();
```

## <a name="handletattach"></a><a name="attach"></a>Uchwyt::Dołącz

Kojarzy określony dojście `HandleT` z bieżącym obiektem.

```cpp
void Attach(
   typename HandleTraits::Type h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Uchwyt.

## <a name="handletclose"></a><a name="close"></a>Uchwyt::Zamknij

Zamyka bieżący `HandleT` obiekt.

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Dojście, który leży `HandleT` u podstaw `HandleT` bieżącego jest zamknięty, a jest ustawiona na nieprawidłowy stan.

Jeśli dojście nie zamyka się poprawnie, wyjątek jest wywoływany w wątku wywołującym.

## <a name="handletdetach"></a><a name="detach"></a>Uchwyt: :Detach

Odłącza bieżący `HandleT` obiekt od jego dojścia.

```cpp
typename HandleTraits::Type Detach();
```

### <a name="return-value"></a>Wartość zwracana

Dojście źródłowe.

### <a name="remarks"></a>Uwagi

Po zakończeniu tej operacji `HandleT` bieżący jest ustawiony na nieprawidłowy stan.

## <a name="handletget"></a><a name="get"></a>Uchwyt::Pobierz

Pobiera wartość dojścia źródłowego.

```cpp
typename HandleTraits::Type Get() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt.

## <a name="handlethandle_"></a><a name="handle"></a>Uchwyt::handle_

Zawiera dojście, który `HandleT` jest reprezentowany przez obiekt.

```cpp
typename HandleTraits::Type handle_;
```

## <a name="handlethandlet"></a><a name="handlet"></a>Uchwyt::Uchwyt

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

*H*<br/>
Uchwyt.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje `HandleT` obiekt, który nie jest prawidłowym dojściem do obiektu. Drugi konstruktor tworzy `HandleT` nowy obiekt z *parametru h*.

## <a name="handletinternalclose"></a><a name="internalclose"></a>Uchwyt::InternalClose

Zamyka bieżący `HandleT` obiekt.

```cpp
virtual bool InternalClose();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli `HandleT` bieżący zamknięty pomyślnie; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Parametr `InternalClose()` ma wartość `protected`.

## <a name="handletisvalid"></a><a name="isvalid"></a>Uchwyt::IsValid

Wskazuje, czy `HandleT` bieżący obiekt reprezentuje dojście.

```cpp
bool IsValid() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** `HandleT` jeśli reprezentuje dojście; w przeciwnym razie **false**.

## <a name="handletoperator"></a><a name="operator-assign"></a>Uchwyt::operator=

Przenosi wartość określonego `HandleT` obiektu do `HandleT` bieżącego obiektu.

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Odwołanie rvalue do dojścia.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `HandleT` obiektu.

### <a name="remarks"></a>Uwagi

Ta operacja unieważnia `HandleT` obiekt określony przez parametr *h*.
