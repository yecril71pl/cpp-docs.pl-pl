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
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212878"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)

Ten temat dotyczy klas MFC ODBC.

Oprócz możliwości wybierania rekordów ze źródła danych zestawy rekordów mogą (opcjonalnie) aktualizować lub usuwać wybrane rekordy lub dodawać nowe rekordy. Trzy czynniki określają możliwość aktualizowania zestawu rekordów: to, czy połączone źródło danych jest możliwe do zaktualizowania, które opcje są określane podczas tworzenia obiektu zestawu rekordów i utworzonego języka SQL.

> [!NOTE]
>  SQL, na którym opiera się obiekt `CRecordset`, może mieć wpływ na możliwość aktualizowania zestawu rekordów. Na przykład, jeśli SQL zawiera klauzulę Join lub **Group by** , MFC ustawia właściwość Update na false.

> [!NOTE]
>  Ten temat dotyczy obiektów pochodnych `CRecordset`, w których nie zaimplementowano pobierania wierszy zbiorczych. Jeśli używasz pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W tym temacie objaśniono:

- [Rola w usłudze zestaw rekordów](#_core_your_role_in_recordset_updating) i co to jest platforma.

- [Zestaw rekordów jako bufor Edytuj](#_core_the_edit_buffer) i [różnice między zestawami dynamicznymi i migawkami](#_core_dynasets_and_snapshots).

[Zestaw rekordów: jak Metoda AddNew, Edit i DELETE Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) opisuje działania tych funkcji z punktu widzenia zestawu rekordów.

[Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) uzupełnia historię aktualizacji zestawu rekordów przez wyjaśnienie, jak transakcje mają wpływ na aktualizacje, jak zamknięcie zestawu rekordów lub przewijania wpływa na aktualizacje w toku oraz jak aktualizacje są współdziałane z aktualizacjami innych użytkowników.

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Rola w ramach aktualizacji zestawu rekordów

W poniższej tabeli przedstawiono rolę w korzystaniu z zestawów rekordów, aby dodawać, edytować lub usuwać rekordy oraz do czego służy platforma.

### <a name="recordset-updating-you-and-the-framework"></a>Aktualizowanie zestawu rekordów: ty i struktura

|Można|Struktura programu|
|---------|-------------------|
|Ustal, czy źródło danych jest aktualizowalne (czy można je dołączyć).|Dostarcza funkcje składowe [CDatabase](../../mfc/reference/cdatabase-class.md) do testowania operacji aktualizowania lub dołączania źródła danych.|
|Otwórz aktualizowalny zestaw rekordów (dowolnego typu).||
|Ustal, czy zestaw rekordów jest aktualizowalny przez wywoływanie funkcji `CRecordset` Update, takich jak `CanUpdate` lub `CanAppend`.||
|Wywołaj funkcje składowe zestawu rekordów, aby dodawać, edytować i usuwać rekordy.|Zarządza mechanicsem wymiany danych między obiektem zestawu rekordów a źródłem danych.|
|Opcjonalnie użyj transakcji, aby kontrolować proces aktualizacji.|Dostarcza `CDatabase` funkcje członkowskie do obsługi transakcji.|

Aby uzyskać więcej informacji na temat transakcji, zobacz [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Bufor edycji

Zebrane zbiorczo elementy członkowskie danych pola zestawu rekordów pełnią rolę bufora edycji, który zawiera jeden rekord — bieżący rekord. Operacje aktualizacji używają tego buforu do działania w bieżącym rekordzie.

- Po dodaniu rekordu do tworzenia nowego rekordu używany jest bufor edycji. Po zakończeniu dodawania rekordu, rekord, który był wcześniej bieżącym, jest ponownie bieżący.

- Podczas aktualizowania (edycji) rekordu, bufor edycji służy do ustawiania elementów członkowskich danych pola zestawu rekordów na nowe wartości. Po zakończeniu aktualizacji zaktualizowany rekord jest nadal aktualny.

Gdy wywoływana jest metoda [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edit](../../mfc/reference/crecordset-class.md#edit), bieżący rekord jest przechowywany, aby można go było przywrócić później, zgodnie z wymaganiami. Po wywołaniu metody [delete](../../mfc/reference/crecordset-class.md#delete)bieżący rekord nie jest przechowywany, ale jest oznaczony jako usunięty i należy przewinąć do innego rekordu.

> [!NOTE]
>  W przypadku usunięcia rekordu nie są odtwarzane żadne role w buforze edycji. Po usunięciu bieżącego rekordu rekord zostanie oznaczony jako usunięty, a zestaw rekordów nie jest rekordem, dopóki nie przewiniesz do innego rekordu.

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Zestawy dynamiczne i migawki

[Zestawy dynamiczne](../../data/odbc/dynaset.md) odświeżają zawartość rekordu podczas przewijania do rekordu. [Migawki](../../data/odbc/snapshot.md) to statyczne reprezentacje rekordów, więc zawartość rekordu nie jest odświeżana, chyba że zostanie wywołana [kwerenda](../../mfc/reference/crecordset-class.md#requery). Aby korzystać ze wszystkich funkcji zestawów dynamicznych, należy pracować ze sterownikiem ODBC, który jest zgodny z poprawnym poziomem obsługi interfejsu API ODBC. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [dynamiczny](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
