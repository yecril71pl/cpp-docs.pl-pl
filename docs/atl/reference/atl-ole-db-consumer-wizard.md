---
title: Kreator konsumenta OLE DB ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/31/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 163949c4421cca8e4d5e414a18bda4ed98f32d3d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861645"
---
# <a name="atl-ole-db-consumer-wizard"></a>Kreator konsumenta OLE DB ATL

Ten kreator konfiguruje klasę konsumenta OLE DB przy użyciu powiązania danych niezbędnych do uzyskania dostępu z określonym źródłem danych przy użyciu określonego dostawcy OLE DB.

> [!NOTE]
> Ten kreator, należy kliknąć przycisk **źródła danych** przycisk, aby wybrać źródło danych, przed wpisaniem nazw w `Class` i **plik .h klasy** pola.

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

   **Źródła danych** przycisk umożliwia konfigurowanie określonym źródłem danych przy użyciu określonego dostawcy OLE DB. Po kliknięciu tego przycisku **właściwości Linku danych** pojawi się okno dialogowe. Aby uzyskać więcej informacji na temat tworzenia parametrów połączenia i **właściwości Linku danych** okno dialogowe, zobacz [omówienie interfejsu API łącza danych](/previous-versions/windows/desktop/ms718102\(v=vs.85\)) w dokumentacji zestawu Windows SDK.

   Następujące dodatkowe informacje w tym artykule opisano ustawienia na kartach **właściwości Linku danych** okno dialogowe.

   - **Dostawca** kartę

      Wybierz odpowiedniego dostawcę, zarządzać połączeniem ze źródła danych. Typ dostawcy zazwyczaj jest określana przez typ bazy danych, z którym chcesz się połączyć. Kliknij przycisk **dalej** przycisku, lub kliknij przycisk **połączenia** kartę.

   - **Połączenie** kartę

      Zawartość na tej karcie zależą od wybranego dostawcy. Chociaż istnieje wiele typów dostawców, w tej sekcji omówiono połączenia dwóch typowych: danych SQL i ODBC. Inne są podobne zmiany w polach opisane w tym miejscu.

      Dla danych SQL:

      1. **Wybierz lub wprowadź nazwę serwera:** kliknij menu listy rozwijanej, aby wyświetlić wszystkich danych zarejestrowanych serwerów w sieci, a następnie wybierz jedno.

      1. **Wprowadź informacje dotyczące logowania na serwerze:** wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

         > [!NOTE]
         > Istnieje problem z zabezpieczeniami, za pomocą funkcji "Zezwalaj na zapisywanie hasła" okno dialogowe właściwości połączenia danych. W polu "Wprowadź informacje do logowania się do serwera" istnieją dwa przyciski radiowe:
         >
         > - **Użyj zabezpieczeń Windows NT zintegrowane**
         > - **Użyj określonej nazwy użytkownika i hasła**
         >
         > Jeśli wybierzesz **Użyj określonej nazwy użytkownika i hasła**, masz możliwość zapisania hasła (przy użyciu pola wyboru "Zezwalaj na zapisywanie hasła"); Jednakże, ta opcja nie jest bezpieczne. Zaleca się, że wybrano **Użyj Windows NT zintegrowane zabezpieczenia**; ta opcja jest bezpieczna, ponieważ jego szyfruje hasło.
         > Może to być sytuacje, w których chcesz wybrać "Zezwalaj na zapisywanie hasła." Na przykład jeśli są zwalnianie biblioteki za pomocą rozwiązania prywatnej bazy danych, możesz powinna nie bezpośrednio dostęp do bazy danych, ale zamiast tego użyć aplikacji warstwy środkowej do weryfikacji użytkownika (za pośrednictwem dowolnego schematu uwierzytelniania, możesz wybrać), a następnie ograniczyć sortowanie danych dostępne dla użytkownika.

      1. **Wybierz bazę danych na serwerze:** kliknij menu listy rozwijanej, aby wyświetlić wszystkie zarejestrowane baz danych na serwerze danych, a następnie wybierz jedno.

         \- lub —

         **Dołącz plik bazy danych jako nazwę bazy danych:** określony plik ma być używany jako bazy danych; wprowadź jawną nazwę ścieżki.

      Dla danych ODBC:

      1. **Określ źródło danych:** można użyć nazwy źródła danych lub parametrów połączenia.

         **Użyj nazwy źródła danych:** tej listy rozwijanej wyświetla źródła danych zarejestrowane na tym komputerze. Możesz skonfigurować źródła danych, które wcześniej przy użyciu Administratora źródła danych ODBC

         \- lub —

         **Użyj parametrów połączenia:** albo wprowadź parametry połączenia, lub kliknij przycisk już uzyskali **kompilacji** przycisk; **wybierz źródło danych** pojawi się okno dialogowe. Wybierz źródło danych maszyny lub pliku, a następnie kliknij przycisk **OK**.

         > [!NOTE]
         > Parametry połączenia można uzyskać, wyświetlając właściwości istniejącego połączenia w **Eksploratora serwera**, lub można utworzyć połączenie przez dwukrotne kliknięcie **Dodaj połączenie** w **serwera Eksplorator**.

      1. **Wprowadź informacje dotyczące logowania na serwerze:** wprowadź nazwę użytkownika i hasło, aby zalogować się do serwera danych.

      1. Wprowadź początkowy katalog do użycia.

      1. Kliknij przycisk **Testuj połączenie**; Jeśli test zakończy się pomyślnie, kliknij przycisk **OK**. W przeciwnym razie sprawdź informacje logowania, spróbuj innej bazy danych lub spróbować innego serwera danych.

   - **Zaawansowane** kartę

      **Ustawienia sieci:** określ **poziom personifikacji** (poziom personifikacji, serwer może być używany podczas personifikowania klienta; odpowiada bezpośrednio z poziomu personifikacji RPC) i  **Poziom ochrony** (odpowiedniego poziomu ochrony danych przesyłanych między klientem i serwerem; odpowiada bezpośrednio do poziomów ochrony RPC).

      **Inne:** w **limit czasu połączenia**, określ czas w sekundach czas bezczynności, zanim zostanie przekroczony limit czasu. W **uprawnień dostępu**, określanie uprawnień dostępu w ramach połączenia danych.

       Aby uzyskać więcej informacji na temat zaawansowanych właściwości inicjujących zapoznaj się z dokumentacją dostarczoną z każdego dostawcy OLE DB.

   - **Wszystkie** kartę

      Ta karta przedstawia podsumowanie właściwości inicjowania dla źródła danych i połączenia, które zostały określone. Możesz edytować te wartości.

   Kliknij przycisk **OK** na zakończenie. **Obiektu bazy danych wybierz** pojawi się okno dialogowe. To okno dialogowe Wybierz tabelę, widoku lub procedury składowanej, która będzie używana przez konsumenta.

