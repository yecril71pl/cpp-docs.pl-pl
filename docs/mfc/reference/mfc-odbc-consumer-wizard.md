---
title: Kreator konsumenta MFC ODBC
ms.date: 05/09/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 2e8741677031ff9b12989d75243a13550d74b608
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707384"
---
# <a name="mfc-odbc-consumer-wizard"></a>Kreator konsumenta MFC ODBC

::: moniker range="vs-2019"

Ten kreator nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator konfiguruje klasę zestawu rekordów ODBC i powiązania danych niezbędnych do uzyskania dostępu z określonym źródłem danych.

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

  **Źródła danych** przycisk umożliwia konfigurowanie określonym źródłem danych przy użyciu podanego sterownika ODBC. Aby uzyskać więcej informacji na temat pliki źródła danych (DSN), zobacz [plikowych źródeł danych](/sql/odbc/reference/file-data-sources) w zestawie SDK ODBC.

  **Wybierz źródło danych** okno dialogowe ma dwie karty:

  - **Źródło danych pliku** karty:

     **Przeszukania** pole określa katalog, w którym można wybrać pliki, które ma być używany jako źródła danych. Wartość domyślna to \Program Files\Common Files\ODBC\Data źródeł. Istniejących źródeł danych plików (pliki DSN) są wyświetlane w polu listy głównego. Możesz albo Konfigurowanie źródeł danych w przód od chwili **plikową nazwę DSN** karcie [Administrator źródła danych ODBC](/sql/odbc/admin/odbc-data-source-administrator), lub utworzyć nowe przy użyciu tego okna dialogowego.

     Aby utworzyć nowe źródło danych pliku to okno dialogowe, kliknij przycisk `New` do określenia nazwy DSN; **Utwórz nowe źródło danych** pojawi się okno dialogowe. W **Utwórz nowe źródło danych** okna dialogowego pole, wybierz odpowiedni sterownik i kliknij `Next`; kliknij **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło danych (musisz wybrać "Wszystkie pliki" do Wyświetl DSN innych plików, takich jak pliki xls); Kliknij przycisk `Next`, a następnie kliknij przycisk **Zakończ**. (Jeśli wybranego pliku DSN nie zostanie wyświetlony okno dialogowe specyficzne dla sterownika, takie jak "ODBC Instalatora programu Microsoft Excel," który przekonwertuje pliku DSN).

     > [!NOTE]
     > Można również utworzyć nowe źródło danych pliku wcześniej przy użyciu Administratora źródła danych ODBC. Z **Start** menu, wybierz opcję **ustawienia**, **Panelu sterowania**, **narzędzia administracyjne**, **źródła danych (ODBC)**, a następnie **Administrator źródła danych ODBC**.

     **Nazwa DSN** okno pozwala określić nazwę źródła danych pliku. Należy się upewnić, że nazwa DSN kończy się rozszerzeniem odpowiedniego pliku, takie jak xls dla plików programu Excel lub .mdb dla plików programu Access.

     Aby uzyskać więcej informacji na temat nazw DSN, zobacz [plikowych źródeł danych](/sql/odbc/reference/file-data-sources) w zestawie SDK ODBC.

  - **Źródła danych komputera** karty:

     Ta karta zawiera listę systemu oraz źródeł danych użytkownika. Źródła danych użytkownika są specyficzne dla użytkownika na tym komputerze. Systemowe źródła danych może służyć przez wszystkich użytkowników na tym komputerze lub w usłudze ogólnosystemowe. Zobacz [źródeł danych komputera](/sql/odbc/reference/machine-data-sources) w zestawie SDK ODBC

     Aby uzyskać więcej informacji na temat źródeł danych ODBC, zobacz [źródeł danych](/sql/odbc/reference/data-sources) w zestawie SDK ODBC.

  Kliknij przycisk **OK**, aby zakończyć. **Obiektu bazy danych wybierz** pojawi się okno dialogowe. To okno dialogowe Wybierz tabelę lub wyświetlić, które będą używane przez konsumenta. Należy pamiętać, że przytrzymać klawisz control i klikając elementy można wybrać wiele widoków i tabel. Kliknij przycisk **OK**, aby zakończyć.

- **Class**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **plik .h**

   Nazwa pliku nagłówkowego klasy konsumenta, domyślnie na podstawie nazwy źródła danych maszyny lub pliku, które wybrano.

- **Plik CPP**

   Nazwa pliku implementacji klasy konsumenta, domyślnie na podstawie nazwy źródła danych maszyny lub pliku, które wybrano.

- **Typ**

   Określa, czy zestaw rekordów jest dynamiczny (ustawienie domyślne) lub migawka.

   - **Dynaset**: Określa, czy zestaw rekordów jest dynamiczny. Dynamiczny jest wynikiem kwerendę, która zawiera widok indeksowany do kwerendy bazy danych. Dynamiczny przechowuje tylko całkowitą indeksu do oryginalnych danych i związku z tym jest wydajność uzyskiwać za pośrednictwem migawki. Punkty indeksu bezpośrednio do każdego wybranego rekordu można odnaleźć wyniku zapytania i wskazuje, gdy rekord zostanie usunięty. Masz również dostęp do aktualnych informacji w rekordach kwerendy. Domyślnie włączone.

   - **Migawka**: Określa, czy zestaw rekordów jest migawką. Migawka jest rezultat zapytania i wgląd w bazę danych w jednym punkcie w czasie. Wszystkie rekordy, które można odnaleźć wyniku kwerendy są buforowane, więc nie widzisz wszelkie zmiany, oryginalnym rekordów.

- **Powiąż wszystkie kolumny**

   Określa, czy wszystkie kolumny w tabeli są powiązane. Jeśli wybierzesz to pole (ustawienie domyślne), wszystkie kolumny są powiązane; Jeśli to pole nie jest zaznaczone, są powiązane żadne kolumny i musisz powiązać je ręcznie w klasie zestawu rekordów.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
