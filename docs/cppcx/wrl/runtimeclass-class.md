---
title: RuntimeClass — Klasa
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: d45fe7c6d794f216da93ffbd95dbb7058d3336f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403194"
---
# <a name="runtimeclass-class"></a>RuntimeClass — Klasa

Reprezentuje klasę WinRT lub COM, który dziedziczy określonych interfejsów i zapewnia określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.

Ta klasa dostarcza implementację standardowy klasy WinRT i COM, zapewniając wykonania `QueryInterface`, `AddRef`, `Release` itp., zarządza licznika odwołań modułu i obsługuje dostarczanie fabryki klas dla obiekty, którą można aktywować.

## <a name="syntax"></a>Składnia

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parametry

*classFlags*<br/>
Parametr opcjonalny. Kombinacji jednego lub więcej [RuntimeClassType](runtimeclasstype-enumeration.md) wartości wyliczenia. `__WRL_CONFIGURATION_LEGACY__` Makr można zdefiniować, aby zmienić domyślną wartość classFlags dla wszystkich klas środowiska uruchomieniowego w projekcie. Jeśli zdefiniowane, RuntimeClass wystąpienia są inne niż agile domyślnie. Jeśli nie zostanie zdefiniowana, RuntimeClass wystąpienia są elastyczne domyślnie. Aby uniknąć niejednoznaczności należy zawsze określić `Microsoft::WRL::FtmBase` w `TInterfaces` lub `RuntimeClassType::InhibitFtmBase`. Uwaga: Jeżeli InhibitFtmBase i FtmBase jest używany zarówno obiekt będzie agile.

*TInterfaces*<br/>
Na liście interfejsów obiekt implementuje poza `IUnknown`, `IInspectable` lub innych interfejsów w wartości clientauthtrustmode [RuntimeClassType](runtimeclasstype-enumeration.md). Również może go wyświetlać innych klas pochodzących z, szczególnie `Microsoft::WRL::FtmBase` na obiekt agile i spowodować, tak aby implementował `IMarshal`.

## <a name="members"></a>Elementy członkowskie

`RuntimeClassInitialize`<br/>
Funkcja, która inicjuje obiekt, jeśli `MakeAndInitialize` funkcji szablonu jest używana do konstruowania obiektu. Zwraca S_OK, jeśli obiekt został pomyślnie zainicjowany lub kod błędu modelu COM, jeśli inicjowanie nie powiodło się. Kod błędu modelu COM są propagowane jako wartość zwracaną `MakeAndInitialize`. Należy pamiętać, że `RuntimeClassInitialize` metoda nie jest wywoływana, jeśli `Make` funkcji szablonu jest używana do konstruowania obiektu.

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                                               | Opis                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Inicjuje bieżące wystąpienie `RuntimeClass` klasy.   |
| [RuntimeClass::~RuntimeClass](#tilde-runtimeclass) | Deinicjuje bieżące wystąpienie `RuntimeClass` klasy. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                                      | Opis                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Zwiększa liczbę odwołań dla bieżącego `RuntimeClass` obiektu.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Dekrementuje liczbę odwołań dla bieżącego `RuntimeClass` obiektu.                              |
| [RuntimeClass::GetIids](#getiids)                         | Pobiera tablicę, która może zawierać interfejsu identyfikatory implementowane przez bieżącą `RuntimeClass` obiektu. |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Pobiera nazwę klasy środowiska uruchomieniowego bieżącego `RuntimeClass` obiektu.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Pobiera bieżący poziom zaufania `RuntimeClass` obiektu.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Pobiera wskaźnik do obiektu słabe odwołanie dla bieżącego `RuntimeClass` obiektu.                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Zwiększa liczbę odwołań do bieżącego `RuntimeClass` obiektu.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Pobiera wskaźnik do określonego interfejsu.                                                 |
| [RuntimeClass::Release](#release)                         | Wykonuje operację wydania COM na bieżącym `RuntimeClass` obiektu.                             |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

Jest to szczegół implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="tilde-runtimeclass"></a>RuntimeClass::~RuntimeClass

Deinicjuje bieżące wystąpienie `RuntimeClass` klasy.

```cpp
virtual ~RuntimeClass();
```

## <a name="addref"></a>RuntimeClass::AddRef

Zwiększa liczbę odwołań dla bieżącego `RuntimeClass` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="decrementreference"></a>RuntimeClass::DecrementReference

Dekrementuje liczbę odwołań dla bieżącego `RuntimeClass` obiektu.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="getiids"></a>RuntimeClass::GetIids

Pobiera tablicę, która może zawierać interfejsu identyfikatory implementowane przez bieżącą `RuntimeClass` obiektu.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount*<br/>
Po zakończeniu tej operacji, całkowita liczba elementów w tablicy *IID*.

*IID*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do tablicy identyfikatorów interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_OUTOFMEMORY.

## <a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Pobiera nazwę klasy środowiska uruchomieniowego bieżącego `RuntimeClass` obiektu.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*<br/>
Po zakończeniu tej operacji, nazwa klasy środowiska uruchomieniowego.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli `__WRL_STRICT__` lub `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nie jest zdefiniowany.

## <a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Pobiera bieżący poziom zaufania `RuntimeClass` obiektu.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl*<br/>
Po zakończeniu tej operacji, bieżący poziom zaufania `RuntimeClass` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

### <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowane, jeśli `__WRL_STRICT__` lub `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nie jest zdefiniowany.

## <a name="getweakreference"></a>RuntimeClass::GetWeakReference

Pobiera wskaźnik do obiektu słabe odwołanie dla bieżącego `RuntimeClass` obiektu.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parametry

*weakReference*<br/>
Gdy ta operacja zostanie ukończone, wskaźnik do obiektu słabe odwołanie.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

## <a name="internaladdref"></a>RuntimeClass::InternalAddRef

Zwiększa liczbę odwołań do bieżącego `RuntimeClass` obiektu.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowa liczba odwołań.

## <a name="queryinterface"></a>RuntimeClass::QueryInterface

Pobiera wskaźnik do określonego interfejsu.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
Identyfikator interfejsu.

*ppvObject*<br/>
Po zakończeniu tego opereation, wskaźnik do interfejsu, określonego przez *riid* parametru.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="release"></a>RuntimeClass::Release

Wykonuje operację wydania COM na bieżącym `RuntimeClass` obiektu.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli licznik odwołań staje się zerem, `RuntimeClass` obiekt zostanie usunięty.

## <a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Inicjuje bieżące wystąpienie `RuntimeClass` klasy.

```cpp
RuntimeClass();
```
