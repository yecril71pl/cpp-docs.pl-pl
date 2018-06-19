---
title: 'MFC: Używanie klas baz danych bez dokumentów i widoków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba2e59b53524975f87e4ad7ffe99b9a4a3cc870d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093899"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: używanie klas baz danych bez dokumentów i widoków
Czasami nie można używać w ramach architektury dokument/widok w aplikacjach baz danych. W tym temacie opisano:  
  
-   [Kiedy nie trzeba używać dokumentów](#_core_when_you_don.92.t_need_documents) np. serializacji dokumentu.  
  
-   [Opcje Kreatora aplikacji](#_core_appwizard_options_for_documents_and_views) do obsługi aplikacji bez serializacji i powiązanych z dokumentem **pliku** polecenia menu, takie jak **nowy**, **Otwórz** , **Zapisać**, i **Zapisz jako**.  
  
-   [Jak pracować z aplikacji, która używa minimalnego dokumentu](#_core_applications_with_minimal_documents).  
  
-   [Struktury aplikacji bez dokumentu lub widok](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Jeśli nie ma potrzeby dokumentów  
 Niektóre aplikacje mają różne koncepcji dokumentu. Te aplikacje zwykle ładowanie wszystkie lub większość z pliku z magazynu w pamięci z **Otwórz plik** polecenia. Zapisują zaktualizowany plik z powrotem do magazynu w całości z **zapisywanie pliku** lub **Zapisz jako** polecenia. Jakie użytkownik widzi jest plik danych.  
  
 Jednak niektóre rodzaje aplikacji, nie wymagają dokumentu. Aplikacje baz danych działa pod względem transakcji. Aplikacja wybiera rekordy z bazy danych i wyświetla je użytkownikowi, często pojedynczo. Jakie użytkownik widzi jest zwykle pojedynczego rekordu bieżącego, która może być tylko jeden w pamięci.  
  
 Jeśli aplikacja nie wymaga dokumentu do przechowywania danych, można zwolnić z niektórych lub wszystkich architektury dokument/widok struktury. Ile zrezygnować z zależy od podejście, które chcesz. Użytkownik może:  
  
-   Użyj minimalnego dokumentu jako miejsce do przechowywania połączenia ze źródłem danych, ale zrezygnować z funkcji normalnego dokumentu, takich jak serializacji. Jest to przydatne, gdy ma kilka widoków danych i chcesz synchronizować wszystkich widoków, aktualizuje je w całości i tak dalej.  
  
-   Użyj okno ramowe, do którego należy narysować bezpośrednio, zamiast przy użyciu widoku. W takim przypadku pominąć dokumentu i przechowywać żadnych danych lub połączenia danych w obiekcie okna ramowego.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Opcje Kreatora aplikacji dla dokumentów i widoków  
 Kreator aplikacji MFC ma kilka opcji w **obsługi bazy danych wybierz**, które są wymienione w poniższej tabeli. Jeśli używasz Kreatora aplikacji MFC do tworzenia aplikacji, te opcje tworzenia aplikacji z dokumentami i widokami. Niektóre opcje zapewniają dokumentów i widoków, które Pomiń niepotrzebne dokumentu funkcji. Aby uzyskać więcej informacji, zobacz [obsługi bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Opcja|Widok|dokument|  
|------------|----------|--------------|  
|**Brak**|Pochodną `CView`.|Nie zapewnia bazy danych obsługi. Jest to opcja domyślna.<br /><br /> W przypadku wybrania **wsparcie dla architektury dokument/widok** opcja [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) strony, zapewnia obsługę pełnego dokumentu, w tym serializacji i `New`,  **Otwórz**, **zapisać**, i **Zapisz jako** polecenia w **pliku** menu. Zobacz [aplikacji bez dokumentu](#_core_applications_with_no_document).|  
|**Tylko pliki nagłówka**|Pochodną `CView`.|Udostępnia podstawowy poziom obsługi bazy danych dla aplikacji.<br /><br /> Obejmuje Afxdb.h. Dodaje biblioteki dll, ale nie powoduje żadnych klasy specyficzne dla bazy danych. Można utworzyć później zestawów rekordów i używać ich do badania i aktualizowania rekordów.|  
|**Widok bazy danych bez obsługi plików**|Pochodne `CRecordView`|Zapewnia obsługę dokumentów, ale nie obsługuje serializacji. Dokument można zapisać zestawu rekordów i koordynacji wielu widoków; nie obsługuje serializacji lub `New`, **Otwórz**, **zapisać**, i **Zapisz jako** poleceń. Zobacz [aplikacje z minimalnym dokumenty](#_core_applications_with_minimal_documents). Jeśli widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera bazy danych, pliki nagłówkowe, biblioteki DLL widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **wsparcie dla architektury dokument/widok** opcji wybranej na [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) strony.)|  
|**Widok bazy danych z obsługą plików**|Pochodne `CRecordView`|Zapewnia obsługę pełnego dokumentu, w tym serializacji i powiązanych z dokumentem **pliku** poleceń menu. Aplikacje baz danych są zazwyczaj działają na podstawie na rekordu, a nie na jeden plik podstawy i dlatego nie ma potrzeby serializacji. Mogą jednak mieć specjalne używany do serializacji. Zobacz [aplikacje z minimalnym dokumenty](#_core_applications_with_minimal_documents). Jeśli widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera bazy danych, pliki nagłówkowe, biblioteki DLL widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **wsparcie dla architektury dokument/widok** opcji wybranej na [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) strony.)|  
  
 Omówienie alternatywami do serializacji i alternatywne używa do serializacji, zobacz [szeregowanie: vs serializacji. Baza danych wejścia/wyjścia](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Aplikacje z minimalnym dokumentów  
 Kreator aplikacji MFC ma dwie opcje, które obsługują aplikacje dostępu do danych opartych na formularzach. Każda opcja tworzy `CRecordView`-pochodnych widoku klasy i dokumentu. Różnią się one pozostaw poza dokumentu.  
  
###  <a name="_core_a_document_without_file_support"></a> Dokument bez obsługi plików  
 Wybierz opcję bazy danych Kreatora aplikacji **bazy danych widoku bez obsługi plików** Jeśli nie ma potrzeby serializacji dokumentu. Dokument służy przydatne w następujących celów:  
  
-   Jest wygodne miejsce do przechowywania `CRecordset` obiektu.  
  
     To użycie równoleżnikami zwykłym dokumencie pojęcia: dokument przechowuje dane (lub, w tym przypadku zestawu rekordów) i widok jest widokiem dokumentu.  
  
-   Jeśli aplikacja wiele widoków (na przykład wiele widoków rekordów), dokument obsługuje koordynowanie widoków.  
  
     Wiele widoków przedstawić te same dane, można użyć `CDocument::UpdateAllViews` funkcji członkowskiej do koordynowania aktualizacji do wszystkich widoków zmianie dowolnego widoku danych.  
  
 Zazwyczaj ta opcja jest używany dla prostych aplikacji opartej na formularzu. Kreator aplikacji obsługuje automatycznie wygodny struktury dla takich aplikacji.  
  
###  <a name="_core_a_document_with_file_support"></a> Dokument z obsługą plików  
 Wybierz opcję bazy danych Kreatora aplikacji **bazy danych widoku z obsługą plików** Jeśli masz alternatywnego wykorzystania powiązanych z dokumentem **pliku** polecenia menu i serializacja dokumentu. Dostęp do danych części programu służy dokumentu w taki sam sposób zgodnie z opisem w [dokumentu bez obsługi plików](#_core_a_document_without_file_support). Na przykład dokumentu możliwości serializacji, można użyć do odczytywania i zapisywania dokumentu profilu serializacji użytkownika, który przechowuje preferencji użytkownika lub inne przydatne informacje. Aby uzyskać więcej informacji, zobacz [szeregowanie: vs serializacji. Baza danych wejścia/wyjścia](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Kreator aplikacji obsługuje tę opcję, ale należy napisać kod, który serializuje dokumentu. Serializowane informacje są przechowywane w elementach członkowskich danych dokumentu.  
  
##  <a name="_core_applications_with_no_document"></a> Aplikacje bez dokumentu  
 Czasami można napisać aplikację, które nie są używane dokumenty i widoki. Bez dokumentów, przechowywać dane (takie jak `CRecordset` obiektu) w klasie okien ramowych lub klasy aplikacji. Wszelkie dodatkowe wymagania zależą od tego, czy interfejs użytkownika przedstawia informacje o aplikacji.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Obsługa baz danych za pomocą interfejsu użytkownika  
 Jeśli masz interfejsu użytkownika (inne niż, na przykład, interfejsu wiersza polecenia konsoli) aplikacji rysuje bezpośrednio do obszaru klienckiego ramkę okna, a nie w widoku. Nie korzysta z takich aplikacji `CRecordView`, `CFormView`, lub `CDialog` interfejs użytkownika głównego, ale zwykle jest używana `CDialog` w zwykłym oknach dialogowych.  
  
###  <a name="_core_writing_applications_without_documents"></a> Pisanie aplikacji bez dokumentów  
 Ponieważ Kreatora aplikacji nie obsługuje tworzenia aplikacji bez dokumentów, należy napisać własny `CWinApp`-klasy, a w razie potrzeby utwórz również `CFrameWnd` lub `CMDIFrameWnd` klasy. Zastąpienie `CWinApp::InitInstance` ani deklarować jako obiektu aplikacji:  
  
```  
CYourNameApp theApp;  
```  
  
 Platformę nadal udostępnia mechanizm map wiadomości oraz wiele innych funkcji.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Oddzielne obsługi bazy danych przy użyciu interfejsu użytkownika  
 Niektóre aplikacje potrzebują bez interfejsu użytkownika, czy tylko minimalne. Na przykład załóżmy, że pisania:  
  
-   Obiekt pośredni dostęp do danych innych aplikacji (klienci) wymagają specjalnego przetwarzania danych między aplikacją a źródłem danych.  
  
-   Aplikacja, która przetwarza dane bez interwencji użytkownika, takie jak aplikacja, która przenosi dane z jednego formatu bazy danych lub który nie obliczeń i wykonuje aktualizacje wsadowe.  
  
 Ponieważ żaden dokument nie jest właścicielem `CRecordset` obiektu, prawdopodobnie chcesz przechowywać go jako element członkowski danych osadzonych w Twojej `CWinApp`-klasy aplikacji. Alternatywne metody obejmują:  
  
-   Nie zachowuje stałe `CRecordset` na wszystkich obiektów. Można przekazać **NULL** Twojego konstruktorów klasy zestawu rekordów. W takim przypadku platformę tworzy tymczasowy `CDatabase` obiektów, korzystając z informacji zawartych w zestawie rekordów `GetDefaultConnect` funkcję elementu członkowskiego. Jest to najprawdopodobniej metoda alternatywna.  
  
-   Tworzenie `CRecordset` obiekt zmiennej globalnej. Ta zmienna powinna być wskaźnik do obiektu zestawu rekordów, utworzony dynamicznie w Twojej `CWinApp::InitInstance` zastąpienia. Dzięki temu można uniknąć próby konstruowania obiektu przed zainicjowaniem platformę.  
  
-   Przy użyciu obiektów zestawu rekordów, tak jak w kontekście widoku lub dokumentu. Tworzenie zestawów rekordów element członkowski funkcji aplikacji lub obiekty ramki okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)