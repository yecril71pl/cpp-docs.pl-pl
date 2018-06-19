---
title: Parametry wyjściowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8733b967ddab7e6f68fcbee1c80e78500a679f96
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104389"
---
# <a name="output-parameters"></a>Parametry wyjściowe
Wywołanie procedury składowanej jest podobny do wywoływania polecenia SQL. Główna różnica polega na czy procedury składowane za pomocą parametrów wyjściowych (lub "outparameters") i wartości zwracane.  
  
 Następujące przechowywane procedury, pierwszy '? "jest zwracana wartość (telefon), a drugi"? "jest parametr wejściowy (nazwa):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 I parametry wyjściowe można określić w mapowaniu parametru:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 Aplikacja musi obsługiwać dane wyjściowe zwrócone z procedury składowane. Różnych dostawców OLE DB zwracać parametrów wyjściowych i wartości zwracane w różnym czasie podczas przetwarzania wyników. Na przykład dostawcy Microsoft OLE DB dla programu SQL Server (SQLOLEDB) podać parametry wyjściowe i nie zwracać kody do po klienta ma pobrać lub anulowane zestawów wyników zwróconych przez procedurę składowaną. Wynik jest zwracany w ostatnim pakiecie TDS z serwera.  
  
## <a name="row-count"></a>Liczba wierszy  
 Jeśli używasz szablony OLE DB konsumentów do wykonania procedury przechowywanej, która ma outparameters liczba wierszy nie jest ustawiony do czasu zamknięcia zestawu wierszy.  
  
 Rozważmy na przykład procedury składowanej z zestawu wierszy i outparameter:  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @_rowcount Outparameter zgłasza liczbę wierszy zwróconych z tabeli testu. Jednak ta procedura składowana ogranicza liczbę wierszy do maksymalnie 50. Na przykład jeśli w teście 100 wierszy, rowcount byłoby 50, (ponieważ ten kod pobiera tylko 50 pierwszych wierszy). Jeśli jest tylko 30 wierszy w tabeli, rowcount byłoby 30. Należy wywołać **Zamknij** lub **CloseAll** do wypełnienia outparameter, aby pobrać jej wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)