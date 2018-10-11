---
title: Klasa CComModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 519837379369f08108d3d5b5b300fe0bcb9ac5e7
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083817"
---
# <a name="ccommodule-class"></a>Ccommodule — klasa

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Tworzy obiekt z określonym identyfikatorem CLSID. Dla bibliotek DLL tylko.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Zwraca `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Zwraca `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Zwraca `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Inicjuje elementy członkowskie danych.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Wprowadza rejestracja standardowych klas obiektów w rejestrze systemowym.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy. Aby uzyskać tylko exe.|
|[CComModule::RegisterServer](#registerserver)|Aktualizacja rejestru systemowego dla każdego obiektu na mapie obiektu.|
|[CComModule::RegisterTypeLib](#registertypelib)|Rejestruje bibliotekę typów.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odwołuje obiektu klasy. Aby uzyskać tylko exe.|
|[CComModule::Term](#term)|Zwalnia składowych danych.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Usuwa obiekt klasa standardowa rejestracji z rejestru systemowego.|
|[CComModule::UnregisterServer](#unregisterserver)|Wyrejestrowuje każdy obiekt na mapie obiektu.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Rejestruje lub wyrejestrowuje rejestracja standardowych klas obiektów.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Statycznie łączy do składnik rejestru ALT. Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Zapewnia zsynchronizowane dostęp do informacji mapie obiektu.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zapewnia zsynchronizowane dostęp do informacji o bibliotece typu.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zapewnia zsynchronizowane dostęp do informacji o klasie okna i dane statyczne, używana podczas tworzenia okna.|
|[CComModule::m_hInst](#m_hinst)|Zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstResource](#m_hinstresource)|Domyślnie zawiera dojście do wystąpienia modułu.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Domyślnie zawiera dojście do wystąpienia modułu.|
|[CComModule::m_pObjMap](#m_pobjmap)|Wskazuje na mapie obiektu utrzymywane przez wystąpienie modułu.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta klasa jest przestarzała i kreatorów generowania kodu biblioteki ATL teraz używać [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) klas pochodnych. Zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji. Informacje, który następuje po jest przeznaczona do użytku z aplikacje utworzone przy użyciu starszych wersji ATL. `CComModule` wciąż są częścią biblioteki ATL dla zapewnienia możliwości.

`CComModule` implementuje modułu serwera COM, umożliwiając klientowi dostęp do składników modułu. `CComModule` obsługuje zarówno biblioteki DLL (w procesie) i moduły (local) EXE.

A `CComModule` wystąpienie korzysta z mapy obiektu do obsługi zestawu definicji obiektu klasy. To mapowanie obiektu jest implementowana jako tablica `_ATL_OBJMAP_ENTRY` struktury i zawiera informacje dotyczące:

- Wprowadzanie i usuwanie opisy obiektów w rejestrze systemowym.

- Tworzenie wystąpień obiektów za pomocą fabryki klas.

- Ustanawianie komunikacji między klientem a głównego obiektu w składniku.

- Wykonywanie Zarządzanie okresem istnienia obiektów klas.

Po uruchomieniu kreatora AppWizard COM ATL, Kreator automatycznie generuje `_Module`, globalnego wystąpienia `CComModule` lub klasa pochodnej od niego. Aby uzyskać więcej informacji na temat Kreator projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Oprócz `CComModule`, ATL dostarcza [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), który implementuje moduł modelu typu apartment dla usług plików exe i Windows. Pochodzi z modułu `CComAutoThreadModule` gdy zachodzi potrzeba tworzenia obiektów w wielu apartamentach.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="getclassobject"></a>  CComModule::GetClassObject

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parametry

*rclsid*<br/>
[in] Identyfikator CLSID obiektu do utworzenia.

*Parametr riid*<br/>
[in] Identyfikator IID żądanego interfejsu.

*ppv*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppv* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Tworzy obiekt z określonym identyfikatorem CLSID i pobiera wskaźnik interfejsu do tego obiektu.

`GetClassObject` jest dostępna tylko dla bibliotek DLL.

##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE, identyfikowanie tego modułu.

### <a name="remarks"></a>Uwagi

Zwraca [m_hInst](#m_hinst) element członkowski danych.

##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca [m_hInstResource](#m_hinstresource) element członkowski danych.

##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Wartość zwracana

HINSTANCE.

### <a name="remarks"></a>Uwagi

Zwraca [m_hInstTypeLib](#m_hinsttypelib) element członkowski danych.

##  <a name="init"></a>  CComModule::Init

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Wskaźnik do tablicy obiektu wpisy mapy.

*h*<br/>
[in] HINSTANCE przekazany do `DLLMain` lub `WinMain`.

*plibid*<br/>
[in] Wskaźnik do identyfikatora LIBID biblioteki typów, skojarzone z tym projektem.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Inicjuje wszystkie elementy członkowskie danych.

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowane dostępu do mapy obiektu.

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowane dostęp do biblioteki typów.

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Uwagi

Zapewnia zsynchronizowane dostęp do informacji o klasie okna i dane statyczne, używana podczas tworzenia okna.

##  <a name="m_hinst"></a>  CComModule::m_hInst

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Uwagi

Zawiera dojście do wystąpienia modułu.

[Init](#init) metody ustawia `m_hInst` na dojście przekazane do `DLLMain` lub `WinMain`.

##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Uwagi

Domyślnie zawiera dojście do wystąpienia modułu.

[Init](#init) metody ustawia `m_hInstResource` na dojście przekazane do `DLLMain` lub `WinMain`. Można jawnie ustawić `m_hInstResource` do dojścia do zasobu.

[GetResourceInstance](#getresourceinstance) metoda zwraca uchwyt przechowywane w `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Uwagi

