---
title: Globalne funkcje rejestracji serwera | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs: C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f5cfffbcc47555ee8cff7cd6e18ea54b5524607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="server-registration-global-functions"></a>Funkcje globalne serwera rejestracji
Funkcje te zapewniają obsługę rejestrowania i wyrejestrowywania obiektów serwera w mapie obiektu.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Ta funkcja jest wywoływana, aby zarejestrować każdy obiekt na mapie obiektów.|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Ta funkcja jest wywoływana, aby wyrejestrować każdy obiekt na mapie obiektów.|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Ta funkcja jest wywoływana, aby zarejestrować obiekty klasy.|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Ta funkcja jest wywoływana, aby można było odwołać obiektów klasy z modułem COM.|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Ta funkcja jest wywoływana można pobrać obiektu klasy.|  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
   
##  <a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer  
 Ta funkcja jest wywoływana, aby zarejestrować każdy obiekt na mapie obiektów.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Wskaźnik do modułu COM.  
  
 `bRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL, wszystkie obiekty w mapie obiektu zostanie zarejestrowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `AtlComModuleRegisterServer`przeprowadzi mapy obiektu ATL wygenerowany automatycznie i rejestruje każdego obiektu w planie. Jeśli `pCLSID` nie jest równa NULL, a następnie obiekt odwołuje się `pCLSID` jest zarejestrowany; w przeciwnym razie wszystkie obiekty są rejestrowane.  
  
 Ta funkcja jest wywoływana [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).  
  
##  <a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer  
 Ta funkcja jest wywoływana, aby wyrejestrować każdy obiekt na mapie obiektów.  
  
```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Wskaźnik do modułu COM.  
  
 `bUnRegTypeLib`  
 Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Wszystkie obiekty w mapie obiektu zostanie wyrejestrowane, jeśli ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `AtlComModuleUnregisterServer`przeprowadzi mapy obiektu ATL i wyrejestrowuje każdego obiektu w planie. Jeśli `pCLSID` nie jest równa NULL, a następnie obiekt odwołuje się `pCLSID` jest niezarejestrowany; w przeciwnym razie są wszystkie obiekty wyrejestrowany.  
  
 Ta funkcja jest wywoływana [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).  
  
##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects  
 Ta funkcja jest wywoływana, aby zarejestrować obiekty klasy.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Wskaźnik do modułu COM.  
  
 `dwClsContext`  
 Określa kontekst, w którym ma być uruchomiona obiektu klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Zobacz [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) więcej szczegółów.  
  
 `dwFlags`  
 Określa typy połączeń z obiektem klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Zobacz [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) więcej szczegółów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika jest wykorzystywany przez [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (przestarzałe w wersji 7.0 ATL) i [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).  
  
##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 Ta funkcja jest wywoływana, aby usunąć fabrykę/fabryki klas z tabeli działających obiektów.  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Wskaźnik do modułu COM.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika jest wykorzystywany przez [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (przestarzałe w wersji 7.0 ATL) i [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).  
  
##  <a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject  
 Ta funkcja jest wywoływana, aby zwrócić fabrykę klasy.  
  
```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `pComModule`  
 Wskaźnik do modułu COM.  
  
 `rclsid`  
 Identyfikator CLSID obiektu do utworzenia.  
  
 `riid`  
 Uzyskanie identyfikatora IID żądanego interfejsu.  
  
 `ppv`  
 Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppv` jest równa NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja pomocnika jest wykorzystywany przez [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (przestarzałe w wersji 7.0 ATL) i [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
