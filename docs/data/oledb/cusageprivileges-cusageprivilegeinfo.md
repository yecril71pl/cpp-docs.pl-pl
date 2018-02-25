---
title: CUsagePrivileges, CUsagePrivilegeInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- m_szObjectCatalog
- CUsagePrivilegeInfo
- m_bIsGrantable
- OBJECT_NAME
- m_szPrivilegeType
- OBJECT_SCHEMA
- IS_GRANTABLE
- CUsagePrivileges
- m_szGrantor
- GRANTOR
- GRANTEE
- m_szObjectSchema
- OBJECT_CATALOG
- m_szObjectType
- m_szObjectName
- m_szGrantee
- OBJECT_TYPE
dev_langs:
- C++
helpviewer_keywords:
- OBJECT_NAME
- GRANTOR
- OBJECT_CATALOG
- CUsagePrivileges typedef class
- m_szPrivilegeType
- OBJECT_SCHEMA
- m_szObjectSchema
- m_szObjectType
- IS_GRANTABLE
- OBJECT_TYPE
- CUsagePrivilegeInfo parameter class
- m_szGrantee
- m_szObjectCatalog
- m_szGrantor
- GRANTEE
- m_bIsGrantable
- m_szObjectName
ms.assetid: 09460e7f-3947-4837-ad1e-407b94acedb8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5db871447d6de6554d7f7e6a555c195edc97498
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cusageprivileges-cusageprivilegeinfo"></a>CUsagePrivileges, CUsagePrivilegeInfo
Call — klasa typedef **CUsagePrivileges** do zaimplementowania w klasie parametru **CUsagePrivilegeInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje uprawnień użycia na obiektów zdefiniowanych w katalogu, które są dostępne lub przyznane przez określonego użytkownika.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [wierszy USAGE_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms722743.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szGrantor|CEDENT|  
|m_szGrantee|CESJONARIUSZ|  
|m_szObjectCatalog|OBJECT_CATALOG|  
|m_szObjectSchema|OBJECT_SCHEMA|  
|m_szObjectName|OBJECT_NAME|  
|m_szObjectType|OBJECT_TYPE|  
|m_szPrivilegeType|PRIVILEGE_TYPE|  
|m_bIsGrantable|IS_GRANTABLE|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRestrictions, klasa](../../data/oledb/crestrictions-class.md)