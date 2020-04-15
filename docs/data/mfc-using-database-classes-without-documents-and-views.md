---
title: 'MFC: używanie klas baz danych bez dokumentów i widoków'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360670"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: używanie klas baz danych bez dokumentów i widoków

Czasami nie można użyć architektury dokumentu/widoku struktury w aplikacjach bazy danych. W tym temacie wyjaśniono:

- [Jeśli nie trzeba używać dokumentów,](#_core_when_you_don.92.t_need_documents) takich jak serializacji dokumentów.

- [Opcje kreatora aplikacji](#_core_appwizard_options_for_documents_and_views) do obsługi aplikacji bez serializacji i bez poleceń menu **plik** związanych z dokumentami, takich jak **Nowy**, **Otwórz,** **Zapisz**i **Zapisz jako**.

- [Jak pracować z aplikacją, która używa minimalnego dokumentu](#_core_applications_with_minimal_documents).

- [Jak uporządkować aplikację bez dokumentu lub widoku](#_core_applications_with_no_document).

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Gdy nie potrzebujesz dokumentów

Niektóre aplikacje mają odrębną koncepcję dokumentu. Te aplikacje zazwyczaj załadować wszystkie lub większość pliku z magazynu do pamięci za pomocą **polecenia File Open.** Zapisują zaktualizowany plik z powrotem do magazynu na raz za pomocą polecenia **Zapisz plik** lub **Zapisz jako.** To, co widzi użytkownik, to plik danych.

Niektóre kategorie aplikacji nie wymagają jednak dokumentu. Aplikacje baz danych działają pod względem transakcji. Aplikacja wybiera rekordy z bazy danych i przedstawia je użytkownikowi, często po jednym na raz. To, co widzi użytkownik, to zwykle pojedynczy bieżący rekord, który może być jedynym w pamięci.

Jeśli aplikacja nie wymaga dokumentu do przechowywania danych, można zrezygnować z niektórych lub wszystkich struktury architektury dokumentu/widoku. To, z jakiej możesz zrezygnować, zależy od preferowanego podejścia. Możesz:

- Użyj minimalnego dokumentu jako miejsca do przechowywania połączenia ze źródłem danych, ale zrezygnuj z normalnych funkcji dokumentu, takich jak serializacja. Jest to przydatne, gdy chcesz kilka widoków danych i chcesz zsynchronizować wszystkie widoki, aktualizując je wszystkie naraz i tak dalej.

- Użyj okna ramki, do którego rysowane są bezpośrednio, a nie za pomocą widoku. W takim przypadku należy pominąć dokument i zapisać wszelkie połączenia danych lub danych w obiekcie okna ramki.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Opcje kreatora aplikacji dla dokumentów i widoków

Kreator aplikacji MFC ma kilka opcji w **obsłudze bazy danych Wybierz**, które są wymienione w poniższej tabeli. Jeśli używasz Kreatora aplikacji MFC do utworzenia aplikacji, wszystkie te opcje tworzą aplikacje z dokumentami i widokami. Niektóre opcje zawierają dokumenty i widoki, które pomijają niepotrzebne funkcje dokumentu. Aby uzyskać więcej informacji, zobacz [Obsługa bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Opcja|Widok|Dokument|
|------------|----------|--------------|
|**Brak**|Pochodzi z `CView`.|Nie zapewnia obsługi bazy danych. Jest to domyślne ustawienie opcji.<br /><br /> Jeśli na stronie [Typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) zostanie wybrana opcja **Obsługa architektury Dokumentu/widoku,** w menu **Plik** zostanie wyświetlona pełna obsługa dokumentów, w tym serializacja i **polecenia Nowy**, **Otwórz**, **Zapisz**i **Zapisz jako.** Zobacz [Aplikacje bez dokumentu](#_core_applications_with_no_document).|
|**Tylko pliki nagłówkowe**|Pochodzi z `CView`.|Zapewnia podstawowy poziom obsługi bazy danych dla aplikacji.<br /><br /> Zawiera Afxdb.h. Dodaje biblioteki łączy, ale nie tworzy żadnych klas specyficznych dla bazy danych. Zestawy rekordów można tworzyć później i używać ich do sprawdzania i aktualizowania rekordów.|
|**Widok bazy danych bez obsługi plików**|Pochodzi z`CRecordView`|Zapewnia obsługę dokumentu, ale nie obsługuje serializacji. Dokument może przechowywać zestaw rekordów i koordynować wiele widoków; nie obsługuje serializacji ani poleceń **Nowy**, **Otwórz**, **Zapisz**i **Zapisz jako.** Zobacz [Aplikacje z minimalnymi dokumentami](#_core_applications_with_minimal_documents). Jeśli dodasz widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera pliki nagłówków bazy danych, biblioteki łączy, widok rekordów i zestaw rekordów. (Dostępne tylko dla aplikacji z opcją **obsługi architektury dokumentu/widoku** wybraną na stronie [Typ aplikacji, Kreator aplikacji MFC).](../mfc/reference/application-type-mfc-application-wizard.md)|
|**Widok bazy danych z obsługą plików**|Pochodzi z`CRecordView`|Zapewnia pełną obsługę dokumentów, w tym serializacji i związanych z dokumentami polecenia menu **plik.** Aplikacje bazy danych zazwyczaj działają na podstawie dla rekordu, a nie na podstawie dla pliku, a więc nie wymagają serializacji. Jednak może mieć specjalne zastosowanie do serializacji. Zobacz [Aplikacje z minimalnymi dokumentami](#_core_applications_with_minimal_documents). Jeśli dodasz widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera pliki nagłówków bazy danych, biblioteki łączy, widok rekordów i zestaw rekordów. (Dostępne tylko dla aplikacji z opcją **obsługi architektury dokumentu/widoku** wybraną na stronie [Typ aplikacji, Kreator aplikacji MFC).](../mfc/reference/application-type-mfc-application-wizard.md)|

Aby zapoznać się z omówieniami alternatyw dla serializacji i alternatywnych zastosowań serializacji, zobacz [Serializacja: Serializacja a dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Wnioski z minimalnymi dokumentami

Kreator aplikacji MFC ma dwie opcje, które obsługują aplikacje dostępu do danych oparte na formularzach. Każda opcja `CRecordView`tworzy klasę widoku pochodnego i dokument. Różnią się one tym, co zostawiają z dokumentu.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Obsługa dokumentu bez plików

Wybierz opcję bazy danych kreatora aplikacji **Widok bazy danych bez obsługi plików,** jeśli nie potrzebujesz serializacji dokumentów. Dokument służy następującym użytecznym celom:

- Jest to wygodne miejsce `CRecordset` do przechowywania obiektu.

   To użycie jest równoległe do pojęć zwykłego dokumentu: dokument przechowuje dane (lub, w tym przypadku, zestaw rekordów), a widok jest widokiem dokumentu.

- Jeśli aplikacja przedstawia wiele widoków (takich jak wiele widoków rekordów), dokument obsługuje koordynowanie widoków.

   Jeśli wiele widoków pokazuje te same `CDocument::UpdateAllViews` dane, można użyć funkcji elementu członkowskiego do koordynowania aktualizacji do wszystkich widoków, gdy dowolny widok zmieni dane.

Zazwyczaj używasz tej opcji dla prostych aplikacji opartych na formularzach. Kreator aplikacji obsługuje wygodną strukturę dla takich aplikacji automatycznie.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument z obsługą plików

Wybierz opcję bazy danych kreatora aplikacji **Widok bazy danych z obsługą plików,** gdy masz alternatywne zastosowanie dla poleceń menu **plik** związanych z dokumentem i serializacji dokumentu. W przypadku części programu dostępu do danych można użyć dokumentu w taki sam sposób, jak opisano w [dokumencie Bez obsługi plików](#_core_a_document_without_file_support). Można użyć możliwości serializacji dokumentu, na przykład do odczytu i zapisu seryjnego dokumentu profilu użytkownika, który przechowuje preferencje użytkownika lub inne przydatne informacje. Aby uzyskać więcej pomysłów, zobacz [Serializacja: Serializacja vs. Wejście/wyjście bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

Kreator aplikacji obsługuje tę opcję, ale należy napisać kod, który serializuje dokument. Przechowywanie informacji seryjnych w członkach danych dokumentu.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplikacje bez dokumentu

Czasami warto napisać aplikację, która nie używa dokumentów lub widoków. Bez dokumentów można przechowywać dane `CRecordset` (takie jak obiekt) w klasie okna ramki lub klasy aplikacji. Wszelkie dodatkowe wymagania zależą od tego, czy aplikacja przedstawia interfejs użytkownika.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Obsługa bazy danych za pomocą interfejsu użytkownika

Jeśli masz interfejs użytkownika (inny niż na przykład interfejs wiersza polecenia konsoli), aplikacja rysuje bezpośrednio do obszaru klienta okna ramki, a nie do widoku. Taka aplikacja nie `CRecordView`używa `CFormView`, `CDialog` lub dla swojego głównego interfejsu `CDialog` użytkownika, ale zwykle używa do zwykłych okien dialogowych.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Pisanie wniosków bez dokumentów

Ponieważ kreator aplikacji nie obsługuje tworzenia aplikacji bez dokumentów, `CWinApp`należy napisać własną klasę pochodną `CFrameWnd` i, w razie potrzeby, również utworzyć lub `CMDIFrameWnd` klasy. Zastąp `CWinApp::InitInstance` i zadeklaruj obiekt aplikacji jako:

```cpp
CYourNameApp theApp;
```

Struktura nadal dostarcza mechanizm mapy wiadomości i wiele innych funkcji.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Obsługa bazy danych oddzielona od interfejsu użytkownika

Niektóre aplikacje nie potrzebują interfejsu użytkownika lub tylko minimalny. Załóżmy na przykład, że piszesz:

- Obiekt pośredniego dostępu do danych, który inne aplikacje (klienci) wymagają specjalnego przetwarzania danych między aplikacją a źródłem danych.

- Aplikacja przetwarza dane bez interwencji użytkownika, na przykład aplikacja, która przenosi dane z jednego formatu bazy danych do innego lub taki, który wykonuje obliczenia i wykonuje aktualizacje partii.

Ponieważ żaden dokument `CRecordset` nie jest właścicielem obiektu, prawdopodobnie chcesz przechowywać `CWinApp`go jako element członkowski danych osadzonych w klasie aplikacji pochodnej. Alternatywy obejmują:

- Nie trzymanie `CRecordset` stałego przedmiotu w ogóle. Null można przekazać do konstruktorów klasy recordset. W takim przypadku struktura tworzy `CDatabase` obiekt tymczasowy przy użyciu informacji `GetDefaultConnect` w funkcji elementu członkowskiego pliku recordset. Jest to najbardziej prawdopodobne podejście alternatywne.

- Uczynienie `CRecordset` obiektu zmienną globalną. Ta zmienna powinna być wskaźnikiem do obiektu recordset, który tworzy się dynamicznie w `CWinApp::InitInstance` zastąpienia. Pozwala to uniknąć próby skonstruowania obiektu przed zainicjowaniem struktury.

- Używanie obiektów do zietń, tak jak w kontekście dokumentu lub widoku. Tworzenie zestawy rekordów w funkcjach członkowskich aplikacji lub ramki-okna obiektów.

## <a name="see-also"></a>Zobacz też

[Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)
