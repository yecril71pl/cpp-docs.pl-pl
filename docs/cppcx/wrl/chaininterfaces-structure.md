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
ms.openlocfilehash: 48b663f2042ff0095466d83fe872ef6196112f76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211544"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces — Struktura

Określa funkcje weryfikacji i inicjowania, które mogą być stosowane do zestawu identyfikatorów interfejsów.

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
Potrzeb Identyfikator interfejsu 0.

*Elementem I1*<br/>
Potrzeb Identyfikator interfejsu 1.

*I2*<br/>
Obowiązkowe Identyfikator interfejsu 2.

*I3*<br/>
Obowiązkowe Identyfikator interfejsu 3.

*I4*<br/>
Obowiązkowe Identyfikator interfejsu 4.

*I5*<br/>
Obowiązkowe Identyfikator interfejsu 5.

*I6*<br/>
Obowiązkowe Identyfikator interfejsu 6.

*I7*<br/>
Obowiązkowe Identyfikator interfejsu 7.

*I8*<br/>
Obowiązkowe Identyfikator interfejsu 8.

*I9*<br/>
Obowiązkowe Identyfikator interfejsu 9.

*Pochodntype*<br/>
Typ pochodny.

*BaseType*<br/>
Typ podstawowy typu pochodnego.

*hasImplements*<br/>
Wartość logiczna, która **`true`** oznacza, że nie można użyć struktury [domieszki](mixin-structure.md) z klasą, która nie pochodzi od [implementuje](implements-structure.md) Stucture.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces:: CanCastTo —](#cancastto)               | Wskazuje, czy określony identyfikator interfejsu może być rzutowany do każdej specjalizacji zdefiniowanej przez `ChainInterface` Parametry szablonu.
[ChainInterfaces:: CastToUnknown —](#casttounknown)       | Rzutuje wskaźnik interfejsu typu zdefiniowanego przez parametr szablonu *I0* na wskaźnik do `IUnknown` .
[ChainInterfaces:: FillArrayWithIid —](#fillarraywithiid) | Przechowuje identyfikator interfejsu zdefiniowany przez parametr szablonu *I0* w określonej lokalizacji w określonej tablicy identyfikatorów interfejsu.
[ChainInterfaces:: Verify](#verify)                     | Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *i9* dziedziczy z `IUnknown` i/lub `IInspectable` , i że *I0* dziedziczy z elementów *I1* za pośrednictwem *i9*.

### <a name="protected-constants"></a>Chronione stałe

Nazwa                                   | Opis
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces:: IidCount —](#iidcount) | Całkowita liczba identyfikatorów interfejsów zawartych w interfejsach określonych przez parametry szablonu *I0* do *i9*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces:: CanCastTo —

Wskazuje, czy określony identyfikator interfejsu może być rzutowany do każdej specjalizacji zdefiniowanej przez parametry szablonu inne niż domyślne.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*ppv*<br/>
Wskaźnik do ostatniego identyfikatora interfejsu, który został pomyślnie przerzutowany.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wszystkie operacje rzutowania zakończyły się powodzeniem; w przeciwnym razie **`false`** .

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces:: CastToUnknown —

Rzutuje wskaźnik interfejsu typu zdefiniowanego przez parametr szablonu *I0* na wskaźnik do `IUnknown` .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` .

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces:: FillArrayWithIid —

Przechowuje identyfikator interfejsu zdefiniowany przez parametr szablonu *I0* w określonej lokalizacji w określonej tablicy identyfikatorów interfejsu.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*indeks*<br/>
Wskaźnik na wartość indeksu do tablicy *IID* .

*IID*<br/>
Tablica identyfikatorów interfejsów.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces:: IidCount —

Całkowita liczba identyfikatorów interfejsów zawartych w interfejsach określonych przez parametry szablonu *I0* do *i9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Wartość zwracana

Całkowita liczba identyfikatorów interfejsów.

### <a name="remarks"></a>Uwagi

Parametry szablonu *I0* i *I1* są wymagane, a parametry *I2* do *i9* są opcjonalne. Liczba IID każdego interfejsu jest zwykle 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces:: Verify

Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *i9* dziedziczy z `IUnknown` i/lub `IInspectable` , i że *I0* dziedziczy z elementów *I1* za pośrednictwem *i9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

Jeśli operacja weryfikacji nie powiedzie się, **`static_assert`** emituje komunikat o błędzie opisujący błąd.

Parametry szablonu *I0* i *I1* są wymagane, a parametry *I2* do *i9* są opcjonalne.
