---
title: Transakcja (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376411"
---
# <a name="transaction-odbc"></a>Transakcja (ODBC)

Ten temat dotyczy klas MFC ODBC.

Transakcja jest sposobem na grupowanie lub partii, serii aktualizacji do [źródła danych,](../../data/odbc/data-source-odbc.md) tak aby wszystkie są zatwierdzone na raz lub żadne są zatwierdzone, jeśli wycofasz transakcję. Jeśli transakcja nie jest używana, zmiany w źródle danych są zatwierdzane automatycznie, a nie są zatwierdzane na żądanie.

> [!NOTE]
> Nie wszystkie sterowniki bazy danych ODBC obsługują transakcje. Wywołanie `CanTransact` funkcji elementu członkowskiego [CDatabase](../../mfc/reference/cdatabase-class.md) lub [CRecordset](../../mfc/reference/crecordset-class.md) obiektu, aby ustalić, czy sterownik obsługuje transakcje dla danej bazy danych. Należy `CanTransact` zauważyć, że nie informuje, czy źródło danych zapewnia pełną obsługę transakcji. Należy również `CDatabase::GetCursorCommitBehavior` wywołać `CommitTrans` `Rollback` i `CDatabase::GetCursorRollbackBehavior` po i sprawdzić wpływ `CRecordset` transakcji na otwarty obiekt.

Wywołania `AddNew` funkcji `Edit` i członków `CRecordset` obiektu wpływają na źródło `Update`danych natychmiast po wywołaniu . `Delete`połączenia również natychmiast zaachują. Natomiast można użyć transakcji składającej się `AddNew`z `Edit` `Update`wielu `Delete`wywołań do , , i `CommitTrans` , które są wykonywane, ale nie są zatwierdzone, dopóki nie zadzwonisz jawnie. Ustanawiając transakcję, można wykonać serię takich wywołań przy zachowaniu możliwości ich wycofania. Jeśli zasób krytyczny jest niedostępny lub inny warunek uniemożliwia ukończenie całej transakcji, można wycofać transakcję zamiast jej zatwierdzania. W takim przypadku żadna ze zmian należących do transakcji nie wpływa na źródło danych.

> [!NOTE]
> Obecnie klasa `CRecordset` nie obsługuje aktualizacji źródła danych, jeśli zaimplementowano pobieranie wiersza zbiorczego. Oznacza to, że `AddNew`nie `Edit` `Delete`można `Update`wykonywać połączeń do , , , lub . Można jednak napisać własne funkcje do wykonywania aktualizacji, a następnie wywołać te funkcje w ramach danej transakcji. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Oprócz wpływu na zestawie rekordów, transakcje wpływają na instrukcje SQL, które są wykonywane `CDatabase` bezpośrednio, o ile używasz ODBC **HDBC** skojarzonego z obiektem lub ODBC **HSTMT** na podstawie tego **HDBC**.

Transakcje są szczególnie przydatne, gdy masz wiele rekordów, które muszą być aktualizowane jednocześnie. W takim przypadku chcesz uniknąć transakcji w połowie zakończone, takie jak może się zdarzyć, jeśli wyjątek został zgłoszony przed ostatnią aktualizacją została wykonana. Grupowanie takich aktualizacji w transakcji umożliwia odzyskiwanie (wycofywanie) ze zmian i zwraca rekordy do stanu pretransakcji. Na przykład, jeśli bank przelewa pieniądze z konta A na konto B, zarówno wypłata z A, jak i depozyt na B muszą zakończyć się pomyślnie, aby prawidłowo przetworzyć środki lub cała transakcja musi zakończyć się niepowodzeniem.

W klasach bazy danych można `CDatabase` wykonywać transakcje za pośrednictwem obiektów. Obiekt `CDatabase` reprezentuje połączenie ze źródłem danych, a co najmniej `CDatabase` jeden zestaw rekordów skojarzony z tym obiektem działa w tabelach bazy danych za pośrednictwem funkcji elementu członkowskiego zestawu rekordów.

> [!NOTE]
> Obsługiwany jest tylko jeden poziom transakcji. Nie można zagnieżdżać transakcji ani transakcji obejmują wiele obiektów bazy danych.

Następujące tematy zawierają więcej informacji na temat sposobu wykonywania transakcji:

- [Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
