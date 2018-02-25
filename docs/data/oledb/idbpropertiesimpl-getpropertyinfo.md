---
title: IDBPropertiesImpl::GetPropertyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
dev_langs:
- C++
helpviewer_keywords:
- GetPropertyInfo method
ms.assetid: 170e9640-5010-4e0d-8a54-f50b23af08ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa96d49ae5a0ac01d90d6f6c5a0efe020d7a5a3e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimplgetpropertyinfo"></a>IDBPropertiesImpl::GetPropertyInfo
Zwraca informacje dotyczące właściwości obsługiwanych przez źródło danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
      STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBProperties::GetPropertyInfo](https://msdn.microsoft.com/en-us/library/ms718175.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które zostały opisane w **IDBProperties::GetPropertyInfo**:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
  
## <a name="remarks"></a>Uwagi  
 Używa [IDBInitializeImpl::m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) do wykonania tej funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbpropertiesimpl — klasa](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)