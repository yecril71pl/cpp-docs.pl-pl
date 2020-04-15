---
title: Kreator konsumenta OLE DB ATL
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 16b2863bc3919edadeef29691c4588838010d9dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319269"
---
# <a name="atl-ole-db-consumer-wizard"></a>Kreator konsumenta OLE DB ATL

::: moniker range="vs-2019"

Ten kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator konfiguruje klasę konsumenta ole db z powiązaniami danych niezbędnymi do uzyskania dostępu do określonego źródła danych za pośrednictwem określonego dostawcy ole db.

> [!NOTE]
> Ten kreator wymaga kliknięcia przycisku **Źródło danych,** aby wybrać `Class` źródło danych przed wprowadzeniem nazw w polach pliku i **.h.**

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

   Przycisk **Źródło danych** umożliwia skonfigurowanie określonego źródła danych przy użyciu określonego dostawcy ole db. Po kliknięciu tego przycisku zostanie wyświetlone okno dialogowe **Właściwości łącza** danych. Aby uzyskać więcej informacji na temat tworzenia ciągów połączeń i okna dialogowego **Właściwości łącza danych,** zobacz [Omówienie interfejsu API łącza danych](/previous-versions/windows/desktop/ms718102(v=vs.85)) w dokumentacji zestawie Windows SDK.

   Poniżej znajdują się dodatkowe informacje opisujące karty w oknie dialogowym **Właściwości łącza danych.**

  - Karta **Dostawca**

      Wybierz odpowiedniego dostawcę do zarządzania połączeniem ze źródłem danych. Typ dostawcy jest zazwyczaj określany przez typ bazy danych, z którą nawiązujesz połączenie. Kliknij przycisk **Dalej** lub kliknij kartę **Połączenie.**

  - **Karta Połączenie**

      Zawartość tej karty zależy od wybranego dostawcy. Chociaż istnieje wiele typów dostawców, w tej sekcji opisano połączenia dla dwóch najczęstszych: danych SQL i ODBC. Pozostałe są podobne odmiany na polach opisanych tutaj.

      W przypadku danych SQL:

      1. **Wybierz lub wprowadź nazwę serwera:** Kliknij menu listy rozwijanej, aby wyświetlić wszystkie zarejestrowane serwery danych w sieci, a następnie wybierz jeden z nich.

      1. **Wprowadź informacje, aby zalogować się do serwera:** Wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

         > [!NOTE]
         > Wystąpił problem z zabezpieczeniami funkcji "Zezwalaj na zapisywanie hasła" w oknie dialogowym Właściwości łącza danych. W części "Wprowadź informacje, aby zalogować się do serwera", istnieją dwa przyciski radiowe:
         >
         > - **Korzystanie ze zintegrowanych zabezpieczeń systemu Windows NT**
         > - **Używanie określonej nazwy użytkownika i hasła**
         >
         > Jeśli wybierzesz **Użyj określonej nazwy użytkownika i hasła,** masz możliwość zapisania hasła (używając pola wyboru "Zezwalaj na zapisywanie hasła"); jednak ta opcja nie jest bezpieczna. Zaleca się wybranie opcji **Użyj zintegrowanych zabezpieczeń systemu Windows NT;** ta opcja jest bezpieczna, ponieważ szyfruje hasło.
         > Mogą wystąpić sytuacje, w których chcesz wybrać opcję "Zezwalaj na zapisywanie hasła". Na przykład jeśli zwalniasz bibliotekę z rozwiązaniem prywatnej bazy danych, nie należy uzyskiwać dostępu do bazy danych bezpośrednio, ale zamiast tego użyć aplikacji warstwy środkowej, aby zweryfikować użytkownika (za pośrednictwem dowolnego schematu uwierzytelniania), a następnie ograniczyć rodzaj danych dostępnych dla użytkownika.

      1. **Wybierz bazę danych na serwerze:** Kliknij menu listy rozwijanej, aby wyświetlić wszystkie zarejestrowane bazy danych na serwerze danych, a następnie wybierz jedną z nich.

         \-lub -

         **Dołącz plik bazy danych jako nazwę bazy danych:** Określ plik, który ma być używany jako baza danych; wprowadzić jawną nazwa ścieżki.

      Dla danych ODBC:

      1. **Określ źródło danych:** Można użyć nazwy źródła danych lub ciągu połączenia.

         **Użyj nazwy źródła danych:** Ta lista rozwijana zawiera źródła danych zarejestrowane w komputerze. Źródła danych można skonfigurować z wyprzedzeniem za pomocą administratora źródła danych ODBC

         \-lub -

         **Użyj ciągu połączenia:** Wprowadź już uzyskany ciąg połączenia lub kliknij przycisk **Buduj;** zostanie wyświetlone okno dialogowe **Wybieranie źródła** danych. Wybierz źródło danych pliku lub komputera i kliknij przycisk **OK**.

         > [!NOTE]
         > Parametry połączenia można uzyskać, przeglądając właściwości istniejącego połączenia w **Eksploratorze serwera**lub można utworzyć połączenie, klikając dwukrotnie **pozycję Dodaj połączenie** w **Eksploratorze serwera**.

      1. **Wprowadź informacje, aby zalogować się do serwera:** Wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

      1. Wprowadź katalog początkowy do użycia.

      1. Kliknij **przycisk Test Połączenia**; jeśli test zakończy się pomyślnie, kliknij przycisk **OK**. Jeśli nie, sprawdź informacje logowania, spróbuj innej bazy danych lub spróbuj użyć innego serwera danych.

  - Karta **Zaawansowane**

      **Ustawienia sieciowe:** Określ **poziom personifikacji** (poziom personifikacji, którego serwer może używać podczas personifikacji klienta; odpowiada bezpośrednio poziomom personifikacji RPC) i **poziom ochrony** (poziom ochrony danych wysyłanych między klientem a serwerem; odpowiada bezpośrednio poziomom ochrony RPC).

      **Inne:** W **obszarze Limit czasu połączenia**określ liczbę sekund czasu bezczynności dozwoloną przed wystąpieniem limitu czasu. W **obszarze Uprawnienia programu Access**określ uprawnienia dostępu do połączenia danych.

      Aby uzyskać więcej informacji na temat zaawansowanych właściwości inicjowania, zapoznaj się z dokumentacją dostarczoną z każdym konkretnym dostawcą ole db.

  - **Karta Wszystkie**

      Na tej karcie jest wyświetlane podsumowanie właściwości inicjowania określonego źródła danych i połączenia. Wartości te można edytować.

      Kliknij przycisk **OK**, aby zakończyć. Zostanie wyświetlone okno dialogowe **Wybierz obiekt bazy danych.** W tym oknie dialogowym wybierz tabelę, widok lub procedurę składowaną, której będzie używać konsument.

