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
ms.openlocfilehash: 459497a1b379b7cc0d90943d10a8a568d51c03d0
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338960"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC: używanie klas baz danych bez dokumentów i widoków
Czasami nie można używać w ramach architektury dokument/widok w aplikacjach baz danych. W tym temacie opisano:  
  
-   [Kiedy nie należy używać dokumentów](#_core_when_you_don.92.t_need_documents) takich jak serializacja dokumentu.  
  
-   [Opcje Kreatora aplikacji](#_core_appwizard_options_for_documents_and_views) do obsługi aplikacji bez serializacji i związanych z dokumentami **pliku** polecenia menu, takie jak **New**, **Otwórz** , **Zapisz**, i **Zapisz jako**.  
  
-   [Jak pracować z aplikacji, która używa minimalnej dokumentu](#_core_applications_with_minimal_documents).  
  
-   [Jak tworzyć strukturę aplikacji bez dokumentów i wyświetlanie](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Jeśli nie potrzebujesz dokumentów  
 Niektóre aplikacje mają różne koncepcji dokumentu. Te aplikacje zwykle załadować wszystkich lub większości plik z magazynu do pamięci z **Otwórz plik** polecenia. Zapisują zaktualizowany plik z powrotem do magazynu w całości przy użyciu **zapisywania pliku** lub **Zapisz jako** polecenia. Jakie użytkownik zobaczy jest plikiem danych.  
  
 Jednak niektóre kategorie aplikacji, nie wymagają dokumentu. Baza danych działania aplikacji dotyczące transakcji. Aplikacja wybiera rekordy z bazy danych i prezentuje je użytkownikowi, często pojedynczo. Jakie użytkownik zobaczy jest zazwyczaj pojedynczy rekord bieżącego, która może być tylko jeden w pamięci.  
  
 Jeśli aplikacja nie wymaga dokumentu do przechowywania danych, można zwolnić z niektórych lub wszystkich architektury dokument/widok struktury. Ile zrezygnować z zależy od podejście, które użytkownik sobie tego życzy. Można:  
  
-   Użyj minimalny dokumentu jako miejsce do przechowywania połączenia ze źródłem danych, ale pominięcie zwykłego dokumentu funkcje, takie jak serializacji. Jest to przydatne, gdy ma kilka widoków danych i chcesz synchronizować wszystkich widoków, aktualizuje je wszystkie na raz i tak dalej.  
  
-   Okno ramki, w którym rysujemy bezpośrednio, zamiast przy użyciu widoku. W tym przypadku pominięto dokument i przechowuje żadnych danych ani połączenia danych w obiekcie ramki okna.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Opcje Kreatora aplikacji dla dokumentów i widoków  
 Kreator aplikacji MFC ma kilka opcji **obsługi bazy danych wybierz**, które są wymienione w poniższej tabeli. Jeśli używasz Kreatora aplikacji MFC do tworzenia aplikacji, te opcje tworzyć aplikacje z dokumentami i widokami. Niektóre opcje zapewniają dokumentów i widoków, które pominięto dokument niepotrzebne funkcje. Aby uzyskać więcej informacji, zobacz [obsługi bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Opcja|Widok|dokument|  
|------------|----------|--------------|  
|**Brak**|Pochodną `CView`.|Nie obsługuje bazy danych. Jest to opcja domyślna.<br /><br /> Jeśli wybierzesz **Obsługa architektury dokument/widok** opcja [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) stronie uzyskiwanie pomocy technicznej pełny dokument, w tym serializacji i **nowy** , **Otwórz**, **Zapisz**, i **Zapisz jako** polecenia na **pliku** menu. Zobacz [aplikacje bez dokumentu](#_core_applications_with_no_document).|  
|**Tylko pliki nagłówka**|Pochodną `CView`.|Zapewnia podstawowy poziom obsługi bazy danych dla aplikacji.<br /><br /> Obejmuje Afxdb.h. Dodaje bibliotek DLL, ale nie tworzy żadnych klasy specyficzne dla bazy danych. Możesz później utworzyć zestawy rekordów i używać ich do badania i aktualizowania rekordów.|  
|**Widok bazy danych bez obsługi plików**|Pochodną `CRecordView`|Zapewnia Obsługa dokumentów, ale nie obsługuje serializacji. Dokumentu można zapisać zestawu rekordów i koordynowanie wielu widoków; nie obsługuje serializacji lub **New**, **Otwórz**, **Zapisz**, i **Zapisz jako** poleceń. Zobacz [aplikacje z minimalnym dokumentami](#_core_applications_with_minimal_documents). Jeśli dodasz widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera pliki nagłówkowe bazy danych, bibliotek DLL, widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **Obsługa architektury dokument/widok** opcji wybranej na [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) strony.)|  
|**Widok bazy danych z obsługą plików**|Pochodną `CRecordView`|Zapewnia obsługę pełny dokument, w tym serializacji i związanych z dokumentami **pliku** poleceń menu. Aplikacje baz danych są zazwyczaj działają na podstawie każdego rekordu, a nie na pliku podstawy i dlatego nie ma potrzeby serializacji. Mogą jednak mieć specjalne użycia serializacji. Zobacz [aplikacje z minimalnym dokumentami](#_core_applications_with_minimal_documents). Jeśli dodasz widok bazy danych, należy określić źródło danych.<br /><br /> Zawiera pliki nagłówkowe bazy danych, bibliotek DLL, widoku rekordu i zestawu rekordów. (Dostępne tylko dla aplikacji za pomocą **Obsługa architektury dokument/widok** opcji wybranej na [typ aplikacji, Kreator aplikacji MFC](../mfc/reference/application-type-mfc-application-wizard.md) strony.)|  
  
 Omówienie alternatywami do serializacji i alternatywne używa serializacji, zobacz [serializacja: serializacja a. Baza danych wejściowych/wyjściowych](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Aplikacje z minimalnym dokumentów  
 Kreator aplikacji MFC ma dwie opcje, które obsługują aplikacje dostępu do danych opartej na formularzu. Każda opcja tworzy `CRecordView`-pochodne klasy widoku i dokument. Różnią się one opuszczają poza dokumentu.  
  
###  <a name="_core_a_document_without_file_support"></a> Dokumentu bez obsługi plików  
 Wybierz opcję bazy danych Kreatora aplikacji **bazy danych w widoku bez obsługi plików** Jeśli nie potrzebujesz serializacja dokumentu. Dokument służy do następujących celów przydatne:  
  
-   Jest to wygodne miejsce do przechowywania `CRecordset` obiektu.  
  
     Użycie tych równoleżnikami zwykłym dokumencie pojęcia: dokumentu są przechowywane dane (lub, w tym przypadku zestawu rekordów) i widok jest widokiem dokumentu.  
  
-   Jeśli aplikacja przedstawi wiele widoków (na przykład wiele widoków rekordów), dokument obsługuje koordynowanie widoków.  
  
     Jeśli wiele widoków wyświetlić te same dane, możesz użyć `CDocument::UpdateAllViews` funkcja elementu członkowskiego do koordynowania aktualizacji wszystkich widoków zmianie dowolnego widoku danych.  
  
 Zazwyczaj używasz tej opcji dla prostej aplikacji opartej na formularzu. Kreator aplikacji automatycznie obsługuje wygodne struktury na potrzeby takich aplikacji.  
  
###  <a name="_core_a_document_with_file_support"></a> Dokument z obsługą plików  
 Wybierz opcję bazy danych Kreatora aplikacji **bazy danych widoku z obsługą plików** przypadku alternatywnego wykorzystania związanych z dokumentami **pliku** poleceń menu i serializacja dokumentu. Dostęp do danych część programu służy dokumentu w taki sam sposób zgodnie z opisem w [dokumentu bez obsługi plików](#_core_a_document_without_file_support). Na przykład możliwość serializacji dokumentu, można użyć do odczytywania i zapisywania dokumentu profilu użytkownika serializacji, który przechowuje preferencji użytkownika lub inne przydatne informacje. Więcej pomysłów, zobacz [serializacja: serializacja a. Baza danych wejściowych/wyjściowych](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Kreator aplikacji obsługuje tę opcję, ale należy napisać kod, który serializuje dokumentu. Store zserializowane informacje w składowych danych dokumentu.  
  
##  <a name="_core_applications_with_no_document"></a> Aplikacje bez dokumentu  
 Czasami można napisać aplikację, która nie korzysta z dokumentów i widoków. Bez dokumentów, dane są przechowywane (takie jak `CRecordset` obiekt) w swojej klasy okien ramowych lub klasy aplikacji. Wszelkie dodatkowe wymagania zależą od tego, czy aplikacja prezentuje interfejsu użytkownika.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Obsługa bazy danych za pomocą interfejsu użytkownika  
 W przypadku interfejsu użytkownika (inne niż na przykład interfejsu wiersza polecenia konsoli) aplikacji rysuje bezpośrednio do obszaru klienckiego okna ramki, a nie w widoku. Taką aplikację nie używa `CRecordView`, `CFormView`, lub `CDialog` interfejs użytkownika głównego, ale zazwyczaj przy użyciu `CDialog` dla zwykłych okien dialogowych.  
  
###  <a name="_core_writing_applications_without_documents"></a> Pisanie aplikacji bez dokumentów  
 Ponieważ Kreatora aplikacji nie obsługuje tworzenia aplikacji bez dokumentów, trzeba napisać własne `CWinApp`-klasy pochodnej i w razie potrzeby utwórz również `CFrameWnd` lub `CMDIFrameWnd` klasy. Zastąp `CWinApp::InitInstance` i zadeklarować obiekt aplikacji jako:  
  
```cpp  
CYourNameApp theApp;  
```  
  
 Struktura nadal dostarcza mechanizm mapy komunikatów i wiele innych funkcji.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Oddzielne obsługi bazy danych z poziomu interfejsu użytkownika  
 Niektóre aplikacje potrzebują, bez interfejsu użytkownika, czy tylko minimalne. Na przykład załóżmy, że piszesz:  
  
-   Obiekt dostępu do danych pośrednich innych aplikacji (klientów) wymagają specjalnych przetwarzania danych między aplikacją a źródłem danych.  
  
-   Aplikacja, która przetwarza dane bez interwencji użytkownika, takie jak aplikacja, która przenosi dane z jednego formatu bazy danych do innego lub, który nie obliczeń i wykonuje aktualizacje usługi batch.  
  
 Ponieważ żaden dokument nie jest właścicielem `CRecordset` obiektu, prawdopodobnie chcesz przechowywać je jako element członkowski danych osadzonych w swojej `CWinApp`-aplikacji klasy pochodnej. Alternatywne metody obejmują:  
  
-   Nie utrzymywanie stałe `CRecordset` obiektu w ogóle. Do Twojej Konstruktory klasy zestawu rekordów można przekazać wartości NULL. W takim przypadku w ramach tworzy tymczasową `CDatabase` obiektu, korzystając z informacji w zestawie rekordów `GetDefaultConnect` funkcja elementu członkowskiego. Jest to najprawdopodobniej alternatywne podejście.  
  
-   Tworzenie `CRecordset` obiektu zmiennej globalnej. Ta zmienna powinna być wskaźnik do obiektu zestawu rekordów, którą tworzysz dynamicznie w swojej `CWinApp::InitInstance` zastąpienia. Umożliwia to uniknięcie, próba utworzenia obiekt przed zainicjowaniem jest struktura.  
  
-   Przy użyciu obiektów zestawu rekordów, tak jak w kontekście dokumentu lub widoku. Tworzenie zestawów rekordów w elemencie członkowskim funkcje aplikacji lub okno ramowe obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)