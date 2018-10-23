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
ms.openlocfilehash: 4a17ff7e6e78b21267b71ba495ba10a98e29cfe7
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808858"
---
# <a name="output-parameters"></a>Parametry wyjściowe

Wywoływanie procedury składowanej jest podobne do polecenia SQL. Główna różnica polega na czy procedury składowane parametry danych wyjściowych (lub "outparameters") i wartości zwracane.

W poniższym procedurą składowaną, pierwszego "?"jest zwracana wartość (telefon), a druga"?" jest parametr wejściowy (nazwa):

```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  

Należy określić w i parametrów out w mapie parametru:

```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter
END_PARAM_MAP()  
```  

Twoja aplikacja musi obsłużyć dane wyjściowe zwrócone z procedury składowane. Różnych dostawców OLE DB wróć parametrów wyjściowych i wartości zwracane w różnym czasie podczas przetwarzania wyników. Na przykład dostawca Microsoft OLE DB dla programu SQL Server (SQLOLEDB) nie podać parametry wyjściowe i zwrócić kody aż po użytkownik ma pobrać lub anulowane zestawy wyników zwrócone przez procedurę składowaną. Wynik jest zwracany w ostatnim pakiecie TDS z serwera.

## <a name="row-count"></a>Liczba wierszy

Jeśli używasz szablony OLE DB odbiorców do wykonania procedury przechowywanej, która ma outparameters liczba wierszy nie jest ustawiona, dopóki nie zamkniesz zestawu wierszy.

Na przykład należy wziąć pod uwagę procedury składowanej przy użyciu zestawu wierszy i outparameter:

```sql
create procedure sp_test
   @_rowcount integer output
as
   select top 50 * from test
   @_rowcount = @@rowcount
return 0
```  

\@_Rowcount outparameter raporty zwróconych liczbę wierszy z tabeli testu. Jednakże tę procedurę składowaną ogranicza liczbę wierszy do 50. Na przykład jeśli wystąpiły 100 wierszy w teście, rowcount będzie 50, (ponieważ ten kod pobiera tylko pierwszych 50 wierszy). Jeśli tylko 30 wierszy w tabeli, rowcount byłoby 30. Pamiętaj wywołać `Close` lub `CloseAll` do wypełniania outparameter, aby pobrać jego wartość.

## <a name="see-also"></a>Zobacz też

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)