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
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371316"
---
# <a name="module-class"></a>Module — Klasa

Reprezentuje kolekcję powiązanych obiektów.

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

*typ modułu*<br/>
Kombinacja co najmniej jednej wartości wyliczenia [ModuleType.](moduletype-enumeration.md)

## <a name="members"></a>Elementy członkowskie

### <a name="protected-classes"></a>Klasy chronione

Nazwa                                                                                | Opis
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Moduł::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Wywołuje program obsługi zdarzeń, gdy ostatni obiekt w bieżącym module jest zwolniony. Program obsługi zdarzeń jest określony przez lambda, functor lub wskaźnik do funkcji.
[Moduł::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Wywołuje program obsługi zdarzeń, gdy ostatni obiekt w bieżącym module jest zwolniony. Program obsługi zdarzeń jest określony przez obiekt i jego element członkowski pointer-to-a-method.
[Moduł::ReleaseNotifier](module-releasenotifier-class.md)               | Wywołuje program obsługi zdarzeń po zwolnieniu ostatniego obiektu w module.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | -----------------------------------------------------------
[Moduł::~Moduł](#tilde-module) | Deinitializes bieżące wystąpienie `Module` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                      | Opis
------------------------- | ---------------------------------------------------
[Moduł::Moduł](#module) | Inicjuje nowe wystąpienie klasy `Module`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Moduł::Utwórz](#create)                               | Tworzy wystąpienie modułu.
[Moduł::DekrówoblicznikObjectCount](#decrementobjectcount)   | Zmniejsza liczbę obiektów śledzonych przez moduł.
[Moduł::GetActivationFactory](#getactivationfactory)   | Pobiera fabrykę aktywacji dla modułu.
[Moduł::GetClassObject](#getclassobject)               | Pobiera pamięć podręczną fabryk klas.
[Moduł::GetModule](#getmodule)                         | Tworzy wystąpienie modułu.
[Moduł::GetObjectCount](#getobjectcount)               | Pobiera liczbę obiektów zarządzanych przez ten moduł.
[Moduł::IncrementObjectCount](#incrementobjectcount)   | Zwiększa liczbę obiektów śledzonych przez moduł.
[Moduł::RegisterCOMObject](#registercomobject)         | Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą się z nimi łączyć.
[Moduł::Zarejestrujobiekty](#registerobjects)             | Rejestruje obiekty COM lub Windows Runtime, aby inne aplikacje mogły się z nimi łączyć.
[Moduł::Zarejestruj sięObtoktwinrt](#registerwinrtobject)     | Rejestruje jeden lub więcej obiektów środowiska wykonawczego systemu Windows, aby inne aplikacje mogły się z nimi łączyć.
[Moduł::Zakończ](#terminate)                         | Powoduje, że wszystkie fabryki tworzone przez moduł, aby zamknąć.
[Moduł::Likwidujaż wyrejestrowy](#unregistercomobject)     | Wyrejestrowaj jeden lub więcej obiektów COM, co uniemożliwia innym aplikacjom łączenie się z nimi.
[Moduł::Wyrejestrowanieobiektów](#unregisterobjects)         | Wyrejestrowanie obiektów w określonym module, tak aby inne aplikacje nie mogły się z nimi połączyć.
[Moduł::Wyrejestrowanieobektwinrt](#unregisterwinrtobject) | Wyrejestrowanie jednego lub więcej obiektów środowiska wykonawczego systemu Windows, tak aby inne aplikacje nie mogły się z nimi połączyć.

### <a name="protected-methods"></a>Metody chronione

Nazwa                      | Opis
------------------------- | --------------------------------
[Moduł::Utwórz](#create) | Tworzy wystąpienie modułu.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                                         | Opis
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Moduł::objectCount_](#objectcount)         | Śledzi, ile klas zostało utworzonych za pomocą funkcji [Make.](make-function.md)
[Moduł::releaseNotifier_](#releasenotifier) | Przechowuje wskaźnik `ReleaseNotifier` do obiektu.

### <a name="macros"></a>Makra

Nazwa                                                                   | Opis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Klasa aktywacji](activatableclass-macros.md)              | Wypełnia wewnętrzna pamięć podręczna zawierająca fabrykę, która może utworzyć wystąpienie określonej klasy. To makro określa domyślne parametry ustawień fabrycznych i identyfikatorów grupy.
[ActivatableClassWithFactory](activatableclass-macros.md)   | Wypełnia wewnętrzna pamięć podręczna zawierająca fabrykę, która może utworzyć wystąpienie określonej klasy. To makro umożliwia określenie określonego parametru fabrycznego.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Wypełnia wewnętrzna pamięć podręczna zawierająca fabrykę, która może utworzyć wystąpienie określonej klasy. To makro umożliwia określenie określonych parametrów fabrycznych i identyfikatorów grupy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>Moduł::~Moduł

Deinitializes bieżące wystąpienie `Module` klasy.

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>Moduł::Utwórz

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

*Wywołania zwrotnego*<br/>
Wywoływane po zwolnieniu obiektu ostatniego wystąpienia modułu.

*obiekt*<br/>
Parametry *obiektu* i *metody* są używane w połączeniu. Wskazuje obiekt ostatniego wystąpienia po zwolnieniu obiektu ostatniego wystąpienia w module.

*Metoda*<br/>
Parametry *obiektu* i *metody* są używane w połączeniu. Wskazuje metodę obiektu ostatniego wystąpienia po zwolnieniu obiektu ostatniego wystąpienia w module.

### <a name="return-value"></a>Wartość zwracana

Odniesienie do modułu.

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>Moduł::DekrówoblicznikObjectCount

Zmniejsza liczbę obiektów śledzonych przez moduł.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją dekrementacji.

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>Moduł::GetActivationFactory

Pobiera fabrykę aktywacji dla modułu.

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*pActivatibleClassId (Liczba nieaktywna klasy.*<br/>
Identyfikator klasy środowiska uruchomieniowego.

*PpIFactory (PpIFactory)*<br/>
IActivationFactory dla określonej klasy środowiska uruchomieniowego.

*Nazwa_serwera*<br/>
Nazwa podzbioru fabryk klas w bieżącym module. Określ nazwę serwera używaną w makrze [ActivatableClassWithFactoryEx](activatableclass-macros.md) lub określ, `nullptr` aby uzyskać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT zwrócony przez GetActivationFactory.

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>Moduł::GetClassObject

Retreives pamięci podręcznej fabryk klas.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Identyfikator klasy.

*Riid*<br/>
Identyfikator interfejsu, którego potrzebujesz.

*Ppv*<br/>
Wskaźnik do zwróconego obiektu.

*Nazwa_serwera*<br/>
Nazwa serwera określona w `ActivatableClassWithFactory`makra `ActivatableClassWithFactoryEx`, `ActivatableClass` lub makra; lub `nullptr` aby uzyskać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko dla środowiska COM, a nie środowiska wykonawczego systemu Windows. Ta metoda udostępnia `IClassFactory` tylko metody.

## <a name="modulegetmodule"></a><a name="getmodule"></a>Moduł::GetModule

Tworzy wystąpienie modułu.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>Moduł::GetObjectCount

Pobiera liczbę obiektów zarządzanych przez ten moduł.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba obiektów zarządzanych przez ten moduł.

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>Moduł::IncrementObjectCount

Zwiększa liczbę obiektów śledzonych przez moduł.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją przyrostu.

## <a name="modulemodule"></a><a name="module"></a>Moduł::Moduł

Inicjuje nowe wystąpienie klasy `Module`.

```cpp
Module();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor jest chroniony i `new` nie można wywołać za pomocą słowa kluczowego. Zamiast tego wywołaj [moduł::GetModule](#getmodule) lub [moduł::Create](#create).

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>Moduł::objectCount_

Śledzi, ile klas zostało utworzonych za pomocą funkcji [Make.](make-function.md)

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>Moduł::RegisterCOMObject

Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą się z nimi łączyć.

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>Parametry

*Nazwa_serwera*<br/>
W pełni kwalifikowana nazwa serwera.

*Clsid*<br/>
Tablica identyfikatorów CLSID do zarejestrowania.

*Fabryk*<br/>
Tablica interfejsów IUnknown obiektów klasy, których dostępność jest publikowana.

*Pliki cookie*<br/>
Po zakończeniu operacji tablica wskaźników do wartości, które identyfikują obiekty klasy, które zostały zarejestrowane. Te wartości są później używane odwołać rejestrację.

*Liczba*<br/>
Liczba identyfikatorów CLSID do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK jeśli successfu; w przeciwnym razie HRESULT, takich jak CO_E_OBJISREG, który wskazuje przyczynę operacji nie powiodło się.

### <a name="remarks"></a>Uwagi

Obiekty COM są rejestrowane w CLSCTX_LOCAL_SERVER wyliczeniu wyliczenia CLSCTX.

Typ połączenia z zarejestrowanymi obiektami jest określony przez kombinację bieżącego parametru szablonu *comflag* i REGCLS_SUSPENDED wyliczenia wyliczenia REGCLS.

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>Moduł::Zarejestrujobiekty

Rejestruje obiekty COM lub Windows Runtime, aby inne aplikacje mogły się z nimi łączyć.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Moduł*<br/>
Tablica obiektów COM lub Windows Runtime.

*Nazwa_serwera*<br/>
Nazwa serwera, który utworzył obiekty.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje przyczynę operacji nie powiodło się.

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>Moduł::Zarejestruj sięObtoktwinrt

Rejestruje jeden lub więcej obiektów środowiska wykonawczego systemu Windows, aby inne aplikacje mogły się z nimi łączyć.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parametry

*Nazwa_serwera*<br/>
Nazwa określająca podzbiór obiektów, których dotyczy ta operacja.

*activatableClassIds*<br/>
Tablica aktywowanych identyfikatorów CLSID do zarejestrowania.

*Cookie*<br/>
Wartość identyfikujący obiekty klasy, które zostały zarejestrowane. Ta wartość jest używana później do odwołania rejestracji.

*Liczba*<br/>
Liczba obiektów do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie błąd HRESULT, taki jak CO_E_OBJISREG, który wskazuje przyczynę niepowodzenia operacji.

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>Moduł::releaseNotifier_

Przechowuje wskaźnik `ReleaseNotifier` do obiektu.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>Moduł::Zakończ

Powoduje, że wszystkie fabryki tworzone przez moduł, aby zamknąć.

```cpp
void Terminate();
```

### <a name="remarks"></a>Uwagi

Zwalnia fabryki w pamięci podręcznej.

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>Moduł::Likwidujaż wyrejestrowy

Wyrejestrowaj jeden lub więcej obiektów COM, co uniemożliwia innym aplikacjom łączenie się z nimi.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*Nazwa_serwera*<br/>
(Nieużywane)

*Pliki cookie*<br/>
Tablica wskaźników do wartości, które identyfikują obiekty klasy do wyrejestrowania. Tablica została utworzona przez [RegisterCOMObject](#registercomobject) metody.

*Liczba*<br/>
Liczba klas do wyrejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta operacja zakończy się pomyślnie; w przeciwnym razie błąd HRESULT, który wskazuje przyczynę operacji nie powiodło się.

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>Moduł::Wyrejestrowanieobiektów

Wyrejestrowanie obiektów w określonym module, tak aby inne aplikacje nie mogły się z nimi połączyć.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Moduł*<br/>
Wskaźnik do modułu.

*Nazwa_serwera*<br/>
Kwalifikująca się nazwa określająca podzbiór obiektów, których dotyczy ta operacja.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli ta operacja zakończy się pomyślnie; w przeciwnym razie błąd HRESULT, który wskazuje przyczynę tej operacji nie powiodło się.

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>Moduł::Wyrejestrowanieobektwinrt

Wyrejestrowanie jednego lub więcej obiektów środowiska wykonawczego systemu Windows, tak aby inne aplikacje nie mogły się z nimi połączyć.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*Cookie*<br/>
Wskaźnik do wartości, która identyfikuje obiekt klasy, którego rejestracja ma zostać odwołana.
