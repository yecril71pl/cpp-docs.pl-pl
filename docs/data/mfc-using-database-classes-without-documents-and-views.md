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
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213359"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: używanie klas baz danych bez dokumentów i widoków

Czasami możesz nie chcieć używać architektury dokumentu/widoku struktury w aplikacjach baz danych. W tym temacie objaśniono:

- [Gdy nie musisz używać dokumentów](#_core_when_you_don.92.t_need_documents) , takich jak Serializacja dokumentu.

- [Opcje Kreatora aplikacji](#_core_appwizard_options_for_documents_and_views) do obsługi aplikacji bez serializacji i poleceń menu **plik** związanych z dokumentem, takich jak **New**, **Open**, **Save**i **Save as**.

- [Jak korzystać z aplikacji używającej minimalnego dokumentu](#_core_applications_with_minimal_documents).

- [Jak określić strukturę aplikacji bez dokumentu lub widoku](#_core_applications_with_no_document).

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Gdy dokumenty nie są potrzebne

Niektóre aplikacje mają odrębną koncepcję dokumentu. Te aplikacje zwykle ładują wszystkie lub większość plików z magazynu do pamięci za pomocą polecenia **Otwórz plik** . Zapisują zaktualizowany plik z powrotem do magazynu wszystkie naraz przy użyciu **pliku Zapisz** lub **Zapisz jako** polecenie. Użytkownik widzi plik danych.

Jednak niektóre kategorie aplikacji nie wymagają dokumentu. Aplikacje bazy danych działają w ramach transakcji. Aplikacja wybiera rekordy z bazy danych i przedstawia je użytkownikowi, często jednocześnie. To, co użytkownik widzi, jest zwykle pojedynczym bieżącym rekordem, który może być jedynym z nich w pamięci.

Jeśli aplikacja nie wymaga dokumentu do przechowywania danych, można przystąpić do części lub całości architektury dokumentu/widoku struktury. Ilość miejsca, z której korzystasz, zależy od preferowanej metody. Możesz:

- Używaj minimalnego dokumentu jako miejsca do przechowywania połączenia ze źródłem danych, ale z użyciem normalnych funkcji dokumentu, takich jak serializacji. Jest to przydatne, gdy potrzebujesz kilku widoków danych i chcesz synchronizować wszystkie widoki, aktualizować je wszystkie jednocześnie i tak dalej.

- Użyj okna ramowego, w którym narysujesz bezpośrednio, zamiast korzystać z widoku. W takim przypadku pomijasz dokument i przechowujesz dane lub połączenia danych w obiekcie ramki okna.

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Opcje Kreatora aplikacji dla dokumentów i widoków

Kreator aplikacji MFC zawiera kilka opcji obsługiwanych w ramach **wyboru bazy danych**, które są wymienione w poniższej tabeli. W przypadku tworzenia aplikacji za pomocą Kreatora aplikacji MFC wszystkie te opcje tworzą aplikacje z dokumentami i widokami. Niektóre opcje zapewniają dokumenty i widoki, które pomijają niepotrzebne funkcje dokumentu. Aby uzyskać więcej informacji, zobacz [Obsługa bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Opcja|Widok|Dokument|
|------------|----------|--------------|
|**Dawaj**|Pochodny od `CView`.|Nie zapewnia obsługi bazy danych. Jest to opcja domyślna.<br /><br /> Jeśli wybierzesz opcję **Obsługa architektury dokumentu/widoku** na stronie [Typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) , uzyskasz pełną obsługę dokumentów, w tym serializacji i **nowe**, **otwarte**, **Zapisz**i **Zapisz jako** polecenia w menu **plik** . Zobacz [aplikacje bez dokumentu](#_core_applications_with_no_document).|
|**Tylko pliki nagłówkowe**|Pochodny od `CView`.|Zapewnia podstawowy poziom obsługi bazy danych dla aplikacji.<br /><br /> Zawiera AFXDB. h. Dodaje biblioteki łączy, ale nie tworzy żadnych klas specyficznych dla bazy danych. Zestawy rekordów można tworzyć później i używać ich do badania i aktualizowania rekordów.|
|**Widok bazy danych bez obsługi plików**|Pochodny od `CRecordView`|Zapewnia obsługę dokumentów, ale nie obsługuje serializacji. Dokument może przechowywać zestaw rekordów i koordynować wiele widoków; nie obsługuje serializacji ani **nowych**, **otwartych**, **Zapisz**i **Zapisz jako** polecenia. Zobacz [aplikacje o minimalnych dokumentach](#_core_applications_with_minimal_documents). Jeśli dołączysz widok bazy danych, musisz określić źródło danych.<br /><br /> Obejmuje pliki nagłówka bazy danych, biblioteki linków, widok rekordów i zestaw rekordów. (Dostępne tylko w przypadku aplikacji z opcją **Obsługa dokumentu/widoku** wybraną na stronie [Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) ).|
|**Widok bazy danych z obsługą plików**|Pochodny od `CRecordView`|Zapewnia obsługę pełnego dokumentu, w tym serializacji i poleceń menu **plików** związanych z dokumentem. Aplikacje bazy danych zwykle działają dla poszczególnych rekordów, a nie na podstawie poszczególnych plików, a więc nie wymagają serializacji. Jednak może istnieć specjalne użycie do serializacji. Zobacz [aplikacje o minimalnych dokumentach](#_core_applications_with_minimal_documents). Jeśli dołączysz widok bazy danych, musisz określić źródło danych.<br /><br /> Obejmuje pliki nagłówka bazy danych, biblioteki linków, widok rekordów i zestaw rekordów. (Dostępne tylko w przypadku aplikacji z opcją **Obsługa dokumentu/widoku** wybraną na stronie [Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) ).|

Aby zapoznać się z alternatywą dla serializacji i alternatywnych zastosowania serializacji, zobacz [serializacji: serializacji a dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Aplikacje z minimalnymi dokumentami

Kreator aplikacji MFC ma dwie opcje, które obsługują aplikacje dostępu do danych oparte na formularzach. Każda opcja tworzy klasę widoku pochodnego `CRecordView`i dokumentu. Różnią się one w porównaniu z dokumentem.

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Dokument bez obsługi plików

Wybierz opcję bazy danych Kreator aplikacji **Widok bazy danych bez obsługi plików** , jeśli nie potrzebujesz serializacji dokumentu. Dokument ten służy do następujących celów:

- Jest to wygodne miejsce do przechowywania `CRecordset` obiektu.

   To użycie powoduje równoległe koncepcje zwykłego dokumentu: dokument przechowuje dane (lub, w tym przypadku zestaw rekordów) i widok to widok dokumentu.

- Jeśli aplikacja wyświetla wiele widoków (takich jak wiele widoków rekordów), dokument obsługuje koordynowanie widoków.

   Jeśli wiele widoków wyświetla te same dane, można użyć funkcji składowej `CDocument::UpdateAllViews`, aby koordynować aktualizacje do wszystkich widoków, gdy dowolny widok zmieni dane.

Ta opcja jest zwykle używana w przypadku prostych aplikacji opartych na formularzach. Kreator aplikacji obsługuje wygodną strukturę dla takich aplikacji automatycznie.

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Dokument z obsługą plików

Wybierz opcję bazy danych Kreator aplikacji **Widok bazy danych z obsługą plików** , gdy istnieje alternatywne użycie poleceń menu **plik** powiązanych z dokumentem i serializacji dokumentu. W przypadku dostępu do danych w programie można użyć dokumentu w taki sam sposób, jak opisano w [dokumencie bez obsługi plików](#_core_a_document_without_file_support). Można użyć możliwości serializacji dokumentu, na przykład w celu odczytania i zapisania serializowanego dokumentu profilu użytkownika, który przechowuje preferencje użytkownika lub inne przydatne informacje. Aby uzyskać więcej sugestii, zobacz [serializacji: serializacji a dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

Kreator aplikacji obsługuje tę opcję, ale należy napisać kod, który serializować dokument. Przechowaj serializowane informacje w elementach członkowskich danych dokumentu.

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Aplikacje bez dokumentu

Czasami warto napisać aplikację, która nie korzysta z dokumentów lub widoków. Bez dokumentów przechowujesz dane (takie jak `CRecordset` Object) w klasie okna ramki lub klasie aplikacji. Wszelkie dodatkowe wymagania zależą od tego, czy aplikacja prezentuje interfejs użytkownika.

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Obsługa bazy danych przy użyciu interfejsu użytkownika

Jeśli dysponujesz interfejsem użytkownika (innym niż, na przykład w interfejsie wiersza polecenia konsoli), aplikacja rysuje się bezpośrednio w obszarze klienta okna ramki, a nie w widoku. Takie aplikacje nie używają `CRecordView`, `CFormView`ani `CDialog` dla głównego interfejsu użytkownika, ale zazwyczaj używają `CDialog` do zwykłych okien dialogowych.

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Pisanie aplikacji bez dokumentów

Ponieważ Kreator aplikacji nie obsługuje tworzenia aplikacji bez dokumentów, należy napisać własną klasę pochodną `CWinApp`i, jeśli to konieczne, również utworzyć klasę `CFrameWnd` lub `CMDIFrameWnd`. Zastąp `CWinApp::InitInstance` i Zadeklaruj obiekt aplikacji jako:

```cpp
CYourNameApp theApp;
```

Struktura nadal dostarcza mechanizm mapowania komunikatów i wiele innych funkcji.

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Obsługa bazy danych oddzielona od interfejsu użytkownika

Niektóre aplikacje nie muszą mieć interfejsu użytkownika lub tylko minimalny. Załóżmy na przykład, że piszesz:

- Pośredni obiekt dostępu do danych, który umożliwia innym aplikacjom (klientom) wywoływanie specjalnego przetwarzania danych między aplikacją a źródłem danych.

- Aplikacja, która przetwarza dane bez interwencji użytkownika, na przykład aplikację, która przenosi dane z jednego formatu bazy danych do innego lub który wykonuje obliczenia w ramach aktualizacji wsadowych.

Ponieważ żaden dokument nie jest właścicielem obiektu `CRecordset`, prawdopodobnie chcesz go zapisać jako osadzony element członkowski danych w klasie aplikacji pochodnej `CWinApp`. Alternatywy obejmują:

- Nie zachowuje trwałego `CRecordset` obiektu. Można przekazać wartość NULL do konstruktorów klas zestawu rekordów. W takim przypadku struktura tworzy tymczasowy obiekt `CDatabase` przy użyciu informacji w `GetDefaultConnect` funkcja członkowska zestawu rekordów. Jest to najbardziej prawdopodobną metodę alternatywną.

- Tworzenie obiektu `CRecordset` jako zmiennej globalnej. Ta zmienna powinna być wskaźnikiem do obiektu zestawu rekordów, który jest tworzony dynamicznie w przesłonięciu `CWinApp::InitInstance`. Pozwala to uniknąć próby konstruowania obiektu przed zainicjowaniem struktury.

- Używanie obiektów zestawu rekordów w ramach kontekstu dokumentu lub widoku. Tworzenie zestawów rekordów w funkcjach składowych obiektów aplikacji lub okien ramowych.

## <a name="see-also"></a>Zobacz też

[Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)
