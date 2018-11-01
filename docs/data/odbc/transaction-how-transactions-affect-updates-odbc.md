---
title: 'Transakcja: jak transakcje wpływają na aktualizacje (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 68ff6970243b36b56ab206b16bb2c3608cef71e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437859"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakcja: jak transakcje wpływają na aktualizacje (ODBC)

Aktualizacje [źródła danych](../../data/odbc/data-source-odbc.md) odbywa się podczas transakcji za pomocą edycji buforu (tej samej metody poza transakcji). Elementy członkowskie danych pola zestawu rekordów zbiorczo służyć jako bufor edycji, który zawiera rekord bieżący zestaw rekordów, tworzy kopię zapasową tymczasowego podczas `AddNew` lub `Edit`. Podczas `Delete` operacji, bieżący rekord nie jest obsługiwane w obrębie transakcji. Aby uzyskać więcej informacji na temat buforu edycji i jak aktualizacje przechowywać bieżącego rekordu, zobacz [zestaw rekordów: jak zestawy rekordów uaktualniają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `AddNew`, `Edit`, lub `Delete`. Zamiast tego trzeba napisać własne funkcje do wykonywania aktualizacji do źródła danych. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Podczas transakcji `AddNew`, `Edit`, i `Delete` operacji może być przekazana lub wycofana. Efekty `CommitTrans` i `Rollback` może spowodować, że nie można przywrócić do usługi buffer Edytuj bieżący rekord. Aby upewnić się, że bieżący rekord zostaną prawidłowo przywrócone, jest ważne, aby zrozumieć sposób, w jaki `CommitTrans` i `Rollback` funkcje elementów członkowskich `CDatabase` działają z funkcji aktualizacji `CRecordset`.

##  <a name="_core_how_committrans_affects_updates"></a> Jak CommitTrans wpływa na aktualizacje

W poniższej tabeli opisano wpływ `CommitTrans` transakcji.

### <a name="how-committrans-affects-updates"></a>Jak CommitTrans wpływa na aktualizacje

|Operacja|Stan źródła danych|
|---------------|---------------------------|
|`AddNew` i `Update`, a następnie `CommitTrans`|Nowy rekord są dodawane do źródła danych.|
|`AddNew` (bez `Update`), a następnie `CommitTrans`|Nowy rekord zostaną utracone. Nie dodany rekord do źródła danych.|
|`Edit` i `Update`, a następnie `CommitTrans`|Edycja zatwierdzane do źródła danych.|
|`Edit` (bez `Update`), a następnie `CommitTrans`|Edytowanie rekordu zostaną utracone. Rekord pozostaje bez zmian w źródle danych.|
|`Delete` Następnie `CommitTrans`|Rekordy zostały usunięte ze źródła danych.|

##  <a name="_core_how_rollback_affects_updates"></a> Wpływ wycofywania transakcji

W poniższej tabeli opisano wpływ `Rollback` transakcji.

### <a name="how-rollback-affects-transactions"></a>Wpływ wycofywania transakcji

|Operacja|Stan bieżący rekord|Należy również|Stan źródła danych|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` i `Update`, następnie `Rollback`|Zawartość bieżącego rekordu są tymczasowo przechowywane w celu zwolnienia miejsca dla nowego rekordu. Nowy rekord jest wprowadzany do edycji buforu. Po `Update` jest wywoływana, bieżący rekord zostanie przywrócony do buforu edycji.||Dodawanie źródła danych wprowadzonych przez `Update` została odwrócona.|
|`AddNew` (bez `Update`), następnie `Rollback`|Zawartość bieżącego rekordu są tymczasowo przechowywane w celu zwolnienia miejsca dla nowego rekordu. Edytuj bufor zawiera nowy rekord.|Wywołaj `AddNew` ponownie, aby przywrócić buforu edycji pusty, nowy rekord. Lub zadzwoń `Move`(0), można przywrócić stare wartości w buforze edycji.|Ponieważ `Update` nie została wywołana nie wprowadzono żadnych zmian wprowadzonych do źródła danych.|
|`Edit` i `Update`, następnie `Rollback`|Bitu wersję bieżącego rekordu są tymczasowo przechowywane. Zmiany zostały wprowadzone do zawartości buforu edycji. Po `Update` jest wywoływana, bitu wersji rekordu jest nadal tymczasowo przechowywane.|*Zestaw dynamiczny*: przewiń poza bieżącym rekordzie, a następnie powrót do przywrócenia bitu wersji rekordu w buforze edycji.<br /><br /> *Migawka*: wywołanie `Requery` odświeżyć zestaw rekordów ze źródła danych.|Zmienia się ze źródłem danych wprowadzonych przez `Update` zostały cofnięte.|
|`Edit` (bez `Update`), następnie `Rollback`|Bitu wersję bieżącego rekordu są tymczasowo przechowywane. Zmiany zostały wprowadzone do zawartości buforu edycji.|Wywołaj `Edit` ponownie, aby przywrócić bitu wersję rekordu w buforze edycji.|Ponieważ `Update` nie została wywołana nie wprowadzono żadnych zmian wprowadzonych do źródła danych.|
|`Delete` Następnie `Rollback`|Zawartość bieżącego rekordu zostanie usunięta.|Wywołaj `Requery` Aby przywrócić zawartość bieżący rekord ze źródła danych.|Usunięcie danych ze źródła danych zostanie odwrócony.|

## <a name="see-also"></a>Zobacz też

[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)