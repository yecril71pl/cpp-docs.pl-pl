---
title: CProcedureColumns, CProcedureColumnInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_guidType
- CProcedureColumnInfo
- IS_NULLABLE
- m_szCatalog
- m_nRowsetNumber
- m_nColumnPropID
- ORDINAL_POSITION
- m_nOrdinalPosition
- COLUMN_GUID
- m_szColumnName
- NUMERIC_PRECISION
- m_nDataType
- m_szSchema
- CHARACTER_OCTET_LENGTH
- NUMERIC_SCALE
- COLUMN_PROPID
- m_guidColumn
- m_nMaxLength
- CHARACTER_MAXIMUM_LENGTH
- m_nPrecision
- m_szName
- CProcedureColumns
- DATA_TYPE
- m_nOctetLength
- m_bIsNullable
- m_nScale
dev_langs: C++
helpviewer_keywords:
- NUMERIC_PRECISION
- COLUMN_PROPID
- DATA_TYPE
- ORDINAL_POSITION
- m_nMaxLength
- DESCRIPTION class data member
- m_guidType
- m_szSchema
- CHARACTER_OCTET_LENGTH
- m_szCatalog
- CProcedureColumns typedef class
- m_nPrecision
- m_nOrdinalPosition
- m_nColumnPropID
- NUMERIC_SCALE
- m_nRowsetNumber
- m_szColumnName
- COLUMN_NAME
- m_nOctetLength
- IS_NULLABLE
- m_szName
- m_bIsNullable
- m_szDescription
- m_nDataType
- m_nScale
- COLUMN_GUID
- CHARACTER_MAXIMUM_LENGTH
- m_guidColumn
- CProcedureColumnInfo parameter class
ms.assetid: c82626c4-8047-4b9c-b342-e35bf37b7611
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e1262dc92f91541b092e3c5cca38b2fa5cbef5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cprocedurecolumns-cprocedurecolumninfo"></a>CProcedureColumns, CProcedureColumnInfo
Call — klasa typedef **CProcedureColumns** do zaimplementowania w klasie parametru **CProcedureColumnInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa zwraca informacje dotyczące kolumn zestawów wierszy zwracanych przez procedury.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [wierszy PROCEDURE_COLUMNS](https://msdn.microsoft.com/en-us/library/ms723092.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szCatalog|PROCEDURE_CATALOG|  
|m_szSchema|PROCEDURE_SCHEMA|  
|m_szName|PROCEDURE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nRowsetNumber|ROWSET_NUMBER|  
|m_nOrdinalPosition|ORDINAL_POSITION|  
|m_bIsNullable|IS_NULLABLE|  
|m_nDataType|DATA_TYPE|  
|m_guidType|TYPE_GUID|  
|m_nMaxLength|CHARACTER_MAXIMUM_LENGTH|  
|m_nOctetLength|CHARACTER_OCTET_LENGTH|  
|m_nPrecision|NUMERIC_PRECISION|  
|m_nScale|NUMERIC_SCALE|  
|m_szDescription|OPIS ELEMENTU|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CRestrictions](../../data/oledb/crestrictions-class.md)