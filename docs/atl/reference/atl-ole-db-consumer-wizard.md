---
title: Kreator konsumenta OLE DB ATL
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: f7bdc371e5575375f5e72a1a6c0c51890921b1f4
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353132"
---
# <a name="atl-ole-db-consumer-wizard"></a>Kreator konsumenta OLE DB ATL

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten Kreator konfiguruje OLE DB klasę konsumenta z powiązaniami danych, które są niezbędne do uzyskania dostępu do określonego źródła danych za pomocą określonego dostawcy OLE DB.

> [!NOTE]
> Ten Kreator wymaga kliknięcia przycisku **źródła danych** , aby wybrać źródło danych przed wprowadzeniem nazw w `Class` polach **pliku i. h** .

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

   Przycisk **Źródło danych** umożliwia skonfigurowanie określonego źródła danych przy użyciu określonego dostawcy OLE DB. Po kliknięciu tego przycisku zostanie wyświetlone okno dialogowe **Właściwości łącza danych** . Aby uzyskać więcej informacji na temat tworzenia parametrów połączenia i okna dialogowego **Właściwości łącza danych** , zobacz [Omówienie interfejsu API linku do danych](/previous-versions/windows/desktop/ms718102(v=vs.85)) w dokumentacji Windows SDK.

   Poniższe informacje dodatkowe opisują karty w oknie dialogowym **Właściwości łącza danych** .

  - Karta **dostawca**

      Wybierz odpowiedniego dostawcę, aby zarządzać połączeniem ze źródłem danych. Typ dostawcy jest zwykle określany na podstawie typu bazy danych, z którą nawiązywane jest połączenie. Kliknij przycisk **dalej** lub kliknij kartę **połączenie** .

  - Karta **połączenie**

      Zawartość tej karty zależy od wybranego dostawcy. Chociaż istnieje wiele typów dostawców, ta sekcja obejmuje połączenia dla dwóch najpopularniejszych danych SQL i ODBC. Inne są podobne do różnych pól opisanych tutaj.

      Dla danych SQL:

      1. **Wybierz lub wprowadź nazwę serwera:** Kliknij menu rozwijane listę, aby wyświetlić wszystkie zarejestrowane serwery danych w sieci, a następnie wybierz jedną z nich.

      1. **Wprowadź informacje, aby zalogować się na serwerze:** Wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

         > [!NOTE]
         > Występuje problem z zabezpieczeniami z funkcją "Zezwalaj na zapisywanie hasła" okna dialogowego Właściwości łącza danych. W obszarze "Wprowadź informacje, aby zalogować się na serwerze" Istnieją dwa przyciski radiowe:
         >
         > - **Korzystanie z zintegrowanych zabezpieczeń systemu Windows NT**
         > - **Użyj określonej nazwy użytkownika i hasła**
         >
         > W przypadku wybrania opcji **Użyj konkretnej nazwy użytkownika i hasła**można zapisać hasło (przy użyciu pola wyboru "Zezwalaj na zapisywanie hasła"). Jednak ta opcja nie jest bezpieczna. Zalecane jest wybranie opcji **Użyj zintegrowanych zabezpieczeń systemu Windows NT**. Ta opcja jest bezpieczna, ponieważ szyfruje hasło.
         > Mogą wystąpić sytuacje, w których chcesz wybrać opcję "Zezwalaj na zapisywanie hasła". Na przykład w przypadku zwalniania biblioteki z rozwiązaniem prywatnej bazy danych nie należy bezpośrednio uzyskiwać dostępu do bazy danych, ale zamiast tego należy użyć aplikacji warstwy środkowej do zweryfikowania użytkownika (za pomocą dowolnego wybranego przez Ciebie schematu uwierzytelniania), a następnie ograniczenia sortowania danych dostępnych dla użytkownika.

      1. **Wybierz bazę danych na serwerze:** Kliknij menu rozwijane listę, aby wyświetlić wszystkie zarejestrowane bazy danych na serwerze danych, a następnie wybierz jeden z nich.

         \- oraz

         **Dołącz plik bazy danych jako nazwę bazy danych:** Określ plik, który ma być używany jako baza danych programu; Wprowadź jawną nazwę ścieżki.

      Dla danych ODBC:

      1. **Określ źródło danych:** Można użyć nazwy źródła danych lub parametrów połączenia.

         **Użyj nazwy źródła danych:** Ta lista rozwijana przedstawia źródła danych zarejestrowane na komputerze. Źródła danych można skonfigurować wcześniej za pomocą administratora źródła danych ODBC.

         \- oraz

         **Użyj parametrów połączenia:** Wprowadź już uzyskane parametry połączenia lub kliknij przycisk **Kompiluj** . zostanie wyświetlone okno dialogowe **Wybieranie źródła danych** . Wybierz plik lub źródło danych maszyny, a następnie kliknij przycisk **OK**.

         > [!NOTE]
         > Parametry połączenia można uzyskać, wyświetlając właściwości istniejącego połączenia w **Eksplorator serwera**lub można utworzyć połączenie przez dwukrotne kliknięcie pozycji **dodaj połączenie** w **Eksplorator serwera**.

      1. **Wprowadź informacje, aby zalogować się na serwerze:** Wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

      1. Wprowadź początkowy wykaz do użycia.

      1. Kliknij pozycję **Testuj połączenie**. Jeśli test zakończy się pomyślnie, kliknij przycisk **OK**. Jeśli nie, sprawdź informacje dotyczące logowania, wypróbuj inną bazę danych lub wypróbuj inny serwer danych.

  - Karta **Zaawansowane**

      **Ustawienia sieci:** Określ **poziom personifikacji** (poziom personifikacji, który może być używany przez serwer podczas personifikowania klienta; odpowiada bezpośrednio na poziomy personifikacji RPC) i **poziom ochrony** (poziom ochrony danych przesyłanych między klientem a serwerem; odpowiada bezpośrednio na poziomy ochrony RPC).

      **Inne:** W obszarze **limit czasu połączenia**Określ liczbę sekund czasu bezczynności dozwoloną przed upływem limitu czasu. W obszarze **uprawnienia dostępu**Określ uprawnienia dostępu do połączenia danych.

      Więcej informacji o zaawansowanych właściwościach inicjowania znajduje się w dokumentacji dostarczonej z konkretnym dostawcą OLE DB.

  - **Wszystkie** karty

      Na tej karcie jest wyświetlane podsumowanie właściwości inicjalizacji określonego źródła danych i połączenia. Można edytować te wartości.

      Kliknij przycisk **OK**, aby zakończyć. Zostanie wyświetlone okno dialogowe **Wybieranie obiektu bazy danych** . W tym oknie dialogowym Wybierz tabelę, widok lub procedurę przechowywaną, która będzie używana przez klienta.

