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
ms.openlocfilehash: 1831a816d0967c2ca53f941128639ea368c1b727
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787548"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory — Klasa

Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parametry

*Base*<br/>
Klasa bazowa.

## <a name="remarks"></a>Uwagi

Klasa bazowa musi dostarczać domyślnego konstruktora.

Poniższy przykład kodu demonstruje sposób używania simpleactivationfactory — za pomocą [ActivatableClassWithFactoryEx](activatableclass-macros.md) makra.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance, metoda](#activateinstance)|Tworzy wystąpienie określonego interfejsu.|
|[SimpleActivationFactory::GetRuntimeClassName, metoda](#getruntimeclassname)|Pobiera nazwę klasy środowiska uruchomieniowego wystąpienia klasy określonej przez *Base* parametru szablonu klasy.|
|[SimpleActivationFactory::GetTrustLevel, metoda](#gettrustlevel)|Pobiera poziom zaufania wystąpienia klasy określonej przez *Base* parametru szablonu klasy.|

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

**Namespace:** Microsoft::WRL

## <a name="activateinstance"></a>SimpleActivationFactory::ActivateInstance, metoda

Tworzy wystąpienie określonego interfejsu.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parametry

*ppvObject*<br/>
Po zakończeniu tej operacji, wskaźnik do wystąpienia obiektu określonego przez `Base` parametru szablonu klasy.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowane, jeśli nie jest pochodną klasy bazowej, określona w parametrze szablonu klasy [RuntimeClass](runtimeclass-class.md), lub nie jest skonfigurowany z WinRt lub WinRtClassicComMix [ RuntimeClassType](runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="getruntimeclassname"></a>SimpleActivationFactory::GetRuntimeClassName, metoda

Pobiera nazwę klasy środowiska uruchomieniowego wystąpienia klasy określonej przez `Base` parametru szablonu klasy.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po zakończeniu tej operacji, nazwa klasy środowiska uruchomieniowego.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowane, jeśli klasa określona przez `Base` parametru szablonu klasy nie jest pochodną [RuntimeClass](runtimeclass-class.md), lub nie jest skonfigurowany z WinRt lub WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="gettrustlevel"></a>SimpleActivationFactory::GetTrustLevel, metoda

Pobiera poziom zaufania wystąpienia klasy określonej przez `Base` parametru szablonu klasy.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Gdy ta operacja zostanie ukończone, poziom zaufania bieżącego obiektu klasy.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.
