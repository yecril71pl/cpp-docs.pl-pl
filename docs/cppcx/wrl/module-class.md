---
title: Module — Klasa
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: f7930247c979c111a7f4798e35ebe7aa95209f37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225751"
---
# <a name="module-class"></a>Module — Klasa

Reprezentuje kolekcję obiektów pokrewnych.

## <a name="syntax"></a>Składnia

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parametry

*moduleType*<br/>
Kombinacja co najmniej jednej wartości wyliczenia [ModuleType](moduletype-enumeration.md) .

## <a name="members"></a>Elementy członkowskie

### <a name="protected-classes"></a>Chronione klasy

Nazwa                                                                                | Opis
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module:: GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w bieżącym module. Procedura obsługi zdarzeń jest określana na podstawie wyrażenia lambda, Funktor lub wskaźnika do funkcji.
[Module:: MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w bieżącym module. Program obsługi zdarzeń jest określany przez obiekt i jego element członkowski typu wskaźnik-a-metoda.
[Module:: ReleaseNotifier](module-releasenotifier-class.md)               | Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w module.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | -----------------------------------------------------------
[Module:: ~ — moduł](#tilde-module) | Deinicjalizuje bieżące wystąpienie `Module` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                      | Opis
------------------------- | ---------------------------------------------------
[Module:: module](#module) | Inicjuje nowe wystąpienie klasy `Module`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module:: Create](#create)                               | Tworzy wystąpienie modułu.
[Moduł::D ecrementObjectCount](#decrementobjectcount)   | Zmniejsza liczbę obiektów śledzonych przez moduł.
[Module:: GetActivationFactory —](#getactivationfactory)   | Pobiera fabrykę aktywacji dla modułu.
[Module:: GetClassObject](#getclassobject)               | Pobiera pamięć podręczną fabryk klas.
[Module:: GetModule](#getmodule)                         | Tworzy wystąpienie modułu.
[Module:: Getobjectcount —](#getobjectcount)               | Pobiera liczbę obiektów zarządzanych przez ten moduł.
[Module:: IncrementObjectCount —](#incrementobjectcount)   | Zwiększa liczbę obiektów śledzonych przez moduł.
[Module:: Registercomobject —](#registercomobject)         | Rejestruje jeden lub więcej obiektów COM, tak aby inne aplikacje mogły się z nimi łączyć.
[Module:: Registerobjects —](#registerobjects)             | Rejestruje obiekty COM lub środowisko wykonawcze systemu Windows, aby inne aplikacje mogły się z nimi łączyć.
[Module:: Registerwinrtobject —](#registerwinrtobject)     | Rejestruje jeden lub więcej obiektów środowisko wykonawcze systemu Windows, tak aby inne aplikacje mogły się z nimi łączyć.
[Module:: terminate](#terminate)                         | Powoduje zamknięcie wszystkich fabryk utworzonych przez moduł.
[Module:: Unregistercomobject —](#unregistercomobject)     | Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innym aplikacjom łączenie się z nimi.
[Module:: Unregisterobjects —](#unregisterobjects)         | Wyrejestrowuje obiekty w określonym module, dzięki czemu inne aplikacje nie mogą się z nimi łączyć.
[Module:: Unregisterwinrtobject —](#unregisterwinrtobject) | Wyrejestrowuje jeden lub więcej obiektów środowisko wykonawcze systemu Windows, tak aby inne aplikacje nie mógł się z nimi połączyć.

### <a name="protected-methods"></a>Metody chronione

Nazwa                      | Opis
------------------------- | --------------------------------
[Module:: Create](#create) | Tworzy wystąpienie modułu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                         | Opis
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module:: objectCount_](#objectcount)         | Śledzi liczbę klas, które zostały utworzone za pomocą funkcji [Make](make-function.md) .
[Module:: releaseNotifier_](#releasenotifier) | Przechowuje wskaźnik do `ReleaseNotifier` obiektu.

### <a name="macros"></a>Makra

Nazwa                                                                   | Opis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | Wypełnia wewnętrzną pamięć podręczną, która zawiera fabrykę, która może utworzyć wystąpienie określonej klasy. To makro określa domyślne parametry fabryki i identyfikatora grupy.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Wypełnia wewnętrzną pamięć podręczną, która zawiera fabrykę, która może utworzyć wystąpienie określonej klasy. To makro umożliwia określenie określonego parametru fabryki.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Wypełnia wewnętrzną pamięć podręczną, która zawiera fabrykę, która może utworzyć wystąpienie określonej klasy. To makro umożliwia określenie określonych parametrów fabryki i identyfikatora grupy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Module:: ~ — moduł

Deinicjalizuje bieżące wystąpienie `Module` klasy.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Module:: Create

Tworzy wystąpienie modułu.

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ modułu.

*wywołania zwrotnego*<br/>
Wywoływana, gdy jest wydano ostatni obiekt wystąpienia modułu.

*object*<br/>
Parametry *obiektu* i *metody* są używane w połączeniu. Wskazuje ostatni obiekt wystąpienia po wydaniu ostatniego obiektu wystąpienia w module.

*Method*<br/>
Parametry *obiektu* i *metody* są używane w połączeniu. Wskazuje metodę ostatniego wystąpienia obiektu, gdy jest on wydawany ostatni obiekt wystąpienia w module.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Moduł::D ecrementObjectCount

Zmniejsza liczbę obiektów śledzonych przez moduł.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją zmniejszania.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Module:: GetActivationFactory —

Pobiera fabrykę aktywacji dla modułu.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*pActivatibleClassId*<br/>
Identyfikator IID klasy środowiska uruchomieniowego.

*ppIFactory*<br/>
IActivationFactory dla określonej klasy środowiska uruchomieniowego.

*serverName*<br/>
Nazwa podzestawu fabryk klas w bieżącym module. Określ nazwę serwera używaną w makrze [ActivatableClassWithFactoryEx](activatableclass-macros.md) lub określ, **`nullptr`** Aby uzyskać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie HRESULT zwrócony przez GetActivationFactory —.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Module:: GetClassObject

Pobiera kolejki pamięć podręczną fabryk klas.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Identyfikator klasy.

*riid*<br/>
Identyfikator interfejsu, którego żądasz.

*ppv*<br/>
Wskaźnik do zwracanego obiektu.

*serverName*<br/>
Nazwa serwera określona w parametrze `ActivatableClassWithFactory` , `ActivatableClassWithFactoryEx` , lub, `ActivatableClass` lub **`nullptr`** Aby uzyskać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko dla modelu COM, a nie środowisko wykonawcze systemu Windows. Ta metoda ujawnia tylko `IClassFactory` metody.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Module:: GetModule

Tworzy wystąpienie modułu.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Module:: Getobjectcount —

Pobiera liczbę obiektów zarządzanych przez ten moduł.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba obiektów zarządzanych przez ten moduł.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Module:: IncrementObjectCount —

Zwiększa liczbę obiektów śledzonych przez moduł.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją przyrostu.

## <a name="modulemodule"></a><a name="module"></a>Module:: module

Inicjuje nowe wystąpienie klasy `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor jest chroniony i nie można go wywołać za pomocą **`new`** słowa kluczowego. Zamiast tego wywołaj dowolny [moduł:: GetModule](#getmodule) lub [module:: Create](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Module:: objectCount_

Śledzi liczbę klas, które zostały utworzone za pomocą funkcji [Make](make-function.md) .

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Module:: Registercomobject —

Rejestruje jeden lub więcej obiektów COM, tak aby inne aplikacje mogły się z nimi łączyć.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
W pełni kwalifikowana nazwa serwera.

*CLSID*<br/>
Tablica identyfikatorów CLSID do zarejestrowania.

*fabryki*<br/>
Tablica interfejsów IUnknown obiektów klasy, których dostępność jest publikowana.

*cookie*<br/>
Po zakończeniu operacji, tablica wskaźników do wartości, które identyfikują obiekty klasy, które zostały zarejestrowane. Te wartości są później używane do odwoływania rejestracji.

*liczbą*<br/>
Liczba identyfikatorów CLSID do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli okaż; w przeciwnym razie wynik HRESULT, taki jak CO_E_OBJISREG, wskazuje przyczynę niepowodzenia operacji.

### <a name="remarks"></a>Uwagi

Obiekty COM są rejestrowane za pomocą modułu wyliczającego CLSCTX_LOCAL_SERVER wyliczenia CLSCTX.

Typ połączenia z zarejestrowanymi obiektami jest określany przez kombinację bieżącego parametru szablonu *comflag* oraz modułu wyliczającego REGCLS_SUSPENDED wyliczenia REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Module:: Registerobjects —

Rejestruje obiekty COM lub środowisko wykonawcze systemu Windows, aby inne aplikacje mogły się z nimi łączyć.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*elementu*<br/>
Tablica obiektów COM lub środowisko wykonawcze systemu Windows.

*serverName*<br/>
Nazwa serwera, który utworzył obiekty.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wartość HRESULT wskazuje przyczynę niepowodzenia operacji.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Module:: Registerwinrtobject —

Rejestruje jeden lub więcej obiektów środowisko wykonawcze systemu Windows, tak aby inne aplikacje mogły się z nimi łączyć.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
Nazwa, która określa podzbiór obiektów, których dotyczy ta operacja.

*activatableClassIds*<br/>
Tablica identyfikatorów CLSID aktywowalnej do zarejestrowania.

*plików*<br/>
Wartość, która identyfikuje obiekty klasy, które zostały zarejestrowane. Ta wartość jest używana później do odwoływania rejestracji.

*liczbą*<br/>
Liczba obiektów do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie błąd HRESULT, taki jak CO_E_OBJISREG, który wskazuje przyczynę niepowodzenia operacji.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Module:: releaseNotifier_

Przechowuje wskaźnik do `ReleaseNotifier` obiektu.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Module:: terminate

Powoduje zamknięcie wszystkich fabryk utworzonych przez moduł.

```cpp
void Terminate();
```

### <a name="remarks"></a>Uwagi

Zwalnia fabryky w pamięci podręcznej.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Module:: Unregistercomobject —

Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innym aplikacjom łączenie się z nimi.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
Przestrzeń

*cookie*<br/>
Tablica wskaźników do wartości, które identyfikują obiekty klasy do wyrejestrowania. Tablica została utworzona przez metodę [registercomobject —](#registercomobject) .

*liczbą*<br/>
Liczba klas do wyrejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta operacja zakończyła się pomyślnie; w przeciwnym razie błąd HRESULT wskazujący przyczynę niepowodzenia operacji.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Module:: Unregisterobjects —

Wyrejestrowuje obiekty w określonym module, dzięki czemu inne aplikacje nie mogą się z nimi łączyć.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*elementu*<br/>
Wskaźnik do modułu.

*serverName*<br/>
Nazwa kwalifikująca, która określa podzbiór obiektów, których dotyczy ta operacja.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta operacja zakończyła się pomyślnie; w przeciwnym razie błąd HRESULT wskazujący przyczynę niepowodzenia tej operacji.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Module:: Unregisterwinrtobject —

Wyrejestrowuje jeden lub więcej obiektów środowisko wykonawcze systemu Windows, tak aby inne aplikacje nie mógł się z nimi połączyć.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*plików*<br/>
Wskaźnik do wartości, która identyfikuje obiekt klasy, którego Rejestracja ma zostać cofnięta.
