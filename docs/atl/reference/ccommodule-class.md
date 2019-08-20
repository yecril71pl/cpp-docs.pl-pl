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
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630655"
---
# <a name="ccommodule-class"></a>Klasa CComModule

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComModule:: GetClassObject](#getclassobject)|Tworzy obiekt o określonym identyfikatorze CLSID. Tylko dla bibliotek DLL.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Zwraca `m_hInst`wartość.|
|[CComModule:: GetResourceInstance](#getresourceinstance)|Zwraca `m_hInstResource`wartość.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Zwraca `m_hInstTypeLib`wartość.|
|[CComModule:: init](#init)|Inicjuje składowe danych.|
|[CComModule:: RegisterClassHelper](#registerclasshelper)|Wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.|
|[CComModule:: RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy. Tylko dla exe.|
|[CComModule:: RegisterServer](#registerserver)|Aktualizuje rejestr systemu dla każdego obiektu na mapie obiektów.|
|[CComModule::RegisterTypeLib](#registertypelib)|Rejestruje bibliotekę typów.|
|[CComModule:: RevokeClassObjects](#revokeclassobjects)|Odwołuje obiekt klasy. Tylko dla exe.|
|[CComModule:: Term](#term)|Zwalnia elementy członkowskie danych.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Usuwa rejestrację klasy standardowej obiektu z rejestru systemowego.|
|[CComModule::UnregisterServer](#unregisterserver)|Wyrejestrowuje każdy obiekt na mapie obiektów.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Rejestruje lub wyrejestrowuje rejestrację klasy standardowej obiektu.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Statycznie łączy się ze składnikiem rejestru ATL. Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Zapewnia zsynchronizowany dostęp do informacji o mapie obiektu.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zapewnia zsynchronizowany dostęp do informacji o bibliotece typów.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.|
|[CComModule::m_hInst](#m_hinst)|Zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstResource](#m_hinstresource)|Domyślnie program zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Domyślnie program zawiera dojście do wystąpienia modułu.|
|[CComModule::m_pObjMap](#m_pobjmap)|Wskazuje mapę obiektów obsługiwaną przez wystąpienie modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta klasa jest przestarzała, a Kreator generowania kodu ATL używa teraz klas pochodnych [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) . Aby uzyskać więcej informacji, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) . Poniższe informacje są przeznaczone do użycia w przypadku aplikacji utworzonych przy użyciu starszych wersji ATL. `CComModule`jest nadal częścią ATL dla funkcji wstecz.

`CComModule`implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu. `CComModule`obsługuje zarówno moduły DLL (wewnątrzprocesowe), jak i EXE (lokalne).

`CComModule` Wystąpienie używa mapy obiektów do obsługi zestawu definicji obiektów klasy. Ta mapa obiektów jest zaimplementowana jako tablica `_ATL_OBJMAP_ENTRY` struktur i zawiera informacje o:

- Wprowadzanie i usuwanie opisów obiektów w rejestrze systemowym.

- Tworzenie wystąpienia obiektów przy użyciu fabryki klas.

- Ustanawianie komunikacji między klientem a obiektem głównym w składniku.

- Wykonywanie zarządzania obiektami klas przez okres istnienia.

Po uruchomieniu biblioteki ATL com AppWizard Kreator automatycznie generuje `_Module`, globalne `CComModule` wystąpienie klasy lub klasę pochodną. Aby uzyskać więcej informacji na temat Kreatora projektu ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Oprócz `CComModule`programu ATL oferuje [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), który implementuje moduł modelu Apartment dla exe i usług systemu Windows. Wykorzystaj moduł `CComAutoThreadModule` od momentu, gdy chcesz tworzyć obiekty w wielu apartamentach.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

`GetClassObject`jest dostępny tylko dla bibliotek DLL.

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE identyfikacji tego modułu.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInst](#m_hinst) .

##  <a name="getresourceinstance"></a>CComModule:: GetResourceInstance

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInstResource](#m_hinstresource) .

##  <a name="gettypelibinstance"></a>CComModule:: GetTypeLibInstance

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca element członkowski danych [m_hInstTypeLib](#m_hinsttypelib) .

##  <a name="init"></a>CComModule:: init

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Wskaźnik do tablicy wpisów mapy obiektu.

*h*<br/>
podczas HINSTANCE przeszedł do `DLLMain` lub `WinMain`.

*plibid*<br/>
podczas Wskaźnik do identyfikatora LIBID biblioteki typów skojarzonej z projektem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

##  <a name="m_csobjmap"></a>CComModule:: m_csObjMap

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do mapowania obiektów.

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do biblioteki typów.

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.

##  <a name="m_hinst"></a>CComModule:: m_hInst

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Uwagi

Zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInst` do dojścia przekazaną `DLLMain` do `WinMain`lub.

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Uwagi

Domyślnie program zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInstResource` do dojścia przekazaną `DLLMain` do `WinMain`lub. Można jawnie ustawić `m_hInstResource` dojście do zasobu.

Metoda [GetResourceInstance](#getresourceinstance) zwraca dojście przechowywane w `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Uwagi

Domyślnie program zawiera dojście do wystąpienia modułu.

Metoda [init](#init) ustawia `m_hInstTypeLib` do dojścia przekazaną `DLLMain` do `WinMain`lub. Można jawnie ustawić `m_hInstTypeLib` do dojścia do biblioteki typów.

Metoda [GetTypeLibInstance](#gettypelibinstance) zwraca dojście przechowywane w `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Uwagi

Wskazuje mapę obiektów obsługiwaną przez wystąpienie modułu.

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Wywołanie`RegisterClassHelper`metody [UpdateRegistryClass](#updateregistryclass) .

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) , aby uzyskać informacje na temat dodawania wpisu do mapy obiektów.

`RegisterServer`zostanie wywołane automatycznie przez `DLLRegisterServer` program dla biblioteki DLL lub `WinMain` przez plik exe uruchamiany z `/RegServer` opcją wiersza polecenia.

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa obiekt Class. Ta metoda jest dostępna tylko dla exe.

##  <a name="term"></a>CComModule:: Term

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

```
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie elementy członkowskie danych.

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Wywołanie`UnregisterClassHelper`metody [UpdateRegistryClass](#updateregistryclass) .

##  <a name="unregisterserver"></a>CComModule:: UnregisterServer

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

`UnregisterServer`zostanie wywołane automatycznie przez `DLLUnregisterServer` program dla biblioteki DLL lub `WinMain` przez plik exe uruchamiany z `/UnregServer` opcją wiersza polecenia.

Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) , aby uzyskać informacje na temat dodawania wpisu do mapy obiektów.

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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

Określając makro [DECLARE_REGISTRY](registry-macros.md#declare_registry) , `UpdateRegistryClass` zostanie wywołane automatycznie podczas przetwarzania mapowania obiektów.

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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
podczas Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. Biblioteki ATL są `%MODULE%`automatycznie stosowane. Aby użyć dodatkowych parametrów wymiennych, zobacz uwagi w celu uzyskania szczegółowych informacji. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarty w zasobie określony przez *lpszRes* lub *nResID*.

Jeśli *bRegister* ma wartość true, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie wyrejestruje obiekt.

Określając makro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) , `UpdateRegistryFromResourceD` zostanie wywołane automatycznie podczas przetwarzania mapowania obiektów.

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie określaj makra DECLARE_REGISTRY_RESOURCE ani DECLARE_REGISTRY_RESOURCEID. Zamiast tego należy utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj `UpdateRegistryFromResourceD`, przekazując tablicę do parametru *pMapEntries* . Spowoduje to dodanie wszystkich wartości `_ATL_REGMAP_ENTRIES` zamiennych ze struktur do mapy wymiany rejestratora.

> [!NOTE]
>  Aby statycznie łączyć się ze składnikiem rejestru ATL (Rejestrator), zobacz [UpdateRegistryFromResourceS](#updateregistryfromresources).

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

Począwszy od biblioteki ATL 7,0 `CComModule` , jest przestarzały: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) , aby uzyskać więcej szczegółów.

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
podczas Wskaźnik do mapowanej mapy przechowującej wartości skojarzone z parametrami wymiennymi skryptu. Biblioteki ATL są `%MODULE%`automatycznie stosowane. Aby użyć dodatkowych parametrów wymiennych, zobacz uwagi w celu uzyskania szczegółowych informacji. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Podobnie jak [](#updateregistryfromresourced) w przypadku `UpdateRegistryFromResourceS` programu UpdateRegistryFromResourceD, z wyjątkiem tworzenia statycznego łącza do składnika rejestru ATL (Rejestrator).

`UpdateRegistryFromResourceS`zostanie wywołany automatycznie podczas przetwarzania mapowania obiektów, pod warunkiem, że `#define _ATL_STATIC_REGISTRY` zostanie on dodany do *PCH. h* (*stdafx. h* w Visual Studio 2017 i wcześniejszych).

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie określaj makra [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ani [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) . Zamiast tego należy utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, gdzie każdy wpis zawiera zmienną symbol zastępczy sparowany z wartością, aby zastąpić symbol zastępczy w czasie wykonywania. Następnie Wywołaj `UpdateRegistryFromResourceS`, przekazując tablicę do parametru *pMapEntries* . Spowoduje to dodanie wszystkich wartości `_ATL_REGMAP_ENTRIES` zamiennych ze struktur do mapy wymiany rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł dotyczący [składnika rejestru ATL (rejestratora)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
