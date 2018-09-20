---
title: Simpleclassfactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/7/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a3e262567927b818072c1e05acd18aa64cbaa6c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446520"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory — Klasa

Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.

## <a name="syntax"></a>Składnia

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parametry

*podstawowy*<br/>
Klasa bazowa.

## <a name="remarks"></a>Uwagi

Klasa bazowa musi dostarczać domyślnego konstruktora.

Poniższy przykład kodu demonstruje sposób używania `SimpleClassFactory` z [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra.

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

**Namespace:** Microsoft::WRL

## <a name="createinstance"></a>SimpleClassFactory::CreateInstance, metoda

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
Musi być `nullptr`; w przeciwnym razie wartość zwracana jest CLASS_E_NOAGGREGATION.

Simpleclassfactory — nie obsługuje agregację. Jeśli agregacji były obsługiwane i tworzony obiekt było częścią agregacji, *pUnkOuter* będzie wskaźnik do kontrolowania `IUnknown` interfejsu agregacji.

*Parametr riid*<br/>
Identyfikator obiektu do utworzenia interfejsu.

*ppvObject*<br/>
Po zakończeniu tej operacji, wskaźnik do wystąpienia obiektu określonego przez *riid* parametru.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli `__WRL_STRICT__` jest zdefiniowany, błąd potwierdzenia jest emitowane, jeśli nie jest pochodną klasy bazowej, określona w parametrze szablonu klasy [RuntimeClass](../windows/runtimeclass-class.md), lub nie jest skonfigurowany z ClassicCom lub WinRtClassicComMix [ RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.
