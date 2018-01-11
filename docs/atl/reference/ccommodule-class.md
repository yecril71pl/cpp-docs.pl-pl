---
title: "Ccommodule — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b86e1f082b7be844afe3b1a84d182d1c722f500
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccommodule-class"></a>Ccommodule — klasa
Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComModule::GetClassObject](#getclassobject)|Tworzy obiekt CLSID określony. Dla bibliotek DLL tylko.|  
|[CComModule::GetModuleInstance](#getmoduleinstance)|Zwraca `m_hInst`.|  
|[CComModule::GetResourceInstance](#getresourceinstance)|Zwraca `m_hInstResource`.|  
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Zwraca `m_hInstTypeLib`.|  
|[CComModule::Init](#init)|Inicjuje elementy członkowskie danych.|  
|[CComModule::RegisterClassHelper](#registerclasshelper)|Wprowadza obiektu klasa standardowa rejestracji w rejestrze systemu.|  
|[CComModule::RegisterClassObjects](#registerclassobjects)|Rejestruje obiekt klasy. Dla plików exe tylko.|  
|[CComModule::RegisterServer](#registerserver)|Aktualizuje rejestru systemowego dla każdego obiektu w mapie obiektu.|  
|[CComModule::RegisterTypeLib](#registertypelib)|Rejestruje bibliotekę typów.|  
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Odwołuje się obiekt klasy. Dla plików exe tylko.|  
|[CComModule::Term](#term)|Wersje elementów członkowskich danych.|  
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Usuwa rejestrację klasa standardowa obiektu z rejestru systemowego.|  
|[CComModule::UnregisterServer](#unregisterserver)|Wyrejestrowuje każdego obiektu w mapie obiektu.|  
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Rejestruje lub wyrejestrowuje rejestrowanie standardowe klasy obiektu.|  
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu.|  
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Statycznie łącza do składnik rejestru ALT. Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComModule::m_csObjMap](#m_csobjmap)|Zapewnia zsynchronizowane dostęp do informacji o obiekcie mapy.|  
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Zapewnia zsynchronizowane dostęp do informacji biblioteki typów.|  
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Zapewnia zsynchronizowane dostęp do informacji o klasie okna i dane statyczne, używane podczas tworzenia okna.|  
|[CComModule::m_hInst](#m_hinst)|Zawiera dojście do wystąpienia modułu.|  
|[CComModule::m_hInstResource](#m_hinstresource)|Domyślnie zawiera dojście do wystąpienia modułu.|  
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Domyślnie zawiera dojście do wystąpienia modułu.|  
|[CComModule::m_pObjMap](#m_pobjmap)|Wskazuje mapy obiektu obsługiwane przez to wystąpienie modułu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta klasa jest przestarzały i używać kreatorów generowania kodu ATL [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) klas pochodnych. Zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) Aby uzyskać więcej informacji. Informacje poniżej jest przeznaczona do użytku z aplikacjami utworzonych za pomocą starszej wersji ATL. `CComModule`jest nadal częścią ATL dla zapewnienia możliwości.  
  
 `CComModule`implementuje moduł serwera COM, umożliwiając klientowi dostęp do składników modułu. `CComModule`obsługuje zarówno (w trakcie) biblioteki DLL i EXE modułów (local).  
  
 A `CComModule` wystąpienie używa mapy obiektu do obsługi zestawu definicji obiektu klasy. Ta mapa obiektu jest zaimplementowany jako tablicę `_ATL_OBJMAP_ENTRY` struktury i zawiera informacje dotyczące:  
  
-   Wprowadzanie i usuwanie opisy obiektów w rejestrze systemu.  
  
-   Tworzenie wystąpień obiektów przez fabrykę klas.  
  
-   Nawiązywania połączenia między klientem a główny obiekt składnika.  
  
-   Wykonywanie Zarządzanie okresem istnienia klasy obiektów.  
  
 Po uruchomieniu z kreatorami AppWizard ATL COM, Kreator automatycznie generuje `_Module`, globalne wystąpienie `CComModule` lub klasą pochodną go. Aby uzyskać więcej informacji o Kreatorze Projekt ATL, zobacz artykuł [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Oprócz `CComModule`, zapewnia ATL [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), która implementuje moduł modelu typu apartment dla usług plików exe i systemu Windows. Pochodzi z modułu `CComAutoThreadModule` umożliwia tworzenie obiektów w wielu apartamentach.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="getclassobject"></a>CComModule::GetClassObject  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in] Identyfikator CLSID obiektu do utworzenia.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID żądanego interfejsu.  
  
 `ppv`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppv` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnika interfejsu do tego obiektu.  
  
 `GetClassObject`jest dostępna tylko dla bibliotek DLL.  
  
##  <a name="getmoduleinstance"></a>CComModule::GetModuleInstance  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HINSTANCE` Identyfikujący ten moduł.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca [m_hInst](#m_hinst) element członkowski danych.  
  
##  <a name="getresourceinstance"></a>CComModule::GetResourceInstance  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HINSTANCE`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca [m_hInstResource](#m_hinstresource) element członkowski danych.  
  
##  <a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE GetTypeLibInstance() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `HINSTANCE`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca [m_hInstTypeLib](#m_hinsttypelib) element członkowski danych.  
  
##  <a name="init"></a>CComModule::Init  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do tablicy wpisów map obiekt.  
  
 `h`  
 [in] `HINSTANCE` Przekazany do **DLLMain** lub `WinMain`.  
  
 `plibid`  
 [in] Wskaźnik do identyfikatora LIBID biblioteki typów skojarzony z projektem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje wszystkie elementy członkowskie danych.  
  
##  <a name="m_csobjmap"></a>CComModule::m_csObjMap  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
CRITICAL_SECTION m_csObjMap;
```  
  
### <a name="remarks"></a>Uwagi  
 Zapewnia zsynchronizowane dostępu do obiektu mapy.  
  
##  <a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
CRITICAL_SECTION m_csTypeInfoHolder;
```  
  
### <a name="remarks"></a>Uwagi  
 Zapewnia zsynchronizowane dostęp do biblioteki typów.  
  
##  <a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
CRITICAL_SECTION m_csWindowCreate;
```  
  
### <a name="remarks"></a>Uwagi  
 Zapewnia zsynchronizowane dostępu do informacji o klasie okna i dane statyczne, używane podczas tworzenia okna.  
  
##  <a name="m_hinst"></a>CComModule::m_hInst  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE m_hInst;
```  
  
### <a name="remarks"></a>Uwagi  
 Zawiera dojście do wystąpienia modułu.  
  
 [Init](#init) zestawy metody `m_hInst` do dojście przekazane do **DLLMain** lub `WinMain`.  
  
##  <a name="m_hinstresource"></a>CComModule::m_hInstResource  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE m_hInstResource;
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie zawiera dojście do wystąpienia modułu.  
  
 [Init](#init) zestawy metody `m_hInstResource` do dojście przekazane do **DLLMain** lub `WinMain`. Można ustawić jawnie `m_hInstResource` do dojścia do zasobu.  
  
 [GetResourceInstance](#getresourceinstance) metoda zwraca uchwyt przechowywane w `m_hInstResource`.  
  
##  <a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HINSTANCE m_hInstTypeLib;
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie zawiera dojście do wystąpienia modułu.  
  
 [Init](#init) zestawy metody `m_hInstTypeLib` do dojście przekazane do **DLLMain** lub `WinMain`. Można ustawić jawnie `m_hInstTypeLib` do dojścia do biblioteki typów.  
  
 [GetTypeLibInstance](#gettypelibinstance) metoda zwraca uchwyt przechowywane w `m_hInstTypeLib`.  
  
##  <a name="m_pobjmap"></a>CComModule::m_pObjMap  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje mapy obiektu obsługiwane przez to wystąpienie modułu.  
  
##  <a name="registerclasshelper"></a>CComModule::RegisterClassHelper  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID obiektu ma zostać zarejestrowany.  
  
 `lpszProgID`  
 [in] Identyfikator ProgID skojarzony z obiektem.  
  
 `lpszVerIndProgID`  
 [in] Identyfikator ProgID niezależny od wersji skojarzony z obiektem.  
  
 `nDescID`  
 [in] Identyfikator zasobu ciągu opisu obiektu.  
  
 `dwFlags`  
 [in] Określa model wątkowy wprowadzenia w rejestrze. Możliwe wartości to **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, lub **AUTPRXFLAG**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Wprowadza obiektu klasa standardowa rejestracji w rejestrze systemu.  
  
 [UpdateRegistryClass](#updateregistryclass) wywołania metody `RegisterClassHelper`.  
  
##  <a name="registerclassobjects"></a>CComModule::RegisterClassObjects  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwClsContext`  
 [in] Określa kontekst, w którym ma być uruchomiona obiektu klasy. Możliwe wartości to **CLSCTX_INPROC_SERVER**, **CLSCTX_INPROC_HANDLER**, lub **CLSCTX_LOCAL_SERVER**. Aby uzyskać opis tych wartości, zobacz [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) w zestawie Windows SDK.  
  
 `dwFlags`  
 [in] Określa typy połączeń z obiektem klasy. Możliwe wartości to **REGCLS_SINGLEUSE**, **REGCLS_MULTIPLEUSE**, lub **REGCLS_MULTI_SEPARATE**. Aby uzyskać opis tych wartości, zobacz [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Rejestruje obiekt klasy EXE OLE inne aplikacje do połączenia się do niego. Ta metoda jest dostępna tylko do plików exe.  
  
##  <a name="registerserver"></a>CComModule::RegisterServer  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bRegTypeLib`  
 [in] Wskazuje, czy będzie można zarejestrować biblioteki typów. Wartość domyślna to **FALSE**.  
  
 `pCLSID`  
 [in] Wskazuje identyfikator CLSID obiektu, który ma zostać zarejestrowany. Jeśli **NULL** (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie zarejestrowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 W zależności od `pCLSID` parametru aktualizacji rejestru systemowego dla obiekt jednej klasy lub dla wszystkich obiektów w mapie obiektu.  
  
 Jeśli `bRegTypeLib` jest **TRUE**, również zostaną zaktualizowane informacje biblioteki typów.  
  
 Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informacji o tym, jak dodać wpis do mapy obiektu.  
  
 `RegisterServer`będzie ona wywoływana automatycznie przez **DLLRegisterServer** biblioteki DLL lub przez `WinMain` dla pliku EXE Uruchom z **/regserver** opcji wiersza polecenia.  
  
##  <a name="registertypelib"></a>CComModule::RegisterTypeLib  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszIndex`  
 [in] Ciąg w formacie `"\\N"`, gdzie `N` jest liczba całkowita indeksu zasobu biblioteki typów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Dodaje informacje o biblioteki typów w rejestrze systemu.  
  
 Jeśli wystąpienie modułu zawiera wiele bibliotek typów, użyj druga wersja tej metody, aby określić, biblioteki typów, które powinny być używane.  
  
##  <a name="revokeclassobjects"></a>CComModule::RevokeClassObjects  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT RevokeClassObjects() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa obiekt klasy. Ta metoda jest dostępna tylko do plików exe.  
  
##  <a name="term"></a>CComModule::Term  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie elementy członkowskie danych.  
  
##  <a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID obiektu do wyrejestrowania.  
  
 `lpszProgID`  
 [in] Identyfikator ProgID skojarzony z obiektem.  
  
 `lpszVerIndProgID`  
 [in] Identyfikator ProgID niezależny od wersji skojarzony z obiektem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa rejestrację klasa standardowa obiektu z rejestru systemowego.  
  
 [UpdateRegistryClass](#updateregistryclass) wywołania metody `UnregisterClassHelper`.  
  
##  <a name="unregisterserver"></a>CComModule::UnregisterServer  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `bUnRegTypeLib`  
 Jeśli **TRUE**, jest również wyrejestrować biblioteki typów.  
  
 `pCLSID`  
 Wskazuje identyfikator CLSID obiektu do wyrejestrowania. Jeśli **NULL** (wartość domyślna) wszystkie obiekty w mapie obiektu zostanie wyrejestrowane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 W zależności od `pCLSID` parametru wyrejestrowuje obiektu klasy jednego lub wszystkich obiektów w mapie obiektu.  
  
 `UnregisterServer`będzie ona wywoływana automatycznie przez **DLLUnregisterServer** biblioteki DLL lub przez `WinMain` dla pliku EXE Uruchom z **/Unregserver** opcji wiersza polecenia.  
  
 Zobacz [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) informacji o tym, jak dodać wpis do mapy obiektu.  
  
##  <a name="updateregistryclass"></a>CComModule::UpdateRegistryClass  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
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
 `clsid`  
 Identyfikator CLSID obiektu zostać zarejestrowany lub wyrejestrowany.  
  
 `lpszProgID`  
 Identyfikator ProgID skojarzony z obiektem.  
  
 `lpszVerIndProgID`  
 Identyfikator ProgID niezależny od wersji skojarzony z obiektem.  
  
 `nDescID`  
 Identyfikator zasobu ciągu opisu obiektu.  
  
 `szDesc`  
 Ciąg zawierający opis obiektu.  
  
 `dwFlags`  
 Określa model wątkowy wprowadzenia w rejestrze. Możliwe wartości to **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, lub **AUTPRXFLAG**.  
  
 `bRegister`  
 Wskazuje, czy obiekt powinien zostać zarejestrowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bRegister` jest **TRUE**, ta metoda wprowadza obiektu klasa standardowa rejestracji w rejestrze systemu.  
  
 Jeśli `bRegister` jest **FALSE**, spowoduje usunięcie obiektu rejestracji.  
  
 W zależności od wartości `bRegister`, `UpdateRegistryClass` wywołuje albo [RegisterClassHelper](#registerclasshelper) lub [UnregisterClassHelper](#unregisterclasshelper).  
  
 Określając [DECLARE_REGISTRY](registry-macros.md#declare_registry) makra `UpdateRegistryClass` zostanie wywołany automatycznie podczas przetwarzania mapy obiektu.  
  
##  <a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
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
 `lpszRes`  
 [in] Nazwa zasobu.  
  
 `nResID`  
 [in] Identyfikator zasobu.  
  
 `bRegister`  
 [in] Wskazuje, czy obiekt powinien zostać zarejestrowany.  
  
 `pMapEntries`  
 [in] Wskaźnik do przechowywania wartości skojarzone z parametry wymienne skryptu mapy zastąpienia. Automatycznie wykorzystuje ATL `%MODULE%`. Aby korzystać z dodatkowych parametrów do zastąpienia, zobacz uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie użyj **NULL** wartość domyślna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Uruchamia skrypt zawarte w zasobie określonym przez `lpszRes` lub `nResID`.  
  
 Jeśli `bRegister` jest **TRUE**, ta metoda rejestruje obiekt w rejestrze systemu; w przeciwnym razie wyrejestrowuje go obiektu.  
  
 Określając [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra `UpdateRegistryFromResourceD` zostanie wywołany automatycznie podczas przetwarzania mapy obiektu.  
  
> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać `DECLARE_REGISTRY_RESOURCE` lub `DECLARE_REGISTRY_RESOURCEID` makra. Zamiast tego Utwórz tablicę **_ATL_REGMAP_ENTRIES** struktur, w którym każdy wpis zawiera symbol zastępczy zmiennej łączyć się z wartości do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj `UpdateRegistryFromResourceD`, przekazanie tablicy `pMapEntries` parametru. Spowoduje to dodanie wartości zastępcze w **_ATL_REGMAP_ENTRIES** struktury do mapy zastępczy rejestratora.  
  
> [!NOTE]
>  Aby połączyć statycznie składnik rejestru Alt (Rejestrator), zobacz [UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Aby uzyskać więcej informacji na temat parametrów wymiennych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResourceS  
 Począwszy od ATL 7.0 `CComModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
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
 `lpszRes`  
 [in] Nazwa zasobu.  
  
 `nResID`  
 [in] Identyfikator zasobu.  
  
 `bRegister`  
 [in] Wskazuje, czy skrypt zasobu powinny być rejestrowane.  
  
 `pMapEntries`  
 [in] Wskaźnik do przechowywania wartości skojarzone z parametry wymienne skryptu mapy zastąpienia. Automatycznie wykorzystuje ATL `%MODULE%`. Aby korzystać z dodatkowych parametrów do zastąpienia, zobacz uwagi, aby uzyskać szczegółowe informacje. W przeciwnym razie użyj **NULL** wartość domyślna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak [UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `UpdateRegistryFromResourceS` tworzy statyczne łącze do składnik rejestru Alt (Rejestrator).  
  
 `UpdateRegistryFromResourceS`zostanie wywołany automatycznie podczas przetwarzania mapy obiektu pod warunkiem, możesz dodać `#define _ATL_STATIC_REGISTRY` do Twojej stdafx.h.  
  
> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, nie należy określać [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) makra. Zamiast tego Utwórz tablicę **_ATL_REGMAP_ENTRIES** struktur, w którym każdy wpis zawiera symbol zastępczy zmiennej łączyć się z wartości do Zastąp symbol zastępczy w czasie wykonywania. Następnie wywołaj `UpdateRegistryFromResourceS`, przekazanie tablicy `pMapEntries` parametru. Spowoduje to dodanie wartości zastępcze w **_ATL_REGMAP_ENTRIES** struktury do mapy zastępczy rejestratora.  
  
 Aby uzyskać więcej informacji na temat parametrów wymiennych i skryptów, zobacz artykuł [składnik rejestru Alt (Rejestrator)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
