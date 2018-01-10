---
title: Sekwencja operacji przy tworzeniu aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae1169b438a181e22696502352c19353421469b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>Sekwencja operacji przy tworzeniu aplikacji MFC
W poniższej tabeli opisano ogólne sekwencji, które zwykle może wykonać podczas opracowywania aplikacji MFC.  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>Sekwencja do tworzenia aplikacji z architekturą  
  
|Zadanie|Jak|Jest w ramach|  
|----------|------------|------------------------|  
|Utworzyć szkielet aplikacji.|Uruchom [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md). Określ opcje, które mają na stronach opcje. Dostępne są następujące opcje tworzenia aplikacji składnika modelu COM, kontenera lub obu; Dodawanie automatyzacji; i tworzenie aplikacji obsługujących bazy danych.|Kreator aplikacji MFC tworzy pliki szkielet aplikacji, w tym pliki źródłowe dla aplikacji, dokumentu, widok i okna ramowe; Plik zasobów; plik projektu; i innych osób, wszystkie dostosowane do specyfikacji.|  
|Zobacz platformę i Kreator aplikacji MFC oferują bez dodawania wiersz z własnego kodu.|Tworzenie szkielet aplikacji i uruchom go w programie Visual C++.|Uruchamianie szkielet aplikacji pochodzi wiele standardowych **pliku**, **Edytuj**, **widoku**, i **pomocy** poleceń menu z platformę. Dla aplikacji MDI również uzyskać funkcjonalnej menu systemu Windows oraz platformę zarządza tworzenie, układ i niszczenie okien podrzędnych MDI.|  
|Utworzyć interfejsu użytkownika.|Użyj Visual C++ [edytory zasobów](../windows/resource-editors.md) do edycji wizualnej interfejs użytkownika:<br /><br /> -Tworzenie menu.<br />-Zdefiniować akceleratorów.<br />-Tworzenie okien dialogowych.<br />-Tworzyć i edytować mapy bitowe, ikony i kursory.<br />-Edytuj narzędzi tworzone przez Kreatora aplikacji MFC.<br />-Tworzyć i edytować inne zasoby.<br /><br /> Można również sprawdzić okien dialogowych w edytorze okien dialogowych.|Domyślny plik zasobów tworzone przez Kreatora aplikacji MFC udostępnia wiele zasobów, które są potrzebne. Visual C++ umożliwia edytowanie istniejących zasobów i dodawanie nowych zasobów łatwo i wizualne.|  
|Mapowanie menu z funkcjami programu obsługi.|Użyj **zdarzenia** przycisk [okna właściwości](/visualstudio/ide/reference/properties-window) nawiązać menu i akceleratorami funkcje programu obsługi w kodzie.|Okno właściwości Wstawia wpisy mapy wiadomości i szablony pusty funkcji do plików źródłowych, określ i zarządza wiele ręcznych zadań kodowania.|  
|Wpisz swój kod obsługi.|Aby przejść bezpośrednio do kodu w edytorze kodu źródłowego za pomocą widoku klasy. Wprowadź kod dla funkcji programu obsługi. Aby uzyskać więcej informacji na widoku klasy i kreatorów, które Dodawanie kodu do projektu, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md).|Widok klas otwiera edytor, Przewija do szablonu funkcji jest puste i umieszcza kursor dla Ciebie.|  
|Przyciski paska narzędzi są mapowane na polecenia.|Mapowanie każdego przycisku na pasku narzędzi do polecenia menu lub akceleratora przypisując przycisku identyfikator odpowiedniego polecenia.|Platformę steruje rysunku, umożliwiające wyłączenie, sprawdzanie i inne aspekty visual przycisków paska narzędzi.|  
|Testowanie funkcji programu obsługi.|Odbuduj program i korzystania z wbudowanych narzędzi debugowania do testowania poprawnie pracować z programów obsługi.|Możesz kroku lub śledzenia przez kod, aby zobaczyć, jak są wywoływane z obsługi. Jeśli wypełniony kod obsługi obsługi wykonywać polecenia. Platformę wyłączy się automatycznie, elementy menu i przycisków paska narzędzi, które nie są obsługiwane.|  
|Dodaj [okien dialogowych](../mfc/dialog-boxes.md).|Projektowanie zasobów szablonu okna dialogowego z edytora okien dialogowych. Następnie utwórz klasy okien dialogowych i kod obsługujący okna dialogowego.|Platformę zarządza okno dialogowe i umożliwia pobieranie wartości wprowadzonej przez użytkownika.|  
|Inicjowanie, weryfikacji i pobierania danych okno dialogowe.|Można również zdefiniować sposób formantów okna dialogowego mają być zainicjowany i sprawdzania poprawności. Zmienne Członkowskie dodawać do klasy okien dialogowych i zamapowania ich do formantów okna dialogowego za pomocą programu Visual Studio. Określ reguły sprawdzania poprawności ma zostać zastosowany do każdego formantu wprowadzania danych. W razie potrzeby, należy podać własne niestandardowe operacji sprawdzania poprawności.|Platformę zarządza inicjowania okno dialogowe i sprawdzania poprawności. Jeśli użytkownik wprowadzi nieprawidłowe informacje, ramach Wyświetla okno komunikatu i umożliwia użytkownikowi ponownie wprowadzić dane.|  
|Utwórz dodatkowe klasy.|Widok klas umożliwiają utworzenie dodatkowych dokumentu, widok i klasy okien ramowych poza tymi, które automatycznie tworzone przez Kreatora aplikacji MFC. Można utworzyć klasy rekordów dodatkowej bazy danych, klasy okien dialogowych i tak dalej. (W widoku klasy, możesz tworzyć klasy nie pochodzi od klasy MFC.)|Widok klas dodaje te klasy do plików źródłowych i pomaga zdefiniować ich połączenia dla poleceń, które obsługują.|  
|Dodaj składniki gotowe do użycia w aplikacji.|Użyj `New Item dialog box` można dodać wiele elementów.|Te elementy można łatwo zintegrować aplikacji i zaoszczędzić wiele pracy.|  
|Implementuje klasy dokumentu.|Wdrożenia z klasy dokumentu specyficzne dla aplikacji lub klasy. Dodaj element członkowski zmienne do przechowywania struktury danych. Dodawanie funkcji Członkowskich zapewnia interfejs do danych.|Platformę już wie, jak wchodzić w interakcję z plikami danych dokumentu. Go można otworzyć i zamknij dokument pliki, zapisywania i odczytywania dane dokumentu, a obsługi innych interfejsów użytkownika. Można skoncentrować się na jak dane dokumentu jest modyfikowany w zakresie.|  
|Implementuje Open, Zapisz i Zapisz jako polecenia.|Pisanie kodu dla dokumentu `Serialize` funkcję elementu członkowskiego.|Platformę Wyświetla okna dialogowe dla **Otwórz**, **zapisać**, i **Zapisz jako** polecenia w **pliku** menu. Zapisuje i odczytuje kopię dokumentu w formacie danych określonego w Twojej `Serialize` funkcję elementu członkowskiego.|  
|Implementuje klasy widoku.|Wdrożenie co najmniej jedną klasę widoku odpowiadający dokumentów. Implementuje funkcje Członkowskie widoku, które mapowane do interfejsu użytkownika z widoku klasy. Różne [CView](../mfc/reference/cview-class.md)-klas pochodnych są dostępne, w tym [clistview —](../mfc/reference/clistview-class.md) i [CTreeView —](../mfc/reference/ctreeview-class.md).|Platformę zarządza większość relacji między dokumentu oraz jego widoku. Funkcje Członkowskie widoku dostępu dokumentu widoku do renderowania jej obrazu na ekranie lub wydruku i aktualizowania struktur danych dokumentu w odpowiedzi na użytkownika poleceń edycji.|  
|Ulepszanie Drukowanie domyślne.|Jeśli potrzebujesz obsługuje wielostronicowe drukowania, Zastąp funkcje Członkowskie widoku.|Platforma obsługuje **drukowania**, **ustawienia strony**, i **Podgląd wydruku** polecenia w **pliku** menu. Musi on Poinformuj jak Podziel dokumentu na wielu stronach.|  
|Dodaj przewijania.|Jeśli zachodzi potrzeba obsługi przewijania, pochodzi z widoku klasy lub klas z [CScrollView](../mfc/reference/cscrollview-class.md).|Widok automatycznie doda paski przewijania, gdy okno widoku stanie się zbyt mały.|  
|Utwórz widoki formularzy.|Jeśli chcesz utworzyć widoków zasobów szablonu okna dialogowego, pochodzi z widoku klasy lub klas z [CFormView](../mfc/reference/cformview-class.md).|Widoku jest używana do wyświetlania formantów zasobów szablonu okna dialogowego. Użytkownik może karcie z formantu do formantu w widoku.|  
|Tworzenie formularzy bazy danych.|Jeśli chcesz, aby aplikacja oparta na formularzu dostępu do danych, pochodzi z klasy widoku [CRecordView](../mfc/reference/crecordview-class.md) (na potrzeby programowania ODBC).|Widok działa tak jak widok formularza, ale jego formantów są połączone z pola [crecordset —](../mfc/reference/crecordset-class.md) obiekt reprezentujący tabeli bazy danych. MFC przenosi dane między formantami a zestaw rekordów dla Ciebie.|  
|Utwórz Edytor tekstu proste.|Jeśli chcesz, aby widok był Edytor tekstowy, pochodzi z widoku klasy lub klas z [CEditView](../mfc/reference/ceditview-class.md) lub [cricheditview —](../mfc/reference/cricheditview-class.md).|Widok zawiera edycji plików wejścia/wyjścia, obsługa Schowka i funkcje. `CRichEditView`zawiera styl tekstu.|  
|Dodaj okna podziału.|Jeśli chcesz obsługiwać Dzielenie okna, Dodaj [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) obiektu okno ramowe SDI lub MDI okna podrzędnego i dołączenie go w tym oknie [OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient) funkcji członkowskiej.|Platformę dostarcza formanty podziału pole obok pasków przewijania i zarządza nimi podzielić na wiele okienka widoku. Jeśli użytkownik dzieli okno, platformę tworzy i dołącza dodatkowy widok obiektów do dokumentu.|  
|Tworzenia, testowania i debugowania aplikacji.|Użyj funkcji Visual C++ do tworzenia, testowania i debugowania aplikacji.|Visual C++ pozwala dostosować kompilacji, łącza i inne opcje. Umożliwia również przeglądać źródło struktury kodu i klasy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Sekwencja operacji przy tworzeniu formantów ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Sekwencja operacji przy tworzeniu aplikacji bazy danych](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [Opieranie się na strukturze](../mfc/building-on-the-framework.md)

