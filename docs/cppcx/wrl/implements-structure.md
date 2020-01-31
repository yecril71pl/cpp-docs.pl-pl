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
ms.openlocfilehash: 0ce6e9193107cbd0d033d99b257e41004b4343a8
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821860"
---
# <a name="implements-structure"></a>Implements — Struktura

Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.

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
Identyfikator interfejsu zerowego. Wypełnione

*Elementem I1*<br/>
Identyfikator pierwszego interfejsu. (Opcjonalnie:)

*I2*<br/>
Identyfikator drugiego interfejsu. (Opcjonalnie:)

*I3*<br/>
Identyfikator trzeciego interfejsu. (Opcjonalnie:)

*I4*<br/>
Identyfikator czwartego interfejsu. (Opcjonalnie:)

*I5*<br/>
Identyfikator piątego interfejsu. (Opcjonalnie:)

*I6*<br/>
Identyfikator szóstego interfejsu. (Opcjonalnie:)

*I7*<br/>
Siódmy identyfikator interfejsu. (Opcjonalnie:)

*I8*<br/>
Identyfikator ósmego interfejsu. (Opcjonalnie:)

*I9*<br/>
Dziewiąty identyfikator interfejsu. (Opcjonalnie:)

*znaczników*<br/>
Flagi konfiguracji dla klasy. Co najmniej jedno Wyliczenie [RuntimeClassType —](runtimeclasstype-enumeration.md) określone w strukturze [RuntimeClassFlags](runtimeclassflags-structure.md) .

## <a name="remarks"></a>Uwagi

Pochodzi z listy określonych interfejsów i implementuje szablony pomocników dla `QueryInterface` i `GetIid`.

Każdy *I0* za pośrednictwem parametru interfejsu *i9* musi pochodzić od `IUnknown`, `IInspectable`lub szablonu [ChainInterfaces](chaininterfaces-structure.md) . Parametr *flags* określa, czy obsługa jest generowana dla `IUnknown` lub `IInspectable`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

| Nazwa        | Opis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonim dla `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Metody chronione

| Nazwa                                              | Opis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implementuje:: CanCastTo —](#cancastto)               | Pobiera wskaźnik do określonego interfejsu.                                                                    |
| [Implementuje:: CastToUnknown —](#casttounknown)       | Pobiera wskaźnik do podstawowego interfejsu `IUnknown`.                                                        |
| [Implementuje:: FillArrayWithIid —](#fillarraywithiid) | Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy. |

### <a name="protected-constants"></a>Chronione stałe

| Nazwa                              | Opis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implementuje:: IidCount —](#iidcount) | Przechowuje liczbę zaimplementowanych identyfikatorów interfejsów. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="cancastto"></a>Implementuje:: CanCastTo —

Pobiera wskaźnik do określonego interfejsu.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppv*<br/>
Jeśli to się powiedzie, wskaźnik do interfejsu określony przez *riid*.

### <a name="return-value"></a>Wartość zwrócona

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT wskazuje błąd, taki jak E_NOINTERFACE.

### <a name="remarks"></a>Uwagi

Jest to wewnętrzna funkcja pomocnicza, która wykonuje operację QueryInterface.

## <a name="casttounknown"></a>Implementuje:: CastToUnknown —

Pobiera wskaźnik do podstawowego interfejsu `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwrócona

Ta operacja zawsze powiedzie się i zwróci wskaźnik `IUnknown`.

### <a name="remarks"></a>Uwagi

Wewnętrzna funkcja pomocnika.

## <a name="fillarraywithiid"></a>Implementuje:: FillArrayWithIid —

Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Indeks (liczony od zera) wskazujący początkowy element tablicy dla tej operacji. Po zakończeniu tej operacji *indeks* jest zwiększany o 1.

*IID*<br/>
Tablica typu IID.

### <a name="remarks"></a>Uwagi

Wewnętrzna funkcja pomocnika.

## <a name="iidcount"></a>Implementuje:: IidCount —

Przechowuje liczbę zaimplementowanych identyfikatorów interfejsów.

```cpp
static const unsigned long IidCount;
```
