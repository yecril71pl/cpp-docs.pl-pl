---
title: "Zestaw rekordów: Więcej informacji na temat aktualizacje (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f996a206ebac40a469f2fc540c5e23ce0f5c2733
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-more-about-updates-odbc"></a>Zestaw rekordów: więcej informacji o aktualizacjach (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano:  
  
-   [Jak inne operacje, takie jak transakcje wpływają na aktualizacje](#_core_how_transactions_affect_updates).  
  
-   [Aktualizacje i innych użytkowników](#_core_your_updates_and_the_updates_of_other_users).  
  
-   [Dodatkowe informacje o funkcjach Członkowskich Update i Delete](#_core_more_about_update_and_delete).  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, niektóre informacje nie ma zastosowania. Na przykład nie można wywołać `AddNew`, **Edytuj**, **usunąć**, i **aktualizacji** funkcji członkowskich; można jednak wykonywać transakcje. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_how_other_operations_affect_updates"></a>Jak inne operacje wpływają na aktualizacje  
 Aktualizacje dotyczy transakcji obowiązująca w momencie aktualizacji, zamykając zestawu rekordów przed ukończeniem transakcji i przewijając przed ukończeniem transakcji.  
  
###  <a name="_core_how_transactions_affect_updates"></a>Jak transakcje wpływają na aktualizacje  
 Poza opis sposobu `AddNew`, **Edytuj**, i **usunąć** pracy, ważne jest, aby zrozumieć, jak **BeginTrans**, **CommitTrans**, i **wycofywania** funkcji Członkowskich [cdatabase —](../../mfc/reference/cdatabase-class.md) korzystanie z funkcji aktualizacji [crecordset —](../../mfc/reference/crecordset-class.md).  
  
 Domyślnie wywołań `AddNew` i **Edytuj** wpływ źródła danych, natychmiast po wywołaniu **aktualizacji**. **Usuń** wywołania zaczynają obowiązywać natychmiast. Można jednak ustanowić transakcji i wykonywanie wsadowe takich połączeń. Aktualizacje nie są trwałe, dopóki nie zostaną zatwierdzone. Jeśli zmienisz zdanie, możesz można wycofać transakcji zamiast jego zatwierdzeniem.  
  
 Aby uzyskać więcej informacji na temat transakcji, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a>Zamykanie zestawu rekordów wpływ aktualizacji  
 Jeśli zamkniesz zestawu rekordów lub skojarzonego `CDatabase` obiektu z transakcją w toku (nie wywołano [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) lub [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), transakcja została wycofana Utwórz kopię automatycznie (o ile z wewnętrzną bazą danych z bazy danych jest aparat bazy danych programu Microsoft Jet).  
  
> [!CAUTION]
>  Jeśli używasz aparatu bazy danych programu Microsoft Jet zamknięcia rekordów wewnątrz transakcji jawnej nie powoduje zwolnienie wszystkich wierszy, które zostały zmodyfikowane lub blokad, które zostały wprowadzone, dopóki jawnych transakcji jest zatwierdzona lub wycofana. Zalecane jest ten użytkownik zawsze zarówno otwierających i zamykających zestawy rekordów wewnątrz lub na zewnątrz jawnych transakcji Jet.  
  
###  <a name="_core_how_scrolling_affects_updates"></a>Przewijanie wpływ aktualizacji  
 Gdy użytkownik [zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) w zestawie rekordów buforu edycji jest wypełniony każdego nowego rekordu bieżącego (poprzedniego rekordu nie znajduje się najpierw). Przewijanie pomija za pośrednictwem wcześniej usuniętych rekordów. Podczas przewijania po `AddNew` lub **Edytuj** wywołania bez wywoływania elementu **aktualizacji**, **CommitTrans**, lub **wycofywania** pierwszy, wszystkie zmiany zostaną utracone (z bez ostrzeżenia dla użytkownika), jako nowego rekordu jest umieszczany w buforze edycji. Bufor edycji jest wypełniony rekordu przewijane w, przechowywane rekord zostanie zwolniona i występuje żadnych zmian w źródle danych. Dotyczy to zarówno `AddNew` i **Edytuj**.  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a>Aktualizacje i aktualizacje dla innych użytkowników  
 Gdy używasz zestawu rekordów, aby zaktualizować dane aktualizacje dotyczące innych użytkowników. Podobnie aktualizacji innych użytkowników w ramach zestawu rekordów dotyczy.  
  
 W środowisku wielodostępnym innych użytkownicy mogą otworzyć zestawów rekordów, który zawiera niektóre z nich tego samego wybranego zestawu rekordów. Zmiany z rekordem przed można pobrać są uwzględniane w twoim zestawie rekordów. Ponieważ zestawów dynamicznych pobrać rekordu za każdym razem, którą można do niego, zestawów dynamicznych odzwierciedlenia zmian zawsze, gdy przewiń do rekordu. Migawki pobrać rekordu przewijania, więc migawki odzwierciedlać tylko te zmiany, które występują przed przewiń do rekordu początkowo po raz pierwszy.  
  
 Rekordów dodawanych przez innych użytkowników, po otwarciu zestawu rekordów nie są wyświetlane w zestawu rekordów, chyba że użytkownik requery. Jeśli zestawu rekordów jest dynamiczny, zmian w istniejących rekordów przez innych użytkowników są wyświetlane w Twojej dynamiczny podczas przewijania dotyczy rekordu. Jeśli zestawu rekordów jest migawką, zmiany nie są wyświetlane, dopóki requery migawki. Jeśli chcesz rekordy dodane lub usunięte przez innych użytkowników w migawki lub rekordów dodawanych przez innych użytkowników w Twojej dynamiczny wywołania [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) odbudować zestawu rekordów. (Należy pamiętać, że usunięcia innych użytkowników widoczne w Twojej dynamiczny). Może także wywołać **Requery** aby rekordy zostanie dodane, ale nie do Zobacz wprowadzone usunięcia.  
  
> [!TIP]
>  Aby wymusić buforowanie cały jednocześnie migawki, należy wywołać `MoveLast` bezpośrednio po otwarciu migawki. Następnie wywołaj **MoveFirst** do rozpoczęcia pracy z rekordów. `MoveLast`jest odpowiednikiem przewijanie za pośrednictwem wszystkich rekordów, ale ich zostały pobiera jednocześnie. Należy jednak pamiętać, że można obniżyć wydajność i nie mogą być wymagane dla niektórych sterowników.  
  
 Efekty aktualizacje dla innych użytkowników są podobne do ich wpływu na użytkownik.  
  
##  <a name="_core_more_about_update_and_delete"></a>Więcej informacji na temat Update i Delete  
 Ta sekcja zawiera dodatkowe informacje pomocne w pracy z **aktualizacji** i **usunąć**.  
  
### <a name="update-success-and-failure"></a>Aktualizacja sukcesów i niepowodzeń  
 Jeśli **aktualizacji** zakończy się powodzeniem, `AddNew` lub **Edytuj** kończy tryb. Aby rozpocząć `AddNew` lub **Edytuj** tryb ponownie, wywołanie `AddNew` lub **Edytuj**.  
  
 Jeśli **aktualizacji** nie powiedzie się (zwraca **FALSE** lub zgłasza wyjątek), pozostają w `AddNew` lub **Edytuj** tryb, w zależności od funkcji wywołana ostatnio. Można następnie wykonaj jedną z następujących czynności:  
  
-   Zmodyfikuj element członkowski danych pola i spróbuj **aktualizacji** ponownie.  
  
-   Wywołanie `AddNew` zresetować elementy członkowskie danych pola wartość null, ustaw wartości elementy członkowskie danych pola, a następnie wywołać **aktualizacji** ponownie.  
  
-   Wywołanie **Edytuj** ponowne załadowanie wartości, które były w zestawie rekordów przed pierwszym wywołaniu `AddNew` lub **Edytuj**Ustaw wartości elementy członkowskie danych pola, a następnie wywołać **aktualizacji**ponownie. Po pomyślnym **aktualizacji** wywołania (z wyjątkiem po `AddNew` wywołać), elementy członkowskie danych pola zachowują swoje nowe wartości.  
  
-   Wywołanie **Przenieś** (w tym **Przenieś** z parametrem **AFX_MOVE_REFRESH**, lub równa 0), która opróżnia wszelkie zmiany i kończy się żadnego `AddNew` lub **Edytuj** tryb efektu.  
  
### <a name="update-and-delete"></a>Update i Delete  
 Ta sekcja dotyczy zarówno **aktualizacji** i **usunąć**.  
  
 Na **aktualizacji** lub **usunąć** operację, należy zaktualizować tylko jeden rekord. Ten rekord jest bieżącego rekordu, co odpowiada wartości danych w polach zestawu rekordów. Jeśli niektóre przyczyny nie zaktualizowanych lub występuje więcej niż jeden rekord, jest zwracany wyjątek, zawierający jedną z następujących **RETCODE** wartości:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED**  
  
 Gdy te wyjątki zostaną zgłoszone, pozostanie w `AddNew` lub **Edytuj** stanu, które były używane w podczas wywołania **aktualizacji** lub **usunąć**. Poniżej przedstawiono najbardziej typowych scenariuszy, w których można zobaczyć te wyjątki. Wszystko jest najbardziej prawdopodobne, zobacz:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED** podczas, używania optymistycznej tryb blokowania i inny użytkownik zmodyfikował rekord, w ramach zapobiega identyfikowanie właściwego rekordu aktualizować lub usuwać sposób.  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED** podczas aktualizowania tabeli nie ma podstawowego klucza lub indeksu unique, a nie ma wystarczającej liczby kolumn w zestawie rekordów do jednoznacznego identyfikowania wiersza tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [Wyjątki: Wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md)