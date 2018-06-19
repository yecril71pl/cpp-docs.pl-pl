---
title: CUsagePrivileges, CUsagePrivilegeInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2dd118f4f841ad2c443ca2ed8dcc9d61afd6eb18
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101266"
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