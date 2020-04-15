---
title: ChainInterfaces — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372654"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces — Struktura

Określa funkcje weryfikacji i inicjowania, które można zastosować do zestawu identyfikatorów interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
(Wymagane) Identyfikator interfejsu 0.

*I1*<br/>
(Wymagane) Identyfikator interfejsu 1.

*I2*<br/>
(Opcjonalnie) Identyfikator interfejsu 2.

*I3*<br/>
(Opcjonalnie) Identyfikator interfejsu 3.

*I4*<br/>
(Opcjonalnie) Identyfikator interfejsu 4.

*I5*<br/>
(Opcjonalnie) Identyfikator interfejsu 5.

*I6*<br/>
(Opcjonalnie) Identyfikator interfejsu 6.

*I7*<br/>
(Opcjonalnie) Identyfikator interfejsu 7.

*I8*<br/>
(Opcjonalnie) Identyfikator interfejsu 8.

*I9*<br/>
(Opcjonalnie) Identyfikator interfejsu 9.

*Typ pochodny*<br/>
Typ pochodny.

*BaseType*<br/>
Typ podstawowy typu pochodnego.

*HasImplements*<br/>
Wartość logiczna, która jeśli **true**, oznacza, że nie można użyć [MixIn](mixin-structure.md) struktury z klasy, która nie pochodzi od [Implements](implements-structure.md) stucture.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Wskazuje, czy określony identyfikator interfejsu może być rzutowany na każdą `ChainInterface` ze specjalizacji zdefiniowanych przez parametry szablonu.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Rzutuje wskaźnik interfejsu typu zdefiniowanego przez parametr szablonu `IUnknown` *I0* na wskaźnik do .
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Przechowuje identyfikator interfejsu zdefiniowany przez parametr szablonu *I0* w określonej lokalizacji w określonej tablicy identyfikatorów interfejsu.
[ChainInterfaces::Sprawdź](#verify)                     | Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu od `IInspectable` *I0* do *I9* dziedziczy i/lub `IUnknown` , a *I0* dziedziczy od *I1* do *I9.*

### <a name="protected-constants"></a>Stałe chronione

Nazwa                                   | Opis
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Całkowita liczba identyfikatorów interfejsu zawartych w interfejsach określonych przez parametry szablonu *od I0* do *I9*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces::CanCastTo

Wskazuje, czy określony identyfikator interfejsu może być rzutowany na każdą ze specjalizacji zdefiniowanych przez domyślne parametry szablonu.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*Ppv*<br/>
Wskaźnik do ostatniego identyfikatora interfejsu, który został pomyślnie oddanych.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wszystkie operacje rzutowania zakończyły się pomyślnie; w przeciwnym razie **false**.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Rzutuje wskaźnik interfejsu typu zdefiniowanego przez parametr szablonu `IUnknown` *I0* na wskaźnik do .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Przechowuje identyfikator interfejsu zdefiniowany przez parametr szablonu *I0* w określonej lokalizacji w określonej tablicy identyfikatorów interfejsu.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Wskaźnik do wartości indeksu do *tablicy iids.*

*iids*<br/>
Tablica identyfikatorów interfejsu.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces::IidCount

Całkowita liczba identyfikatorów interfejsu zawartych w interfejsach określonych przez parametry szablonu *od I0* do *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Wartość zwracana

Całkowita liczba identyfikatorów interfejsu.

### <a name="remarks"></a>Uwagi

Parametry szablonu *I0* i *I1* są wymagane, a parametry *od I2* do *I9* są opcjonalne. Liczba identyfikatorów każdego interfejsu jest zazwyczaj 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces::Sprawdź

Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu od `IInspectable` *I0* do *I9* dziedziczy i/lub `IUnknown` , a *I0* dziedziczy od *I1* do *I9.*

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

Jeśli operacja weryfikacji nie `static_assert` powiedzie się, emituje komunikat o błędzie opisujący błąd.

Parametry szablonu *I0* i *I1* są wymagane, a parametry *od I2* do *I9* są opcjonalne.
