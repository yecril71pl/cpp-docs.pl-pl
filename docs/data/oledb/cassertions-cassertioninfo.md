---
title: CAssertions, CAssertionInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAssertions
- m_szCatalog
- m_bInitiallyDeferred
- CONSTRAINT_NAME
- m_szSchema
- INITIALLY_DEFERRED
- m_bIsDeferrable
- m_szName
- CAssertionInfo
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- IS_DEFERRABLE
dev_langs:
- C++
helpviewer_keywords:
- CAssertionInfo parameter class
- DESCRIPTION class data member
- CAssertions typedef class
- IS_DEFERRABLE
- m_szSchema
- m_bInitiallyDeferred
- CONSTRAINT_CATALOG
- m_szCatalog
- CONSTRAINT_NAME
- CONSTRAINT_SCHEMA
- m_szName
- m_szDescription
- INITIALLY_DEFERRED
- m_bIsDeferrable
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6b3a114d4df8effe682798c966811be0eacc41e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094433"
---
# <a name="cassertions-cassertioninfo"></a>CAssertions, CAssertionInfo
Call — klasa typedef **CAssertions** do zaimplementowania w klasie parametru **CAssertionInfo**.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Aby uzyskać więcej informacji na temat używania klasy typedef.  
  
 Ta klasa identyfikuje potwierdzenia zdefiniowanych w katalogu, będące własnością danego użytkownika.  
  
 W poniższej tabeli wymieniono elementy danych klasy **CAssertionInfo** i OLE DB kolumny. Zobacz [wierszy potwierdzenia](https://msdn.microsoft.com/en-us/library/ms719776.aspx) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji o schemacie i kolumn.  
  
|Elementy członkowskie danych|Kolumny OLE DB|  
|------------------|--------------------|  
|m_szCatalog|CONSTRAINT_CATALOG|  
|m_szSchema|CONSTRAINT_SCHEMA|  
|m_szName|CONSTRAINT_NAME|  
|m_bIsDeferrable|IS_DEFERRABLE|  
|m_bInitiallyDeferred|INITIALLY_DEFERRED|  
|m_szDescription|OPIS ELEMENTU|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbsch.h  
  
## <a name="see-also"></a>Zobacz też  
 [CRestrictions, klasa](../../data/oledb/crestrictions-class.md)