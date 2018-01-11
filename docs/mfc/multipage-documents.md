---
title: Dokumenty wielostronicowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43bc9bbe4653e34c37ae46439baa1e649d6d8042
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multipage-documents"></a>Dokumenty wielostronicowe
W tym artykule opisano protokół drukowania systemu Windows oraz wyjaśniono, jak dokumentów zawierających więcej niż jedną stronę. Artykuł obejmuje następujące tematy:  
  
-   [Protokół drukowania](#_core_the_printing_protocol)  
  
-   [Zastępowanie funkcji klasy widoku](#_core_overriding_view_class_functions)  
  
-   [Podział na strony](#_core_pagination)  
  
-   [Stron drukarki, a strony z dokumentu](#_core_printer_pages_vs.._document_pages)  
  
-   [Godzina drukowania podział na strony](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a>Protokół drukowania  
 Aby wydrukować dokument wielostronicowe, framework i widoku interakcje w następujący sposób. Najpierw Wyświetla platformę **drukowania** okno dialogowe, tworzy kontekstu urządzenia dla drukarki i wywołania [StartDoc](../mfc/reference/cdc-class.md#startdoc) funkcji członkowskiej klasy [CDC](../mfc/reference/cdc-class.md) obiektu. Następnie, dla każdej strony dokumentu, struktura wywołuje [StartPage](../mfc/reference/cdc-class.md#startpage) funkcji członkowskiej klasy `CDC` obiektów, powoduje, że obiekt widoku, aby wydrukować strony i wywołania [EndPage](../mfc/reference/cdc-class.md#endpage) funkcję elementu członkowskiego. Jeśli przed rozpoczęciem określonej strony, należy zmienić tryb drukarki, widok wywołuje [ResetDC](../mfc/reference/cdc-class.md#resetdc), aktualizacje, które [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktury zawierającego nowe informacje o trybie drukarki. Podczas drukowania całego dokumentu struktura wywołuje [EndDoc](../mfc/reference/cdc-class.md#enddoc) funkcję elementu członkowskiego.  
  
##  <a name="_core_overriding_view_class_functions"></a>Zastępowanie funkcji klasy widoku  
 [CView](../mfc/reference/cview-class.md) klasa definiuje kilka funkcji elementów członkowskich, które są wywoływane przez platformę podczas drukowania. Przez zastąpienie tych funkcji w klasie widoku, musisz podać połączeń między struktury drukowania logiki i logiki drukowania w klasie widoku. W poniższej tabeli wymieniono te funkcje Członkowskie.  
  
### <a name="cviews-overridable-functions-for-printing"></a>Funkcje z możliwością zastąpienia CView na potrzeby drukowania  
  
|Nazwa|Przyczynę zastąpienia|  
|----------|---------------------------|  
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Aby wstawić wartości w oknie dialogowym drukowania, szczególnie długość dokumentu|  
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Aby przydzielić czcionek ani innych zasobów GDI|  
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Aby dostosować atrybuty kontekstu urządzenia dla danej strony, lub godzina drukowania podział na strony|  
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Aby wydrukować daną stronę|  
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Można cofnąć alokacji zasobów GDI|  
  
 Można nie przetwarzanie związane z drukowaniem w także inne funkcje, ale te funkcje są tymi, którzy sterują proces drukowania.  
  
 Poniższa ilustracja przedstawia kroki związane z procesem drukowania i wskazuje, gdzie każdy z `CView`na drukowanie elementu członkowskiego funkcje są wywoływane. Dalszej części tego artykułu opisano większość tych kroków bardziej szczegółowo. Dodatkowe części procesu drukowania są opisane w artykule [alokowanie zasobów GDI](../mfc/allocating-gdi-resources.md).  
  
 ![Przetwarzanie pętli drukowanie](../mfc/media/vc37c71.gif "vc37c71")  
Drukowanie pętli  
  
##  <a name="_core_pagination"></a>Podział na strony  
 Platformę przechowuje wiele informacji o zadaniu drukowania w [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury. Niektóre wartości w `CPrintInfo` odnoszą się do dzielenia; te wartości są dostępne, jak pokazano w poniższej tabeli.  
  
### <a name="page-number-information-stored-in-cprintinfo"></a>Numer strony informacji przechowywanych w cprintinfo —  
  
|Zmiennej członkowskiej lub<br /><br /> nazwy funkcji|Numer strony, do których odwołuje się|  
|-----------------------------------------------|----------------------------|  
|`GetMinPage`/`SetMinPage`|Pierwszej strony z dokumentu|  
|`GetMaxPage`/`SetMaxPage`|Ostatniej strony z dokumentu|  
|`GetFromPage`|Pierwsza strona ma być drukowana|  
|`GetToPage`|Ostatnia strona ma być drukowana|  
|`m_nCurPage`|Obecnie drukowanej strony|  
  
 Strony cyfry start 1, czyli pierwszej strony jest numerowane 1, 0 nie. Aby uzyskać więcej informacji na temat tych i innych członków [cprintinfo —](../mfc/reference/cprintinfo-structure.md), zobacz *odwołania MFC*.  
  
 Na początku procesu drukowania, struktura wywołuje widoku [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkcji członkowskiej, wskaźnik do przekazywania `CPrintInfo` struktury. Kreator aplikacji zawiera implementację `OnPreparePrinting` wywołującym [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), innej funkcji członkowskiej klasy `CView`. `DoPreparePrinting`to funkcja, która wyświetla okno dialogowe Drukuj i tworzy kontekstu urządzenia drukarki.  
  
 W tym momencie aplikacji nie może ustalić liczbę stron znajdują się w dokumencie. Używa wartości domyślnej 1 i 0xFFFF numery pierwszej i ostatniej strony dokumentu. Jeśli znasz liczbę stron dokumentu, należy zastąpić `OnPreparePrinting` i Wywołaj [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) dla `CPrintInfo` struktury przed wysłaniem do `DoPreparePrinting`. Dzięki temu można określić długość dokumentu.  
  
 `DoPreparePrinting`następnie wyświetla okno dialogowe drukowania. Gdy powróci ona `CPrintInfo` struktura zawiera wartości podane przez użytkownika. Jeśli użytkownik chce drukowanie wybranego zakresu stron, użytkownik można określić początkową i końcową numery stron w oknie dialogowym drukowania. Platformę pobierają te wartości przy użyciu `GetFromPage` i `GetToPage` funkcje [cprintinfo —](../mfc/reference/cprintinfo-structure.md). Jeśli użytkownik nie określono zakres stron, struktura wywołuje `GetMinPage` i `GetMaxPage` i używa wartości zwracanych do wydruku w całym dokumencie.  
  
 Dla każdej strony z dokumentu do wydrukowania struktura wywołuje dwóch funkcji Członkowskich w klasie widoku [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) i [OnPrint](../mfc/reference/cview-class.md#onprint)i przekazuje każdej funkcji dwa parametry: wskaźnik do [ CDC](../mfc/reference/cdc-class.md) obiektu i wskaźnika do `CPrintInfo` struktury. Po każdej aktualizacji wywołania framework `OnPrepareDC` i `OnPrint`, przekazaniem inną wartość w `m_nCurPage` członkiem `CPrintInfo` struktury. W ten sposób platformę informuje widoku strony, która ma być drukowana.  
  
 [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) funkcji członkowskiej służy także do wyświetlania na ekranie. Przed dokonaniem rysunku powoduje dostosowań do kontekstu urządzenia. `OnPrepareDC`pełni podobną rolę w drukowaniu, jednak istnieje kilka różnic: najpierw `CDC` obiekt reprezentuje kontekstu urządzenia drukarki zamiast kontekstu urządzenia ekranu, a druga Strona, `CPrintInfo` obiekt jest przekazywany jako drugiego parametru. (Ten parametr jest **NULL** podczas `OnPrepareDC` jest wywoływana dla ekranu.) Zastąpienie `OnPrepareDC` zmiany kontekstu urządzenia oparte na drukowanie strony. Na przykład można przenieść pochodzenia okienka ekranu i obszaru przycinania, aby upewnić się, że wydruku odpowiedniej części dokumentu.  
  
 [OnPrint](../mfc/reference/cview-class.md#onprint) funkcji członkowskiej wykonuje rzeczywiste drukowanie strony. Artykuł [jak domyślne drukowania jest wykonywane](../mfc/how-default-printing-is-done.md) pokazuje, jak struktura wywołuje [OnDraw](../mfc/reference/cview-class.md#ondraw) z kontekstu urządzenia drukarki do wykonania drukowania. Mówiąc ściślej, wywołania framework `OnPrint` z `CPrintInfo` struktury i kontekst urządzenia i `OnPrint` przekazuje kontekst urządzenia do `OnDraw`. Zastąpienie `OnPrint` do wykonania żadnych renderowania, które należy wykonać tylko podczas drukowania, a nie do ekranu. Na przykład, aby wydrukować nagłówków i stopek (zapoznaj się z artykułem [nagłówków i stopek](../mfc/headers-and-footers.md) Aby uzyskać więcej informacji). Następnie wywołaj `OnDraw` z zastąpienia z `OnPrint` wspólne dla zarówno ekranu renderowania i drukowania.  
  
 Fakt który `OnDraw` nie renderowania, dla obu rozdzielczości i drukowanie oznacza, że aplikacja jest w trybie WYSIWYG: "What you see is what you get." Jednak zdarzyć, że nie są zapisywania WYSIWYG aplikacji. Na przykład należy wziąć pod uwagę tekstu edytor, który używa pogrubioną czcionką do drukowania, ale wyświetla kody kontroli, aby wskazać pogrubioną na ekranie. W takiej sytuacji należy użyć `OnDraw` wyłącznie do wyświetlania na ekranie. Jeśli zastąpienie `OnPrint`, Zastąp wywołanie `OnDraw` z wywołaniem do oddzielnych funkcji rysowania. Ta funkcja pobiera dokument sposób wyświetlania w dokumencie przy użyciu atrybutów, które nie będą wyświetlane na ekranie.  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a>Vs stron drukarki. Strony z dokumentu  
 W przypadku odwoływania się do strony liczb, czasami jest niezbędne do rozróżniania koncepcji drukarki strony i koncepcji dokumentu, strony. Z punktu widzenia drukarki strona jest jeden arkusz papieru. Jednak jeden arkusz papieru nie zawsze jest równa jedną stronę dokumentu. Na przykład podczas drukowania, biuletynu, gdzie arkusze mają być składane, jeden arkusz papieru może zawierać pierwsza i ostatnia strona dokumentu obok siebie. Podobnie podczas drukowania arkusza kalkulacyjnego, dokument nie składają się z stron w ogóle. Zamiast tego jeden arkusz papieru może zawierać wiersze od 1 do 20, kolumny 6 do 10.  
  
 Wszystkie strony numery w [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury odwoływać się do stron drukarki. Wywołania framework `OnPrepareDC` i `OnPrint` raz dla każdego z nich papieru, który zostanie przekazany do drukarki. Jeśli zastąpienie [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkcja Określ długość dokumentu, należy użyć stron drukarki. Jeśli ma odpowiednika (oznacza to, że jedną stronę drukarki jest równa jedną stronę dokumentu), wówczas jest to łatwe. Jeśli z drugiej strony, strony z dokumentu i strony drukarki nie bezpośrednio odpowiadają musi tłumaczenie między nimi. Rozważmy na przykład drukowanie arkusza kalkulacyjnego. W przypadku przesłaniania `OnPreparePrinting`, musisz obliczyć ile arkuszy będą musieli wydrukować cały arkusz kalkulacyjny, a następnie użyj tej wartości podczas wywoływania metody `SetMaxPage` funkcji członkowskiej klasy `CPrintInfo`. Podobnie w przypadku przesłaniania `OnPrepareDC`, muszą tłumaczyć `m_nCurPage` do zakresu wierszy i kolumn, które będą wyświetlane w tym arkuszu określonego i odpowiednio dostosować pochodzenia okienka ekranu.  
  
##  <a name="_core_print.2d.time_pagination"></a>Godzina drukowania podział na strony  
 W niektórych sytuacjach klasy widoku może nie wiedzieć z wyprzedzeniem jak długo ma dokumentu, dopóki ma faktycznie wydrukowana. Na przykład załóżmy, że aplikacja nie jest WYSIWYG, więc długość dokumentu na ekranie nie odpowiada jego długość po wydrukowaniu.  
  
 Powoduje to problem, aby zastąpić [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) dla klasy widoku: nie można przekazać wartości do `SetMaxPage` funkcji [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury, ponieważ nie wiadomo, długość dokument. Jeśli użytkownik nie określono numer strony, aby zatrzymać za pomocą okna dialogowego drukowania, platformę nie może ustalić, kiedy przestać wydruku pętli. Jedynym sposobem, aby określić, kiedy przestać wydruku pętli jest wydrukować dokument i zobaczyć po jej zakończeniu. Klasy widoku musi sprawdzić do końca dokumentu, podczas drukowania, a po osiągnięciu końcu poinformuje platformę.  
  
 Platformę opiera się na klasie widoku [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) funkcji w celu przekazania kiedy przestać. Po każdym wywołaniu `OnPrepareDC`, platformę sprawdza członkiem `CPrintInfo` struktury `m_bContinuePrinting`. Jego wartość domyślna to **wartość TRUE.** Tak długo, jak pozostaje więc w ramach nadal wydruku pętli. Jeśli wartość jest ustawiona na **FALSE**, zatrzymuje framework. Aby wykonać podział na strony godzina drukowania, Zastąp `OnPrepareDC` do sprawdzenia, czy koniec dokumentu został osiągnięty i ustaw `m_bContinuePrinting` do **FALSE** gdy ma.  
  
 Domyślna implementacja `OnPrepareDC` ustawia `m_bContinuePrinting` do **FALSE** Jeśli bieżąca strona jest większa niż 1. Oznacza to, że jeśli nie została określona długość dokumentu, platformę przyjęto założenie, że dokument jest długo jedną stronę. W wyniku tego jest to, że należy zachować ostrożność, jeśli zostanie wywołana wersja klasy podstawowej `OnPrepareDC`. Nie wolno zakładać, że `m_bContinuePrinting` będzie **TRUE** po wywołaniu metody klasy podstawowej wersji.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Nagłówki i stopki](../mfc/headers-and-footers.md)  
  
-   [Alokowanie zasobów GDI](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie](../mfc/printing.md)   
 [Cview — klasa](../mfc/reference/cview-class.md)   
 [Klasa CDC](../mfc/reference/cdc-class.md)