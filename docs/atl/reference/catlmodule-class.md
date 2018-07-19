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
ms.openlocfilehash: 5291ae4783e252341371844ca08e390958c3ff89
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882575"
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
|[CAtlModule::AddTermFunc](#addtermfunc)|Dodaje nową funkcję wywoływana, gdy kończy się modułu.|  
|[CAtlModule::GetGITPtr](#getgitptr)|Zwraca wskaźnik interfejsu globalnego.|  
|[CAtlModule::GetLockCount](#getlockcount)|Zwraca liczbę blokad.|  
|[CAtlModule::Lock](#lock)|Zwiększa liczbę blokad.|  
|[CAtlModule::Term](#term)|Zwalnia wszystkie składowe danych.|  
|[CAtlModule::Unlock](#unlock)|Zmniejsza liczbę blokad.|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Ta metoda jest wywoływana `UpdateRegistryFromResourceD` wykonywania aktualizacji rejestru.|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu. Ta metoda statycznie łączy składnik rejestru ALT.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|Zawiera unikatowy identyfikator GUID bieżącego modułu.|  
|[CAtlModule::m_pGIT](#m_pgit)|Wskaźnik do tabeli interfejsu globalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest używana przez [klasa CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), [klasa CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), i [klasa CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) zapewnia obsługę biblioteki DLL, aplikacje, EXE i Windows usług, odpowiednio.  
  
 Aby uzyskać więcej informacji na temat modułów ATL, zobacz [klasy modułów ATL](../../atl/atl-module-classes.md).  
  
 Ta klasa zastępuje przestarzałe [klasa CComModule](../../atl/reference/ccommodule-class.md) stosowane we wcześniejszych wersjach ATL.  
  
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
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Parametry wymienne pozwalają rejestratora klientów określić dane czasu wykonywania. Aby to zrobić, Rejestrator przechowuje mapy zastąpienia, w którym wchodzi wartości skojarzone z parametry zmienne w skrypcie. Rejestrator sprawia, że te wpisy w czasie wykonywania.  
  
 Zobacz temat [przy użyciu zastępowalnych parametrów (Preprocesor rejestratora)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) Aby uzyskać więcej informacji.  
  
##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc  
 Dodaje nową funkcję wywoływana, gdy kończy się modułu.  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pFunc*  
 Wskaźnik do funkcji, które można dodać.  
  
 *Magazyn danych*  
 Danych zdefiniowane przez użytkownika, przekazana do funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
##  <a name="catlmodule"></a>  CAtlModule::CAtlModule  
 Konstruktor.  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje elementy członkowskie danych i inicjuje sekcję krytyczną wokół wątek modułu.  
  
##  <a name="dtor"></a>  CAtlModule:: ~ CAtlModule  
 Destruktor.  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie składowe danych.  
  
##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr  
 Pobiera wskaźnik do Tabela interfejsu globalnego.  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *ppGIT*  
 Wskaźnik do zmiennej, która zostanie wyświetlony wskaźnik, aby tabela interfejsu globalnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub kod błędu. E_POINTER jest zwracany, jeśli *ppGIT* jest równa NULL.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt Tabela interfejsu globalnego nie istnieje, jest ona tworzona i adresu jest przechowywany w zmiennej składowej [CAtlModule::m_pGIT](#m_pgit).  
  
 W kompilacjach debugowania, wystąpi błąd asercji Jeśli *ppGIT* jest równa NULL, lub jeśli nie można uzyskać wskaźnik Tabela interfejsu globalnego.  
  
 Zobacz [IGlobalInterfaceTable](http://msdn.microsoft.com/library/windows/desktop/ms678517) uzyskać informacji na temat Tabela interfejsu globalnego.  
  
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
 Zwiększa liczbę blokad i zwraca zaktualizowaną wartość. Ta wartość może być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="m_libid"></a>  CAtlModule::m_libid  
 Zawiera unikatowy identyfikator GUID bieżącego modułu.  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>  CAtlModule::m_pGIT  
 Wskaźnik do tabeli interfejsu globalnego.  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>  CAtlModule::Term  
 Zwalnia wszystkie składowe danych.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie składowe danych. Ta metoda jest wywoływana przez destruktor.  
  
##  <a name="unlock"></a>  CAtlModule::Unlock  
 Zmniejsza liczbę blokad.  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczbę blokad zmniejsza i zwraca zaktualizowaną wartość. Ta wartość może być przydatne w przypadku diagnostyki i debugowania.  
  
##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD  
 Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu.  
  
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
 *lpszRes*  
 Nazwa zasobu.  
  
 *nResID*  
 Identyfikator zasobu.  
  
 *bRegister*  
 Wartość TRUE, jeśli obiekt powinien zostać zarejestrowany; Wartość FALSE w przeciwnym razie.  
  
 *pMapEntries*  
 Wskaźnik do mapy zastąpienie przechowywania wartości skojarzone z parametrów zastępowalnych skryptu. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów zastępowalnych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Uruchamia skrypt zawarte w zasób określony przez *lpszRes lub nResID*. Jeśli *bRegister* ma wartość TRUE, ta metoda rejestruje obiekt w rejestrze systemowym; w przeciwnym razie usuwa obiekt z rejestru.  
  
 Aby statycznie połączyć składnik rejestru Alt (Rejestrator), zobacz [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Ta metoda wywołuje [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) i [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).  
  
##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper  
 Ta metoda jest wywoływana `UpdateRegistryFromResourceD` wykonywania aktualizacji rejestru.  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszRes*  
 Nazwa zasobu.  
  
 *bRegister*  
 Wskazuje, czy obiekt powinien zostać zarejestrowany.  
  
 *pMapEntries*  
 Wskaźnik do mapy zastąpienie przechowywania wartości skojarzone z parametrów zastępowalnych skryptu. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów zastępowalnych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia wykonania [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).  
  
##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS  
 Uruchamia skrypt zawarte w określonego zasobu, aby zarejestrować lub wyrejestrować obiektu. Ta metoda statycznie łączy składnik rejestru ALT.  
  
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
 *nResID*  
 Identyfikator zasobu.  
  
 *lpszRes*  
 Nazwa zasobu.  
  
 *bRegister*  
 Wskazuje, czy skrypt zasobu powinny być rejestrowane.  
  
 *pMapEntries*  
 Wskaźnik do mapy zastąpienie przechowywania wartości skojarzone z parametrów zastępowalnych skryptu. ATL automatycznie używa modułu %. Aby korzystać z dodatkowych parametrów zastępowalnych, zobacz [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). W przeciwnym razie użyj wartości domyślnej o wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) z wyjątkiem `CAtlModule::UpdateRegistryFromResourceS` tworzy statycznego linku do składnik rejestru Alt (Rejestrator).  
  
## <a name="see-also"></a>Zobacz też  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)   
 [Składnik rejestru (Rejestrator)](../../atl/atl-registry-component-registrar.md)  
