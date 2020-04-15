---
title: InvokeHelper — Struktura
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371385"
---
# <a name="invokehelper-structure"></a>InvokeHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Typ interfejsu delegata.

*TCallback (Powrót do systemu)*<br/>
Typ funkcji obsługi zdarzeń.

*argCount (ArgCount)*<br/>
Liczba argumentów w `InvokeHelper` specjalizacji.

## <a name="remarks"></a>Uwagi

Zapewnia implementację `Invoke()` metody na podstawie określonej liczby i typu argumentów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa     | Opis
-------- | -----------------------------------------------------------------------------
`Traits` | Synonim dla klasy, która definiuje typ każdego argumentu obsługi zdarzeń.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                        | Opis
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Inicjuje nowe wystąpienie klasy `InvokeHelper`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                            | Opis
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Wywołaj](#invoke) | Wywołuje program obsługi zdarzeń, którego podpis zawiera określoną liczbę argumentów.

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                                 | Opis
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Reprezentuje program obsługi zdarzeń do wywołania, gdy wystąpi zdarzenie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InvokeHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="invokehelpercallback_"></a><a name="callback"></a>InvokeHelper::callback_

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Uwagi

Reprezentuje program obsługi zdarzeń do wywołania, gdy wystąpi zdarzenie.

Parametr `TCallback` szablonu określa typ programu obsługi zdarzeń.

## <a name="invokehelperinvoke"></a><a name="invoke"></a>InvokeHelper::Wywołaj

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>Parametry

*argument1*<br/>
Argument 1.

*argument 2*<br/>
Argument 2.

*arg3 ( arg3 )*<br/>
Argument 3.

*arg4 ( arg4 )*<br/>
Argument 4.

*argument 5*<br/>
Argument 5.

*arg6 (arg6)*<br/>
Argument 6.

*argument 7*<br/>
Argument 7.

*arg8 (8)*<br/>
Argument 8.

*argument 9*<br/>
Argument 9.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie hresult, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Wywołuje program obsługi zdarzeń, którego podpis zawiera określoną liczbę argumentów.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>InvokeHelper::InvokeHelper

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parametry

*Wywołania zwrotnego*<br/>
Program obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `InvokeHelper`.

Parametr `TCallback` szablonu określa typ programu obsługi zdarzeń.
