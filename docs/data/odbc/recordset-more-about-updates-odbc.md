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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368672"
---
# <a name="recordset-more-about-updates-odbc"></a>Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono:

- [Jak inne operacje, takie jak transakcje, wpływają na aktualizacje](#_core_how_transactions_affect_updates).

- [Twoje aktualizacje i aktualizacje innych użytkowników](#_core_your_updates_and_the_updates_of_other_users).

- [Więcej informacji o funkcjach elementów członkowskich Aktualizacji i Usuwania](#_core_more_about_update_and_delete).

> [!NOTE]
> Ten temat dotyczy obiektów pochodzących z `CRecordset` których pobieranie wiersza zbiorczego nie zostało zaimplementowane. Jeśli zaimplementowano pobieranie wiersza zbiorczego, niektóre informacje nie mają zastosowania. Na przykład nie można `AddNew` `Edit`wywołać funkcji , , `Delete`i `Update` elementów członkowskich; można jednak wykonywać transakcje. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Jak inne operacje wpływają na aktualizacje

Na aktualizacje mają wpływ transakcje obowiązujące w momencie aktualizacji, zamknięcie pakietu rekordów przed zakończeniem transakcji i przewijanie przed zakończeniem transakcji.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Jak transakcje wpływają na aktualizacje

Poza zrozumieniem, jak `AddNew`, `Edit` `Delete` i pracy, `BeginTrans`ważne `CommitTrans`jest, aby zrozumieć, jak , i `Rollback` funkcje członkowskie [CDatabase](../../mfc/reference/cdatabase-class.md) pracy z funkcjami aktualizacji [CRecordset](../../mfc/reference/crecordset-class.md).

Domyślnie wywołania `AddNew` `Edit` i wpływają na źródło `Update`danych natychmiast po wywołaniu . `Delete`natychmiastowe zaatraktuje. Ale można ustanowić transakcję i wykonać partię takich wywołań. Aktualizacje nie są trwałe, dopóki ich nie zatwierdzisz. Jeśli zmienisz zdanie, możesz wycofać transakcję zamiast ją zatwierdzać.

Aby uzyskać więcej informacji o transakcjach, zobacz [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Jak zamknięcie aktui recordset wpływa na aktualizacje

Jeśli zamkniesz zestawie rekordów `CDatabase` lub skojarzony z nim obiekt z transakcją w toku (nie został wywołany [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) lub [CDatabase::Rollback),](../../mfc/reference/cdatabase-class.md#rollback)transakcja zostanie wycofana automatycznie (chyba że wewnętrznej bazy danych jest aparat bazy danych Microsoft Jet).

> [!CAUTION]
> Jeśli używasz aparatu bazy danych Microsoft Jet, zamknięcie zestawu rekordów wewnątrz jawnej transakcji nie powoduje zwolnienia żadnych wierszy, które zostały zmodyfikowane lub blokady, które zostały umieszczone, dopóki jawna transakcja nie zostanie zatwierdzona lub wycofana. Zaleca się, aby zawsze otwierać i zamykać zestawy rekordów wewnątrz lub na zewnątrz jawnej transakcji Jet.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Jak przewijanie wpływa na aktualizacje

Podczas [tworzenia rekordu: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) w ach rekordów bufor edycji jest wypełniany każdym nowym bieżącym rekordem (poprzedni rekord nie jest przechowywany jako pierwszy). Przewijanie przeskakuje rekordy wcześniej usunięte. Jeśli przewiń `AddNew` `Edit` po lub `Update` `CommitTrans`połączenia `Rollback` bez wywoływania , lub po raz pierwszy, wszelkie zmiany zostaną utracone (bez ostrzeżenia dla Ciebie), jak nowy rekord jest wprowadzany do buforu edycji. Bufor edycji jest wypełniony rekordem przewiniętym do, przechowywany rekord jest zwalniany i nie ma żadnych zmian w źródle danych. Dotyczy to zarówno `AddNew` `Edit`i .

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Aktualizacje i aktualizacje innych użytkowników

Podczas aktualizowania danych za pomocą zestawu rekordów aktualizacje mają wpływ na innych użytkowników. Podobnie aktualizacje innych użytkowników w okresie istnienia pliku recordset wpływają na Ciebie.

W środowisku dla wielu użytkowników inni użytkownicy mogą otwierać zestawy rekordów zawierające niektóre z tych samych rekordów wybranych w komecie rekordów. Zmiany w rekordzie przed jego pobraniem są odzwierciedlane w zamówiórie. Ponieważ dynasets pobiera rekord za każdym razem, gdy do niego przewijasz, dynasety odzwierciedlają zmiany przy każdym przewinięciu do rekordu. Migawki pobierają rekord przy pierwszym przewinięciu do niego, więc migawki odzwierciedlają tylko te zmiany, które występują przed początkowo przewinąć do rekordu.

Rekordy dodane przez innych użytkowników po otwarciu akuliowania pliku records nie są wyświetlane w pliku recordset, chyba że zostanie ono ponowniequerowe. Jeśli zestaw rekordów jest dynaset, zmiany do istniejących rekordów przez innych użytkowników są wyświetlane w zestawie dynamiki podczas przewijania do rekordu, którego dotyczy problem. Jeśli twój plik recordset jest migawką, zmiany nie są wyświetlane, dopóki nie zostanie ponownie podyzwalna migawka. Jeśli chcesz zobaczyć rekordy dodane lub usunięte przez innych użytkowników w migawce lub rekordy dodane przez innych użytkowników w zestawie dynaset, zadzwoń [CRecordset::Requery,](../../mfc/reference/crecordset-class.md#requery) aby odbudować zestaw rekordów. (Należy pamiętać, że usunięcia innych użytkowników są wyświetlane w zestawie dynamiki). Możesz również `Requery` wywołać, aby wyświetlić dodane rekordy, ale nie, aby zobaczyć usunięcia.

> [!TIP]
> Aby wymusić buforowanie całej migawki `MoveLast` na raz, wywołaj natychmiast po otwarciu migawki. Następnie `MoveFirst` wywołanie, aby rozpocząć pracę z rekordami. `MoveLast`jest odpowiednikiem przewijania wszystkich rekordów, ale pobiera je wszystkie naraz. Należy jednak pamiętać, że może to obniżyć wydajność i może nie być wymagane dla niektórych sterowników.

Wpływ aktualizacji na innych użytkowników jest podobny do ich wpływu na Ciebie.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Więcej informacji o aktualizacji i usuwaniu

Ta sekcja zawiera dodatkowe informacje `Update` ułatwiające pracę z i `Delete`.

### <a name="update-success-and-failure"></a>Aktualizuj sukces i niepowodzenie

Jeśli `Update` się powiedzie, `AddNew` tryb lub `Edit` kończy się. Aby ponownie `AddNew` `Edit` rozpocząć lub `AddNew` tryb, zadzwoń lub `Edit`.

Jeśli `Update` nie powiedzie się (zwraca FALSE `AddNew` lub `Edit` zgłasza wyjątek), pozostaje w trybie lub trybie, w zależności od funkcji, które zostały wywołane jako ostatni. Następnie można wykonać jedną z następujących czynności:

- Zmodyfikuj element `Update` członkowski danych pola i spróbuj ponownie.

- Wywołanie, `AddNew` aby zresetować elementy członkowskie danych pola do null, `Update` ustawić wartości elementów członkowskich danych pola, a następnie wywołać ponownie.

- Wywołanie, `Edit` aby ponownie załadować wartości, które znajdowały się w zestawie rekordów przed pierwszym wywołaniem `AddNew` lub `Edit`, ustawić wartości elementów członkowskich danych pola, a następnie wywołać `Update` ponownie. Po pomyślnym `Update` wywołaniu `AddNew` (z wyjątkiem po wywołaniu) elementy członkowskie danych pola zachowują swoje nowe wartości.

- Wywołanie `Move` `Move` (w tym z parametrem AFX_MOVE_REFRESH lub 0), który opróżnia wszelkie zmiany i kończy dowolny `AddNew` tryb lub `Edit` w efekcie.

### <a name="update-and-delete"></a>Aktualizowanie i usuwanie

Ta sekcja dotyczy `Update` zarówno `Delete`i .

W `Update` przypadku `Delete` operacji lub jeden i tylko jeden rekord powinien zostać zaktualizowany. Ten rekord jest bieżącym rekordem, który odpowiada wartościom danych w polach zbioru rekordów. Jeśli z jakiegoś powodu nie ma to wpływu na żadne rekordy lub dotyczy więcej niż jednego rekordu, zostanie zgłoszony wyjątek zawierający jedną z następujących wartości **RETCODE:**

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Gdy te wyjątki są generowane, `AddNew` `Edit` pozostajesz w stanie `Update` lub `Delete`byłeś w kiedy dzwoniłeś lub . Oto najbardziej typowe scenariusze, w których można zobaczyć te wyjątki. Najprawdopodobniej zobaczysz:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, gdy używasz trybu blokowania optymistycznego, a inny użytkownik zmodyfikował rekord w sposób uniemożliwiający platformie identyfikowanie prawidłowego rekordu w celu zaktualizowania lub usunięcia.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, gdy aktualizowana tabela nie ma klucza podstawowego ani unikatowego indeksu i nie ma wystarczającej liczby kolumn w tablicy rekordów, aby jednoznacznie zidentyfikować wiersz tabeli.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md)
