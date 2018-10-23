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
ms.openlocfilehash: 769f2bf2c0ef6c2c92b4c0468569e91d399cea59
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808449"
---
# <a name="defining-stored-procedures"></a>Definiowanie procedur składowanych

Przed wywołaniem procedury składowanej, należy najpierw zdefiniować, za pomocą [DEFINE_COMMAND](../../data/oledb/define-command.md) makra. Podczas definiowania polecenia oznaczenia parametry znakiem zapytania (?) jako znacznik parametru:  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
Składnia (Użyj nawiasów klamrowych i tak dalej), przykłady kodu, w tym temacie jest specyficzne dla programu SQL Server. Składnia używanego w przechowywanych procedur może się różnić zależnie od dostawcy, których używasz.  
  
Następnie w mapie parametr należy określić parametry, używane w poleceniu listą parametrów w kolejności występowania w poleceniu:  
  
```cpp  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
Poprzedni przykład definiuje procedury składowanej, ponieważ przechodzi ona. Zwykle wydajność ponownego użycia kodu, bazy danych zawiera zestaw wstępnie zdefiniowanych procedur składowanych z nazwy, takie jak "Sprzedaż według roku" lub "dt_adduserobject." Można wyświetlić ich definicji przy użyciu programu SQL Server Enterprise Manager. Wywoływania ich w następujący sposób (umieszczanie '?' parametry są zależne od interfejsu procedury składowanej):  
  
```cpp  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
Następnie można zadeklarować klasy poleceń:  
  
```cpp  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
Na koniec wywołaj procedurę składowaną `OpenRowset` w następujący sposób:  
  
```cpp  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
Należy również zauważyć, który można zdefiniować procedurę składowaną, za pomocą atrybutów bazy danych [db_command —](../../windows/db-command.md) w następujący sposób:  
  
```cpp  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Zobacz też  

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)