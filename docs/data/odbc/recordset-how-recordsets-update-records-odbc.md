---
title: 'Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: bf71f562714e2dacfe75540e1e532219b3eb307f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034485"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)

Ten temat dotyczy klas MFC ODBC.

Oprócz możliwość wybierania rekordów ze źródła danych zestawy rekordów (opcjonalnie) zaktualizować lub usunąć wybrane rekordy lub dodawać nowe rekordy. Trzech czynników updateability zestaw rekordów: czy połączonego źródła danych można aktualizować, opcje, można określić podczas tworzenia obiektu zestawu rekordów i SQL Server, który jest tworzony.

> [!NOTE]
>  SQL, na którym Twoja `CRecordset` opiera się obiekt może mieć wpływ na updateability zestawu rekordów. Na przykład jeśli SQL zawiera instrukcję join lub **GROUP BY** klauzuli MFC ustawia updateability na wartość FALSE.

> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

W tym temacie opisano:

- [Twoja rola w aktualizowania rekordów](#_core_your_role_in_recordset_updating) i struktura jest dla Ciebie.

- [Zestaw rekordów jako bufor edycji](#_core_the_edit_buffer) i [różnice między zestawów dynamicznych i migawek](#_core_dynasets_and_snapshots).

[Zestaw rekordów: Jak działają funkcje AddNew, Edit i Usuń pracy (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) opisuje akcje te funkcje z punktu widzenia zestawu rekordów.

[Zestaw rekordów: Więcej o aktualizacje (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) kończy historię aktualizacji zestawu rekordów, wyjaśniające, jak transakcje wpływają na aktualizacje, jak zamknąć zestawu rekordów lub przewijanie wpływa na aktualizacje w toku i sposób interakcji aktualizacje za pomocą aktualizacji innych użytkowników.

##  <a name="_core_your_role_in_recordset_updating"></a> Twoja rola w aktualizacji zestawu rekordów

W poniższej tabeli przedstawiono Twojej roli przy użyciu zestawów rekordów, aby dodać, edytować lub usuwać rekordy oraz platformę jest dla Ciebie.

### <a name="recordset-updating-you-and-the-framework"></a>Aktualizowanie zestawu rekordów: Użytkownik i struktury

|Można|Struktura|
|---------|-------------------|
|Ustal, czy źródło danych jest można aktualizować (lub appendable).|Dostarcza [CDatabase](../../mfc/reference/cdatabase-class.md) funkcji elementów członkowskich do testowania updateability lub appendability źródła danych.|
|Otwórz nadaje się do aktualizacji zestawu rekordów (dowolnego typu).||
|Ustal, czy zestaw rekordów jest nadaje się do aktualizacji, przez wywołanie metody `CRecordset` aktualizacji funkcji, takich jak `CanUpdate` lub `CanAppend`.||
|Wywołaj rekordów elementów członkowskich do dodawania, edytowania i usuwania rekordów.|Zarządza mechanika wymiana danych między obiekt zestawu rekordów a źródłem danych.|
|Opcjonalnie można użyć transakcji do kontrolowania procesu aktualizacji.|Dostarcza `CDatabase` funkcji elementów członkowskich do obsługi transakcji.|

Aby uzyskać więcej informacji na temat transakcji, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="_core_the_edit_buffer"></a> Bufor edycji

Podjęta zbiorczo, elementy członkowskie danych pola zestawu rekordów pełnić rolę buforu edycji, który zawiera jeden rekord — bieżącego rekordu. Operacje aktualizacji używają tego buforu może działać w bieżącym rekordzie.

- Po dodaniu rekordu, bufor edycji jest używany do tworzenia nowego rekordu. Po dodaniu rekordu, rekord, który został wcześniej bieżącego staje się bieżącym ponownie.

- Po zaktualizowaniu buforu (Edytuj) rekord edycji służy można skonfigurować elementy członkowskie danych pola zestawu rekordów na nowe wartości. Po zakończeniu aktualizowania zaktualizowanym rekordem jest obecne.

Gdy wywołujesz [działają funkcje AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edytuj](../../mfc/reference/crecordset-class.md#edit), bieżącego rekordu są przechowywane, więc można go przywrócić później zgodnie z potrzebami. Gdy wywołujesz [Usuń](../../mfc/reference/crecordset-class.md#delete), bieżący rekord nie są przechowywane, ale jest oznaczony jako usunięty, i musi przewiń do innego rekordu.

> [!NOTE]
>  Bufor edycji odgrywa żadnej roli w usuwania rekordów. Po usunięciu bieżącego rekordu, rekord zostanie oznaczony jako usunięty, a zestaw rekordów jest "ale nie na rekord", dopóki przewiń do innego rekordu.

##  <a name="_core_dynasets_and_snapshots"></a> Migawki i zestawów dynamicznych

[Zestawy dynamiczne](../../data/odbc/dynaset.md) Odśwież zawartość rekordu podczas przewijania w rekordzie. [Migawki](../../data/odbc/snapshot.md) są statyczne reprezentujących rekordy, więc zawartość rekordu nie są odświeżane, chyba że wywołujesz [Requery](../../mfc/reference/crecordset-class.md#requery). Aby korzystać z funkcji zestawów dynamicznych, musisz pracować ze sterownikiem ODBC, który jest zgodny z odpowiedniego poziomu obsługi interfejsu API ODBC. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [dynamiczny](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: Jak działają funkcje AddNew, edytowanie i usuwanie pracy (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)