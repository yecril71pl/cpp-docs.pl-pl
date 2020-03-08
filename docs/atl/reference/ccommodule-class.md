---
title: Klasa CComModule
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 482f29bae28841ab40ca8a8f80ab7f0df42ddc8b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863221"
---
# <a name="ccommodule-class"></a>Klasa CComModule

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComModule:: GetClassObject](#getclassobject)|Tworzy obiekt o określonym identyfikatorze CLSID. Tylko dla bibliotek DLL.|
|[CComModule:: GetModuleInstance](#getmoduleinstance)|Zwraca wartość `m_hInst`.|
|[CComModule:: GetResourceInstance](#getresourceinstance)|Zwraca wartość `m_hInstResource`.|
|[CComModule:: GetTypeLibInstance](#gettypelibinstance)|Zwraca wartość `m_hInstTypeLib`.|
|[CComModule:: init](#init)|Inicjuje składowe danych.|
|[CComModule:: RegisterClassHelper](#registerclasshelper)|Wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.|
|[CComModule:: RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy. Tylko dla exe.|
|[CComModule:: RegisterServer](#registerserver)|Aktualizuje rejestr systemu dla każdego obiektu na mapie obiektów.|
|[CComModule:: RegisterTypeLib](#registertypelib)|Rejestruje bibliotekę typów.|
|[CComModule:: RevokeClassObjects](#revokeclassobjects)|Odwołuje obiekt klasy. Tylko dla exe.|
|[CComModule:: Term](#term)|Zwalnia elementy członkowskie danych.|
|[CComModule:: UnregisterClassHelper](#unregisterclasshelper)|Usuwa rejestrację klasy standardowej obiektu z rejestru systemowego.|
|[CComModule:: UnregisterServer](#unregisterserver)|Wyrejestrowuje każdy obiekt na mapie obiektów.|
|[CComModule:: UpdateRegistryClass](#updateregistryclass)|Rejestruje lub wyrejestrowuje rejestrację klasy standardowej obiektu.|
|[CComModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|
|[CComModule:: UpdateRegistryFromResourceS](#updateregistryfromresources)|Statycznie łączy się ze składnikiem rejestru ATL. Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CComModule:: m_csObjMap](#m_csobjmap)|Zapewnia zsynchronizowany dostęp do informacji o mapie obiektu.|
|[CComModule:: m_csTypeInfoHolder](#m_cstypeinfoholder)|Zapewnia zsynchronizowany dostęp do informacji o bibliotece typów.|
|[CComModule:: m_csWindowCreate](#m_cswindowcreate)|Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.|
|[CComModule:: m_hInst](#m_hinst)|Zawiera dojście do wystąpienia modułu.|
|[CComModule:: m_hInstResource](#m_hinstresource)|Domyślnie program zawiera dojście do wystąpienia modułu.|
|[CComModule:: m_hInstTypeLib](#m_hinsttypelib)|Domyślnie program zawiera dojście do wystąpienia modułu.|
|[CComModule:: m_pObjMap](#m_pobjmap)|Wskazuje mapę obiektów obsługiwaną przez wystąpienie modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta klasa jest przestarzała, a Kreator generowania kodu ATL używa teraz klas pochodnych [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) . Aby uzyskać więcej informacji, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) . Poniższe informacje są przeznaczone do użycia w przypadku aplikacji utworzonych przy użyciu starszych wersji ATL. `CComModule` jest nadal częścią ATL dla funkcji wstecz.

`CComModule` implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu. `CComModule` obsługuje zarówno moduły DLL (wewnątrzprocesowe), jak i EXE (lokalne).

Wystąpienie `CComModule` używa mapy obiektów do obsługi zestawu definicji obiektów klasy. Ta mapa obiektów jest zaimplementowana jako tablica struktur `_ATL_OBJMAP_ENTRY` i zawiera informacje dotyczące:

- Wprowadzanie i usuwanie opisów obiektów w rejestrze systemowym.

- Tworzenie wystąpienia obiektów przy użyciu fabryki klas.

- Ustanawianie komunikacji między klientem a obiektem głównym w składniku.

- Wykonywanie zarządzania obiektami klas przez okres istnienia.

Po uruchomieniu biblioteki ATL COM AppWizard Kreator automatycznie generuje `_Module`, globalne wystąpienie `CComModule` lub klasy pochodzącej od niej. Aby uzyskać więcej informacji na temat Kreatora projektu ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Oprócz `CComModule`, ATL udostępnia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), który implementuje moduł modelu Apartment dla usług exe i Windows. Wykorzystaj moduł z `CComAutoThreadModule`, gdy chcesz utworzyć obiekty w wielu apartamentach.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
podczas Identyfikator CLSID obiektu, który ma zostać utworzony.

*riid*<br/>
podczas Identyfikator IID żądanego interfejsu.

*ppv*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *PPV* ma wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Tworzy obiekt o określonym identyfikatorze CLSID i Pobiera wskaźnik interfejsu do tego obiektu.

`GetClassObject` jest dostępna tylko dla bibliotek DLL.

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE identyfikacji tego modułu.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInst](#m_hinst) .

##  <a name="getresourceinstance"></a>CComModule:: GetResourceInstance

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInstResource](#m_hinstresource) .

##  <a name="gettypelibinstance"></a>CComModule:: GetTypeLibInstance

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInstTypeLib](#m_hinsttypelib) .

##  <a name="init"></a>CComModule:: init

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*St*<br/>
podczas Wskaźnik do tablicy wpisów mapy obiektu.

*c*<br/>
podczas HINSTANCE przeszedł do `DLLMain` lub `WinMain`.

*plibid*<br/>
podczas Wskaźnik do identyfikatora LIBID biblioteki typów skojarzonej z projektem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

##  <a name="m_csobjmap"></a>CComModule:: m_csObjMap

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do mapowania obiektów.

##  <a name="m_cstypeinfoholder"></a>CComModule:: m_csTypeInfoHolder

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do biblioteki typów.

##  <a name="m_cswindowcreate"></a>CComModule:: m_csWindowCreate

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.

##  <a name="m_hinst"></a>CComModule:: m_hInst

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Uwagi

Zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInst` do dojścia przekazaną do `DLLMain` lub `WinMain`.

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Uwagi

Domyślnie program zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInstResource` do dojścia przekazaną do `DLLMain` lub `WinMain`. Można jawnie ustawić `m_hInstResource` do dojścia do zasobu.

Metoda [GetResourceInstance](#getresourceinstance) zwraca dojście przechowywane w `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>CComModule:: m_hInstTypeLib

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Uwagi

Domyślnie program zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInstTypeLib` do dojścia przekazaną do `DLLMain` lub `WinMain`. Można jawnie ustawić `m_hInstTypeLib` do dojścia do biblioteki typów.

Metoda [GetTypeLibInstance](#gettypelibinstance) zwraca dojście przechowywane w `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>CComModule:: m_pObjMap

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Uwagi

Wskazuje mapę obiektów obsługiwaną przez wystąpienie modułu.

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
podczas Identyfikator CLSID obiektu, który ma zostać zarejestrowany.

*lpszProgID*<br/>
podczas Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
podczas Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

*nDescID*<br/>
podczas Identyfikator zasobu ciągu dla opisu obiektu.

*flagiDW*<br/>
podczas Określa model wątkowości, który ma zostać wprowadzony w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.

Metoda [UpdateRegistryClass](#updateregistryclass) wywołuje `RegisterClassHelper`.

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
podczas Określa kontekst, w którym obiekt klasy ma być uruchamiany. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Aby uzyskać opis tych wartości, zobacz [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) w Windows SDK.

*flagiDW*<br/>
podczas Określa typy połączeń do obiektu klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Aby uzyskać opis tych wartości, zobacz [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Rejestruje obiekt klasy EXE za pomocą OLE, tak aby inne aplikacje mogły się z nim połączyć. Ta metoda jest dostępna tylko dla exe.

##  <a name="registerserver"></a>CComModule:: RegisterServer

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
podczas Wskazuje, czy biblioteka typów zostanie zarejestrowana. Wartość domyślna to FALSE.

*pCLSID*<br/>
podczas Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od parametru *pCLSID* program aktualizuje rejestr systemu dla obiektu pojedynczej klasy lub dla wszystkich obiektów na mapie obiektów.

Jeśli *bRegTypeLib* ma wartość true, informacje o bibliotece typów również zostaną zaktualizowane.

Aby uzyskać informacje na temat dodawania wpisu do mapy obiektów, zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

`RegisterServer` będzie automatycznie wywoływana przez `DLLRegisterServer` dla biblioteki DLL lub przez `WinMain` dla pliku EXE z opcją wiersza polecenia `/RegServer`.

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
podczas Ciąg w formacie `"\\N"`, gdzie `N` jest indeksem liczb całkowitych zasobu biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dodaje informacje o bibliotece typów do rejestru systemowego.

Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj drugiej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

##  <a name="revokeclassobjects"></a>CComModule:: RevokeClassObjects

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa obiekt Class. Ta metoda jest dostępna tylko dla exe.

##  <a name="term"></a>CComModule:: Term

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie elementy członkowskie danych.

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
podczas Identyfikator CLSID obiektu, który ma zostać wyrejestrowany.

*lpszProgID*<br/>
podczas Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
podczas Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa rejestrację klasy standardowej obiektu z rejestru systemowego.

Metoda [UpdateRegistryClass](#updateregistryclass) wywołuje `UnregisterClassHelper`.

##  <a name="unregisterserver"></a>CComModule:: UnregisterServer

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
W przypadku wartości TRUE biblioteka typów jest również wyrejestrowana.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu, który ma zostać wyrejestrowany. W przypadku wartości NULL (wartość domyślna) wszystkie obiekty w mapie obiektów zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od parametru *pCLSID* wyrejestruje obiekt pojedynczej klasy lub wszystkie obiekty na mapie obiektów.

`UnregisterServer` będzie automatycznie wywoływana przez `DLLUnregisterServer` dla biblioteki DLL lub przez `WinMain` dla pliku EXE z opcją wiersza polecenia `/UnregServer`.

Aby uzyskać informacje na temat dodawania wpisu do mapy obiektów, zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Identyfikator CLSID obiektu, który ma zostać zarejestrowany lub wyrejestrowany.

*lpszProgID*<br/>
Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

*nDescID*<br/>
Identyfikator zasobu ciągu dla opisu obiektu.

*szDesc*<br/>
Ciąg zawierający opis obiektu.

*flagiDW*<br/>
Określa model wątkowości, który ma zostać wprowadzony w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

*bRegister*<br/>
Wskazuje, czy obiekt powinien być zarejestrowany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli *bRegister* ma wartość true, ta metoda wprowadza rejestrację klasy standardowej obiektu w rejestrze systemu.

Jeśli *bRegister* ma wartość false, usuwa rejestrację obiektu.

W zależności od wartości *bRegister*, `UpdateRegistryClass` wywołuje [RegisterClassHelper](#registerclasshelper) lub [UnregisterClassHelper](#unregisterclasshelper).

Określając [DECLARE_REGISTRY](registry-macros.md#declare_registry) makro, `UpdateRegistryClass` zostanie wywołane automatycznie podczas przetwarzania mapowania obiektów.

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
podczas Nazwa zasobu.

*nResID*<br/>
podczas Identyfikator zasobu.

*bRegister*<br/>
podczas Wskazuje, czy obiekt powinien być zarejestrowany.

*pMapEntries*<br/>
podczas Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. ATL automatycznie używa `%MODULE%`. Aby użyć dodatkowych parametrów wymiennych, zobacz uwagi w celu uzyskania szczegółowych informacji. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarty w zasobie określony przez *lpszRes* lub *nResID*.

Jeśli *bRegister* ma wartość true, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie wyrejestruje obiekt.

Określając [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makro, `UpdateRegistryFromResourceD` zostanie automatycznie wywołane podczas przetwarzania mapowania obiektów.

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE ani DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego Utwórz tablicę struktur `_ATL_REGMAP_ENTRIES`, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj `UpdateRegistryFromResourceD`, przekazując tablicę do parametru *pMapEntries* . Spowoduje to dodanie wszystkich wartości zastępczych ze struktur `_ATL_REGMAP_ENTRIES` do mapy wymiany rejestratora.

> [!NOTE]
>  Aby statycznie łączyć się ze składnikiem rejestru ATL (Rejestrator), zobacz [UpdateRegistryFromResourceS](#updateregistryfromresources).

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

Od biblioteki ATL 7,0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parametry

*lpszRes*<br/>
podczas Nazwa zasobu.

*nResID*<br/>
podczas Identyfikator zasobu.

*bRegister*<br/>
podczas Wskazuje, czy skrypt zasobów powinien być zarejestrowany.

*pMapEntries*<br/>
podczas Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. ATL automatycznie używa `%MODULE%`. Aby użyć dodatkowych parametrów wymiennych, zobacz uwagi w celu uzyskania szczegółowych informacji. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Podobnie jak w przypadku programu [UpdateRegistryFromResourceD](#updateregistryfromresourced) , z wyjątkiem `UpdateRegistryFromResourceS` tworzy statyczne łącze do składnika rejestru ATL (Rejestrator).

`UpdateRegistryFromResourceS` będzie wywoływana automatycznie podczas przetwarzania mapowania obiektów, pod warunkiem dodania `#define _ATL_STATIC_REGISTRY` do *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i jego wcześniejszych).

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ani [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra. Zamiast tego Utwórz tablicę struktur `_ATL_REGMAP_ENTRIES`, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj `UpdateRegistryFromResourceS`, przekazując tablicę do parametru *pMapEntries* . Spowoduje to dodanie wszystkich wartości zastępczych ze struktur `_ATL_REGMAP_ENTRIES` do mapy wymiany rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
