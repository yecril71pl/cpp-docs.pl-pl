---
title: Definiowanie procedur składowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1e03a5ae2e7c75d905216a6be92630376484d047
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101305"
---
# <a name="defining-stored-procedures"></a>Definiowanie procedur składowanych
Przed wywołaniem procedury składowanej, należy najpierw zdefiniować, za pomocą [DEFINE_COMMAND](../../data/oledb/define-command.md) makra. Podczas definiowania polecenia oznaczenia parametrów znakiem zapytania (?) jako znacznik parametru:  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Należy pamiętać, że składnia (Użyj nawiasów klamrowych i tak dalej), przykłady kodu, w tym temacie dotyczą programu SQL Server. Składni używanej w sieci procedur składowanych mogą się różnić w zależności od dostawcy, którego używasz.  
  
 Następnie w planie parametr należy określić parametry, których można użyć w poleceniu, listą parametrów w kolejności występowania w poleceniu:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 Poprzedni przykład definiuje procedury składowanej, ponieważ przechodzi ona. Zazwyczaj wydajne ponowne kodu, bazy danych zawiera zestaw wstępnie zdefiniowanych procedur składowanych z nazwy, takie jak "Sprzedaży przez rok" lub "dt_adduserobject." Można wyświetlić ich definicje programu SQL Server Enterprise Manager. Należy wywołać je w następujący sposób (położenie '?' parametrów zależy od interfejsu procedury składowanej):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 Następnie należy zadeklarować klasy polecenia:  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 Na koniec wywołać procedury składowanej `OpenRowset` w następujący sposób:  
  
```  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 Należy również zauważyć, który można zdefiniować procedury składowanej przy użyciu atrybutu bazy danych [db_command —](../../windows/db-command.md) w następujący sposób:  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)