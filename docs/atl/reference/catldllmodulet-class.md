---
title: CAtlDllModuleT Class
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247103"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT Class

Ta klasa reprezentuje modułu dla biblioteki DLL.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa jest pochodną `CAtlDllModuleT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor.|
|[CAtlDllModuleT::~CAtlDllModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Sprawdza, czy można zwolnić bibliotekę DLL.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Zwraca fabrykę klas.|
|[CAtlDllModuleT::DllMain](#dllmain)|Punkt wejścia opcjonalne do biblioteki dołączanej (dynamicznie DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Dodaje wpisy do rejestru systemowego dla obiektów w bibliotece DLL.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Usuwa wpisy w rejestrze systemowym dla obiektów w bibliotece DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Zwraca fabrykę klas. Wywoływane przez [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Uwagi

`CAtlDllModuleT` reprezentuje moduł dla biblioteki dołączanej (dynamicznie DLL) i dostarcza funkcje używane przez wszystkie projekty biblioteki DLL. Ta specjalizacja [CAtlModuleT](../../atl/reference/catlmodulet-class.md) klasy obejmuje obsługę rejestracji.

Aby uzyskać więcej informacji na temat modułów ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT

Konstruktor.

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>  CAtlDllModuleT::~CAtlDllModuleT

Destruktor.

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow

Sprawdza, czy można zwolnić bibliotekę DLL.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli biblioteka DLL może być zwolniony, lub wartość S_FALSE, jeśli jest ona nieosiągalna.

##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject

Zwraca fabrykę klas.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*<br/>
Identyfikator IID żądanego interfejsu.

*ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain

Punkt wejścia opcjonalne do biblioteki dołączanej (dynamicznie DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*dwReason*<br/>
Jeśli ustawienie DLL_PROCESS_ATTACH DLL_THREAD_ATTACH i DLL_THREAD_DETACH wywołania powiadomienia są wyłączone.

*lpReserved*<br/>
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Wyłączanie DLL_THREAD_ATTACH i DLL_THREAD_DETACH powiadomienie o wywołania mogą być przydatne optymalizacji dla aplikacji wielowątkowych, które mają wiele bibliotek DLL, który często tworzyć i usuwać wątków i niepotrzebne te powiadomienia na poziomie wątku, z których bibliotek DLL Odłączenie/załącznika.

##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer

Dodaje wpisy do rejestru systemowego dla obiektów w bibliotece DLL.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer

Usuwa wpisy w rejestrze systemowym dla obiektów w bibliotece DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów zostanie usunięta z rejestru. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject

Tworzy obiekt z określonym identyfikatorem CLSID.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*<br/>
Identyfikator IID żądanego interfejsu.

*ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) i jest włączone dla zachowania zgodności z poprzednimi wersjami.

## <a name="see-also"></a>Zobacz także

[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
