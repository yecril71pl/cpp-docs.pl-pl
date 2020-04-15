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
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376422"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakcja: jak transakcje wpływają na aktualizacje (ODBC)

Aktualizacje [źródła danych](../../data/odbc/data-source-odbc.md) są zarządzane podczas transakcji za pomocą buforu edycji (ta sama metoda używana poza transakcjami). Elementy członkowskie danych pól zestawu rekordów służą łącznie jako bufor edycji zawierający bieżący rekord, który zestaw rekordów tymczasowo kopii zapasowej podczas `AddNew` lub . `Edit` Podczas `Delete` operacji bieżący rekord nie jest archiwizny w ramach transakcji. Aby uzyskać więcej informacji na temat buforu edycji i sposobu przechowywania bieżącego rekordu przez aktualizacje, zobacz [Tablica rekordów: Jak recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `AddNew`zbiorczego, nie można wywołać , `Edit`lub `Delete`. Zamiast tego należy napisać własne funkcje, aby wykonać aktualizacje do źródła danych. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Podczas transakcji `AddNew`, `Edit`i `Delete` operacje mogą być zatwierdzone lub wycofane. Skutki `CommitTrans` i `Rollback` może spowodować bieżący rekord nie zostanie przywrócony do buforu edycji. Aby upewnić się, że bieżący rekord jest prawidłowo `CommitTrans` przywrócony, ważne `CDatabase` jest, aby `CRecordset`zrozumieć, jak funkcje i `Rollback` element członkowski pracy z funkcjami aktualizacji programu .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Jak CommitTrans wpływa na aktualizacje

W poniższej tabeli `CommitTrans` wyjaśniono wpływ transakcji na transakcje.

### <a name="how-committrans-affects-updates"></a>Jak CommitTrans wpływa na aktualizacje

|Operacja|Stan źródła danych|
|---------------|---------------------------|
|`AddNew`i `Update`, a następnie`CommitTrans`|Nowy rekord jest dodawany do źródła danych.|
|`AddNew`(bez `Update`), a następnie`CommitTrans`|Nowy rekord jest tracony. Rekord nie został dodany do źródła danych.|
|`Edit`i `Update`, a następnie`CommitTrans`|Zmiany zatwierdzone do źródła danych.|
|`Edit`(bez `Update`), a następnie`CommitTrans`|Zmiany w rekordzie zostaną utracone. Rekord pozostaje niezmieniony w źródle danych.|
|`Delete`Następnie`CommitTrans`|Rekordy usunięte ze źródła danych.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Jak wycofywanie wpływa na transakcje

W poniższej tabeli `Rollback` wyjaśniono wpływ transakcji na transakcje.

### <a name="how-rollback-affects-transactions"></a>Jak wycofywanie wpływa na transakcje

|Operacja|Stan bieżącego rekordu|Należy również|Stan źródła danych|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`i `Update`, a następnie`Rollback`|Zawartość bieżącego rekordu jest tymczasowo przechowywana w celu udostępnienia miejsca na nowy rekord. Nowy rekord jest wprowadzany do buforu edycji. Po `Update` wywołaniu bieżącego rekordu zostanie przywrócony do buforu edycji.||Oprócz źródła danych `Update` wykonane przez jest odwrócony.|
|`AddNew`(bez `Update`), a następnie`Rollback`|Zawartość bieżącego rekordu jest tymczasowo przechowywana w celu udostępnienia miejsca na nowy rekord. Edytuj bufor zawiera nowy rekord.|Wywołanie `AddNew` ponownie, aby przywrócić bufor edycji do pustego, nowego rekordu. Lub `Move`wywołać (0), aby przywrócić stare wartości do buforu edycji.|Ponieważ `Update` nie został wywołany, nie wprowadzono żadnych zmian w źródle danych.|
|`Edit`i `Update`, a następnie`Rollback`|Nieedytowana wersja bieżącego rekordu jest tymczasowo przechowywana. Zmiany są dokonywane w zawartości buforu edycji. Po `Update` wywołaniu nieedytowana wersja rekordu jest nadal tymczasowo przechowywana.|*Dynaset*: Przewiń bieżący rekord, a następnie z powrotem, aby przywrócić nieedytowane wersje rekordu do buforu edycji.<br /><br /> *Migawka*: Wywołanie `Requery` odświeżenia zbioru rekordów ze źródła danych.|Zmiany w źródle `Update` danych wprowadzone przez są wycofywane.|
|`Edit`(bez `Update`), a następnie`Rollback`|Nieedytowana wersja bieżącego rekordu jest tymczasowo przechowywana. Zmiany są dokonywane w zawartości buforu edycji.|Wywołanie `Edit` ponownie, aby przywrócić nieedytowane wersji rekordu do buforu edycji.|Ponieważ `Update` nie został wywołany, nie wprowadzono żadnych zmian w źródle danych.|
|`Delete`Następnie`Rollback`|Zawartość bieżącego rekordu zostanie usunięta.|Wywołanie, `Requery` aby przywrócić zawartość bieżącego rekordu ze źródła danych.|Usunięcie danych ze źródła danych jest odwrócone.|

## <a name="see-also"></a>Zobacz też

[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[Klasa CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