- **Klasa**

   Po wybraniu źródła danych to pole jest wypełniane domyślną nazwą klasy na podstawie wybranej tabeli lub procedury składowanej (zobacz **Wybierz źródło danych** poniżej). Można edytować nazwę klasy.

- **plik h**

   Po wybraniu źródła danych to pole zostanie wypełnione domyślną nazwą klasy nagłówka w oparciu o wybraną tabelę lub procedurę przechowywaną (zobacz **Wybierz źródło danych** poniżej). Można edytować nazwę pliku nagłówka lub wybrać istniejący plik nagłówkowy.

- **Przypisanych**

   Ta opcja określa, czy Kreator utworzy klasy konsumenckie przy użyciu atrybutów lub deklaracji szablonu. Po wybraniu tej opcji Kreator używa atrybutów zamiast deklaracji szablonu (jest to opcja domyślna). Po oddzieleniu zaznaczenia tej opcji Kreator używa deklaracji szablonu zamiast atrybutów.

  - W przypadku wybrania **typu** odbiorcy **tabeli**Kreator używa `db_source` `db_table` atrybutów i do tworzenia deklaracji klasy metody dostępu tabeli i tabeli, a `db_column` następnie używa do tworzenia mapy kolumn. Na przykład tworzy tę mapę:

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     Zamiast używać `CTable` klasy szablonu do deklarowania klasy akcesora tabeli i tabeli oraz makr BEGIN_COLUMN_MAP i END_COLUMN_MAP do tworzenia mapy kolumn, jak w poniższym przykładzie:

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

  - W przypadku wybrania **typu** odbiorcy **polecenia**Kreator używa `db_source` `db_command` atrybutów i i używa `db_column` do tworzenia mapy kolumn. Na przykład tworzy tę mapę:

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     Zamiast używać deklaracji klas metody dostępu polecenia i polecenia w pliku h klasy polecenia, na przykład:

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     Aby uzyskać więcej informacji [, zobacz podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

- **Typ**

   Wybierz jeden z tych przycisków radiowych, aby określić, czy Klasa odbiorcy będzie pochodna, czy `CTable` `CCommand` (domyślnie).

  - **Tabela**

      Wybierz tę opcję, jeśli chcesz użyć `CTable` lub, `db_table` Aby utworzyć deklaracje klas metody dostępu tabeli i tabeli.

  - **Polecenie**

      Wybierz tę opcję, jeśli chcesz użyć `CCommand` polecenia lub, `db_command` Aby utworzyć deklaracje klas metody dostępu poleceń i poleceń. Jest to wybór domyślny.

- **Pomoc techniczna**

   Zaznacz pola wyboru, aby określić rodzaje aktualizacji, które mają być obsługiwane przez odbiorcę (wartość domyślna to None). Każdy z poniższych elementów ustawi [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) i odpowiednie wpisy dla [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) na mapie zestawu właściwości.

  - **Zmień**

      Określa, że konsument obsługuje aktualizacje danych wierszy w zestawie wierszy.

  - **Insert**

      Określa, że konsument obsługuje wstawianie wierszy do zestawu wierszy.

  - **Usuwanie**

      Określa, że konsument obsługuje usuwanie wierszy z zestawu wierszy.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Klient ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Parametry połączenia i linki danych (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
