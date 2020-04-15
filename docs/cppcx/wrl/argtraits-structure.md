---
title: ArgTraits — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377169"
---
# <a name="argtraits-structure"></a>ArgTraits — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parametry

*Funkcja TMemberFunction*<br/>
Parametr Typename dla struktury ArgTraits, `Invoke` która nie może być zgodna z podpisem żadnej metody.

*TDelegateInterface*<br/>
Interfejs delegata.

*Targ1 ( TArg1 )*<br/>
Typ pierwszego argumentu `Invoke` metody.

*Targ2 (polski)*<br/>
Typ drugiego argumentu `Invoke` metody.

*Targ3 ( TArg3 )*<br/>
Typ trzeciego argumentu `Invoke` metody.

*Targ4 ( TArg4 )*<br/>
Typ czwartego argumentu `Invoke` metody.

*Targ5 ( TArg5 )*<br/>
Typ piątego argumentu `Invoke` metody.

*Targ6 ( TArg6 )*<br/>
Typ szóstego argumentu `Invoke` metody.

*Targ7 ( TArg7 )*<br/>
Typ siódmego argumentu `Invoke` metody.

*Targ8 ( TArg8 )*<br/>
Typ ósmego argumentu `Invoke` metody.

*Targ9 ( TArg9 )*<br/>
Typ dziewiątego argumentu `Invoke` metody.

## <a name="remarks"></a>Uwagi

Struktura `ArgTraits` deklaruje określony interfejs delegata i funkcję anonimowego elementu członkowskiego, która ma określoną liczbę parametrów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa       | Opis
---------- | ----------------------
`Arg1Type` | Typedef dla TArg1.
`Arg2Type` | Typedef dla TArg2.
`Arg3Type` | Typedef dla TArg3.
`Arg4Type` | Typedef dla TArg4.
`Arg5Type` | Typedef dla TArg5.
`Arg6Type` | Typedef dla TArg6.
`Arg7Type` | Typedef dla TArg7.
`Arg8Type` | Typedef dla TArg8.
`Arg9Type` | Typedef dla TArg9.

### <a name="public-constants"></a>Stałe publiczne

Nazwa                     | Opis
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Przechowuje liczbę parametrów na `Invoke` metodę interfejsu delegata.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ArgTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="argtraitsargs"></a><a name="args"></a>ArgTraits::args

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę parametrów na `Invoke` metodę interfejsu delegata. Gdy `args` jest równa -1, nie może `Invoke` być zgodne dla podpisu metody.
