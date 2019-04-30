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
ms.openlocfilehash: 63cac6931428644cc5ddec7d87e49007e95e039d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398254"
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
Identyfikator interfejsu zerowego. (Obowiązkowe)

*I1*<br/>
Identyfikator pierwszego interfejsu. (opcjonalnie)

*I2*<br/>
Identyfikator drugiego interfejsu. (opcjonalnie)

*I3*<br/>
Identyfikator trzeciego interfejsu. (opcjonalnie)

*I4*<br/>
Identyfikator czwartego interfejsu. (opcjonalnie)

*I5*<br/>
Identyfikator piątego interfejsu. (opcjonalnie)

*I6*<br/>
Identyfikator szóstego interfejsu. (opcjonalnie)

*I7*<br/>
Identyfikator siódmego interfejsu. (opcjonalnie)

*I8*<br/>
Identyfikator ósmego interfejsu. (opcjonalnie)

*I9*<br/>
Identyfikator dziewiątego interfejsu. (opcjonalnie)

*flagi*<br/>
Flagi konfiguracji dla klasy. Co najmniej jeden [RuntimeClassType](runtimeclasstype-enumeration.md) wyliczenia, które są określone w [runtimeclassflags —](runtimeclassflags-structure.md) struktury.

## <a name="remarks"></a>Uwagi

Pochodzi z listy określonych interfejsów i implementuje szablony pomocnika na potrzeby `QueryInterface` i `GetIid`.

Każdy *I0* za pośrednictwem *I9* parametru interfejs musi pochodzić z klasy `IUnknown`, `IInspectable`, lub [chaininterfaces —](chaininterfaces-structure.md) szablonu. *Flagi* parametr określa, czy obsługa jest generowany dla `IUnknown` lub `IInspectable`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

| Nazwa        | Opis                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| Synonim dla `RuntimeClassFlags<WinRt>`. |

### <a name="protected-methods"></a>Metody chronione

| Nazwa                                              | Opis                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements::CanCastTo](#cancastto)               | Pobiera wskaźnik do określonego interfejsu.                                                                    |
| [Implements::CastToUnknown](#casttounknown)       | Pobiera wskaźnik do bazowego `IUnknown` interfejsu.                                                        |
| [Implements::FillArrayWithIid](#fillarraywithiid) | Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy. |

### <a name="protected-constants"></a>Stałe chronione

| Nazwa                              | Opis                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements::IidCount](#iidcount) | Przechowuje liczbę zaimplementowanego interfejsu identyfikatorów. |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="cancastto"></a>Implements::CanCastTo

Pobiera wskaźnik do określonego interfejsu.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppv*<br/>
Jeśli operacja się powiedzie, wskaźnik do interfejsu określonego przez *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie HRESULT, która wskazuje błąd, takich jak E_NOINTERFACE.

### <a name="remarks"></a>Uwagi

Jest to funkcja pomocnicza wewnętrznej, która wykonuje operację QueryInterface.

## <a name="casttounknown"></a>Implements::CastToUnknown

Pobiera wskaźnik do bazowego `IUnknown` interfejsu.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Ta operacja zawsze powiedzie się i zwraca `IUnknown` wskaźnika.

### <a name="remarks"></a>Uwagi

Funkcja pomocnika wewnętrznego.

## <a name="fillarraywithiid"></a>Implements::FillArrayWithIid

Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera indeks, który wskazuje element początkowy tablicy do wykonania tej operacji. Po zakończeniu tej operacji, *indeksu* jest zwiększana o 1.

*IID*<br/>
Tablica typu IID.

### <a name="remarks"></a>Uwagi

Funkcja pomocnika wewnętrznego.

## <a name="iidcount"></a>Implements::IidCount

Przechowuje liczbę zaimplementowanego interfejsu identyfikatorów.

```cpp
static const unsigned long IidCount;
```
