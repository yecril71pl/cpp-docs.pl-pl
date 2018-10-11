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
ms.openlocfilehash: 34daf1f1c8624206070c73c9f012192c8b3dec66
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082634"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl — Klasa

Udostępnia implementację [ISessionProperties](/previous-versions/windows/desktop/ms713721) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Z klasą pochodną `ISessionPropertiesImpl`.  
  
*PropClass*<br/>
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

Zobacz [ISessionProperties::GetProperties](/previous-versions/windows/desktop/ms723643) w *OLE DB Podręcznik programisty*. 

## <a name="setproperties"></a> ISessionPropertiesImpl::SetProperties

Ustawia właściwości w `DBPROPSET_SESSION` grupy właściwości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ISessionProperties::SetProperties](/previous-versions/windows/desktop/ms714405) w *OLE DB Podręcznik programisty*.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)