---
title: Klasa CAtlBaseModule | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
dev_langs:
- C++
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07f1252fe993ff2f2e646528996c1a53d25c5a63
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="catlbasemodule-class"></a>Klasa CAtlBaseModule
W każdym projekcie ATL tworzenia wystąpienia tej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlBaseModule : public _ATL_BASE_MODULE
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Dodaje wystąpienia zasobu do listy przechowywanej uchwytów.|  
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Zwraca dojście do wystąpienia określonego zasobu.|  
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.|  
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Zwraca wystąpienie zasobów z `CAtlBaseModule` obiektu.|  
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Usuwa wystąpienia zasobu z listy przechowywanych uchwytów.|  
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Zmienna, która wskazuje, czy Inicjowanie modułu nie powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `CAtlBaseModule` _AtlBaseModule o nazwie znajduje się w każdym projekcie ATL, zawierający dojścia do wystąpienia modułu, dojścia do modułu zawierającego zasoby (które domyślnie są tego samego), a tablica dojść do zapewnienia podstawowej modułów zasoby. `CAtlBaseModule` może być bezpiecznie uzyskać dostęp wiele wątków.  
  
 Ta klasa zastępuje przestarzałe [ccommodule —](../../atl/reference/ccommodule-class.md) klasy używany w starszych wersjach ATL.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)  
  
 `CAtlBaseModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance  
 Dodaje wystąpienia zasobu do listy przechowywanej uchwytów.  
  
```
bool AddResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Wystąpienie zasobu do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli zasób został pomyślnie dodany, wartość false w przeciwnym razie wartość.  
  
##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule  
 Konstruktor.  
  
```
CAtlBaseModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Tworzy `CAtlBaseModule`.  
  
##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt  
 Zwraca dojście do wystąpienia określonego zasobu.  
  
```
HINSTANCE GetHInstanceAt(int i) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *i*  
 Liczba wystąpienia zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście wystąpienia zasobu lub wartość NULL, jeśli nie ma odpowiedniego wystąpień zasobów.  
  
##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance  
 Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie modułu.  
  
##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance  
 Zwraca wystąpienie zasobów.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie zasobów.  
  
##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed  
 Zmienna, która wskazuje, czy Inicjowanie modułu nie powiodło się.  
  
```
static bool m_bInitFailed;
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość true, jeśli moduł został zainicjowany, false, jeśli nie można go zainicjować.  
  
##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance  
 Usuwa wystąpienia zasobu z listy przechowywanych uchwytów.  
  
```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Wystąpienie zasobu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli zasób został pomyślnie usunięty, wartość false w przeciwnym razie wartość.  
  
##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance  
 Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.  
  
```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hInst`  
 Nowe wystąpienie zasobów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie zaktualizowanego zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
