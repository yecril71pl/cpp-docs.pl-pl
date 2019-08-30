---
title: Kreator konsumenta MFC ODBC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 84fdc0d180f5b1b0f2e64c3597cb474611ad3914
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177432"
---
# <a name="mfc-odbc-consumer-wizard"></a>Kreator konsumenta MFC ODBC

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten Kreator konfiguruje klasę zestawu rekordów ODBC i powiązania danych niezbędne do uzyskania dostępu do określonego źródła danych.

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

  Przycisk **Źródło danych** umożliwia skonfigurowanie określonego źródła danych przy użyciu określonego sterownika ODBC. Aby uzyskać więcej informacji na temat plików źródła danych (DSN), zobacz [plikowe źródła danych](/sql/odbc/reference/file-data-sources) w zestawie ODBC SDK.

  Okno dialogowe **Wybieranie źródła danych** zawiera dwie karty:

  - Karta **źródła danych pliku** :

     Pole **Szukaj w** określa katalog, w którym należy wybrać pliki, które mają być używane jako źródła danych. Wartość domyślna to \Program Files\Common Files\ODBC\Data sources. Istniejące plikowe źródła danych (pliki. DSN) pojawiają się w głównym polu listy. Źródła danych można skonfigurować wcześniej za pomocą karty Plikowe **DSN** [administratora źródła danych ODBC](/sql/odbc/admin/odbc-data-source-administrator)lub utworzyć nowe przy użyciu tego okna dialogowego.

     Aby utworzyć nowe plikowe źródło danych z tego okna dialogowego, kliknij `New` , aby określić nazwę DSN; zostanie wyświetlone okno dialogowe **Utwórz nowe źródło danych** . W oknie dialogowym **Utwórz nowe źródło danych** wybierz odpowiedni sterownik i kliknij `Next`przycisk **Przeglądaj**, a następnie wybierz nazwę pliku, który ma być używany jako źródło danych (wybierz opcję "wszystkie pliki", aby wyświetlić pliki inne niż DSN, takie jak pliki xls); kliknij przycisk , a następnie kliknij przycisk **Zakończ.** `Next` (W przypadku wybrania pliku bez nazwy DSN zostanie wyświetlone okno dialogowe specyficzne dla sterownika, takie jak "Instalator ODBC programu Microsoft Excel", który przekonwertuje plik na nazwę DSN).

     > [!NOTE]
     > Możesz również utworzyć nowe plikowe źródło danych za pomocą administratora źródła danych ODBC. Z menu **Start** wybierz kolejno opcje **Ustawienia**, **Panel sterowania**, **Narzędzia administracyjne**, **źródła danych (ODBC)** , a następnie **administratora źródła danych ODBC**.

     Pole **nazwa DSN** umożliwia określenie nazwy źródła danych pliku. Musisz się upewnić, że nazwa DSN jest zakończona odpowiednimi rozszerzeniami plików, takimi jak pliki xls dla programu Excel lub pliki. mdb dla plików dostępu.

     Aby uzyskać więcej informacji na temat nazw DSN, zobacz [plikowe źródła danych](/sql/odbc/reference/file-data-sources) w zestawie ODBC SDK.

  - Karta **źródła danych komputera** :

     Ta karta zawiera listę źródeł danych systemu i użytkownika. Źródła danych użytkownika są specyficzne dla użytkownika na tej maszynie. Systemowe źródła danych mogą być używane przez wszystkich użytkowników na tym komputerze lub w usłudze systemowo. Zobacz [źródła danych maszyn](/sql/odbc/reference/machine-data-sources) w zestawie SDK ODBC

     Aby uzyskać więcej informacji na temat źródeł danych ODBC, zobacz [źródła danych](/sql/odbc/reference/data-sources) w zestawie ODBC SDK.

  Kliknij przycisk **OK**, aby zakończyć. Zostanie wyświetlone okno dialogowe **Wybieranie obiektu bazy danych** . W tym oknie dialogowym Wybierz tabelę lub widok, które będą używane przez konsumenta. Należy pamiętać, że można wybrać wiele widoków i tabel, przytrzymując klawisz sterowania podczas klikania elementów. Kliknij przycisk **OK**, aby zakończyć.

- **Class**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **plik h**

   Nazwa pliku nagłówkowego klasy odbiorcy, domyślnie oparta na nazwie wybranego źródła danych pliku lub komputera.

- **plik. cpp**

   Nazwa pliku implementacji klasy odbiorcy, domyślnie oparta na nazwie wybranego źródła danych pliku lub komputera.

- **Typ**

   Określa, czy zestaw rekordów jest dynamicznym (domyślnym) czy migawką.

   - **Zestaw dynamiczny**: Określa, że zestaw rekordów jest dynamiczny. Dynamiczny jest wynikiem zapytania, które zawiera indeksowany widok do danych zapytania bazy danych. Zestaw dynamiczny pamięci podręcznej tworzy tylko integralny indeks danych oryginalnych i w ten sposób oferuje wzrost wydajności dla migawki. Indeks wskazuje bezpośrednio na każdy rekord znaleziony w wyniku zapytania i wskazuje, czy rekord został usunięty. Masz również dostęp do zaktualizowanych informacji w rekordach zapytań. Domyślnie włączone.

   - **Migawka**: Określa, że zestaw rekordów jest migawką. Migawka jest wynikiem zapytania i jest widokiem w bazie danych w jednym punkcie czasu. Wszystkie rekordy Znalezione w wyniku zapytania są buforowane, więc nie są widoczne żadne zmiany w oryginalnych rekordach.

- **Powiąż wszystkie kolumny**

   Określa, czy wszystkie kolumny w zaznaczonej tabeli są powiązane. Jeśli zaznaczysz to pole (domyślnie), wszystkie kolumny są powiązane; Jeśli to pole nie zostanie zaznaczone, nie są powiązane żadne kolumny i musisz powiązać je ręcznie z klasą zestawów rekordów.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Korzystanie z MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
