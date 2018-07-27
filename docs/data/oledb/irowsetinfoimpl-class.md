---
title: Irowsetinfoimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ccf4d6b34362d4c8b7875319af444f755d741e7
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322039"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl — Klasa
Udostępnia implementację na potrzeby [IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `IRowsetInfoImpl`.  
  
 *PropClass*  
 Klasa definiowanych przez użytkownika właściwości, która domyślnie *T*. 

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** altdb.h   
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Getproperties —](#getproperties)|Zwraca bieżące ustawienia właściwości wszystkich obsługiwanych przez zestaw wierszy.|  
|[Getreferencedrowset —](#getreferencedrowset)|Zwraca wskaźnik interfejsu do zestawu wierszy, do której stosują się zakładki.|  
|[Getspecification —](#getspecification)|Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs obowiązkowy zestawów wierszy. Ta klasa implementuje właściwości zestawu wierszy przy użyciu [Mapa zestawu właściwości](../../data/oledb/begin-propset-map.md) zdefiniowany w klasie polecenia. Mimo że klasy zestawu wierszy jest wyświetlane, można za pomocą właściwości klasy poleceń zestawy, zestaw wierszy jest dostarczany ze swoją własną kopią właściwości czasu wykonywania, po utworzeniu obiektu sesji lub polecenie.  
  
## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties
Zwraca bieżące ustawienia właściwości w `DBPROPSET_ROWSET` grupy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetInfo::GetProperties](https://msdn.microsoft.com/library/ms719611.aspx) w *OLE DB Podręcznik programisty*. 

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset
Zwraca wskaźnik interfejsu do zestawu wierszy, do której stosują się zakładki.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetInfo::GetReferencedRowset](https://msdn.microsoft.com/library/ms721145.aspx) w *OLE DB Podręcznik programisty*. *IOrdinal* parametr musi być kolumną zakładki. 

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification
Zwraca wskaźnik interfejsu na obiekcie (polecenie lub sesji), który utworzył ten zestaw wierszy.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IRowsetInfo::GetSpecification](https://msdn.microsoft.com/library/ms716746.aspx) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody za pomocą [igetdatasourceimpl —](../../data/oledb/igetdatasourceimpl-class.md) można pobrać właściwości z obiektu źródła danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
