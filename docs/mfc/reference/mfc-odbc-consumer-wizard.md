---
title: Kreator konsumenta MFC ODBC
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: f86eded7cc7c04a85b1bcd93e917bd5a2b5c9696
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590882"
---
# <a name="mfc-odbc-consumer-wizard"></a>Kreator konsumenta MFC ODBC

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 tego kreatora kodu jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie ulega zmianie poprzez usunięcie tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wypełnij [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.

Ten kreator konfiguruje klasę zestawu rekordów ODBC i powiązania danych niezbędnych do uzyskania dostępu z określonym źródłem danych.

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

   **Źródła danych** przycisk umożliwia konfigurowanie określonym źródłem danych przy użyciu podanego sterownika ODBC. Aby uzyskać więcej informacji na temat pliki źródła danych (DSN), zobacz [plikowych źródeł danych](/previous-versions/windows/desktop/ms715401) w zestawie SDK ODBC.

   **Wybierz źródło danych** okno dialogowe ma dwie karty:

   - **Źródło danych pliku** karty:

      **Przeszukania** pole określa katalog, w którym można wybrać pliki, które ma być używany jako źródła danych. Wartość domyślna to \Program Files\Common Files\ODBC\Data źródeł. Istniejących źródeł danych plików (pliki DSN) są wyświetlane w polu listy głównego. Możesz albo Konfigurowanie źródeł danych w przód od chwili **plikową nazwę DSN** karcie [Administrator źródła danych ODBC](/previous-versions/windows/desktop/ms714024), lub utworzyć nowe przy użyciu tego okna dialogowego.

      Aby utworzyć nowe źródło danych pliku to okno dialogowe, kliknij przycisk `New` do określenia nazwy DSN; **Utwórz nowe źródło danych** pojawi się okno dialogowe. W **Utwórz nowe źródło danych** okna dialogowego pole, wybierz odpowiedni sterownik i kliknij `Next`; kliknij **Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło danych (musisz wybrać "Wszystkie pliki" do Wyświetl DSN innych plików, takich jak pliki xls); Kliknij przycisk `Next`, a następnie kliknij przycisk **Zakończ**. (Jeśli wybranego pliku DSN nie zostanie wyświetlony okno dialogowe specyficzne dla sterownika, takie jak "ODBC Instalatora programu Microsoft Excel," który przekonwertuje pliku DSN).

      > [!NOTE]
      > Można również utworzyć nowe źródło danych pliku wcześniej przy użyciu Administratora źródła danych ODBC. Z **Start** menu, wybierz opcję **ustawienia**, **Panelu sterowania**, **narzędzia administracyjne**, **źródła danych (ODBC)**, a następnie **Administrator źródła danych ODBC**.

      **Nazwa DSN** okno pozwala określić nazwę źródła danych pliku. Należy się upewnić, że nazwa DSN kończy się rozszerzeniem odpowiedniego pliku, takie jak xls dla plików programu Excel lub .mdb dla plików programu Access.

      Aby uzyskać więcej informacji na temat nazw DSN, zobacz [plikowych źródeł danych](/previous-versions/windows/desktop/ms715401) w zestawie SDK ODBC.

   - **Źródła danych komputera** karty:

      Ta karta zawiera listę systemu oraz źródeł danych użytkownika. Źródła danych użytkownika są specyficzne dla użytkownika na tym komputerze. Systemowe źródła danych może służyć przez wszystkich użytkowników na tym komputerze lub w usłudze ogólnosystemowe. Zobacz [źródeł danych komputera](/previous-versions/windows/desktop/ms710952) w zestawie SDK ODBC

      Aby uzyskać więcej informacji na temat źródeł danych ODBC, zobacz [źródeł danych](/previous-versions/windows/desktop/ms711688) w zestawie SDK ODBC.

   Kliknij przycisk **OK** na zakończenie. **Obiektu bazy danych wybierz** pojawi się okno dialogowe. To okno dialogowe Wybierz tabelę lub wyświetlić, które będą używane przez konsumenta. Należy pamiętać, że przytrzymać klawisz control i klikając elementy można wybrać wiele widoków i tabel. Kliknij przycisk **OK** na zakończenie.

- **Class**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **plik .h**

   Nazwa pliku nagłówkowego klasy konsumenta, domyślnie na podstawie nazwy źródła danych maszyny lub pliku, które wybrano.

- **Plik CPP**

   Nazwa pliku implementacji klasy konsumenta, domyślnie na podstawie nazwy źródła danych maszyny lub pliku, które wybrano.

- **Typ**

   Określa, czy zestaw rekordów jest dynamiczny (ustawienie domyślne) lub migawka.

   - **Zestaw dynamiczny**: Określa, czy zestaw rekordów jest dynamiczny. Dynamiczny jest wynikiem kwerendę, która zawiera widok indeksowany do kwerendy bazy danych. Dynamiczny przechowuje tylko całkowitą indeksu do oryginalnych danych i związku z tym jest wydajność uzyskiwać za pośrednictwem migawki. Punkty indeksu bezpośrednio do każdego wybranego rekordu można odnaleźć wyniku zapytania i wskazuje, gdy rekord zostanie usunięty. Masz również dostęp do aktualnych informacji w rekordach kwerendy. Domyślnie włączone.

   - **Migawka**: Określa, czy zestaw rekordów jest migawką. Migawka jest rezultat zapytania i wgląd w bazę danych w jednym punkcie w czasie. Wszystkie rekordy, które można odnaleźć wyniku kwerendy są buforowane, więc nie widzisz wszelkie zmiany, oryginalnym rekordów.

- **Powiąż wszystkie kolumny**

   Określa, czy wszystkie kolumny w tabeli są powiązane. Jeśli wybierzesz to pole (ustawienie domyślne), wszystkie kolumny są powiązane; Jeśli to pole nie jest zaznaczone, są powiązane żadne kolumny i musisz powiązać je ręcznie w klasie zestawu rekordów.

## <a name="see-also"></a>Zobacz też

[Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)

