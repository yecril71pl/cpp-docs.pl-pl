---
title: 'Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: b34f6f51c6ff3a0995f4cf6044ddd7949644f42c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665299"
---
# <a name="recordset-more-about-updates-odbc"></a>Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano:

- [Jak inne operacje, takie jak transakcje wpływają na aktualizacje](#_core_how_transactions_affect_updates).

- [Aktualizacje i innych użytkowników](#_core_your_updates_and_the_updates_of_other_users).

- [Więcej informacji na temat funkcji elementów członkowskich Update i Delete](#_core_more_about_update_and_delete).

> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli udało Ci się wdrożyć zbiorcze pobieranie z wiersza, niektóre informacje nie ma zastosowania. Na przykład nie można wywołać `AddNew`, `Edit`, `Delete`, i `Update` funkcji składowych; Jednakże, można wykonać transakcji. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_how_other_operations_affect_updates"></a> Jak inne operacje wpływają na aktualizacje

Aktualizacje są zagrożone transakcji obowiązuje w czasie aktualizacji, zamykając zestawu rekordów przed ukończeniem transakcji i przewijając przed ukończeniem transakcji.

###  <a name="_core_how_transactions_affect_updates"></a> Jak transakcje wpływają na aktualizacje

Poza zrozumienia sposobu `AddNew`, `Edit`, i `Delete` pracy, ważne jest, aby zrozumieć sposób, w jaki `BeginTrans`, `CommitTrans`, i `Rollback` funkcje elementów członkowskich [CDatabase](../../mfc/reference/cdatabase-class.md) działają z Funkcje update [CRecordset](../../mfc/reference/crecordset-class.md).

Domyślnie wywołuje w celu `AddNew` i `Edit` mogą wpłynąć na źródło danych natychmiast, gdy zostanie wywołana `Update`. `Delete` wywołania zaczynają obowiązywać natychmiast. Jednak można było określić transakcji i wykonywanie partii takich połączeń. Aktualizacje nie są trwałe, aż je zatwierdzisz. Jeśli zmienisz zdanie, można wycofać transakcji, zamiast go zatwierdzania.

Aby uzyskać więcej informacji na temat transakcji, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Jak zamknięcia zestawu rekordów wpływa na aktualizacje

Jeśli zamkniesz zestaw rekordów lub związanych z nią `CDatabase` obiektu z transakcją w toku (nie wywołano [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) lub [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), transakcja została wycofana Utwórz kopię automatycznie (o ile bazy danych zaplecza jest aparat bazy danych Microsoft Jet).

> [!CAUTION]
>  Jeśli używasz aparatu bazy danych Microsoft Jet zamknięcia zestawu rekordów wewnątrz transakcji jawnej nie powoduje zwalnianie wierszy, które zostały zmodyfikowane ani blokad, które zostały wprowadzone do momentu jawnego transakcji nie zostanie przekazana lub wycofana. Zaleca się że należy zawsze zarówno otwierających i zamykających zestawy rekordów wewnątrz lub na zewnątrz transakcji jawnej Jet.

###  <a name="_core_how_scrolling_affects_updates"></a> Jak przewijanie wpływa na aktualizacje

Po użytkownik [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) w zestawie rekordów buforu edycji jest wypełniany każdego nowego rekordu bieżącej (poprzedniego rekordu nie znajduje się najpierw). Przewijanie pomija za pośrednictwem wcześniej usuniętych rekordów. Po przewinięciu w po `AddNew` lub `Edit` wywołania bez wywoływania `Update`, `CommitTrans`, lub `Rollback` najpierw wszelkie zmiany zostaną utracone (z bez ostrzeżenia dla użytkownika) jako nowy rekord jest umieszczany w buforze edycji. Bufor edycji zostanie wypełnione przy użyciu rekordu przewijane w, przechowywane rekordu jest zwalniana i nie zmienią się w źródle danych. Dotyczy to zarówno `AddNew` i `Edit`.

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Aktualizacje i aktualizacje innych użytkowników

Gdy używasz zestawu rekordów do aktualizowania danych aktualizacje wpłynąć na innych użytkowników. Podobnie aktualizacje innych użytkowników w okresie istnienia rekordów napotkasz.

W środowisku wielodostępnym innych użytkownicy mogą otwierać zestawy rekordów, które zawierają niektóre z tych samych wybranych w twoim zestawie rekordów. Zmiany z rekordem, przed pobraniem go są odzwierciedlane w twoim zestawie rekordów. Ponieważ zestawów dynamicznych pobrać rekordu za każdym razem, gdy przewiń do niego, zestawów dynamicznych odzwierciedlać zmiany, każdym razem, gdy przewiń do rekordu. Migawki pobrać rekordu przewijania, więc migawek odzwierciedlenia tych zmian, występujących przed przewiń do rekordu początkowo po raz pierwszy.

Rekordów dodanych przez innych użytkowników, po otwarciu zestawu rekordów nie są wyświetlane w twoim zestawie rekordów, chyba że użytkownik requery. Jeśli rekordów jest dynamiczny, zmiany w istniejących rekordach przez innych użytkowników są wyświetlane w swojej dynamiczny podczas przewijania, do których to dotyczy rekordu. Jeśli rekordów jest migawką, zmiany nie są wyświetlane do czasu requery migawki. Jeśli chcesz zobaczyć rekordów dodanych lub usunięty przez innych użytkowników w swojej migawki lub rekordów dodanych przez innych użytkowników w Twojej dynamiczny wywołać [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) odbudować zestawu rekordów. (Zwróć uwagę, że usuwania innych użytkowników pojawiają się w Twojej dynamiczny). Może również wywołać `Requery` Aby wyświetlić rekordy dodasz, ale nie do Zobacz wprowadzone usunięcia.

> [!TIP]
>  Aby wymusić buforowania cały migawki jednocześnie, należy wywołać `MoveLast` bezpośrednio po otwarciu migawki. Następnie wywołaj `MoveFirst` do rozpoczęcia pracy z rekordów. `MoveLast` jest odpowiednikiem przewijanie przez wszystkie rekordy, ale pobierany je wszystkie na raz. Należy jednak pamiętać, to może obniżyć wydajność i może nie być wymagana dla niektórych sterowników.

Efekty aktualizacje dla innych użytkowników są podobne do ich wpływu na użytkownik.

##  <a name="_core_more_about_update_and_delete"></a> Więcej informacji na temat Update i Delete

Ta sekcja zawiera dodatkowe informacje pomocne podczas pracy z programami `Update` i `Delete`.

### <a name="update-success-and-failure"></a>Aktualizacja sukcesów i niepowodzeń

Jeśli `Update` zakończy się powodzeniem, `AddNew` lub `Edit` trybu. Aby rozpocząć `AddNew` lub `Edit` tryb ponownie, wywołanie `AddNew` lub `Edit`.

Jeśli `Update` zakończy się niepowodzeniem (zwraca wartość FALSE lub zgłasza wyjątek), pozostają w `AddNew` lub `Edit` tryb, w zależności od funkcji użytkownik o nazwie ostatniego. Można następnie wykonaj jedną z następujących czynności:

- Zmodyfikuj element członkowski danych pola i spróbuj `Update` ponownie.

- Wywołaj `AddNew` zresetować elementy członkowskie danych pola na wartość Null, ustaw wartości elementów członkowskich danych pola, a następnie wywołaj `Update` ponownie.

- Wywołaj `Edit` ponowne załadowanie wartości, które były w zestawie rekordów przed pierwszym wywołaniu `AddNew` lub `Edit`, ustaw wartości elementów członkowskich danych pola, a następnie wywołaj `Update` ponownie. Po pomyślnym przeprowadzeniu `Update` wywołać (z wyjątkiem po `AddNew` wywołania), elementy członkowskie danych pola zachowują swoje nowe wartości.

- Wywołania `Move` (w tym `Move` z parametrem AFX_MOVE_REFRESH lub 0), która czyści dowolne zmiany i kończy się dowolny `AddNew` lub `Edit` tryb efekt.

### <a name="update-and-delete"></a>Aktualizowanie i usuwanie

Ten rozdział ma zastosowanie do obu `Update` i `Delete`.

Na `Update` lub `Delete` operację, należy zaktualizować jeden i tylko jeden rekord. Ten rekord jest bieżący rekord, który odnosi się do wartości danych w polach zestawu rekordów. Jeśli z dowolnej przyczyny dotyczą żadnych rekordów lub występuje więcej niż jeden rekord, zgłaszany jest wyjątek zawierającą jeden z następujących **RETCODE** wartości:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Po zgłoszeniu tych wyjątków pozostaną w `AddNew` lub `Edit` stanu aktywnej w momencie wywołana `Update` lub `Delete`. Poniżej przedstawiono najbardziej typowych scenariuszy, w których zobaczysz tych wyjątków. Możesz najbardziej prawdopodobne zobaczyć:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, gdy używany jest tryb blokowanie optymistyczne i inny użytkownik zmodyfikował rekord w taki sposób, który uniemożliwia ramach identyfikowanie właściwy rekord, zaktualizować lub usunąć.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED podczas aktualizowania tabeli nie ma klucza podstawowego lub unikatowego indeksu, a nie ma wystarczającej liczby kolumn w zestawie rekordów do jednoznacznego identyfikowania wiersza tabeli.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md)