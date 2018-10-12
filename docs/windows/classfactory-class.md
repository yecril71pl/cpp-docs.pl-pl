---
title: ClassFactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4facba4a35e28818f22ba17f6d835b781cd76061
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163273"
---
# <a name="classfactory-class"></a>ClassFactory — Klasa

Implementuje podstawowe funkcje `IClassFactory` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
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

Korzystanie z `ClassFactory` do implementacji fabryki zdefiniowanych przez użytkownika.

Następujący wzorzec programowania pokazuje sposób użycia [implementuje](../windows/implements-structure.md) struktury, aby określić więcej niż trzy interfejsy na fabrykę klas.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                        | Opis
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>Metody publiczne

Nazwa                                            | Opis
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Zwiększa liczbę odwołań dla bieżącego `ClassFactory` obiektu.
[ClassFactory::LockServer](#lockserver)         | Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżącą `ClassFactory` obiektu.
[ClassFactory::QueryInterface](#queryinterface) | Pobiera wskaźnik do interfejsu, określony przez parametr.
[ClassFactory::Release](#release)               | Dekrementuje liczbę odwołań dla bieżącego `ClassFactory` obiektu.

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

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="addref"></a>ClassFactory::AddRef

Zwiększa liczbę odwołań dla bieżącego `ClassFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

## <a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="lockserver"></a>ClassFactory::LockServer

Zwiększa lub zmniejsza liczbę podstawowych obiektów, które są śledzone przez bieżącą `ClassFactory` obiektu.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stada*<br/>
**wartość true,** się zwiększać liczbę śledzonych obiektów. **FALSE** zmniejszyć liczbę obiektów śledzonych.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_FAIL.

### <a name="remarks"></a>Uwagi

`ClassFactory` przechowuje informacje o obiektów w wystąpieniu bazowego [modułu](../windows/module-class.md) klasy.

## <a name="queryinterface"></a>ClassFactory::QueryInterface

Pobiera wskaźnik do interfejsu, określony przez parametr.

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

## <a name="release"></a>ClassFactory::Release

Dekrementuje liczbę odwołań dla bieżącego `ClassFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.
