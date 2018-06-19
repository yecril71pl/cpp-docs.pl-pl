---
title: CViewTableUsage, CViewTableInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- m_szCatalog
- CViewTableInfo
- m_szTableCatalog
- m_szSchema
- m_szTableName
- m_szName
- CViewTableUsage
dev_langs:
- C++
helpviewer_keywords:
- CViewTableInfo parameter class
- CViewTableUsage typedef class
- m_szSchema
- m_szTableSchema
- TABLE_CATALOG
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- m_szName
- m_szTableCatalog
- m_szTableName
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b66c159e2825884ef59fbfb278b5eddd99d38c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100567"
---
# <a name="cviewtableusage-cviewtableinfo"></a>CViewTableUsage, CViewTableInfo
Call — klasa typedef **CViewTableUsage** do zaimplementowania w klasie parametru **CViewTableInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje wyświetlane tabel, zdefiniowanych w katalogu, które są dostępne dla danego użytkownika.  
  
 W poniższej tabeli wymieniono klasy elementów członkowskich danych i OLE DB kolumny. Zobacz [wierszy VIEW_TABLE_USAGE](https://msdn.microsoft.com/en-us/library/ms719727.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szCatalog|VIEW_CATALOG|  
|m_szSchema|VIEW_SCHEMA|  
|m_szName|VIEW_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRestrictions, klasa](../../data/oledb/crestrictions-class.md)