---
title: CPrimaryKeys, CPrimaryKeyInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_nOrdinal
- m_szTableSchema
- m_nColumnPropID
- CPrimaryKeys
- COLUMN_GUID
- CPrimaryKeyInfo
- m_szColumnName
- m_szTableCatalog
- COLUMN_PROPID
- m_guidColumn
- ORDINAL
- m_szTableName
dev_langs: C++
helpviewer_keywords:
- COLUMN_PROPID
- m_szTableSchema
- TABLE_CATALOG
- ORDINAL data member
- CPrimaryKeys typedef class
- TABLE_NAME
- m_nColumnPropID
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szTableCatalog
- m_szTableName
- m_nOrdinal
- CPrimaryKeyInfo parameter class
- COLUMN_GUID
- m_guidColumn
ms.assetid: c27b97a4-a156-4f66-89e3-95f85d7d6281
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8733d83204f353c092997083eef6ca2d4159b2a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cprimarykeys-cprimarykeyinfo"></a>CPrimaryKeys, CPrimaryKeyInfo
Call — klasa typedef **CPrimaryKeys** do zaimplementowania w klasie parametru **CPrimaryKeyInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje kolumny klucza podstawowego, zdefiniowanych w katalogu przez danego użytkownika.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [wierszy PRIMARY_KEYS](https://msdn.microsoft.com/en-us/library/ms714362.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nOrdinal|LICZBA PORZĄDKOWA|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRestrictions](../../data/oledb/crestrictions-class.md)