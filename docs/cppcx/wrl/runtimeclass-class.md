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
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376235"
---
# <a name="runtimeclass-class"></a>RuntimeClass — Klasa

Reprezentuje klasę WinRT lub COM, która dziedziczy określone interfejsy i zapewnia określoną obsługę środowiska wykonawczego systemu Windows, klasyczną wersję COM i słabe wsparcie referencyjne.

Ta klasa zapewnia standardową implementację klas WinRT i `QueryInterface`COM, `Release` zapewniając implementację , `AddRef`itp., zarządza liczbą odwołań modułu i obsługuje dostarczanie fabryki klas dla obiektów aktywowanych.

## <a name="syntax"></a>Składnia

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parametry

*lagi klasy*<br/>
Parametr opcjonalny. Kombinacja co najmniej jednej wartości [wyliczenia RuntimeClassType.](runtimeclasstype-enumeration.md) Makro `__WRL_CONFIGURATION_LEGACY__` można zdefiniować, aby zmienić domyślną wartość classFlags dla wszystkich klas środowiska uruchomieniowego w projekcie. Jeśli zdefiniowane, RuntimeClass wystąpień są domyślnie nieaskładne. Jeśli nie jest zdefiniowany, RuntimeClass wystąpień są elastyczne domyślnie. Aby uniknąć niejednoznaczności, należy `Microsoft::WRL::FtmBase` `TInterfaces` zawsze `RuntimeClassType::InhibitFtmBase`określić w lub . Uwaga: jeśli InhibitFtmBase i FtmBase są używane, obiekt będzie elastyczny.

*TInterfaces (Wszczegieńce)*<br/>
Lista interfejsów implementuje obiekt `IUnknown`poza `IInspectable` , lub innych interfejsów kontrolowanych przez [RuntimeClassType](runtimeclasstype-enumeration.md). Może również wymienić inne klasy, które `Microsoft::WRL::FtmBase` mają być uzyskane z, w `IMarshal`szczególności, aby obiekt zwinny i spowodować jego wdrożenie .

## <a name="members"></a>Elementy członkowskie

`RuntimeClassInitialize`<br/>
Funkcja, która inicjuje `MakeAndInitialize` obiekt, jeśli funkcja szablonu jest używana do konstruowania obiektu. Zwraca S_OK, jeśli obiekt został pomyślnie zainicjowany, lub kod błędu COM, jeśli inicjowanie nie powiodło się. Kod błędu COM jest propagowany jako `MakeAndInitialize`wartość zwracana . Należy zauważyć, że `RuntimeClassInitialize` metoda `Make` nie jest wywoływana, jeśli funkcja szablonu jest używana do konstruowania obiektu.

### <a name="public-constructors"></a>Konstruktory publiczne

