---
title: CProcedures, CProcedureInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CProcedures
- m_szCatalog
- CProcedureInfo
- m_szSchema
- m_szDefinition
- m_szName
- m_nType
dev_langs:
- C++
helpviewer_keywords:
- DESCRIPTION class data member
- m_szSchema
- m_nType
- m_szCatalog
- CProcedureInfo parameter class
- m_szName
- m_szDescription
- m_szDefinition
- CProcedures typedef class
ms.assetid: d0c7375e-ee0c-441d-aae6-6108150860a0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac55323f3c3ed22c1cb90fdd2c2eb848b0fb9cd1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cprocedures-cprocedureinfo"></a>CProcedures, CProcedureInfo
Call — klasa typedef **CProcedures** do zaimplementowania w klasie parametru **CProcedureInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje procedury zdefiniowanych w katalogu, będące własnością danego użytkownika.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [wierszy procedury](https://msdn.microsoft.com/en-us/library/ms724021.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szCatalog|PROCEDURE_CATALOG|  
|m_szSchema|PROCEDURE_SCHEMA|  
|m_szName|PROCEDURE_NAME|  
|m_nType|PROCEDURE_TYPE|  
|m_szDefinition|PROCEDURE_DEFINITION|  
|m_szDescription|OPIS ELEMENTU|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRestrictions, klasa](../../data/oledb/crestrictions-class.md)