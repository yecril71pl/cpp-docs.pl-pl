---
title: IDBPropertiesImpl::GetProperties | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
dev_langs: C++
helpviewer_keywords: GetProperties method
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac54b08dba170dd33d2e5e19cae50715aeab4fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idbpropertiesimplgetproperties"></a>IDBPropertiesImpl::GetProperties
Zwraca wartości właściwości w grupach właściwości źródła danych, informacje o źródle danych i inicjowania, aktualnie ustawione dla obiekt źródła danych lub wartości właściwości w grupie właściwości Initialization, które są aktualnie ustawione na Moduł wyliczający.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) w *OLE DB Podręcznik programisty*.  
  
 Niektóre parametry odpowiadają *OLE DB Podręcznik programisty* parametry różnych nazw, które zostały opisane w **IDBProperties::GetProperties**:  
  
|Parametry szablonu OLE DB|*OLE DB Podręcznik programisty* parametrów|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawca został zainicjowany, ta metoda zwraca wartości właściwości w **DBPROPSET_DATASOURCE**, **DBPROPSET_DATASOURCEINFO**, **DBPROPSET_DBINIT** właściwości grupy, które są aktualnie ustawione na obiekt źródła danych. Jeśli dostawca nie jest zainicjowany, zwraca **DBPROPSET_DBINIT** tylko właściwości grupy.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Idbpropertiesimpl — klasa](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)