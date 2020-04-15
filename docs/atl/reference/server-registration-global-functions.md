---
title: Funkcje globalne rejestracji serwera
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325927"
---
# <a name="server-registration-global-functions"></a>Funkcje globalne rejestracji serwera

Te funkcje zapewniają obsługę rejestrowania i wyrejestrowywania obiektów serwera na mapie obiektu.

> [!IMPORTANT]
> Funkcji wymienionych w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[Serwer Rejestrowy AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Ta funkcja jest wywoływana, aby zarejestrować każdy obiekt na mapie obiektów.|
|[Serwer AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Ta funkcja jest wywoływana, aby wyrejestrować każdy obiekt na mapie obiektów.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Ta funkcja jest wywoływana, aby zarejestrować obiekty klasy.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Ta funkcja jest wywoływana do odwoływania obiektów klasy z modułu COM.|
|[AtlComModuleGetClassObject (Koszt ekwiwalectwa atlComModuleGetClassObject)](#atlcommodulegetclassobject)|Ta funkcja jest wywoływana, aby uzyskać obiekt klasy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>Serwer Rejestrowy AtlComModuleRegisterServer

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
PRAWDA, jeśli biblioteka typów ma być zarejestrowana.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli null, wszystkie obiekty na mapie obiektu zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

`AtlComModuleRegisterServer`przechadza się po automatycznie generowanej mapie obiektów ATL i rejestruje każdy obiekt na mapie. Jeśli *pCLSID* nie ma wartości NULL, zarejestrowany jest tylko obiekt, do którym odwołuje się *pCLSID;* w przeciwnym razie wszystkie obiekty są rejestrowane.

Ta funkcja jest wywoływana przez [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>Serwer AtlComModuleUnregisterServer

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
PRAWDA, jeśli biblioteka typów ma być zarejestrowana.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma być wyrejestrowany. Jeśli NULL wszystkie obiekty na mapie obiektu będą wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

`AtlComModuleUnregisterServer`przekierowuje mapę obiektu ATL i wyrejestruje każdy obiekt na mapie. Jeśli *pCLSID* nie ma wartości NULL, wówczas tylko obiekt, do którym odnosi się *pCLSID,* jest wyrejestrowany; w przeciwnym razie wszystkie obiekty są wyrejestrowane.

Ta funkcja jest wywoływana przez [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

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
Określa kontekst, w którym ma być uruchamiany obiekt klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Zobacz [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) aby uzyskać więcej informacji.

*Dwflags*<br/>
Określa typy połączeń z obiektem klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Zobacz [REGCLS,](/windows/win32/api/combaseapi/ne-combaseapi-regcls) aby uzyskać więcej informacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (przestarzałe w ATL 7.0) i [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

Ta funkcja jest wywoływana, aby usunąć fabrykę/fabryki klas z tabeli działających obiektów.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parametry

*pComModule*<br/>
Wskaźnik do modułu COM.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (przestarzałe w ATL 7.0) i [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject (Koszt ekwiwalectwa atlComModuleGetClassObject)

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

*rclsid ( rclsid )*<br/>
Identyfikator CLSID obiektu, który ma zostać utworzony.

*Riid*<br/>
Identyfikator żądanego interfejsu.

*Ppv*<br/>
Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppv* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja pomocnika jest wykorzystywana przez [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (przestarzałe w ATL 7.0) i [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