- **Class**

   Po wybraniu źródła danych, to pole jest wypełniane domyślną nazwę klasy na podstawie tabeli lub procedury składowanej, które wybrano (zobacz **wybierz źródło danych** poniżej). Można edytować nazwę klasy.

- **plik .h**

   Po wybraniu źródła danych, to pole jest wypełniane domyślną nazwę klasy nagłówek na podstawie tabeli lub procedury składowanej, które wybrano (zobacz **wybierz źródło danych** poniżej). Możesz zmienić nazwę pliku nagłówka, lub wybrać istniejący plik nagłówkowy.

- **Opartego na atrybutach**

   Ta opcja określa, czy Kreator utworzy klasy konsumentów przy użyciu atrybutów lub deklaracji szablonu. Po wybraniu tej opcji, kreator używa atrybutów zamiast deklaracji szablonu (jest to opcja domyślna). Jeśli wyłączysz tę opcję, kreator używa deklaracji szablonu zamiast atrybutów.

   - Po wybraniu odbiorcy **typu** z **tabeli**, kreator używa `db_source` i `db_table` atrybutów, aby utworzyć tabelę i metoda dostępu do tabeli deklaracje klas i używa `db_column` do Tworzenie mapy kolumny. Na przykład tworzy tej mapy:

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      zamiast używania `CTable` klasy szablonu, aby zadeklarować w tabeli i akcesora tabeli i BEGIN_COLUMN_MAP i END_COLUMN_MAP makra do tworzenia mapy kolumny, jak w poniższym przykładzie:

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

   - Po wybraniu odbiorcy **typu** z **polecenia**, kreator używa `db_source` i `db_command` atrybutów i używa `db_column` do tworzenia mapy kolumny. Na przykład tworzy tej mapy:

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      Zamiast korzystać z poleceń i polecenia deklaracjach metod dostępu do klasy w pliku .h klasy poleceń, na przykład:

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      Zobacz [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.

- **Typ**

   Wybierz jedną z tych przycisków radiowych, aby określić, czy klasa odbiorcy będą pochodzić z `CTable` lub `CCommand` (ustawienie domyślne).

   - **Tabela**

      Wybierz tę opcję, jeśli chcesz używać `CTable` lub `db_table` utworzyć tabelę i metoda dostępu do tabeli deklaracji klasy.

   - **Polecenie**

      Wybierz tę opcję, jeśli chcesz używać `CCommand` lub `db_command` do tworzenia poleceń i polecenia akcesor deklaracji klasy. To ustawienie domyślne.

- **Obsługa**

   Zaznacz pole wyboru, aby określić rodzaje aktualizacje, które są obsługiwane w konsumencie (domyślna wartość to brak). Następujące czynniki ustawi [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892\(v=vs.85\)) i odpowiednie wpisy [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676\(v=vs.85\)) we właściwości ustaw mapy.

   - **Zmiany**

      Określa, że odbiorcy obsługuje aktualizacje danych wierszy w zestawie wierszy.

   - **Wstaw**

      Określa, że użytkownik obsługuje wstawiania wierszy do zestawu wierszy.

   - **Delete**

      Określa, że odbiorcy obsługuje usuwania wierszy z zestawu wierszy.

## <a name="see-also"></a>Zobacz także

[Konsumenta ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Parametry połączenia i połączeń między danymi (OLE DB)](/previous-versions/windows/desktop/ms718376\(v=vs.85\))
