---
title: Invokehelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24abb55c0754b9dc5b5300ca6cd50079f003717a
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808371"
---
# <a name="invokehelper-structure"></a>InvokeHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*TCallback*<br/>
Typ funkcji procedury obsługi zdarzeń.

*argCount*<br/>
Liczba argumentów w `InvokeHelper` specjalizacji.

## <a name="remarks"></a>Uwagi

Udostępnia implementację `Invoke()` metody na podstawie określonej liczby i typów argumentów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa     | Opis
-------- | -----------------------------------------------------------------------------
`Traits` | Synonim dla klasy, która definiuje typ każdego argumentu procedury obsługi zdarzeń.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                        | Opis
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Inicjuje nowe wystąpienie klasy `InvokeHelper` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                            | Opis
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | Wywołuje program obsługi zdarzeń, którego podpis zawiera określoną liczbę argumentów.

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                                 | Opis
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Reprezentuje program obsługi zdarzeń do wywołania po wystąpieniu zdarzenia.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InvokeHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="callback"></a>InvokeHelper::callback_

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Uwagi

Reprezentuje program obsługi zdarzeń do wywołania po wystąpieniu zdarzenia.

`TCallback` Parametr szablonu określa typ programu obsługi zdarzeń.

## <a name="invoke"></a>InvokeHelper::Invoke

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*arg1*<br/>
Argument 1.

*argument2*<br/>
Argument 2.

*arg3*<br/>
Argument 3.

*Arg4*<br/>
Argument 4.

*arg5*<br/>
Argument 5.

*arg6*<br/>
Argument 6.

*arg7*<br/>
Argument 7.

*arg8*<br/>
Argument 8.

*arg9*<br/>
Argument 9.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Wywołuje program obsługi zdarzeń, którego podpis zawiera określoną liczbę argumentów.

## <a name="invokehelper"></a>InvokeHelper::InvokeHelper

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parametry

*Wywołanie zwrotne*<br/>
Program obsługi zdarzeń.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `InvokeHelper` klasy.

`TCallback` Parametr szablonu określa typ programu obsługi zdarzeń.
