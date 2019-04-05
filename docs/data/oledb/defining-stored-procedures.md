---
title: Definiowanie procedur składowanych
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
ms.openlocfilehash: 0f4c4ad84abf2a5de2cdf09e7064396ea01eeebe
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035049"
---
# <a name="defining-stored-procedures"></a>Definiowanie procedur składowanych

Przed wywołaniem procedury składowanej, należy najpierw zdefiniować, za pomocą [DEFINE_COMMAND](../../data/oledb/define-command.md) makra. Podczas definiowania polecenia oznaczenia parametry znakiem zapytania (?) jako znacznik parametru:

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{INSERT {name, phone} INTO shippers (?,?)}"))
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

Poprzedni przykład definiuje procedury składowanej, ponieważ przechodzi ona. Zazwyczaj do efektywnego ponownego użycia kodu, baza danych zawiera zestaw wstępnie zdefiniowanych procedur składowanych z nazwami takich jak `Sales by Year` lub `dt_adduserobject`. Można wyświetlić ich definicji przy użyciu programu SQL Server Enterprise Manager. Wywoływania ich w następujący sposób (umieszczanie *?* Parametry są zależne od interfejsu procedura składowana):

```cpp
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }"))
DEFINE_COMMAND_EX(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }"))
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

## <a name="see-also"></a>Zobacz także

[korzystanie z procedur składowanych](../../data/oledb/using-stored-procedures.md)