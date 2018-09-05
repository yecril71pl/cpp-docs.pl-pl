---
title: Klasa CAtlDllModuleT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec36cddae835d46c5db6245f85e4294aa52225e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766577"
---
# <a name="catldllmodulet-class"></a>Klasa CAtlDllModuleT

Ta klasa reprezentuje modułu dla biblioteki DLL.

## <a name="syntax"></a>Składnia

```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parametry

*T*  
Klasa jest pochodną `CAtlDllModuleT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor.|
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destruktor.|

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

##  <a name="dtor"></a>  CAtlDllModuleT:: ~ CAtlDllModuleT

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

*rclsid*  
Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*  
Identyfikator IID żądanego interfejsu.

*ppv*  
Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain

Punkt wejścia opcjonalne do biblioteki dołączanej (dynamicznie DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parametry

*dwReason*  
Jeśli ustawienie DLL_PROCESS_ATTACH DLL_THREAD_ATTACH i DLL_THREAD_DETACH wywołania powiadomienia są wyłączone.

*lpReserved*  
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

*bRegTypeLib*  
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer

Usuwa wpisy w rejestrze systemowym dla obiektów w bibliotece DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*  
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

*rclsid*  
Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*  
Identyfikator IID żądanego interfejsu.

*ppv*  
Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) i jest włączone dla zachowania zgodności z poprzednimi wersjami.

## <a name="see-also"></a>Zobacz też

[Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
[Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)   
[Klasy modułów](../../atl/atl-module-classes.md)