Domyślnie zawiera dojście do wystąpienia modułu.

[Init](#init) metody ustawia `m_hInstTypeLib` na dojście przekazane do `DLLMain` lub `WinMain`. Można jawnie ustawić `m_hInstTypeLib` do dojścia do biblioteki typów.

[GetTypeLibInstance](#gettypelibinstance) metoda zwraca uchwyt przechowywane w `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Uwagi

Wskazuje na mapie obiektu utrzymywane przez wystąpienie modułu.

##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
[in] Identyfikator CLSID obiektu do zarejestrowania.

*lpszProgID*<br/>
[in] Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
[in] Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

*nDescID*<br/>
[in] Identyfikator zasobu ciągu opisu obiektu.

*Flagidw*<br/>
[in] Określa model wątkowy wprowadzenia w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wprowadza rejestracja standardowych klas obiektów w rejestrze systemowym.

[UpdateRegistryClass](#updateregistryclass) wywołania metody `RegisterClassHelper`.

##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parametry

*dwClsContext*<br/>
[in] Określa kontekst, w którym ma być uruchamiane obiektu klasy. Możliwe wartości to CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER lub CLSCTX_LOCAL_SERVER. Aby uzyskać opis tych wartości, zobacz [CLSCTX](/windows/desktop/api/wtypesbase/ne-wtypesbase-tagclsctx) w zestawie Windows SDK.

*Flagidw*<br/>
[in] Określa typy połączeń do obiektu klasy. Możliwe wartości to REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE lub REGCLS_MULTI_SEPARATE. Aby uzyskać opis tych wartości, zobacz [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Rejestruje obiekt klasy EXE z OLE, dzięki czemu inne aplikacje mogą nawiązać z nim. Ta metoda jest dostępna tylko na pliku exe.

##  <a name="registerserver"></a>  CComModule::RegisterServer

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parametry

*bRegTypeLib*<br/>
[in] Wskazuje, czy będzie można zarejestrować biblioteki typów. Wartość domyślna to FALSE.

*pCLSID*<br/>
[in] Wskazuje identyfikator CLSID obiektu do zarejestrowania. Jeśli zostanie zarejestrowany o wartości NULL (wartość domyślna) wszystkie obiekty na mapie obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od *pCLSID* parametr aktualizuje rejestr systemu dla obiektu pojedynczą klasę lub dla wszystkich obiektów na mapie obiektu.

Jeśli *bRegTypeLib* ma wartość PRAWDA, zostaną również zaktualizowane informacje o typie biblioteki.

Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informacji na temat dodać wpis do mapy obiektu.

`RegisterServer` zostanie wywołana automatycznie przez `DLLRegisterServer` biblioteki DLL lub przez `WinMain` do uruchamiania z pliku EXE `/RegServer` opcji wiersza polecenia.

##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parametry

*lpszIndex*<br/>
[in] Ciąg w formacie `"\\N"`, gdzie `N` jest indeksem całkowitą zasobu biblioteki typów.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Dodaje informacje o biblioteki typów do rejestru systemowego.

Jeśli wystąpienie modułu zawiera wiele bibliotek typów, należy użyć drugiej wersji tej metody, aby określić, biblioteki typów, które powinny być używane.

##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa obiekt klasy. Ta metoda jest dostępna tylko na pliku exe.

##  <a name="term"></a>  CComModule::Term

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
void Term() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie składowe danych.

##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
[in] Identyfikator CLSID obiektu do wyrejestrowania.

*lpszProgID*<br/>
[in] Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
[in] Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Usuwa obiekt klasa standardowa rejestracji z rejestru systemowego.

[UpdateRegistryClass](#updateregistryclass) wywołania metody `UnregisterClassHelper`.

##  <a name="unregisterserver"></a>  CComModule::UnregisterServer

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parametry

*bUnRegTypeLib*<br/>
W przypadku opcji TRUE również jest wyrejestrowywany biblioteki typów.

*pCLSID*<br/>
Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli wartość NULL (wartość domyślna) wszystkie obiekty na mapie obiektu zostanie wyrejestrowany.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W zależności od *pCLSID* parametru wyrejestrowuje obiektu klasy jednego lub wszystkich obiektów na mapie obiektu.

`UnregisterServer` zostanie wywołana automatycznie przez `DLLUnregisterServer` biblioteki DLL lub przez `WinMain` do uruchamiania z pliku EXE `/UnregServer` opcji wiersza polecenia.

Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informacji na temat dodać wpis do mapy obiektu.

##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

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

*Identyfikator klasy*<br/>
Identyfikator CLSID obiektu zarejestrowanych lub niezarejestrowanych.

*lpszProgID*<br/>
Identyfikator ProgID skojarzony z obiektem.

*lpszVerIndProgID*<br/>
Identyfikator ProgID niezależny od wersji skojarzony z obiektem.

*nDescID*<br/>
Identyfikator zasobu ciągu opisu obiektu.

*szDesc*<br/>
Ciąg zawierający opis obiektu.

*Flagidw*<br/>
Określa model wątkowy wprowadzenia w rejestrze. Możliwe wartości to THREADFLAGS_APARTMENT, THREADFLAGS_BOTH lub AUTPRXFLAG.

*bRegister*<br/>
Wskazuje, czy obiekt powinien zostać zarejestrowany.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli *bRegister* ma wartość TRUE, ta metoda przechodzi rejestracja standardowych klas obiektów w rejestrze systemowym.

Jeśli *bRegister* ma wartość FAŁSZ, spowoduje usunięcie obiektu rejestracji.

W zależności od wartości *bRegister*, `UpdateRegistryClass` wywołuje albo [RegisterClassHelper](#registerclasshelper) lub [UnregisterClassHelper](#unregisterclasshelper).

Określając [DECLARE_REGISTRY](registry-macros.md#declare_registry) makra `UpdateRegistryClass` zostanie wywołana automatycznie podczas przetwarzania obiektu mapy.

##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

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
[in] Nazwa zasobu.

*nResID*<br/>
[in] Identyfikator zasobu.

*bRegister*<br/>
[in] Wskazuje, czy obiekt powinien zostać zarejestrowany.

*pMapEntries*<br/>
[in] Wskaźnik do mapy zastąpienie przechowywania wartości skojarzone z parametrów zastępowalnych skryptu. Automatycznie używa ATL `%MODULE%`. Aby korzystać z dodatkowych parametrów zastępowalnych, zobacz uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Uruchamia skrypt zawarte w zasób określony przez *lpszRes* lub *nResID*.

Jeśli *bRegister* ma wartość TRUE, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie jego wyrejestrowuje obiektu.

Określając [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra `UpdateRegistryFromResourceD` zostanie wywołana automatycznie podczas przetwarzania obiektu mapy.

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać DECLARE_REGISTRY_RESOURCE lub DECLARE_REGISTRY_RESOURCEID makra. Zamiast tego utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, w których każdy wpis zawiera symbol zastępczy zmiennej sparowane z wartością do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj `UpdateRegistryFromResourceD`, przekazując tablicę *pMapEntries* parametru. Spowoduje to dodanie na wartości zastępcze w `_ATL_REGMAP_ENTRIES` struktury do mapy zastąpienie rejestratora.

> [!NOTE]
>  Aby statycznie połączyć składnik rejestru Alt (Rejestrator), zobacz [UpdateRegistryFromResourceS](#updateregistryfromresources).

Aby uzyskać więcej informacji na temat parametrów zastępowalnych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS

Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ATL](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji.

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
[in] Nazwa zasobu.

*nResID*<br/>
[in] Identyfikator zasobu.

*bRegister*<br/>
[in] Wskazuje, czy skrypt zasobu powinny być rejestrowane.

*pMapEntries*<br/>
[in] Wskaźnik do mapy zastąpienie przechowywania wartości skojarzone z parametrów zastępowalnych skryptu. Automatycznie używa ATL `%MODULE%`. Aby korzystać z dodatkowych parametrów zastępowalnych, zobacz uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie użyj wartości domyślnej o wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Podobnie jak [UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `UpdateRegistryFromResourceS` tworzy statycznego linku do składnik rejestru Alt (Rejestrator).

`UpdateRegistryFromResourceS` zostanie on wywołany automatycznie po mapy obiektu jest przetwarzany, pod warunkiem dodasz `#define _ATL_STATIC_REGISTRY` do stdafx.h usługi.

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie określaj [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra. Zamiast tego utworzyć tablicę `_ATL_REGMAP_ENTRIES` struktur, w których każdy wpis zawiera symbol zastępczy zmiennej sparowane z wartością do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj `UpdateRegistryFromResourceS`, przekazując tablicę *pMapEntries* parametru. Spowoduje to dodanie na wartości zastępcze w `_ATL_REGMAP_ENTRIES` struktury do mapy zastąpienie rejestratora.

Aby uzyskać więcej informacji na temat parametrów zastępowalnych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
