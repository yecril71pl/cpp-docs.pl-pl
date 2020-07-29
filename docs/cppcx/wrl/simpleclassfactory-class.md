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
ms.openlocfilehash: 66794789e51a2635fae646cca49e4fae8385dfe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211154"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory — Klasa

Zapewnia podstawowy mechanizm tworzenia klasy bazowej.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*Opiera*<br/>
Klasa bazowa.

## <a name="remarks"></a>Uwagi

Klasa bazowa musi udostępniać Konstruktor domyślny.

Poniższy przykład kodu demonstruje sposób użycia `SimpleClassFactory` z makrem [ActivatableClassWithFactoryEx](activatableclass-macros.md) .

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

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory:: CreateInstance — Metoda

Tworzy wystąpienie określonego interfejsu.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
Musi być **`nullptr`** ; w przeciwnym razie wartość zwracana jest CLASS_E_NOAGGREGATION.

SimpleClassFactory nie obsługuje agregacji. Jeśli agregacja była obsługiwana, a tworzony obiekt był częścią agregacji, *pUnkOuter* byłby wskaźnikiem do interfejsu sterującego `IUnknown` agregacji.

*riid*<br/>
Identyfikator interfejsu obiektu do utworzenia.

*ppvObject*<br/>
Po zakończeniu tej operacji wskaźnik do wystąpienia obiektu określonego przez parametr *riid* .

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowany, jeśli klasa bazowa określona w parametrze szablonu klasy nie pochodzi od [RuntimeClass](runtimeclass-class.md)lub nie została skonfigurowana przy użyciu wartości wyliczenia ClassicCom lub WinRtClassicComMix [RuntimeClassType —](runtimeclasstype-enumeration.md) .
