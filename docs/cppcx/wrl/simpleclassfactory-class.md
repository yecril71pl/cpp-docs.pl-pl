---
title: SimpleClassFactory — Klasa
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373547"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory — Klasa

Zapewnia podstawowy mechanizm do tworzenia klasy podstawowej.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*Podstawowej*<br/>
Klasa podstawowa.

## <a name="remarks"></a>Uwagi

Klasa podstawowa musi zawierać konstruktora domyślnego.

Poniższy przykład kodu pokazuje, `SimpleClassFactory` jak używać z [macro ActivatableClassWithFactoryEx.](activatableclass-macros.md)

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance, metoda](#createinstance)|Tworzy wystąpienie określonego interfejsu.|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory::Metoda tworzenia instance

Tworzy wystąpienie określonego interfejsu.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter (Nieunikat.*<br/>
Musi `nullptr`być ; w przeciwnym razie zwracana jest wartość CLASS_E_NOAGGREGATION.

SimpleClassFactory nie obsługuje agregacji. Jeśli agregacja były obsługiwane i obiekt tworzony był częścią agregacji, *pUnkOuter* będzie wskaźnik do interfejsu sterującego `IUnknown` agregacji.

*Riid*<br/>
Identyfikator interfejsu obiektu do utworzenia.

*ppvObiekt*<br/>
Po zakończeniu tej operacji wskaźnik do wystąpienia obiektu określonego przez *riid* parametru.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowany, jeśli klasa podstawowa określona w parametrze szablonu klasy nie pochodzi z [runtimeclass](runtimeclass-class.md)lub nie jest skonfigurowana z wartością wyliczania ClassicCom lub WinRtClassicComMix [RuntimeClassType.](runtimeclasstype-enumeration.md)
