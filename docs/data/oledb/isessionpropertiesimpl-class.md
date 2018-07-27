---
title: Isessionpropertiesimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3759b67ef5d9ee9832649b3b0d516dbfb04440b
ms.sourcegitcommit: e5792fcb89b9ba64c401f90f4f26a8e45d4a2359
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2018
ms.locfileid: "39322023"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl — Klasa
Udostępnia implementację [ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Z klasą pochodną `ISessionPropertiesImpl`.  
  
 *PropClass*  
 Klasa definiowanych przez użytkownika właściwości, która domyślnie *T*.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Getproperties —](#getproperties)|Zwraca listę właściwości, w grupie właściwości sesji, które obecnie są ustawiane w sesji.|  
|[Setproperties —](#setproperties)|Ustawia właściwości w grupie właściwości sesji.|  
  
## <a name="remarks"></a>Uwagi  
 Obowiązkowego interfejsu w ramach sesji. Ta klasa implementuje właściwości sesji przez wywołanie statycznego funkcją zdefiniowaną przez [Mapa zestawu właściwości](../../data/oledb/begin-propset-map.md). Mapa zestawu właściwości powinny być określone w swojej klasy sesji.  
  
## <a name="getproperties"></a> ISessionPropertiesImpl::GetProperties
Zwraca listę wszystkich właściwości w `DBPROPSET_SESSION` grupy właściwości, które obecnie są ustawiane w sesji.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetProperties)(ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ISessionProperties::GetProperties](https://msdn.microsoft.com/library/ms723643.aspx) w *OLE DB Podręcznik programisty*. 

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties
Ustawia właściwości w `DBPROPSET_SESSION` grupy właściwości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [ISessionProperties::SetProperties](https://msdn.microsoft.com/library/ms714405.aspx) w *OLE DB Podręcznik programisty*.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
