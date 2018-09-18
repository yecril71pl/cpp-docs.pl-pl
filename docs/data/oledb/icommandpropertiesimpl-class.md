---
title: Icommandpropertiesimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
- SetProperties
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b31a023e39241a5393fbb9f36177ca42f88fd57e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070902"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl — Klasa

Udostępnia implementację [ICommandProperties](/previous-versions/windows/desktop/ms723044\(v=vs.85\)) interfejsu.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Klasy pochodzące z  
  
*PropClass*<br/>
Właściwości klasy.  

## <a name="requirements"></a>Wymagania  

**Nagłówek:** atldb.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="interface-methods"></a>Metody interfejsu  
  
|||  
|-|-|  
|[Getproperties —](#getproperties)|Zwraca listę właściwości grupy właściwości zestawu wierszy, które obecnie są żądane w zestawie wierszy.|  
|[Setproperties —](#setproperties)|Ustawia właściwości w grupie właściwość zestawu wierszy.|  
  
## <a name="remarks"></a>Uwagi  

Jest to parametr obowiązkowy dla polecenia. Implementacja jest dostarczany przez funkcję statyczną, zdefiniowane przez [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) makra.  

## <a name="getproperties"></a> ICommandPropertiesImpl::GetProperties

Zwraca wszystkie zestawy żądanej właściwości z użyciem mapowania właściwości polecenia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ICommandProperties::GetProperties](/previous-versions/windows/desktop/ms723119\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
### <a name="remarks"></a>Uwagi  

Zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="setproperties"></a> ICommandPropertiesImpl::SetProperties

Ustawia właściwości dla obiektu polecenia.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobacz [ICommandProperties::SetProperties](/previous-versions/windows/desktop/ms711497\(v=vs.85\)) w *OLE DB Podręcznik programisty*.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)