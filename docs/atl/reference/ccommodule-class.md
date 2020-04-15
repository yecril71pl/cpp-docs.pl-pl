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
ms.openlocfilehash: 652c5f078ddbaf8d3e333f7003d6515a94dd8f83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327759"
---
# <a name="ccommodule-class"></a>Klasa CComModule

Od ATL 7.0, `CComModule` jest przestarzałe: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Tworzy obiekt określonego identyfikatora CLSID. Tylko w przypadku bibliotek DLL.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Zwraca wartość `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Zwraca wartość `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Zwraca wartość `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Inicjuje elementy członkowskie danych.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy. Tylko w przypadku EXE.|
|[CComModule::Serwer rejestru](#registerserver)|Aktualizuje rejestr systemowy dla każdego obiektu na mapie obiektu.|
|[CComModule::RegisterTypeLib](#registertypelib)|Rejestruje bibliotekę typów.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odwołuje obiekt klasy. Tylko w przypadku EXE.|
|[CComModule::Termin](#term)|Zwalnia członków danych.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Usuwa rejestrację klasy standardowej obiektu z rejestru systemowego.|
|[CComModule::Wyrejestrowanie serwera](#unregisterserver)|Wyrejestrowaje każdy obiekt na mapie obiektu.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Rejestruje lub wyrejestrowyje rejestrację klasy standardowej obiektu.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Statycznie łącza do składnika rejestru ATL. Uruchamia skrypt zawarty w określonym zasobie, aby zarejestrować lub wyrejestrować obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Zapewnia zsynchronizowany dostęp do informacji mapy obiektu.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zapewnia zsynchronizowany dostęp do informacji z biblioteki typów.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.|
|[CComModule::m_hInst](#m_hinst)|Zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstResource](#m_hinstresource)|Domyślnie zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Domyślnie zawiera dojście do wystąpienia modułu.|
|[CComModule::m_pObjMap](#m_pobjmap)|Wskazuje mapę obiektu obsługiwana przez wystąpienie modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta klasa jest przestarzała, a kreatorzy generowania kodu ATL używają teraz klas pochodnych [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule.](../../atl/reference/catlmodule-class.md) Zobacz [klasy modułów ATL, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji. Następujące informacje są przeznaczone do użytku z aplikacjami utworzonymi ze starszymi wersjami atl. `CComModule`jest nadal częścią ATL dla możliwości wstecz.

`CComModule`implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu. `CComModule`obsługuje zarówno moduły DLL (w toku), jak i EXE (lokalne).

Wystąpienie `CComModule` używa mapy obiektu do obsługi zestawu definicji obiektów klasy. Ta mapa obiektu jest implementowana `_ATL_OBJMAP_ENTRY` jako tablica struktur i zawiera informacje dla:

- Wprowadzanie i usuwanie opisów obiektów w rejestrze systemowym.

- Tworzenie wystąpienia obiektów za pośrednictwem fabryki klas.

- Ustanawianie komunikacji między klientem a obiektem głównym w składniku.

- Wykonywanie zarządzania okresem istnienia obiektów klas.

Po uruchomieniu kreatora aplikacji ATL COM automatycznie generuje `_Module`, globalne `CComModule` wystąpienie lub klasę z niego wywodzącą się z niego. Aby uzyskać więcej informacji na temat Kreatora projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Oprócz `CComModule`, ATL zapewnia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), który implementuje moduł modelu mieszkania dla EXEs i usług Systemu Windows. Wywiesić moduł z `CComAutoThreadModule` kiedy chcesz utworzyć obiekty w wielu mieszkaniach.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CComModule::GetClassObject

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid ( rclsid )*<br/>
[w] Identyfikator CLSID obiektu, który ma zostać utworzony.

*Riid*<br/>
[w] Identyfikator żądanego interfejsu.

*Ppv*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppv* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnik interfejsu do tego obiektu.

`GetClassObject`jest dostępna tylko dla bibliotek DLL.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CComModule::GetModuleInstance

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE identyfikacji tego modułu.

### <a name="remarks"></a>Uwagi

Zwraca [element](#m_hinst) członkowski m_hInst danych.

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CComModule::GetResourceInstance

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

An HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca [element](#m_hinstresource) członkowski m_hInstResource danych.

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Wartość zwracana

An HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca [element](#m_hinsttypelib) członkowski m_hInstTypeLib danych.

## <a name="ccommoduleinit"></a><a name="init"></a>CComModule::Init

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] Wskaźnik do tablicy wpisów mapy obiektów.

*H*<br/>
[w] HINSTANCE przeszedł `DLLMain` do `WinMain`lub .

*plibid ( plibid )*<br/>
[w] Wskaźnik do LIBID biblioteki typów skojarzonych z projektem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CComModule::m_csObjMap

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do mapy obiektów.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do biblioteki typów.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowany dostęp do informacji o klasie okna i danych statycznych używanych podczas tworzenia okna.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CComModule::m_hInst

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Uwagi

Zawiera dojście do wystąpienia modułu.

[Init](#init) Ustawia `m_hInst` metody do uchwytu przekazywane do `DLLMain` lub `WinMain`.

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CComModule::m_hInstResource

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Uwagi

Domyślnie zawiera dojście do wystąpienia modułu.

[Init](#init) Ustawia `m_hInstResource` metody do uchwytu przekazywane do `DLLMain` lub `WinMain`. Można jawnie `m_hInstResource` ustawić dojście do zasobu.

[Metoda GetResourceInstance](#getresourceinstance) zwraca dojście przechowywane w `m_hInstResource`.

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Uwagi

Domyślnie zawiera dojście do wystąpienia modułu.

[Init](#init) Ustawia `m_hInstTypeLib` metody do uchwytu przekazywane do `DLLMain` lub `WinMain`. Można jawnie `m_hInstTypeLib` ustawić dojście do biblioteki typów.

Metoda [GetTypeLibInstance](#gettypelibinstance) zwraca dojście przechowywane w `m_hInstTypeLib`pliku .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CComModule::m_pObjMap

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Uwagi

Wskazuje mapę obiektu obsługiwana przez wystąpienie modułu.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CComModule::RegisterClassHelper

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
[w] Identyfikator CLSID obiektu, który ma zostać zarejestrowany.

*lpszProgID*<br/>
[w] Identyfikator progid skojarzony z obiektem.

*lpszVerIndProgID*<br/>
[w] ProgID niezależny od wersji skojarzony z obiektem.

*nDescID (identyfikator nDescID)*<br/>
[w] Identyfikator zasobu ciągu dla opisu obiektu.

*Dwflags*<br/>
[w] Określa model wątków, który ma być wprowadzany w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.

Wywołanie `RegisterClassHelper`metody [UpdateRegistryClass](#updateregistryclass) .

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CComModule::RegisterClassObjects

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
[w] Określa kontekst, w którym ma być uruchamiany obiekt klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Aby uzyskać opis tych wartości, zobacz [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) w windows SDK.

*Dwflags*<br/>
[w] Określa typy połączeń z obiektem klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Aby uzyskać opis tych wartości, zobacz [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Rejestruje obiekt klasy EXE z ole, dzięki czemu inne aplikacje mogą się z nim łączyć. Ta metoda jest dostępna tylko dla EXEs.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CComModule::Serwer rejestru

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
[w] Wskazuje, czy biblioteka typów zostanie zarejestrowana. Wartością domyślną jest FAŁSZ.

*pCLSID (pCLSID)*<br/>
[w] Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną zarejestrowane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od parametru *pCLSID* aktualizuje rejestr systemowy dla pojedynczego obiektu klasy lub dla wszystkich obiektów na mapie obiektu.

Jeśli *bRegTypeLib* jest true, informacje o bibliotece typów zostaną również zaktualizowane.

Zobacz [OBJECT_ENTRY_AUTO,](object-map-macros.md#object_entry_auto) aby uzyskać informacje na temat dodawania wpisu do mapy obiektu.

`RegisterServer`zostanie wywołana automatycznie `DLLRegisterServer` przez dla biblioteki DLL lub `WinMain` `/RegServer` przez uruchomienie EXE z opcją wiersza polecenia.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CComModule::RegisterTypeLib

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
[w] Ciąg w `"\\N"`formacie `N` , gdzie jest indeksem liczb całkowitych zasobu TYPELIB.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Dodaje informacje o bibliotece typów do rejestru systemowego.

Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj drugiej wersji tej metody, aby określić, która biblioteka typów powinna być używana.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CComModule::RevokeClassObjects

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa obiekt klasy. Ta metoda jest dostępna tylko dla EXEs.

## <a name="ccommoduleterm"></a><a name="term"></a>CComModule::Termin

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkich elementów członkowskich danych.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
[w] Identyfikator CLSID obiektu, który ma być wyrejestrowany.

*lpszProgID*<br/>
[w] Identyfikator progid skojarzony z obiektem.

*lpszVerIndProgID*<br/>
[w] ProgID niezależny od wersji skojarzony z obiektem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa rejestrację klasy standardowej obiektu z rejestru systemowego.

Wywołanie `UnregisterClassHelper`metody [UpdateRegistryClass](#updateregistryclass) .

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CComModule::Wyrejestrowanie serwera

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
Jeśli true, biblioteka typów jest również wyrejestrowany.

*pCLSID (pCLSID)*<br/>
Wskazuje identyfikator CLSID obiektu, który ma być wyrejestrowany. Jeśli wartość NULL (wartość domyślna), wszystkie obiekty na mapie obiektu zostaną wyrejestrowane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od parametru *pCLSID* wyrejestrowano pojedynczy obiekt klasy lub wszystkie obiekty na mapie obiektu.

`UnregisterServer`zostanie wywołana automatycznie `DLLUnregisterServer` przez dla biblioteki DLL lub `WinMain` `/UnregServer` przez uruchomienie EXE z opcją wiersza polecenia.

Zobacz [OBJECT_ENTRY_AUTO,](object-map-macros.md#object_entry_auto) aby uzyskać informacje na temat dodawania wpisu do mapy obiektu.

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CComModule::UpdateRegistryClass

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

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

*Clsid*<br/>
Identyfikator CLSID obiektu, który ma zostać zarejestrowany lub wyrejestrowany.

*lpszProgID*<br/>
Identyfikator progid skojarzony z obiektem.

*lpszVerIndProgID*<br/>
ProgID niezależny od wersji skojarzony z obiektem.

*nDescID (identyfikator nDescID)*<br/>
Identyfikator zasobu ciągu dla opisu obiektu.

*szDesc (szDesc)*<br/>
Ciąg zawierający opis obiektu.

*Dwflags*<br/>
Określa model wątków, który ma być wprowadzany w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

*Bregister*<br/>
Wskazuje, czy obiekt powinien zostać zarejestrowany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli *bRegister* ma wartość PRAWDA, ta metoda wprowadza rejestrację klasy standardowej obiektu w rejestrze systemowym.

Jeśli *bRegister* jest FALSE, usuwa rejestracji obiektu.

W zależności od wartości *bRegister*, `UpdateRegistryClass` wywołuje [registerclasshelper](#registerclasshelper) lub [UnregisterClassHelper](#unregisterclasshelper).

Określając makro [DECLARE_REGISTRY,](registry-macros.md#declare_registry) `UpdateRegistryClass` zostanie wywołane automatycznie podczas przetwarzania mapy obiektu.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

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
[w] Nazwa zasobu.

*nResID (700)*<br/>
[w] Identyfikator zasobu.

*Bregister*<br/>
[w] Wskazuje, czy obiekt powinien zostać zarejestrowany.

*pMapEntries (Nieskładka)*<br/>
[w] Wskaźnik do mapy zastępczej przechowującej wartości skojarzone z wymiennymi parametrami skryptu. ATL automatycznie używa `%MODULE%`. Aby użyć dodatkowych parametrów wymiennych, zobacz Uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie należy użyć wartości domyślnej NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarty w zasobie określonym przez *lpszRes* lub *nResID*.

Jeśli *bRegister* ma wartość TRUE, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie wyrejestruje obiekt.

Określając [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra, `UpdateRegistryFromResourceD` zostanie wywołana automatycznie podczas przetwarzania mapy obiektu.

> [!NOTE]
> Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE ani DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego należy utworzyć `_ATL_REGMAP_ENTRIES` tablicę struktur, w której każdy wpis zawiera zmienny symbol zastępczy sparowany z wartością zastępującą symbol zastępczy w czasie wykonywania. Następnie `UpdateRegistryFromResourceD`wywołać , przekazując tablicę dla *pMapEntries* parametru. Spowoduje to dodanie wszystkich `_ATL_REGMAP_ENTRIES` wartości zastępczych w strukturach do mapy zastępczej rejestratora.

> [!NOTE]
> Aby statycznie połączyć się ze składnikiem rejestru ATL (Rejestrator), zobacz [UpdateRegistryFromResourceS](#updateregistryfromresources).

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł [Składnik rejestru ATL (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResourceS

Od ATL 7.0, `CComModule` jest przestarzały: zobacz [atl moduł klas, aby](../../atl/atl-module-classes.md) uzyskać więcej informacji.

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
[w] Nazwa zasobu.

*nResID (700)*<br/>
[w] Identyfikator zasobu.

*Bregister*<br/>
[w] Wskazuje, czy skrypt zasobu powinien być zarejestrowany.

*pMapEntries (Nieskładka)*<br/>
[w] Wskaźnik do mapy zastępczej przechowującej wartości skojarzone z wymiennymi parametrami skryptu. ATL automatycznie używa `%MODULE%`. Aby użyć dodatkowych parametrów wymiennych, zobacz Uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie należy użyć wartości domyślnej NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Podobnie jak [UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `UpdateRegistryFromResourceS` tworzy statyczne łącze do składnika rejestru ATL (Rejestrator).

`UpdateRegistryFromResourceS`zostanie wywołana automatycznie podczas przetwarzania mapy obiektu, pod `#define _ATL_STATIC_REGISTRY` warunkiem dodania do *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych).

> [!NOTE]
> Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ani [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra. Zamiast tego należy utworzyć `_ATL_REGMAP_ENTRIES` tablicę struktur, w której każdy wpis zawiera zmienny symbol zastępczy sparowany z wartością zastępującą symbol zastępczy w czasie wykonywania. Następnie `UpdateRegistryFromResourceS`wywołać , przekazując tablicę dla *pMapEntries* parametru. Spowoduje to dodanie wszystkich `_ATL_REGMAP_ENTRIES` wartości zastępczych w strukturach do mapy zastępczej rejestratora.

Aby uzyskać więcej informacji na temat wymiennych parametrów i skryptów, zobacz artykuł [Składnik rejestru ATL (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