- **Klasa**

   Po wybraniu źródła danych to pole jest wypełniane domyślną nazwą klasy na podstawie wybranej tabeli lub procedury składowanej (zobacz **Wybieranie źródła danych** poniżej). Można edytować nazwę klasy.

- **.h plik**

   Po wybraniu źródła danych to pole jest wypełniane domyślną nazwą klasy nagłówka na podstawie wybranej tabeli lub procedury składowanej (zobacz **Wybieranie źródła danych** poniżej). Można edytować nazwę pliku nagłówka lub wybrać istniejący plik nagłówka.

- **Przypisane**

   Ta opcja określa, czy kreator utworzy klasy konsumentów przy użyciu atrybutów lub deklaracji szablonów. Po wybraniu tej opcji kreator używa atrybutów zamiast deklaracji szablonów (jest to opcja domyślna). Po usunięciu zaznaczenia tej opcji kreator używa deklaracji szablonów zamiast atrybutów.

  - W przypadku wybrania **opcji Typ** **tabeli** `db_source` dla `db_table` konsumenta kreator używa atrybutów i atrybutów `db_column` do tworzenia deklaracji klas akcesorów tabeli i tabeli oraz używa do utworzenia mapy kolumn. Na przykład tworzy tę mapę:

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     zamiast używać klasy `CTable` szablonu do deklarowania klasy akcesora tabeli i tabeli oraz BEGIN_COLUMN_MAP i END_COLUMN_MAP makra do utworzenia mapy kolumn, jak w tym przykładzie:

    ```cpp
    // Table accessor class
        class COrdersAccessor; // Table class
        class COrders : public CTable<CAccessor<COrdersAccessor>>;
    // ...
    // Column map
        BEGIN_COLUMN_MAP(COrderDetailsAccessor)
            COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
            COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
            // ...
        END_COLUMN_MAP()
    ```

  - Jeśli wybierzesz **typ** **polecenia**konsumenta, `db_source` kreator `db_command` użyje atrybutów i atrybutów oraz użyje `db_column` do utworzenia mapy kolumny. Na przykład tworzy tę mapę:

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     zamiast używać deklaracji klasy dostępu do polecenia i polecenia w pliku .h klasy polecenia, na przykład:

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     Aby uzyskać więcej informacji, zobacz [Podstawowa mechanika atrybutów.](../../windows/basic-mechanics-of-attributes.md)

- **Typ**

   Wybierz jeden z tych przycisków radiowych, aby `CTable` określić, czy klasa konsumenta będzie pochodną lub `CCommand` (domyślnie).

  - **Tabeli**

      Tę opcję należy zaznaczyć, jeśli chcesz użyć `CTable` lub `db_table` utworzyć deklaracje klas akcesorów tabeli i tabeli.

  - **Polecenie**

      Tę opcję należy zaznaczyć, jeśli chcesz użyć `CCommand` lub `db_command` utworzyć deklaracje klasy akcesora poleceń i poleceń. Jest to wybór domyślny.

- **Pomoc techniczna**

   Zaznacz pola wyboru, aby określić rodzaje aktualizacji, które mają być obsługiwane przez konsumenta (wartość domyślna to brak). Każdy z poniższych zestaw [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) i odpowiednie wpisy dla [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) na mapie zestawu właściwości.

  - **Zmień**

      Określa, że konsument obsługuje aktualizacje danych wiersza w zestawie wierszy.

  - **Insert**

      Określa, że obsługa obsługi klienta wstawiania wierszy do zestawu wierszy.

  - **Usuwanie**

      Określa, że obsługa klienta usunięcie wierszy z zestawu wierszy.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[ATL OLE DB Konsument](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Parametry połączenia i łącza danych (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
