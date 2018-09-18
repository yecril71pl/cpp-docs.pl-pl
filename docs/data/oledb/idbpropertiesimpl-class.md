---
title: Idbpropertiesimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c786783963bf2f3613228b87a7ede23eb75a450
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025597"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl — Klasa

Udostępnia implementację na potrzeby `IDBProperties` interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Z klasą pochodną `IDBPropertiesImpl`.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Getproperties —](#getproperties)|Zwraca wartości właściwości w grupach właściwości źródła danych, informacje o źródle danych i inicjowania, które są aktualnie ustawiony na obiekt źródła danych lub wartości właściwości w grupie właściwości inicjowania, które obecnie są ustawione na Moduł wyliczający.|  
|[GetPropertyInfo](#getpropertyinfo)|Zwraca informacje o wszystkich właściwości obsługiwane przez dostawcę.|  
|[Setproperties —](#setproperties)|Ustawia właściwości grupy właściwości źródła danych i inicjowanie, obiekty źródła danych lub grupie właściwości inicjowania dla modułów wyliczających.|  
  
## <a name="remarks"></a>Uwagi  

[IDBProperties](/previous-versions/windows/desktop/ms719607\(v=vs.85\)) obowiązkowego interfejsu dla obiekty źródła danych i opcjonalny interfejs dla modułów wyliczających. Jednakże jeśli moduł wyliczający udostępnia [IDBInitialize](/previous-versions/windows/desktop/ms713706\(v=vs.85\)), musi uwidaczniać `IDBProperties`. `IDBPropertiesImpl` implementuje `IDBProperties` przy użyciu statycznych funkcji zdefiniowanych przez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

## <a name="getproperties"></a> IDBPropertiesImpl::GetProperties

Zwraca wartości właściwości w grupach właściwości źródła danych, informacje o źródle danych i inicjowania, które są aktualnie ustawiony na obiekt źródła danych lub wartości właściwości w grupie właściwości inicjowania, które obecnie są ustawione na Moduł wyliczający.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IDBProperties::GetProperties](/previous-versions/windows/desktop/ms714344\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBProperties::GetProperties`:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
### <a name="remarks"></a>Uwagi  

Jeśli dostawca jest inicjowany, ta metoda zwraca wartości właściwości w DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT właściwości grupy, które są aktualnie ustawiony na obiekt źródła danych. Jeśli dostawca nie został zainicjowany, zwraca tylko właściwości grupy DBPROPSET_DBINIT. 
  
## <a name="getpropertyinfo"></a> IDBPropertiesImpl::GetPropertyInfo

Zwraca informacje o właściwościach obsługiwane przez źródło danych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IDBProperties::GetPropertyInfo](/previous-versions/windows/desktop/ms718175\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które są opisane w `IDBProperties::GetPropertyInfo`:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|*cPropertySets*|*cPropertyIDSets*|  
|*rgPropertySets*|*rgPropertyIDSets*|  
  
### <a name="remarks"></a>Uwagi  

Używa [IDBInitializeImpl::m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) do zaimplementowania tej funkcji. 

## <a name="setproperties"></a> IDBPropertiesImpl::SetProperties

Ustawia właściwości grupy właściwości źródła danych i inicjowanie, obiekty źródła danych lub grupie właściwości inicjowania dla modułów wyliczających.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [IDBProperties::SetProperties](/previous-versions/windows/desktop/ms723049\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  

Jeśli dostawca jest inicjowany, ta metoda ustawia wartości właściwości w DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO, DBPROPSET_DBINIT grupy właściwości dla obiektu źródła danych. Jeśli dostawca nie został zainicjowany, ustawia DBPROPSET_DBINIT tylko właściwości grupy.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)