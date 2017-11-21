---
title: Klasa CAtlDllModuleT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c178cb10c6f14d257e9c03b499ea8f2fa01eddf4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catldllmodulet-class"></a>Klasa CAtlDllModuleT
Ta klasa reprezentuje modułu dla biblioteki DLL.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodne `CAtlDllModuleT`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Konstruktor.|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testy, jeśli biblioteka DLL może być usunięty z pamięci.|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Zwraca fabrykę klas.|  
|[CAtlDllModuleT::DllMain](#dllmain)|Punkt wejścia opcjonalne do biblioteki dołączanej (dynamicznie DLL).|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Dodaje wpisy do rejestru systemowego dla obiektów w bibliotece DLL.|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Usuwa wpisy rejestru systemowego dla obiektów w bibliotece DLL.|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Zwraca fabrykę klas. Wywoływane przez [metody DllGetClassObject](#dllgetclassobject).|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlDllModuleT`reprezentuje moduł dla biblioteki dołączanej (dynamicznie DLL) i udostępnia funkcje używane przez wszystkie projekty biblioteki DLL. To specjalizacja [CAtlModuleT](../../atl/reference/catlmodulet-class.md) klasa obejmuje obsługę rejestracji.  
  
 Aby uzyskać więcej informacji o modułach w ATL, zobacz [klasy modułów ALT](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT  
 Konstruktor.  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT  
 Destruktor.  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow  
 Testy, jeśli biblioteka DLL może być usunięty z pamięci.  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli biblioteka DLL może być zwolniony lub wartości S_FALSE, jeśli nie jest.  
  
##  <a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject  
 Zwraca fabrykę klas.  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 Identyfikator CLSID obiektu do utworzenia.  
  
 `riid`  
 Uzyskanie identyfikatora IID żądanego interfejsu.  
  
 `ppv`  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppv` jest równa NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="dllmain"></a>CAtlDllModuleT::DllMain  
 Punkt wejścia opcjonalne do biblioteki dołączanej (dynamicznie DLL).  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwReason`  
 Jeśli ustawiono DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH i DLL_THREAD_DETACH wywołania powiadomienia są wyłączone.  
  
 *lpReserved*  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca wartość PRAWDA.  
  
### <a name="remarks"></a>Uwagi  
 Wyłączenie DLL_THREAD_ATTACH i powiadomień DLL_THREAD_DETACH wywołania mogą być przydatne optymalizacji dla aplikacji wielowątkowych, które mają wiele bibliotek DLL, który często tworzenie i usuwanie wątków i którego biblioteki DLL nie muszą tych wątku poziom powiadomienia o Załącznik/oderwania.  
  
##  <a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer  
 Dodaje wpisy do rejestru systemowego dla obiektów w bibliotece DLL.  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany. Wartość domyślna to TRUE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer  
 Usuwa wpisy rejestru systemowego dla obiektów w bibliotece DLL.  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać usunięta z rejestru. Wartość domyślna to TRUE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="getclassobject"></a>CAtlDllModuleT::GetClassObject  
 Tworzy obiekt CLSID określony.  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 Identyfikator CLSID obiektu do utworzenia.  
  
 `riid`  
 Uzyskanie identyfikatora IID żądanego interfejsu.  
  
 `ppv`  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppv` jest równa NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) i jest on dołączony do zgodności z poprzednimi wersjami.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
 [Klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
