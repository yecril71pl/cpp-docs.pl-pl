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
ms.openlocfilehash: 8e5132f4a8711f6420cd9b52751550a96d10d8fc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787518"
---
# <a name="activationfactory-class"></a>ActivationFactory — Klasa

Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.

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
Interfejsu zerowego.

*I1*<br/>
Pierwszy interfejs.

*I2*<br/>
Drugi interfejs.

## <a name="remarks"></a>Uwagi

`ActivationFactory` udostępnia metody rejestracji i podstawowe funkcje dla `IActivationFactory` interfejsu. `ActivationFactory` Umożliwia także udostępnić implementację fabrycznej.

Poniższy fragment kodu ilustruje symbolicznie sposób użycia activationfactory —.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Poniższy fragment kodu przedstawia sposób użycia [implementuje](implements-structure.md) struktury, aby określić więcej niż trzy identyfikatory interfejsu.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                       | Opis
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Inicjuje `ActivationFactory` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                           | Opis
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Zwiększa liczbę odwołań bieżącego `ActivationFactory` obiektu.
[ActivationFactory::GetIids](#getiids)                         | Pobiera tablicę zaimplementowanego interfejsu identyfikatorów.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Pobiera nazwę klasy środowiska uruchomieniowego, obiektu, który bieżącego `ActivationFactory` tworzy wystąpienie.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Pobiera poziom zaufania, obiektu, który bieżącego `ActivationFactory` tworzy wystąpienie.
[ActivationFactory::QueryInterface](#queryinterface)           | Pobiera wskaźnik do określonego interfejsu.
[ActivationFactory::Release](#release)                         | Dekrementuje liczbę odwołań bieżącego `ActivationFactory` obiektu.

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

**Namespace:** Microsoft::WRL

## <a name="activationfactory"></a>ActivationFactory::ActivationFactory

Inicjuje `ActivationFactory` klasy.

```cpp
ActivationFactory();
```

## <a name="addref"></a>ActivationFactory::AddRef

Zwiększa liczbę odwołań bieżącego `ActivationFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="getiids"></a>ActivationFactory::GetIids

Pobiera tablicę zaimplementowanego interfejsu identyfikatorów.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Po zakończeniu tej operacji, liczba identyfikatorów interfejsu w *IID* tablicy.

*IID*<br/>
Po zakończeniu tej operacji, tablicę implementowane identyfikatorów interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. E_OUTOFMEMORY jest możliwe błąd HRESULT.

## <a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Pobiera nazwę klasy środowiska uruchomieniowego, obiektu, który bieżącego `ActivationFactory` tworzy wystąpienie.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po zakończeniu tej operacji, dojścia do ciągu, który zawiera nazwę klasy środowiska uruchomieniowego obiektu, bieżący `ActivationFactory` tworzy wystąpienie.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Pobiera poziom zaufania, obiektu, który bieżącego `ActivationFactory` tworzy wystąpienie.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Po zakończeniu tej operacji, poziom zaufania środowiska uruchomieniowego klasy `ActivationFactory` tworzy wystąpienie.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie jest emitowane Błąd asercji i *trustLvl* ustawiono `FullTrust`.

## <a name="queryinterface"></a>ActivationFactory::QueryInterface

Pobiera wskaźnik do określonego interfejsu.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*ppvObject*<br/>
Po zakończeniu tej operacji, wskaźnik do interfejsu, określony przez parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="release"></a>ActivationFactory::Release

Dekrementuje liczbę odwołań bieżącego `ActivationFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.
