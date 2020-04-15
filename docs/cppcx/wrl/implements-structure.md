---
title: Implements — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: 223f37d7cabbd0b8cd238582773c05d7b9eaabf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371407"
---
# <a name="implements-structure"></a>Implements — Struktura

Implementuje `QueryInterface` `GetIid` i dla określonych interfejsów.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Identyfikator interfejsu zerowego. (Obowiązkowe)

*I1*<br/>
Pierwszy identyfikator interfejsu. (opcjonalnie)

*I2*<br/>
Drugi identyfikator interfejsu. (opcjonalnie)

*I3*<br/>
Trzeci identyfikator interfejsu. (opcjonalnie)

*I4*<br/>
Czwarty identyfikator interfejsu. (opcjonalnie)

*I5*<br/>
Identyfikator piątego interfejsu. (opcjonalnie)

*I6*<br/>
Szósty identyfikator interfejsu. (opcjonalnie)

*I7*<br/>
Identyfikator siódmego interfejsu. (opcjonalnie)

*I8*<br/>
Identyfikator ósmego interfejsu. (opcjonalnie)

*I9*<br/>
Identyfikator dziewiątego interfejsu. (opcjonalnie)

*flagi*<br/>
Flagi konfiguracji dla klasy. Co najmniej jedno [wyliczenia RuntimeClassType,](runtimeclasstype-enumeration.md) które są określone w strukturze [RuntimeClassFlags.](runtimeclassflags-structure.md)

## <a name="remarks"></a>Uwagi

Pochodzi z listy określonych interfejsów i implementuje szablony pomocników dla `QueryInterface` i `GetIid`.

Każdy parametr interfejsu *I0* do *I9* `IUnknown`musi `IInspectable`pochodzić z szablonu [ChainInterfaces lub ChainInterfaces.](chaininterfaces-structure.md) Parametr *flags* określa, czy dla `IUnknown` `IInspectable`lub .

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

| Nazwa        | Opis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonimem . `RuntimeClassFlags<WinRt>` |

### <a name="protected-methods"></a>Metody chronione

| Nazwa                                              | Opis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementacje::CanCastTo](#cancastto)               | Pobiera wskaźnik do określonego interfejsu.                                                                    |
| [Implementuje::CastToUnknown](#casttounknown)       | Pobiera wskaźnik do `IUnknown` interfejsu źródłowego.                                                        |
| [Implementuje::FillArrayWithIid](#fillarraywithiid) | Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy. |

### <a name="protected-constants"></a>Stałe chronione

| Nazwa                              | Opis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementuje::IidCount](#iidcount) | Przechowuje liczbę zaimplementowanych identyfikatorów interfejsu. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a>Implementacje::CanCastTo

Pobiera wskaźnik do określonego interfejsu.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Odwołanie do identyfikatora interfejsu.

*Ppv*<br/>
Jeśli się powiedzie, wskaźnik do interfejsu określonego przez *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd, takich jak E_NOINTERFACE.

### <a name="remarks"></a>Uwagi

Jest to wewnętrzna funkcja pomocnika, która wykonuje queryinterface operacji.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a>Implementuje::CastToUnknown

Pobiera wskaźnik do `IUnknown` interfejsu źródłowego.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Ta operacja zawsze powiedzie `IUnknown` się i zwraca wskaźnik.

### <a name="remarks"></a>Uwagi

Wewnętrzna funkcja pomocnika.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a>Implementuje::FillArrayWithIid

Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Indeks od zera, który wskazuje początkowy element tablicy dla tej operacji. Po zakończeniu tej operacji *indeks* jest zwiększany o 1.

*iids*<br/>
Tablica typu IID.

### <a name="remarks"></a>Uwagi

Wewnętrzna funkcja pomocnika.

## <a name="implementsiidcount"></a><a name="iidcount"></a>Implementuje::IidCount

Przechowuje liczbę zaimplementowanych identyfikatorów interfejsu.

```cpp
static const unsigned long IidCount;
```
