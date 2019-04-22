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
ms.openlocfilehash: 17109508cf99888ccde79be39a41c5361da24c6e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787310"
---
# <a name="argtraits-structure"></a>ArgTraits — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*TMemberFunction*<br/>
Parametr TypeName argtraits — struktura, która nie pasuje do żadnego `Invoke` podpis metody.

*TDelegateInterface*<br/>
Interfejs delegata.

*TArg1*<br/>
Typ pierwszego argumentu `Invoke` metody.

*TArg2*<br/>
Typ drugiego argumentu `Invoke` metody.

*TArg3*<br/>
Typ trzeciego argumentu `Invoke` metody.

*TArg4*<br/>
Typ czwartego argumentu `Invoke` metody.

*TArg5*<br/>
Typ piątego argumentu `Invoke` metody.

*TArg6*<br/>
Typ szóstego argumentu `Invoke` metody.

*TArg7*<br/>
Typ siódmego argumentu `Invoke` metody.

*TArg8*<br/>
Typ ósmego argumentu `Invoke` metody.

*TArg9*<br/>
Typ dziewiątego argumentu `Invoke` metody.

## <a name="remarks"></a>Uwagi

`ArgTraits` Struktury deklaruje określonego delegata interfejsu i funkcji anonimowej składowej, która ma określoną liczbę parametrów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa       | Opis
---------- | ----------------------
`Arg1Type` | Element typedef dla TArg1.
`Arg2Type` | Element typedef dla TArg2.
`Arg3Type` | Element typedef dla TArg3.
`Arg4Type` | Element typedef dla TArg4.
`Arg5Type` | Element typedef dla TArg5.
`Arg6Type` | Element typedef dla TArg6.
`Arg7Type` | Element typedef dla TArg7.
`Arg8Type` | Element typedef dla TArg8.
`Arg9Type` | Element typedef dla TArg9.

### <a name="public-constants"></a>Publiczne stałe

Nazwa                     | Opis
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Śledzi liczbę parametrów `Invoke` metodę interfejsu delegata.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ArgTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="args"></a>ArgTraits::args

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Uwagi

Śledzi liczbę parametrów `Invoke` metodę interfejsu delegata. Gdy `args` jest równa -1, może wystąpić w przypadku niezgodności `Invoke` podpis metody.
