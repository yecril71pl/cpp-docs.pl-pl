---
title: ActivationFactory — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368704"
---
# <a name="activationfactory-class"></a>ActivationFactory — Klasa

Włącza jedną lub więcej klas, które mają być aktywowane przez środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Interfejs zerowy.

*I1*<br/>
Pierwszy interfejs.

*I2*<br/>
Drugi interfejs.

## <a name="remarks"></a>Uwagi

`ActivationFactory`zapewnia metody rejestracji i podstawowe `IActivationFactory` funkcje interfejsu. `ActivationFactory`umożliwia również zapewnienie niestandardowej implementacji fabrycznej.

Poniższy fragment kodu symbolicznie ilustruje sposób korzystania z ActivationFactory.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Poniższy fragment kodu pokazuje, jak używać [Implements](implements-structure.md) struktury, aby określić więcej niż trzy identyfikatory interfejsu.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                       | Opis
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Inicjuje `ActivationFactory` klasę.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                           | Opis
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Zwiększa liczbę odwołań bieżącego `ActivationFactory` obiektu.
[ActivationFactory::GetIids](#getiids)                         | Pobiera tablicę zaimplementowanych identyfikatorów interfejsu.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Pobiera nazwę klasy środowiska wykonawczego obiektu, `ActivationFactory` który jest wystąpienia bieżącego.
[ActivationFactory::GetTrustPoziom](#gettrustlevel)             | Pobiera poziom zaufania obiektu, który `ActivationFactory` jest tworzone w bieżącym.
[ActivationFactory::QueryInterface](#queryinterface)           | Pobiera wskaźnik do określonego interfejsu.
[ActivationFactory::Release](#release)                         | Zmniejsza liczbę odwołań bieżącego `ActivationFactory` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>ActivationFactory::ActivationFactory

Inicjuje `ActivationFactory` klasę.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>ActivationFactory::AddRef

Zwiększa liczbę odwołań bieżącego `ActivationFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd.

## <a name="activationfactorygetiids"></a><a name="getiids"></a>ActivationFactory::GetIids

Pobiera tablicę zaimplementowanych identyfikatorów interfejsu.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount (licz) iidCount*<br/>
Po zakończeniu tej operacji liczba identyfikatorów wstawionych w *tablicy iids.*

*iids*<br/>
Po zakończeniu tej operacji tablica zaimplementowanych identyfikatorów interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd. E_OUTOFMEMORY jest możliwa awaria HRESULT.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Pobiera nazwę klasy środowiska wykonawczego obiektu, `ActivationFactory` który jest wystąpienia bieżącego.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parametry

*nazwa środowiska wykonawczego*<br/>
Po zakończeniu tej operacji dojście do ciągu zawierającego nazwę klasy runtime obiektu, który powoduje wystąpienia bieżącego. `ActivationFactory`

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>ActivationFactory::GetTrustPoziom

Pobiera poziom zaufania obiektu, który `ActivationFactory` jest tworzone w bieżącym.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parametry

*trustLvl (włask zaufanie)*<br/>
Po zakończeniu tej operacji poziom zaufania klasy środowiska `ActivationFactory` wykonawczego, który wystąpienia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie błąd potwierdzenia jest emitowany, `FullTrust`a *trustLvl* jest ustawiony na .

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>ActivationFactory::QueryInterface

Pobiera wskaźnik do określonego interfejsu.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*ppvObiekt*<br/>
Po zakończeniu tej operacji wskaźnik do interfejsu określony przez parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd.

## <a name="activationfactoryrelease"></a><a name="release"></a>ActivationFactory::Release

Zmniejsza liczbę odwołań bieżącego `ActivationFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który opisuje błąd.
