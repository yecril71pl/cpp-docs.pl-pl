---
title: Klasa CComAutoThreadModule | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
dev_langs: C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 094d10069b854d122e835f7d12f9ef095775db2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomautothreadmodule-class"></a>Klasa CComAutoThreadModule
Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadAllocator`  
 [in] Klasa zarządzania wyboru wątku. Wartość domyślna to [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateInstance](#createinstance)|Wybiera wątku, a następnie tworzy obiekt w apartamencie skojarzone.|  
|[GetDefaultThreads](#getdefaultthreads)|(Statyczny) Dynamicznie oblicza liczbę wątków dla modułu na podstawie liczby procesorów.|  
|[Init](#init)|Tworzy moduł wątków.|  
|[Blokady](#lock)|Zwiększa liczbę blokad modułu i w bieżącym wątku.|  
|[Odblokowywanie](#unlock)|Zmniejsza liczbę blokad modułu i w bieżącym wątku.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|Zawiera identyfikator bieżącego wątku.|  
|[m_Allocator](#m_allocator)|Zarządza wyboru wątku.|  
|[m_nThreads](#m_nthreads)|Zawiera liczbę wątków w module.|  
|[m_pApartments](#m_papartments)|Zarządza apartamentach modułu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta klasa jest przestarzała, zastąpione przez [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) i [CAtlModule](../../atl/reference/catlmodule-class.md) klas pochodnych. Informacje poniżej jest przeznaczona dla starszych wersji ATL.  
  
 `CComAutoThreadModule`pochodną [ccommodule —](../../atl/reference/ccommodule-class.md) do zaimplementowania wątków w puli, modelu typu apartment serwer COM dla usług plików exe i systemu Windows. `CComAutoThreadModule`używa [CComApartment](../../atl/reference/ccomapartment-class.md) do zarządzania apartamentu dla każdego wątku w module.  
  
 Pochodzi z modułu `CComAutoThreadModule` umożliwia tworzenie obiektów w wielu apartamentach. Należy również uwzględnić pozycje [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu, aby określić [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako fabryki klasy.  
  
 Domyślnie uzyskanie modułu z kreatorami AppWizard COM ATL (Kreator projektu ATL w programie Visual Studio .NET) `CComModule`. Aby użyć `CComAutoThreadModule`, należy zmodyfikować definicję klasy. Na przykład:  
  
 [!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [Ccommodule —](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="createinstance"></a>CComAutoThreadModule::CreateInstance  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>Parametry  
 *pfnCreateInstance*  
 [in] Wskaźnik do funkcji creator.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID żądanego interfejsu.  
  
 `ppvObj`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObj` jest równa NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Wybiera wątku, a następnie tworzy obiekt w apartamencie skojarzone.  
  
##  <a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>Uwagi  
 Zawiera identyfikator bieżącego wątku.  
  
##  <a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wątków, które mogą być tworzone w EXE module.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja statyczna dynamicznie oblicza maksymalną liczbę wątków dla modułu EXE, na podstawie liczby procesorów. Domyślnie ta wartość zwrotna jest przekazywana do [Init](#init) metodę w celu utworzenia wątki.  
  
##  <a name="init"></a>CComAutoThreadModule::Init  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] Wskaźnik do tablicy wpisów map obiekt.  
  
 `h`  
 [in] `HINSTANCE` Przekazany do **DLLMain** lub `WinMain`.  
  
 `plibid`  
 [in] Wskaźnik do identyfikatora LIBID biblioteki typów skojarzony z projektem.  
  
 `nThreads`  
 [in] Liczba wątków, które ma zostać utworzony. Domyślnie `nThreads` jest wartość zwrócona przez [GetDefaultThreads](#getdefaultthreads).  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje elementów członkowskich danych i tworzy liczbę wątków, określony przez `nThreads`.  
  
##  <a name="lock"></a>CComAutoThreadModule::Lock  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
### <a name="remarks"></a>Uwagi  
 Dokonuje atomic zwiększając liczbę blokad modułu i bieżącego wątku. `CComAutoThreadModule`używa liczbę blokad modułu w celu określenia, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.  
  
##  <a name="m_allocator"></a>CComAutoThreadModule::m_Allocator  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>Uwagi  
 Obiekt zarządzania wyboru wątku. Domyślnie `ThreadAllocator` parametr szablonu klasy jest [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
##  <a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>Uwagi  
 Zawiera liczbę wątków w EXE module. Gdy [Init](#init) jest nazywany `m_nThreads` ustawiono `nThreads` wartość parametru. Apartamentu skojarzone każdy wątek jest zarządzana przez [CComApartment](../../atl/reference/ccomapartment-class.md) obiektu.  
  
##  <a name="m_papartments"></a>CComAutoThreadModule::m_pApartments  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>Uwagi  
 Wskazuje tablicę [CComApartment](../../atl/reference/ccomapartment-class.md) obiektów, z których każdy zarządza typu apartment w module. Liczba elementów w tablicy jest oparta na [m_nThreads](#m_nthreads) elementu członkowskiego.  
  
##  <a name="unlock"></a>CComAutoThreadModule::Unlock  
 Począwszy od ATL 7.0 `CComAutoThreadModule` jest przestarzała: zobacz [klasy modułów ALT](../../atl/atl-module-classes.md) więcej szczegółów.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która może być przydatne w przypadku diagnostyki lub testowania.  
  
### <a name="remarks"></a>Uwagi  
 Dokonuje atomic zmniejszyć liczbę blokad modułu i bieżącego wątku. `CComAutoThreadModule`używa liczbę blokad modułu w celu określenia, czy wszyscy klienci uzyskują dostęp do modułu. Liczba blokad w bieżącym wątku jest używana do celów statystycznych.  
  
 Gdy liczbę blokad modułu do zera, moduł może być usunięty z pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
