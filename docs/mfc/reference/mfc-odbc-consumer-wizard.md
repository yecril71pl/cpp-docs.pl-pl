---
title: Kreator konsumenta MFC ODBC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373024"
---
# <a name="mfc-odbc-consumer-wizard"></a>Kreator konsumenta MFC ODBC

::: moniker range="vs-2019"

Ten kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator konfiguruje klasę zestaw rekordów ODBC i powiązania danych niezbędne do uzyskania dostępu do określonego źródła danych.

## <a name="uielement-list"></a>Lista elementów UI

- **Źródło danych**

  Przycisk **Źródło danych** umożliwia skonfigurowanie określonego źródła danych przy użyciu określonego sterownika ODBC. Aby uzyskać więcej informacji na temat plików źródłowych danych (DSN), zobacz [Źródła danych plików](/sql/odbc/reference/file-data-sources) w SDK ODBC.

  Okno dialogowe **Wybieranie źródła danych** ma dwie karty:

  - Karta **Źródło danych pliku:**

     Pole **Szukaj w** określa katalog, w którym mają być wybierane pliki, które mają być używane jako źródła danych. Wartością domyślną jest \Program Files\Common Files\ODBC\Data Sources. Istniejące źródła danych plików (pliki dsn) są wyświetlane w polu listy głównej. Źródła danych można skonfigurować z wyprzedzeniem za pomocą karty **Plik DSN** na [administratorze źródła danych ODBC](/sql/odbc/admin/odbc-data-source-administrator)lub utworzyć nowe za pomocą tego okna dialogowego.

     Aby utworzyć nowe źródło danych pliku z `New` tego okna dialogowego, kliknij, aby określić nazwę DSN; zostanie wyświetlone okno dialogowe **Tworzenie nowego źródła danych.** W oknie dialogowym **Tworzenie nowego źródła danych** `Next`wybierz odpowiedni sterownik i kliknij przycisk ; kliknij **przycisk Przeglądaj**i wybierz nazwę pliku, który ma być używany jako źródło danych (należy wybrać opcję "Wszystkie pliki", aby wyświetlić pliki inne niż DSN, takie jak pliki xls); kliknij `Next`przycisk , a następnie kliknij przycisk **Zakończ**. (Jeśli wybrano plik niezwiązany z DSN, zostanie wyświetlone okno dialogowe specyficzne dla sterownika, takie jak "Instalator programu ODBC Microsoft Excel", które spowoduje przekonwertowanie pliku na nazwę DSN).

     > [!NOTE]
     > Można również utworzyć nowe źródło danych pliku wcześniej za pomocą administratora źródła danych ODBC. Z menu **Start** wybierz polecenie **Ustawienia**, **Panel sterowania**, Narzędzia **administracyjne**, **Źródła danych (ODBC),** a następnie **administrator źródła danych ODBC**.

     Pole **Nazwa DSN** umożliwia określenie nazwy źródła danych pliku. Należy upewnić się, że nazwa DSN kończy się odpowiednim rozszerzeniem pliku, takim jak xls dla plików excela lub pliki mdb programu Access.

     Aby uzyskać więcej informacji na temat dsn, zobacz [Źródła danych plików](/sql/odbc/reference/file-data-sources) w SDK ODBC.

  - Karta **Źródło danych maszyny:**

     Ta karta zawiera listę źródeł danych systemowych i danych użytkownika. Źródła danych użytkownika są specyficzne dla użytkownika na tym komputerze. Systemowe źródła danych mogą być używane przez wszystkich użytkowników na tym komputerze lub w usłudze ogólnosystemowej. Zobacz [Źródła danych maszyn w](/sql/odbc/reference/machine-data-sources) SDK ODBC

     Aby uzyskać więcej informacji na temat źródeł danych ODBC, zobacz [Źródła danych](/sql/odbc/reference/data-sources) w SDK ODBC.

  Kliknij przycisk **OK**, aby zakończyć. Zostanie wyświetlone okno dialogowe **Wybierz obiekt bazy danych.** W tym oknie dialogowym wybierz tabelę lub widok, którego będzie używać konsument. Należy pamiętać, że można wybrać wiele widoków i tabel, przytrzymując klawisz sterowania podczas klikania elementów. Kliknij przycisk **OK**, aby zakończyć.

- **Klasa**

   Nazwa klasy konsumenta, domyślnie na podstawie nazwy wybranego źródła danych pliku lub komputera.

- **.h plik**

   Nazwa pliku nagłówka klasy konsumenta, domyślnie na podstawie nazwy wybranego pliku lub źródła danych komputera.

- **.cpp**

   Nazwa pliku implementacji klasy konsumenta, domyślnie na podstawie nazwy wybranego źródła danych pliku lub komputera.

- **Typ**

   Określa, czy zestaw rekordów jest zestawem dynaset (domyślnym) czy migawką.

  - **Dynaset**: Określa, że zestaw rekordów jest zestawem dynaset. Dynaset jest wynikiem kwerendy, która udostępnia widok indeksowany do danych poszukiwanej bazy danych. Dynaset buforuje tylko integralną indeks do oryginalnych danych i w związku z tym oferuje przyrost wydajności w migawce. Indeks wskazuje bezpośrednio na każdy rekord znaleziony w wyniku kwerendy i wskazuje, czy rekord został usunięty. Masz również dostęp do zaktualizowanych informacji w poszukiwanych rekordach. Domyślnie włączone.

  - **Migawka**: Określa, że plik recordset jest migawką. Migawka jest wynikiem kwerendy i jest widok do bazy danych w jednym momencie w czasie. Wszystkie rekordy znalezione w wyniku kwerendy są buforowane, więc nie są widoczne żadne zmiany w oryginalnych rekordach.

- **Powiąż wszystkie kolumny**

   Określa, czy wszystkie kolumny w wybranej tabeli są powiązane. Jeśli zaznaczysz to pole (domyślnie), wszystkie kolumny są powiązane; Jeśli to pole nie zostanie zaznaczone, żadne kolumny nie są powiązane i należy je powiązać ręcznie w klasie recordset.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[MFC ODBC zużywają](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)
