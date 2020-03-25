---
title: 'Zestaw rekordów: blokowanie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212865"
---
# <a name="recordset-locking-records-odbc"></a>Zestaw rekordów: blokowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie objaśniono:

- [Rodzaje blokowania rekordów dostępne](#_core_record.2d.locking_modes).

- [Jak blokować rekordy w zestawie rekordów podczas aktualizacji](#_core_locking_records_in_your_recordset).

W przypadku aktualizowania rekordu w źródle danych przy użyciu zestawu rekordów aplikacja może zablokować rekord, tak aby żaden inny użytkownik nie mógł zaktualizować rekordu w tym samym czasie. Stan rekordu aktualizowany przez dwóch użytkowników w tym samym czasie jest niezdefiniowany, chyba że system może zagwarantować, że dwóch użytkowników nie można jednocześnie zaktualizować rekordu.

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli zaimplementowano pobieranie wierszy zbiorczych, niektóre informacje nie są stosowane. Na przykład nie można wywołać `Edit` i `Update` funkcji Członkowskich. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Tryby blokowania rekordów

Klasy baz danych zapewniają dwa [tryby blokowania rekordów](../../mfc/reference/crecordset-class.md#setlockingmode):

- Optymistyczne blokowanie (wartość domyślna)

- Zablokowanie pesymistyczne

Aktualizacja rekordu odbywa się w trzech krokach:

1. Aby rozpocząć operację, należy wywołać funkcję [Edytuj](../../mfc/reference/crecordset-class.md#edit) element członkowski.

1. Zmienisz odpowiednie pola bieżącego rekordu.

1. Kończysz operację — i zazwyczaj zatwierdzasz aktualizację — przez wywołanie funkcji elementu członkowskiego [aktualizacji](../../mfc/reference/crecordset-class.md#update) .

Optymistyczne blokowanie blokuje rekord w źródle danych tylko podczas wywołania `Update`. Jeśli używasz optymistycznego blokowania w środowisku wielodostępnym, aplikacja powinna obsłużyć `Update` warunku niepowodzenia. Pesymistyczne blokowanie blokuje rekord zaraz po wywołaniu `Edit` i nie zwolni go do momentu wywołania `Update` (niepowodzenia są wskazywane przez mechanizm `CDBException` nie przez wartość FALSE zwracaną przez `Update`). Zablokowanie pesymistyczne ma potencjalną wydajność dla innych użytkowników, ponieważ współbieżny dostęp do tego samego rekordu może zaczekać, aż zakończy się proces `Update` aplikacji.

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Blokowanie rekordów w zestawie rekordów

Aby zmienić domyślny [tryb blokowania](#_core_record.2d.locking_modes) obiektu zestawu rekordów, należy zmienić tryb przed wywołaniem `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Aby zmienić bieżący tryb blokowania dla zestawu rekordów

1. Wywołaj funkcję elementu członkowskiego [Setlockmode](../../mfc/reference/crecordset-class.md#setlockingmode) określającą `CRecordset::pessimistic` lub `CRecordset::optimistic`.

Nowy tryb blokowania będzie obowiązywać, dopóki nie zostanie ponownie zmieniony lub zestaw rekordów zostanie zamknięty.

> [!NOTE]
>  Stosunkowo mało sterowniki ODBC obsługują obecnie pesymistyczne blokowanie.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
