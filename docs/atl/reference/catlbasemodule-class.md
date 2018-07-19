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
ms.openlocfilehash: a0bb470030984f83eaf7949f0889546129e96c40
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880771"
---
# <a name="catlbasemodule-class"></a>Klasa CAtlBaseModule
Ta klasa jest tworzone w każdym projekcie ATL.  
  
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
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Dodaje wystąpienie zasobu do listy przechowywanych uchwyty.|  
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Zwraca uchwyt do wystąpienia określonego zasobu.|  
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.|  
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Zwraca wystąpienie zasobu z `CAtlBaseModule` obiektu.|  
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Usuwa wystąpienia zasobu z listy przechowywanych uchwyty.|  
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Zmienna, która wskazuje, czy wystąpiło niepowodzenie inicjowania modułu.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie `CAtlBaseModule` nazwane _AtlBaseModule znajduje się w każdy Projekt ATL, zawierający dojścia do wystąpienia modułu, dojścia do modułu zawierającego zasoby, (które domyślnie są takie same), a tablica dojść do modułów, podając podstawowe zasoby. `CAtlBaseModule` bezpiecznie możliwy z wielu wątków.  
  
 Ta klasa zastępuje przestarzałe [CComModule](../../atl/reference/ccommodule-class.md) klasy stosowane we wcześniejszych wersjach ATL.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)  
  
 `CAtlBaseModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="addresourceinstance"></a>  CAtlBaseModule::AddResourceInstance  
 Dodaje wystąpienie zasobu do listy przechowywanych uchwyty.  
  
```
bool AddResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hInst*  
 Wystąpienie zasobu do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli zasób został pomyślnie dodany, wartość false w przeciwnym razie.  
  
##  <a name="catlbasemodule"></a>  CAtlBaseModule::CAtlBaseModule  
 Konstruktor.  
  
```
CAtlBaseModule() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Tworzy `CAtlBaseModule`.  
  
##  <a name="gethinstanceat"></a>  CAtlBaseModule::GetHInstanceAt  
 Zwraca uchwyt do wystąpienia określonego zasobu.  
  
```
HINSTANCE GetHInstanceAt(int i) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *i*  
 Liczba wystąpień zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt wystąpienia zasobu lub wartość NULL, jeśli nie ma odpowiednich wystąpień zasobu.  
  
##  <a name="getmoduleinstance"></a>  CAtlBaseModule::GetModuleInstance  
 Zwraca wystąpienie modułu z `CAtlBaseModule` obiektu.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie modułu.  
  
##  <a name="getresourceinstance"></a>  CAtlBaseModule::GetResourceInstance  
 Zwraca wystąpienie zasobu.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie zasobu.  
  
##  <a name="m_binitfailed"></a>  CAtlBaseModule::m_bInitFailed  
 Zmienna, która wskazuje, czy wystąpiło niepowodzenie inicjowania modułu.  
  
```
static bool m_bInitFailed;
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość true, jeśli moduł zainicjowany, wartość false, jeśli nie można zainicjować.  
  
##  <a name="removeresourceinstance"></a>  CAtlBaseModule::RemoveResourceInstance  
 Usuwa wystąpienia zasobu z listy przechowywanych uchwyty.  
  
```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hInst*  
 Wystąpienie zasobu do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli zasób został pomyślnie usunięty, wartość false w przeciwnym razie.  
  
##  <a name="setresourceinstance"></a>  CAtlBaseModule::SetResourceInstance  
 Ustawia wystąpienia zasobu `CAtlBaseModule` obiektu.  
  
```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hInst*  
 Nowe wystąpienie zasobu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wystąpienie zaktualizowanego zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasy modułów](../../atl/atl-module-classes.md)
