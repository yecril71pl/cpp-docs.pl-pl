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
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366962"
---
# <a name="recordset-locking-records-odbc"></a>Zestaw rekordów: blokowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono:

- [Rodzaje blokowania rekordów dostępne](#_core_record.2d.locking_modes).

- [Jak zablokować rekordy w zestawie rekordów podczas aktualizacji](#_core_locking_records_in_your_recordset).

Podczas korzystania z zestawu rekordów do aktualizowania rekordu w źródle danych aplikacja może zablokować rekord, aby żaden inny użytkownik nie mógł zaktualizować rekordu w tym samym czasie. Stan rekordu aktualizowanego przez dwóch użytkowników w tym samym czasie jest niezdefiniowany, chyba że system może zagwarantować, że dwóch użytkowników nie może zaktualizować rekordu jednocześnie.

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli zaimplementowano pobieranie wiersza zbiorczego, niektóre informacje nie mają zastosowania. Na przykład nie można `Edit` `Update` wywołać i funkcji członkowskich. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Tryby blokowania nagrywania

Klasy bazy danych zapewniają dwa [tryby blokowania rekordów:](../../mfc/reference/crecordset-class.md#setlockingmode)

- Blokowanie optymistyczne (domyślnie)

- Pesymistyczne blokowanie

Aktualizowanie rekordu odbywa się w trzech krokach:

1. Operację można rozpocząć, wywołując funkcję [Edytuj](../../mfc/reference/crecordset-class.md#edit) element członkowski.

1. Możesz zmienić odpowiednie pola bieżącego rekordu.

1. Zakończenie operacji — i zwykle zatwierdzić aktualizację — wywołując [Update](../../mfc/reference/crecordset-class.md#update) funkcji elementu członkowskiego.

Optymistyczne blokowanie blokuje rekord w źródle `Update` danych tylko podczas wywołania. Jeśli używasz optymistyczne blokowanie w środowisku wielu użytkowniczu, aplikacja powinna obsługiwać warunek `Update` awarii. Pesymistyczne blokowanie blokuje rekord natychmiast po `Edit` wywołaniu i nie `Update` zwalnia go, dopóki nie `CDBException` zadzwonisz (błędy są oznaczone `Update`za pomocą mechanizmu, a nie przez wartość FALSE zwrócone przez ). Pesymistyczne blokowanie ma potencjalne kary wydajności dla innych użytkowników, ponieważ równoczesny dostęp do tego `Update` samego rekordu może czekać do zakończenia procesu aplikacji.

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Blokowanie rekordów w twoim rekordzie

Jeśli chcesz zmienić [tryb blokowania](#_core_record.2d.locking_modes) obiektu zestawu rekordów z domyślnego, musisz `Edit`zmienić tryb przed wywołaniem .

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Aby zmienić bieżący tryb blokowania dla zestawu rekordów

1. Wywołanie funkcji elementu członkowskiego [SetLockingMode,](../../mfc/reference/crecordset-class.md#setlockingmode) określając jedną lub `CRecordset::pessimistic` `CRecordset::optimistic`.

Nowy tryb blokowania pozostaje w mocy, dopóki nie zmienisz go ponownie lub zestaw rekordów zostanie zamknięty.

> [!NOTE]
> Stosunkowo niewiele sterowników ODBC obsługuje obecnie pesymistyczne blokowanie.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
