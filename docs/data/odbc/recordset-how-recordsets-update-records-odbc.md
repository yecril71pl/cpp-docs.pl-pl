---
title: 'Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366979"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)

Ten temat dotyczy klas MFC ODBC.

Oprócz możliwości wybierania rekordów ze źródła danych, zestawy rekordów mogą (opcjonalnie) aktualizować lub usuwać wybrane rekordy lub dodawać nowe rekordy. Trzy czynniki określają możliwość aktualizacji zbioru rekordów: czy podłączone źródło danych można aktualizować, opcje określone podczas tworzenia obiektu zestawu rekordów i tworzony program SQL.

> [!NOTE]
> Sql, na `CRecordset` którym obiekt jest oparty może mieć wpływ na możliwości aktualizacji pliku recordset. Na przykład jeśli sql zawiera sprzężenie lub **group by** klauzuli, MFC ustawia możliwość aktualizacji na FALSE.

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli korzystasz z pobierania wierszy zbiorczych, zobacz [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W tym temacie wyjaśniono:

- [Twoja rola w aktualizacji recordset](#_core_your_role_in_recordset_updating) i co robi dla Ciebie ramach.

- [Zestaw rekordów jako bufor edycji](#_core_the_edit_buffer) i [różnice między dynasets i migawki](#_core_dynasets_and_snapshots).

[Recordset: How AddNew, Edit, and Delete Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) opisuje działania tych funkcji z punktu widzenia pliku recordset.

[Recordset: Więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) kończy wątek aktualizacji pliku recordset, wyjaśniając, jak transakcje wpływają na aktualizacje, jak zamykanie aktu lub przewijanie wpływa na aktualizacje w toku i jak aktualizacje wchodzą w interakcję z aktualizacjami innych użytkowników.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Twoja rola w aktualizacji na recordset

W poniższej tabeli przedstawiono rolę w używaniu zestawy rekordów do dodawania, edytowania lub usuwania rekordów, wraz z tym, co robi dla Ciebie ramach.

### <a name="recordset-updating-you-and-the-framework"></a>Aktualizacja nastawy: Ty i struktura

|Można|Ramy prawne|
|---------|-------------------|
|Określ, czy źródło danych można aktualizować (czy dołączać).|Dostarcza funkcje członkowskie [CDatabase](../../mfc/reference/cdatabase-class.md) do testowania możliwości aktualizacji lub dołączalności źródła danych.|
|Otwórz aktualizowany apecie (dowolnego typu).||
|Określ, czy zestawie rekordów `CRecordset` można aktualizować, wywołując funkcje aktualizacji, takie jak `CanUpdate` lub `CanAppend`.||
|Wywoływanie funkcji elementu członkowskiego wynajęcie rekordów w celu dodania, edycji i usunięcia rekordów.|Zarządza mechaniką wymiany danych między obiektem zestawem rekordów a źródłem danych.|
|Opcjonalnie użyj transakcji, aby kontrolować proces aktualizacji.|Dostarcza `CDatabase` funkcje członkowskie do obsługi transakcji.|

Aby uzyskać więcej informacji o transakcjach, zobacz [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Bufor edycji

Razem przyjmowane elementy członkowskie danych pól zestawu rekordów służą jako bufor edycji zawierający jeden rekord — bieżący rekord. Operacje aktualizacji używają tego buforu do działania w bieżącym rekordzie.

- Po dodaniu rekordu bufor edycji jest używany do tworzenia nowego rekordu. Po zakończeniu dodawania rekordu rekord, który był wcześniej bieżący, staje się ponownie bieżący.

- Podczas aktualizowania (edytowania) rekordu bufor edycji jest używany do ustawiania elementów członkowskich danych pola zestawu rekordów na nowe wartości. Po zakończeniu aktualizacji zaktualizowany rekord jest nadal aktualny.

Po wywołaniu [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edit](../../mfc/reference/crecordset-class.md#edit)bieżący rekord jest przechowywany, dzięki czemu można go później przywrócić w razie potrzeby. Po [wywołaniu delete](../../mfc/reference/crecordset-class.md#delete)bieżący rekord nie jest przechowywany, ale jest oznaczony jako usunięty i należy przewinąć do innego rekordu.

> [!NOTE]
> Bufor edycji nie odgrywa żadnej roli w usuwaniu rekordów. Po usunięciu bieżącego rekordu rekord jest oznaczony jako usunięty, a jego plan rejestrowania jest "nie na rekordzie", dopóki nie przewiniesz do innego rekordu.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasets i migawki

[Dynasets odświeża](../../data/odbc/dynaset.md) zawartość rekordu podczas przewijania do rekordu. [Migawki](../../data/odbc/snapshot.md) są statycznymi reprezentacjami rekordów, więc zawartość rekordu nie jest odświeżana, chyba że wywołasz [ponowne powołynie](../../mfc/reference/crecordset-class.md#requery). Aby korzystać ze wszystkich funkcji dynasets, należy pracować ze sterownikiem ODBC, który jest zgodny z poprawnym poziomem obsługi interfejsu API ODBC. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
