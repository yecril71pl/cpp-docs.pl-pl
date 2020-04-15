---
title: SimpleActivationFactory — Klasa
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370934"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory — Klasa

Zapewnia podstawowy mechanizm tworzenia środowiska wykonawczego systemu Windows lub klasycznej klasy podstawowej COM.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa podstawowa.

## <a name="remarks"></a>Uwagi

Klasa podstawowa musi zawierać konstruktora domyślnego.

Poniższy przykład kodu pokazuje, jak używać SimpleActivationFactory z macro [ActivatableClassWithFactoryEx.](activatableclass-macros.md)

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, metoda](#activateinstance)|Tworzy wystąpienie określonego interfejsu.|
|[SimpleActivationFactory::GetRuntimeClassName, metoda](#getruntimeclassname)|Pobiera nazwę klasy runtime wystąpienia klasy określonej przez parametr szablonu klasy *podstawowej.*|
|[SimpleActivationFactory::GetTrustLevel, metoda](#gettrustlevel)|Pobiera poziom zaufania wystąpienia klasy określonej przez parametr szablonu klasy *podstawowej.*|

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

`SimpleActivationFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>SimpleActivationFactory::Metoda aktywacji instance

Tworzy wystąpienie określonego interfejsu.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parametry

*ppvObiekt*<br/>
Po zakończeniu tej operacji wskaźnik do wystąpienia obiektu `Base` określonego przez parametr szablonu klasy.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowany, jeśli klasa podstawowa określona w parametrze szablonu klasy nie pochodzi z [runtimeclass](runtimeclass-class.md)lub nie jest skonfigurowana z wartością wyliczania WinRt lub WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>SimpleActivationFactory::Metoda GetRuntimeClassName

Pobiera nazwę klasy runtime wystąpienia klasy określone `Base` przez parametr szablonu klasy.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parametry

*nazwa środowiska wykonawczego*<br/>
Po zakończeniu tej operacji nazwa klasy środowiska wykonawczego.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowany, `Base` jeśli klasa określona przez parametr szablonu klasy nie pochodzi z [runtimeclass](runtimeclass-class.md)lub nie jest skonfigurowany z winrt lub WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>SimpleActivationFactory::Metoda GetTrustLevel

Pobiera poziom zaufania wystąpienia klasy określone przez `Base` parametr szablonu klasy.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parametry

*trustLvl (włask zaufanie)*<br/>
Po zakończeniu tej operacji poziom zaufania bieżącego obiektu klasy.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.
