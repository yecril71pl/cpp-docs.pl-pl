---
title: ClassFactory — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: bbf20e2269e6d62206e06e748174d7b88898cd68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198102"
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
Interfejs zerowego.

*Elementem I1*<br/>
Pierwszy interfejs.

*I2*<br/>
Drugi interfejs.

## <a name="remarks"></a>Uwagi

Użyj `ClassFactory` , aby zapewnić implementację fabryki zdefiniowanej przez użytkownika.

Poniższy wzorzec programowania ilustruje sposób użycia struktury [Implements](implements-structure.md) do określenia więcej niż trzech interfejsów w fabryce klasy.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                        | Opis
------------------------------------------- | -----------
[ClassFactory:: ClassFactory](#classfactory) |

### <a name="public-methods"></a>Metody publiczne

Nazwa                                            | Opis
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory:: AddRef](#addref)                 | Zwiększa liczbę odwołań dla bieżącego `ClassFactory` obiektu.
[ClassFactory:: LockServer —](#lockserver)         | Zwiększa lub zmniejsza liczbę obiektów bazowych, które są śledzone przez bieżący `ClassFactory` obiekt.
[ClassFactory:: QueryInterface](#queryinterface) | Pobiera wskaźnik do interfejsu określonego przez parametr.
[ClassFactory:: Release](#release)               | Zmniejsza liczbę odwołań dla bieżącego `ClassFactory` obiektu.

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

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory:: AddRef

Zwiększa liczbę odwołań dla bieżącego `ClassFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT, która opisuje awarię.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory:: ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory:: LockServer —

Zwiększa lub zmniejsza liczbę obiektów bazowych, które są śledzone przez bieżący `ClassFactory` obiekt.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Zarodowych*<br/>
**`true`** Aby zwiększyć liczbę śledzonych obiektów. **`false`** zmniejszenie liczby śledzonych obiektów.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie E_FAIL.

### <a name="remarks"></a>Uwagi

`ClassFactory`śledzi obiekty w podstawowym wystąpieniu klasy [modułu](module-class.md) .

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory:: QueryInterface

Pobiera wskaźnik do interfejsu określonego przez parametr.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identyfikator interfejsu.

*ppvObject*<br/>
Po zakończeniu tej operacji wskaźnik do interfejsu określony przez parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT, która opisuje awarię.

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory:: Release

Zmniejsza liczbę odwołań dla bieżącego `ClassFactory` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT, która opisuje awarię.