| Nazwa                                               | Opis                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [Klasa wykonywania::Klasa środowiska wykonawczego](#runtimeclass)        | Inicjuje bieżące `RuntimeClass` wystąpienie klasy.   |
| [Klasa wykonywania::~Klasa środowiska wykonawczego](#tilde-runtimeclass) | Deinitializes bieżące wystąpienie `RuntimeClass` klasy. |

### <a name="public-methods"></a>Metody publiczne

| Nazwa                                                      | Opis                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Klasa środowiska wykonawczego::AddRef](#addref)                           | Zwiększa liczbę odwołań dla `RuntimeClass` bieżącego obiektu.                              |
| [Klasa wykonywania::Dekrówreferacji](#decrementreference)   | Zmniejsza liczbę odwołań dla `RuntimeClass` bieżącego obiektu.                              |
| [Klasa wykonywania::GetIids](#getiids)                         | Pobiera tablicy, która może zawierać identyfikatory interfejsu `RuntimeClass` zaimplementowane przez bieżący obiekt. |
| [Klasa wykonywania::GetRuntimeClassName](#getruntimeclassname) | Pobiera nazwę klasy środowiska wykonawczego `RuntimeClass` bieżącego obiektu.                                  |
| [Klasa środowiska uruchomieniowego::GetTrustLevel](#gettrustlevel)             | Pobiera poziom zaufania bieżącego `RuntimeClass` obiektu.                                         |
| [Klasa środowiska wykonawczego::GetWeakReference](#getweakreference)       | Pobiera wskaźnik do obiektu słabe odniesienia `RuntimeClass` dla bieżącego obiektu.                 |
| [Klasa środowiska wykonawczego::InternalAddRef](#internaladdref)           | Zwiększa liczbę odwołań do `RuntimeClass` bieżącego obiektu.                               |
| [Klasa środowiska wykonawczego::QueryInterface](#queryinterface)           | Pobiera wskaźnik do określonego identyfikatora interfejsu.                                                 |
| [Klasa runtimeclass::Release](#release)                         | Wykonuje operację wydania COM na `RuntimeClass` bieżącym obiekcie.                             |

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

Jest to szczegół implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>Klasa wykonywania::~Klasa środowiska wykonawczego

Deinitializes bieżące wystąpienie `RuntimeClass` klasy.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>Klasa środowiska wykonawczego::AddRef

Zwiększa liczbę odwołań dla `RuntimeClass` bieżącego obiektu.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>Klasa wykonywania::Dekrówreferacji

Zmniejsza liczbę odwołań dla `RuntimeClass` bieżącego obiektu.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>Klasa wykonywania::GetIids

Pobiera tablicy, która może zawierać identyfikatory interfejsu `RuntimeClass` zaimplementowane przez bieżący obiekt.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parametry

*iidCount (licz) iidCount*<br/>
Po zakończeniu tej operacji całkowita liczba elementów w *identyfikatorach tablicowych*.

*iids*<br/>
Po zakończeniu tej operacji wskaźnik do tablicy identyfikatorów interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>Klasa wykonywania::GetRuntimeClassName

Pobiera nazwę klasy środowiska wykonawczego `RuntimeClass` bieżącego obiektu.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*nazwa środowiska wykonawczego*<br/>
Po zakończeniu tej operacji nazwa klasy środowiska wykonawczego.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowany, jeśli `__WRL_STRICT__` lub `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nie jest zdefiniowany.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>Klasa środowiska uruchomieniowego::GetTrustLevel

Pobiera poziom zaufania bieżącego `RuntimeClass` obiektu.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parametry

*trustLvl (włask zaufanie)*<br/>
Po zakończeniu tej operacji poziom zaufania `RuntimeClass` bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

### <a name="remarks"></a>Uwagi

Błąd potwierdzenia jest emitowany, jeśli `__WRL_STRICT__` lub `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nie jest zdefiniowany.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>Klasa środowiska wykonawczego::GetWeakReference

Pobiera wskaźnik do obiektu słabe odniesienia `RuntimeClass` dla bieżącego obiektu.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parametry

*Weakreference*<br/>
Po zakończeniu tej operacji wskaźnik do obiektu słabe odniesienia.

### <a name="return-value"></a>Wartość zwracana

Zawsze S_OK.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>Klasa środowiska wykonawczego::InternalAddRef

Zwiększa liczbę odwołań do `RuntimeClass` bieżącego obiektu.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowe liczby odwołań.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>Klasa środowiska wykonawczego::QueryInterface

Pobiera wskaźnik do określonego identyfikatora interfejsu.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parametry

*Riid*<br/>
Identyfikator interfejsu.

*ppvObiekt*<br/>
Po zakończeniu tej opereation, wskaźnik do interfejsu określonego przez *riid* parametru.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="runtimeclassrelease"></a><a name="release"></a>Klasa runtimeclass::Release

Wykonuje operację wydania COM na `RuntimeClass` bieżącym obiekcie.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Jeśli liczba odwołań staje `RuntimeClass` się równa zero, obiekt zostanie usunięty.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>Klasa wykonywania::Klasa środowiska wykonawczego

Inicjuje bieżące `RuntimeClass` wystąpienie klasy.

```cpp
RuntimeClass();
```
