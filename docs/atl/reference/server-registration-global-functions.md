---
title: Funkcje globalne rejestracji serwera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c43e28e035691b04181bef2162de828f3271a600
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082757"
---
# <a name="server-registration-global-functions"></a>Funkcje globalne rejestracji serwera

Te funkcje umożliwiają rejestrowanie i wyrejestrowywanie serwera obiektów na mapie obiektu.

> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Ta funkcja jest wywoływana, aby zarejestrować każdy obiekt na mapie obiektów.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Ta funkcja jest wywoływana, aby wyrejestrować każdy obiekt na mapie obiektów.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Ta funkcja jest wywoływana, aby zarejestrować obiekty klasy.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Ta funkcja jest wywoływana, aby można było odwołać klasy obiektów z modułem COM.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Ta funkcja jest wywoływana, aby uzyskać obiekt klasy.|  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

Ta funkcja jest wywoływana, aby zarejestrować każdy obiekt na mapie obiektów.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

*bRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do zarejestrowania. Jeśli ma wartość NULL, będą rejestrowane wszystkie obiekty na mapie obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`AtlComModuleRegisterServer` przedstawia mapy obiektu ATL wygenerowany automatycznie i rejestruje każdy obiekt na mapie. Jeśli *pCLSID* nie jest równa NULL, a następnie tylko obiekt odwołuje się *pCLSID* jest zarejestrowany; w przeciwnym razie wszystkie obiekty zarejestrowane.

Ta funkcja jest wywoływana [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

Ta funkcja jest wywoływana, aby wyrejestrować każdy obiekt na mapie obiektów.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

*bUnRegTypeLib*<br/>
Wartość TRUE, jeśli biblioteka typów ma zostać zarejestrowany.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli ma wartość NULL wszystkich obiektów na mapie obiektu będzie można wyrejestrować.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

`AtlComModuleUnregisterServer` przedstawiono na mapie obiektu ATL i wyrejestrowuje każdy obiekt na mapie. Jeśli *pCLSID* nie jest równa NULL, a następnie tylko obiekt odwołuje się *pCLSID* jest niezarejestrowany; w przeciwnym razie wszystkie obiekty są wyrejestrować.

Ta funkcja jest wywoływana [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

##  <a name="atlcommoduleregisterclassobjects"></a>  AtlComModuleRegisterClassObjects

Ta funkcja jest wywoływana, aby zarejestrować obiekty klasy.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

*dwClsContext*<br/>
Określa kontekst, w którym ma być uruchamiane obiektu klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Zobacz [CLSCTX](/windows/desktop/api/wtypesbase/ne-wtypesbase-tagclsctx) Aby uzyskać więcej informacji.

*Flagidw*<br/>
Określa typy połączeń do obiektu klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Zobacz [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) Aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (przestarzałe w wersji 7.0 ATL) i [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

##  <a name="atlcommodulerevokeclassobjects"></a>  AtlComModuleRevokeClassObjects

Ta funkcja jest wywoływana, aby usunąć fabrykę/fabryki klas z tabeli działających obiektów.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (przestarzałe w wersji 7.0 ATL) i [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

Ta funkcja jest wywoływana, aby zwrócić fabrykę klasy.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

*rclsid*<br/>
Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*<br/>
Identyfikator IID żądanego interfejsu.

*ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywany przez [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (przestarzałe w wersji 7.0 ATL) i [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
