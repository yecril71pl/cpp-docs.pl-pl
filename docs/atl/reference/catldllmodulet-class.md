---
title: Klasa CAtlDllModuleT
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
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319012"
---
# <a name="catldllmodulet-class"></a>Klasa CAtlDllModuleT

Ta klasa reprezentuje moduł dla biblioteki DLL.

## <a name="syntax"></a>Składnia

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa pochodzi `CAtlDllModuleT`od .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor.|
|[CAtlDllModuleT::~CAtlDllModuleT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Sprawdza, czy biblioteka DLL może zostać zwolniona.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Zwraca fabrykę klas.|
|[CAtlDllModuleT::DllMain](#dllmain)|Opcjonalny punkt wejścia do biblioteki łączy dynamicznych (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Dodaje wpisy do rejestru systemowego dla obiektów w dll.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Usuwa wpisy w rejestrze systemowym dla obiektów w dll.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Zwraca fabrykę klas. Wywoływany przez [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Uwagi

`CAtlDllModuleT`reprezentuje moduł biblioteki łączy dynamicznych (DLL) i udostępnia funkcje używane przez wszystkie projekty biblioteki DLL. Ta specjalizacja [CAtlModuleT](../../atl/reference/catlmodulet-class.md) klasy obejmuje obsługę rejestracji.

Aby uzyskać więcej informacji na temat modułów w ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT

Konstruktor.

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT::~CAtlDllModuleT

Destruktor.

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow

Sprawdza, czy biblioteka DLL może zostać zwolniona.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli biblioteka DLL może zostać zwolniona lub S_FALSE, jeśli nie może.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject

Zwraca fabrykę klas.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid ( rclsid )*<br/>
Identyfikator CLSID obiektu, który ma zostać utworzony.

*Riid*<br/>
Identyfikator żądanego interfejsu.

*Ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppv* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

Opcjonalny punkt wejścia do biblioteki łączy dynamicznych (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*dwReason (właśc.*<br/>
Jeśli ustawiona jest DLL_PROCESS_ATTACH, połączenia powiadomień DLL_THREAD_ATTACH i DLL_THREAD_DETACH są wyłączone.

*lpReserved (niesłuszne)*<br/>
Zarezerwowany.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Wyłączenie DLL_THREAD_ATTACH i DLL_THREAD_DETACH wywołania powiadomień może być użyteczną optymalizacją dla aplikacji wielowątkowych, które mają wiele bibliotek DLL, które często tworzą i usuwają wątki i których biblioteki DLL nie potrzebują tych powiadomień na poziomie wątku załącznik/odłączenie.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer

Dodaje wpisy do rejestru systemowego dla obiektów w dll.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma być zarejestrowana. Wartością domyślną jest PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer

Usuwa wpisy w rejestrze systemowym dla obiektów w dll.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
PRAWDA, jeśli biblioteka typów ma zostać usunięta z rejestru. Wartością domyślną jest PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject

Tworzy obiekt określonego identyfikatora CLSID.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid ( rclsid )*<br/>
Identyfikator CLSID obiektu, który ma zostać utworzony.

*Riid*<br/>
Identyfikator żądanego interfejsu.

*Ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppv* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) i jest uwzględniona dla zgodności z powrotem.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)<br/>
[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasy modułów](../../atl/atl-module-classes.md)
