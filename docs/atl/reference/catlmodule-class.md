---
title: Klasa CAtlModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2be5d5a777d4b9aed9ee4d07016771ee91c913b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365285"
---
# <a name="catlmodule-class"></a>Klasa CAtlModule
Ta klasa udostępnia metody używane przez kilka klasy modułów ALT.  
  
## <a name="syntax"></a>Składnia  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|Konstruktor.|  
|[CAtlModule:: ~ CAtlModule](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Zastępuje tę metodę, aby dodać parametry do mapy zastępczy składnik rejestru Alt (Rejestrator).|  
|[CAtlModule::AddTermFunc](#addtermfunc)|Dodaje nowe funkcja wywoływana, gdy kończy modułu.|  
|[CAtlModule::GetGITPtr](#getgitptr)|Zwraca wskaźnik interfejsu globalnego.|  
|[CAtlModule::GetLockCount](#getlockcount)|Zwraca liczbę blokad.|  
|[CAtlModule::Lock](#lock)|Zwiększa liczbę blokad.|  
|[CAtlModule::Term](#term)|Zwalnia wszystkie elementy członkowskie danych.|  
|[CAtlModule::Unlock](#unlock)|Zmniejsza liczbę blokad.|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Ta metoda jest wywoływana przez `UpdateRegistryFromResourceD` do przeprowadzenia aktualizacji rejestru.|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu. Ta metoda statycznie łączy się składnik rejestru ALT.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|Zawiera unikatowy identyfikator GUID bieżącego modułu.|  
|[CAtlModule::m_pGIT](#m_pgit)|Wskaźnik do Tabela interfejsu globalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez [klasy CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), [klasy CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), i [klasy CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) zapewnia obsługę biblioteki DLL, aplikacje, EXE i Usługi systemu Windows, odpowiednio.  
  
 Aby uzyskać więcej informacji o modułach w ATL, zobacz [klasy modułów ALT](../../atl/atl-module-classes.md).  
  
 Ta klasa zastępuje przestarzałe [ccommodule — klasa](../../atl/reference/ccommodule-class.md) używany w starszych wersjach ATL.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements  
 Zastępuje tę metodę, aby dodać parametry do mapy zastępczy składnik rejestru Alt (Rejestrator).  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>Parametry  
 *pRegistrar*  
 Zastrzeżone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Parametry wymienne Zezwalaj klientowi rejestratora Określ dane czasu wykonywania. Aby to zrobić, rejestratora obsługuje mapy zastąpienia, w której wchodzi wartości skojarzone z parametry zmienne w skrypcie. Rejestratora sprawia, że te wpisy w czasie wykonywania.  
  
 Zobacz temat [przy użyciu parametry wymienne (Rejestrator preprocesora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) więcej szczegółów.  
  
##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc  
 Dodaje nowe funkcja wywoływana, gdy kończy modułu.  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pFunc*  
 Wskaźnik funkcji do dodania.  
  
 `dw`  
 Dane zdefiniowane przez użytkownika, przekazany do funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="catlmodule"></a>  CAtlModule::CAtlModule  
 Konstruktor.  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje elementów członkowskich danych i inicjuje sekcja krytyczna wokół modułu wątku.  
  
##  <a name="dtor"></a>  CAtlModule:: ~ CAtlModule  
 Destruktor.  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie elementy członkowskie danych.  
  
##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr  
 Pobiera wskaźnik do Tabela interfejsu globalnego.  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ppGIT`  
 Wskaźnik do zmiennej, która zostanie wyświetlony wskaźnik do Tabela interfejsu globalnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub błąd o kodzie błędu. E_POINTER jest zwracany, gdy `ppGIT` jest równa NULL.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tabela interfejsu globalnego obiekt nie istnieje, jest tworzona i jego adresu są przechowywane w zmiennej członkowskiej [CAtlModule::m_pGIT](#m_pgit).  
  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli `ppGIT` jest równa NULL, lub jeśli nie można uzyskać wskaźnika Tabela interfejsu globalnego.  
  
 Zobacz [IGlobalInterfaceTable](http://msdn.microsoft.com/library/windows/desktop/ms678517) dla informacji na temat Tabela interfejsu globalnego.  
  
##  <a name="getlockcount"></a>  CAtlModule::GetLockCount  
 Zwraca liczbę blokad.  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę blokad. Ta wartość może być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="lock"></a>  CAtlModule::Lock  
 Zwiększa liczbę blokad.  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwiększa liczbę blokad i zwraca zaktualizowanej wartości. Ta wartość może być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="m_libid"></a>  CAtlModule::m_libid  
 Zawiera unikatowy identyfikator GUID bieżącego modułu.  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>  CAtlModule::m_pGIT  
 Wskaźnik do Tabela interfejsu globalnego.  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>  CAtlModule::Term  
 Zwalnia wszystkie elementy członkowskie danych.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie elementy członkowskie danych. Ta metoda jest wywoływana przez destruktor.  
  
##  <a name="unlock"></a>  CAtlModule::Unlock  
 Zmniejsza liczbę blokad.  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zmniejsza liczbę blokad i zwraca zaktualizowanej wartości. Ta wartość może być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD  
 Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszRes`  
 Nazwa zasobu.  
  
 `nResID`  
 Identyfikator zasobu.  
  
 `bRegister`  
 **Wartość TRUE,** Jeśli obiekt powinien zostać zarejestrowany; **FALSE** inaczej.  
  
 `pMapEntries`  
 Wskaźnik do przechowywania wartości skojarzone z parametry wymienne skryptu mapy zastąpienia. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów do zastąpienia, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj **NULL** wartość domyślna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Uruchamia skrypt zawarte w zasobie określonym przez *lpszRes lub nResID*. Jeśli `bRegister` jest **TRUE**, ta metoda rejestruje obiekt w rejestrze systemu; w przeciwnym razie usuwa obiekt z rejestru.  
  
 Aby połączyć statycznie składnik rejestru Alt (Rejestrator), zobacz [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Ta metoda wywołuje [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) i [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).  
  
##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper  
 Ta metoda jest wywoływana przez `UpdateRegistryFromResourceD` do przeprowadzenia aktualizacji rejestru.  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszRes`  
 Nazwa zasobu.  
  
 `bRegister`  
 Wskazuje, czy obiekt powinien zostać zarejestrowany.  
  
 `pMapEntries`  
 Wskaźnik do przechowywania wartości skojarzone z parametry wymienne skryptu mapy zastąpienia. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów do zastąpienia, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj **NULL** wartość domyślna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia implementacji [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).  
  
##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS  
 Uruchamia skrypt zawartych w określonym zasobie do zarejestrowania lub wyrejestrowania obiektu. Ta metoda statycznie łączy się składnik rejestru ALT.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nResID`  
 Identyfikator zasobu.  
  
 `lpszRes`  
 Nazwa zasobu.  
  
 `bRegister`  
 Wskazuje, czy skrypt zasobu powinny być rejestrowane.  
  
 `pMapEntries`  
 Wskaźnik do przechowywania wartości skojarzone z parametry wymienne skryptu mapy zastąpienia. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów do zastąpienia, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj **NULL** wartość domyślna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `CAtlModule::UpdateRegistryFromResourceS` tworzy statyczne łącze do składnik rejestru Alt (Rejestrator).  
  
## <a name="see-also"></a>Zobacz też  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)   
 [Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)  
