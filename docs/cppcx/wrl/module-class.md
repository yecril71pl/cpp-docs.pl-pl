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
ms.openlocfilehash: db3eb123382ac70f6198d094c5eb3fe44d3bbcd9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787391"
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
Kombinacji jednego lub więcej [ModuleType](moduletype-enumeration.md) wartości wyliczenia.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-classes"></a>Klasy chronionych

Nazwa                                                                                | Opis
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.
[Module::MethodReleaseNotifier](module-methodreleasenotifier-class.md)   | Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                             | Opis
-------------------------------- | -----------------------------------------------------------
[Module:: ~ Module](#tilde-module) | Deinicjuje bieżące wystąpienie `Module` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                      | Opis
------------------------- | ---------------------------------------------------
[Module::module](#module) | Inicjuje nowe wystąpienie klasy `Module` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::Create](#create)                               | Tworzy wystąpienie modułu.
[Module::DecrementObjectCount](#decrementobjectcount)   | Zmniejsza liczbę obiektów śledzonych przez moduł.
[Module::GetActivationFactory](#getactivationfactory)   | Pobiera fabrykę aktywacji dla modułu.
[Module::GetClassObject](#getclassobject)               | Pobiera pamięć podręczną fabryki klas.
[Module::GetModule](#getmodule)                         | Tworzy wystąpienie modułu.
[Module::GetObjectCount](#getobjectcount)               | Pobiera liczbę obiektów zarządzanych przez ten moduł.
[Module::IncrementObjectCount](#incrementobjectcount)   | Zwiększa liczbę obiektów śledzonych przez moduł.
[Module::RegisterCOMObject](#registercomobject)         | Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą łączyć się z nimi.
[Module::RegisterObjects](#registerobjects)             | Rejestruje obiekty COM lub środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.
[Module::RegisterWinRTObject](#registerwinrtobject)     | Rejestruje co najmniej jeden obiekt środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.
[Module::terminate](#terminate)                         | Powoduje, że wszystkie fabryki tworzone przez moduł, aby zamknąć.
[Module::UnregisterCOMObject](#unregistercomobject)     | Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innych aplikacji na połączenie z nich.
[Module::UnregisterObjects](#unregisterobjects)         | Wyrejestrowuje obiektów w określonym module, tak aby inne aplikacje nie mogą nawiązać z nimi.
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego Windows, tak aby inne aplikacje nie mogą nawiązać z nimi.

### <a name="protected-methods"></a>Metody chronione

Nazwa                      | Opis
------------------------- | --------------------------------
[Module::Create](#create) | Tworzy wystąpienie modułu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                         | Opis
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectCount_](#objectcount)         | Przechowuje informacje o ile klasy zostały utworzone przy użyciu [wprowadzić](make-function.md) funkcji.
[Module::releaseNotifier_](#releasenotifier) | Przechowuje wskaźnik do `ReleaseNotifier` obiektu.

### <a name="macros"></a>Makra

Nazwa | Opis elementu------| --- [ActivatableClass](activatableclass-macros.md) |  Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro określa domyślne parametry identyfikator fabryki i grupy.
[ActivatableClassWithFactory](activatableclass-macros.md) | Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro, można określić parametru określonego fabryki.
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro umożliwia określenie konkretnego fabryki i parametry Identyfikatora grupy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="tilde-module"></a>Module:: ~ Module

Deinicjuje bieżące wystąpienie `Module` klasy.

```cpp
virtual ~Module();
```

## <a name="create"></a>Module::Create

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

*callback*<br/>
Wywołuje się, gdy ostatni obiekt wystąpienia modułu jest zwalniany.

*object*<br/>
*Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje ostatni obiekt wystąpienia po udostępnieniu ostatni obiekt wystąpienia w module.

*— Metoda*<br/>
*Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje metodę ostatniego wystąpienia obiektu po udostępnieniu ostatni obiekt wystąpienia w module.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="decrementobjectcount"></a>Module::DecrementObjectCount

Zmniejsza liczbę obiektów śledzonych przez moduł.

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed wykonaniem operacji dekrementacji.

## <a name="getactivationfactory"></a>Module::GetActivationFactory

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
IID klasy środowiska uruchomieniowego.

*ppIFactory*<br/>
IActivationFactory dla klasy określonego środowiska uruchomieniowego.

*serverName*<br/>
Nazwa podzbiór fabryki klas w bieżącego modułu. Określ nazwę serwera, używane w [ActivatableClassWithFactoryEx](activatableclass-macros.md) makro, lub określ `nullptr` można pobrać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wynik HRESULT zwracane przez getactivationfactory —.

## <a name="getclassobject"></a>Module::GetClassObject

Retreives pamięci podręcznej fabryki klas.

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator klasy.

*Parametr riid*<br/>
Identyfikator interfejsu, który w przypadku żądania.

*ppv*<br/>
Wskaźnik zwracany obiekt.

*serverName*<br/>
Nazwa serwera, który jest określony w jednej `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, lub `ActivatableClass` — makro; lub `nullptr` można pobrać domyślną nazwę serwera.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Użyj tej metody tylko dla modelu COM, nie środowiska wykonawczego Windows. Ta metoda ujawnia tylko `IClassFactory` metody.

## <a name="getmodule"></a>Module::GetModule

Tworzy wystąpienie modułu.

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="getobjectcount"></a>Module::GetObjectCount

Pobiera liczbę obiektów zarządzanych przez ten moduł.

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca liczba obiektów zarządzanych przez ten moduł.

## <a name="incrementobjectcount"></a>Module::IncrementObjectCount

Zwiększa liczbę obiektów śledzonych przez moduł.

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed wykonaniem operacji przyrostu.

## <a name="module"></a>Module::module

Inicjuje nowe wystąpienie klasy `Module` klasy.

```cpp
Module();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor jest chroniona i nie może zostać wywołany z `new` — słowo kluczowe. Zamiast tego należy wywołać albo [Module::GetModule](#getmodule) lub [Module::Create](#create).

## <a name="objectcount"></a>Module::objectCount_

Przechowuje informacje o ile klasy zostały utworzone przy użyciu [wprowadzić](make-function.md) funkcji.

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module::RegisterCOMObject

Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą łączyć się z nimi.

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
W pełni kwalifikowaną nazwę serwera.

*clsids*<br/>
Tablica CLSID do zarejestrowania.

*fabryki*<br/>
Tablica interfejsów IUnknown typów obiektów klas, których udostępnienie jest on publikowany.

*cookies*<br/>
Po zakończeniu operacji, tablicę wskaźników do wartości, które identyfikują klasy obiektów, które zostały zarejestrowane. Wartości te są później używane odwołać rejestracji.

*Liczba*<br/>
Liczba CLSID do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK Jeśli okaż; w przeciwnym razie wartość HRESULT takich jak CO_E_OBJISREG, która wskazuje przyczynę operacja nie powiodła się.

### <a name="remarks"></a>Uwagi

Obiekty COM są zarejestrowane w usłudze modułu wyliczającego CLSCTX_LOCAL_SERVER CLSCTX wyliczenia.

Typ połączenia, aby zarejestrowane obiekty jest określony przy użyciu kombinacji bieżącego *comflag* parametrem szablonu i moduł wyliczający REGCLS_SUSPENDED REGCLS wyliczenia.

## <a name="registerobjects"></a>Module::RegisterObjects

Rejestruje obiekty COM lub środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*module*<br/>
Tablica obiektów COM i środowiska wykonawczego Windows.

*serverName*<br/>
Nazwa serwera, na którym są tworzone obiekty.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się.

## <a name="registerwinrtobject"></a>Module::RegisterWinRTObject

Rejestruje co najmniej jeden obiekt środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
Nazwa, która określa podzbiór obiektów wpływ tej operacji.

*activatableClassIds*<br/>
Tablica aktywowalnej CLSID do zarejestrowania.

*cookie*<br/>
Wartość, która identyfikuje obiektów klas, które zostały zarejestrowane. Ta wartość jest używana później, aby można było odwołać rejestracji.

*Liczba*<br/>
Liczba obiektów do zarejestrowania.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, takich jak CO_E_OBJISREG, która wskazuje przyczynę operacja nie powiodła się.

## <a name="releasenotifier"></a>Module::releaseNotifier_

Przechowuje wskaźnik do `ReleaseNotifier` obiektu.

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module::terminate

Powoduje, że wszystkie fabryki tworzone przez moduł, aby zamknąć.

```cpp
void Terminate();
```

### <a name="remarks"></a>Uwagi

Zwalnia fabryk w pamięci podręcznej.

## <a name="unregistercomobject"></a>Module::UnregisterCOMObject

Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innych aplikacji na połączenie z nich.

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*serverName*<br/>
(Nieużywane)

*cookies*<br/>
Tablica wskaźników do wartości, które identyfikują obiektów klasy do wyrejestrowania. Tablica został utworzony przez [registercomobject —](#registercomobject) metody.

*Liczba*<br/>
Liczba klasy, aby wyrejestrować.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę operacja nie powiodła się.

## <a name="unregisterobjects"></a>Module::UnregisterObjects

Wyrejestrowuje obiektów w określonym module, tak aby inne aplikacje nie mogą nawiązać z nimi.

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*module*<br/>
Wskaźnik do modułu.

*serverName*<br/>
Kwalifikującym się nazwa, która określa podzbiór obiektów wpływ tej operacji.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę tej operacji nie powiodło się.

## <a name="unregisterwinrtobject"></a>Module::UnregisterWinRTObject

Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego Windows, tak aby inne aplikacje nie mogą nawiązać z nimi.

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>Parametry

*cookie*<br/>
Wskaźnik do wartość, która identyfikuje obiekt klasy, którego rejestracja ma zostać odwołane.
