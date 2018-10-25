---
title: Parametry wyjściowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: d37cd1cd1facbdba1aeb4c8bc7f655bc3df954c0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073022"
---
# <a name="output-parameters"></a>Parametry wyjściowe

Wywoływanie procedury składowanej jest podobne do polecenia SQL. Główna różnica polega na czy procedury składowane parametry danych wyjściowych (lub "outparameters") i wartości zwracane.

W poniższym procedurą składowaną, pierwszego "?"jest zwracana wartość (telefon), a druga"?" jest parametr wejściowy (nazwa):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }"))
```

Należy określić w i parametrów out w mapie parametru:

```cpp
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

`@_rowcount` Outparameter raporty zwróconych liczbę wierszy z tabeli testu. Jednakże tę procedurę składowaną ogranicza liczbę wierszy do 50. Na przykład jeśli wystąpiły 100 wierszy w teście, rowcount będzie 50, (ponieważ ten kod pobiera tylko pierwszych 50 wierszy). Jeśli tylko 30 wierszy w tabeli, rowcount byłoby 30. Pamiętaj wywołać `Close` lub `CloseAll` do wypełniania outparameter, aby pobrać jego wartość.

## <a name="see-also"></a>Zobacz też

[Korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)