---
title: CSchemata, CSchemataInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEFAULT_CHARACTER_SET_CATALOG
- DEFAULT_CHARACTER_SET_SCHEMA
- m_szCharName
- CSchemataInfo
- m_szCatalog
- m_szCharCatalog
- m_szOwner
- m_szCharSchema
- CSchemata
- m_szName
- DEFAULT_CHARACTER_SET_NAME
dev_langs: C++
helpviewer_keywords:
- m_szCharName
- CSchemata typedef class
- DEFAULT_CHARACTER_SET_NAME
- m_szOwner
- CSchemataInfo parameter class
- DEFAULT_CHARACTER_SET_CATALOG
- m_szCharSchema
- m_szCatalog
- m_szName
- m_szCharCatalog
- DEFAULT_CHARACTER_SET_SCHEMA
ms.assetid: 9d06d65a-c27b-446d-bc42-c7e487b0d9c5
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1171117cba0d4a6448326d6e45d455557d9442b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cschemata-cschematainfo"></a>CSchemata, CSchemataInfo
Call — klasa typedef **CSchemata** do zaimplementowania w klasie parametru **CSchemataInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje schematów, które są należących do danego użytkownika.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [zestawu wierszy SCHEMATU](https://msdn.microsoft.com/en-us/library/ms716887.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szCatalog|CATALOG_NAME|  
|m_szName|SCHEMA_NAME|  
|m_szOwner|SCHEMA_OWNER|  
|m_szCharCatalog|DEFAULT_CHARACTER_SET_CATALOG|  
|m_szCharSchema|DEFAULT_CHARACTER_SET_SCHEMA|  
|m_szCharName|DEFAULT_CHARACTER_SET_NAME|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRestrictions](../../data/oledb/crestrictions-class.md)