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
ms.openlocfilehash: 9fd315f017d3dcc9823054ea99e845ec99bc4192
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787309"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces — Struktura

Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.

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
(Wymagane) Identyfikator interfejsu: 0.

*I1*<br/>
(Wymagane) Identyfikator interfejsu: 1.

*I2*<br/>
(Opcjonalnie) Identyfikator interfejsu: 2.

*I3*<br/>
(Opcjonalnie) Identyfikator interfejsu 3.

*I4*<br/>
(Opcjonalnie) Identyfikator interfejsu: 4.

*I5*<br/>
(Opcjonalnie) Identyfikator interfejsu 5.

*I6*<br/>
(Opcjonalnie) Identyfikator interfejsu 6.

*I7*<br/>
(Opcjonalnie) Identyfikator interfejsu 7.

*I8*<br/>
(Opcjonalnie) Identyfikator interfejsu 8.

*I9*<br/>
(Opcjonalnie) Identyfikator interfejsu: 9.

*DerivedType*<br/>
Typ pochodny.

*BaseType*<br/>
Typ podstawowy typu pochodnego.

*hasImplements*<br/>
Wartość logiczna, że jeśli **true**, oznacza, że nie można użyć [domieszki](mixin-structure.md) struktury z klasą, która nie pochodzi od [implementuje](implements-structure.md) stucture.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na każdej specjalizacji definicją `ChainInterface` parametry szablonu.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Rzutuje wskaźnika interfejsu typu zdefiniowanego przez *I0* parametr szablonu na wskaźnik do `IUnknown`.
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Identyfikator interfejsu zdefiniowanych przez magazynów *I0* parametru szablonu w określonej lokalizacji w określonej tablicy interfejsu identyfikatorów.
[ChainInterfaces::Verify](#verify)                     | Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *I9* dziedziczy `IUnknown` i/lub `IInspectable`oraz że *I0* dziedziczy z *I1* za pośrednictwem *I9*.

### <a name="protected-constants"></a>Stałe chronione

Nazwa                                   | Opis
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Całkowita liczba interfejsu identyfikatory zawarte w interfejsach, określonego przez parametry szablonu *I0* za pośrednictwem *I9*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="cancastto"></a>ChainInterfaces::CanCastTo

Wskazuje, czy identyfikator określonego interfejsu, mogą być rzutowane na każdej specjalizacji zdefiniowane przez parametry szablonu innych niż domyślne.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*ppv*<br/>
Wskaźnik do ostatniego Identyfikatora interfejsu, który został pomyślnie rzutowania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wszystkie operacje rzutowania zakończyło się pomyślnie; w przeciwnym razie **false**.

## <a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Rzutuje wskaźnika interfejsu typu zdefiniowanego przez *I0* parametr szablonu na wskaźnik do `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown`.

## <a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Identyfikator interfejsu zdefiniowanych przez magazynów *I0* parametru szablonu w określonej lokalizacji w określonej tablicy interfejsu identyfikatorów.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Wskaźnik do wartości indeksu do *IID* tablicy.

*IID*<br/>
Tablica identyfikatorów interfejsu.

## <a name="iidcount"></a>ChainInterfaces::IidCount

Całkowita liczba interfejsu identyfikatory zawarte w interfejsach, określonego przez parametry szablonu *I0* za pośrednictwem *I9*.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Wartość zwracana

Całkowita liczba identyfikatorów interfejsu.

### <a name="remarks"></a>Uwagi

Parametry szablonu *I0* i *I1* są wymagane i parametry *I2* za pośrednictwem *I9* są opcjonalne. Liczba IID każdego interfejsu, jest zazwyczaj 1.

## <a name="verify"></a>ChainInterfaces::Verify

Sprawdza, czy każdy interfejs zdefiniowany przez parametry szablonu *I0* za pośrednictwem *I9* dziedziczy `IUnknown` i/lub `IInspectable`oraz że *I0* dziedziczy z *I1* za pośrednictwem *I9*.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

W przypadku niepowodzenia operacji weryfikacji `static_assert` emituje komunikat o błędzie opisujący błąd.

Parametry szablonu *I0* i *I1* są wymagane i parametry *I2* za pośrednictwem *I9* są opcjonalne.
