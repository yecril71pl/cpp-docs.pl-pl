---
title: Dokumenty wielostronicowe
ms.date: 11/19/2018
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
ms.openlocfilehash: c73692c315b07d6b690180886d494ee12f85f52d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621055"
---
# <a name="multipage-documents"></a>Dokumenty wielostronicowe

W tym artykule opisano protokół drukowania systemu Windows i wyjaśniono, jak drukować dokumenty zawierające więcej niż jedną stronę. Artykuł obejmuje następujące tematy:

- [Protokół drukowania](#_core_the_printing_protocol)

- [Zastępowanie funkcji wyświetlania klas](#_core_overriding_view_class_functions)

- [Dzielenia na strony](#_core_pagination)

- [Strony drukarki a strony dokumentów](#_core_printer_pages_vs.._document_pages)

- [Stronicowanie w czasie drukowania](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Protokół drukowania

Do drukowania dokumentu wielostronicowego, struktura i widok są współpracujące w następujący sposób. Najpierw środowisko wyświetla okno dialogowe **Drukowanie** , tworzy kontekst urządzenia dla drukarki i wywołuje funkcję elementu członkowskiego [StartDoc](reference/cdc-class.md#startdoc) obiektu [przechwytywania](reference/cdc-class.md) . Następnie dla każdej strony dokumentu, struktura wywołuje funkcję elementu członkowskiego [StartPage](reference/cdc-class.md#startpage) `CDC` obiektu, instruuje obiekt widoku, aby wydrukował stronę i wywołuje funkcję elementu członkowskiego [EndPage](reference/cdc-class.md#endpage) . Jeśli tryb drukarki należy zmienić przed rozpoczęciem określonej strony, widok wywołuje [ResetDC](reference/cdc-class.md#resetdc), która aktualizuje strukturę [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) zawierającą nowe informacje o trybie drukarki. Po wydrukowaniu całego dokumentu struktura wywołuje funkcję członkowską [EndDoc](reference/cdc-class.md#enddoc) .

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Zastępowanie funkcji wyświetlania klas

Klasa [CView](reference/cview-class.md) definiuje kilka funkcji Członkowskich, które są wywoływane przez platformę podczas drukowania. Zastępując te funkcje w klasie widoku, udostępniasz połączenia między logiką drukowania struktury i logiką drukowania klasy widoku. W poniższej tabeli wymieniono te funkcje elementów członkowskich.

### <a name="cviews-overridable-functions-for-printing"></a>CView funkcje do drukowania

|Nazwa|Powód przesłaniania|
|----------|---------------------------|
|[OnPreparePrinting](reference/cview-class.md#onprepareprinting)|Aby wstawić wartości w oknie dialogowym Drukowanie, w szczególności długość dokumentu|
|[OnBeginPrinting](reference/cview-class.md#onbeginprinting)|Aby przydzielić czcionki lub inne zasoby GDI|
|[OnPrepareDC](reference/cview-class.md#onpreparedc)|Aby dostosować atrybuty kontekstu urządzenia dla danej strony lub do wykonywania stronicowania w czasie drukowania|
|[Wydruku](reference/cview-class.md#onprint)|Aby wydrukować daną stronę|
|[OnEndPrinting](reference/cview-class.md#onendprinting)|Aby cofnąć alokację zasobów GDI|

Można również wykonywać przetwarzanie związane z drukowaniem w innych funkcjach, ale te funkcje są tymi, które umożliwiają proces drukowania.

Na poniższej ilustracji przedstawiono kroki związane z procesem drukowania i pokazano, gdzie `CView` są wywoływane poszczególne funkcje elementów członkowskich drukowania. W pozostałej części tego artykułu opisano większość tych kroków bardziej szczegółowo. Dodatkowe części procesu drukowania zostały opisane w artykule [alokowanie zasobów GDI](allocating-gdi-resources.md).

![Proces pętli drukowania](../mfc/media/vc37c71.gif "Proces pętli drukowania") <br/>
Pętla drukowania

## <a name="pagination"></a><a name="_core_pagination"></a>Dzielenia na strony

Struktura przechowuje wiele informacji o zadaniu drukowania w strukturze [CPrintInfo](reference/cprintinfo-structure.md) . Kilka wartości `CPrintInfo` związanych z podziałem na strony; te wartości są dostępne, jak pokazano w poniższej tabeli.

### <a name="page-number-information-stored-in-cprintinfo"></a>Informacje o numerze strony przechowywane w CPrintInfo

|Zmienna członkowska lub<br /><br /> nazwy funkcji|Numer strony, do której istnieje odwołanie|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Pierwsza strona dokumentu|
|`GetMaxPage`/`SetMaxPage`|Ostatnia strona dokumentu|
|`GetFromPage`|Pierwsza strona do wydrukowania|
|`GetToPage`|Ostatnia strona do wydrukowania|
|`m_nCurPage`|Trwa drukowanie strony|

Numery stron zaczynają się od 1, oznacza to, że pierwsza strona ma numer 1, a nie 0. Aby uzyskać więcej informacji na temat tych i innych elementów członkowskich [CPrintInfo](reference/cprintinfo-structure.md), zobacz *Kompendium MFC*.

Na początku procesu drukowania, struktura wywołuje funkcję elementu członkowskiego [OnPreparePrinting](reference/cview-class.md#onprepareprinting) widoku, przekazując wskaźnik do `CPrintInfo` struktury. Kreator aplikacji zapewnia implementację `OnPreparePrinting` , która wywołuje [DoPreparePrinting by otworzyć](reference/cview-class.md#doprepareprinting), inną funkcję członkowską `CView` . `DoPreparePrinting`jest funkcją, która wyświetla okno dialogowe Drukuj i tworzy kontekst urządzenia drukarki.

W tym momencie aplikacja nie wie, ile stron znajduje się w dokumencie. Używa wartości domyślnych 1 i 0xFFFF dla numerów pierwszej i ostatniej strony dokumentu. Jeśli wiesz, ile stron posiada dokument, Zastąp `OnPreparePrinting` i Wywołaj metodę [SetMaxPage]--brokenlink--(Reference/CPrintInfo-Class. MD # SetMaxPage) dla `CPrintInfo` struktury, zanim wyślesz ją do usługi `DoPreparePrinting` . Pozwala to określić długość dokumentu.

`DoPreparePrinting`następnie zostanie wyświetlone okno dialogowe Drukowanie. Gdy zwróci, `CPrintInfo` Struktura zawiera wartości określone przez użytkownika. Jeśli użytkownik chce wydrukować tylko wybrany zakres stron, może określić początkową i końcową liczbę numerów stron w oknie dialogowym drukowania. Struktura pobiera te wartości przy użyciu `GetFromPage` funkcji i `GetToPage` programu [CPrintInfo](reference/cprintinfo-structure.md). Jeśli użytkownik nie określi zakresu stron, struktura wywołuje `GetMinPage` i `GetMaxPage` i używa wartości zwracanych do wydrukowania całego dokumentu.

Dla każdej strony dokumentu do wydrukowania, struktura wywołuje dwie funkcje składowe w klasie widoku, [OnPrepareDC](reference/cview-class.md#onpreparedc) i [OnPrint](reference/cview-class.md#onprint)i przekazuje każdą funkcję dwa parametry: wskaźnik [do obiektu](reference/cdc-class.md) przerzutowania i wskaźnik do `CPrintInfo` struktury. Za każdym razem, gdy struktura wywołuje `OnPrepareDC` i `OnPrint` , przekazuje inną wartość w *m_nCurPage* składowej `CPrintInfo` struktury. W ten sposób struktura informuje widok, która strona powinna zostać wydrukowana.

Funkcja członkowska [OnPrepareDC](reference/cview-class.md#onpreparedc) jest również używana do wyświetlania ekranu. Wprowadza zmiany kontekstu urządzenia przed rysowaniem. `OnPrepareDC`Program obsługuje podobną rolę w drukowaniu, ale istnieje kilka różnic: najpierw `CDC` obiekt reprezentuje kontekst urządzenia drukarki zamiast kontekstu urządzenia ekranu, a drugi, `CPrintInfo` obiekt jest przenoszona jako drugi parametr. (Ten parametr ma **wartość null** , gdy `OnPrepareDC` jest wywoływany na potrzeby wyświetlania ekranu). Przesłoń, `OnPrepareDC` Aby wprowadzić zmiany kontekstu urządzenia na podstawie tego, która strona jest drukowana. Na przykład można przenieść Źródło okienka ekranu i obszar wycinka, aby upewnić się, że jest drukowana odpowiednia część dokumentu.

Funkcja składowej [OnPrint](reference/cview-class.md#onprint) wykonuje rzeczywiste drukowanie strony. W tym artykule opisano sposób tworzenia [domyślnego drukowania](how-default-printing-is-done.md) pokazuje, w jaki sposób struktura wywołuje [OnDraw](reference/cview-class.md#ondraw) z kontekstem urządzenia drukarki do wykonywania operacji drukowania. Dokładniej, struktura wywołuje `OnPrint` `CPrintInfo` strukturę i kontekst urządzenia i `OnPrint` przekazuje kontekst urządzenia do `OnDraw` . Przesłoń `OnPrint` , aby wykonać wszystkie renderingi, które powinny być wykonywane tylko podczas drukowania, a nie na ekranie. Na przykład, aby wydrukować nagłówki lub stopki (zobacz [nagłówki i stopki](headers-and-footers.md) artykułów, aby uzyskać więcej informacji). Następnie Wywołaj `OnDraw` z przesłonięcia, `OnPrint` Aby wykonać renderowanie wspólne dla wyświetlania ekranu i drukowania.

Fakt, że `OnDraw` renderowanie zarówno ekranu, jak i drukowania oznacza, że aplikacja jest w trybie WYSIWYG: "co widzisz." Załóżmy jednak, że nie piszesz aplikacji w trybie WYSIWYG. Rozważmy na przykład edytor tekstu, który używa pogrubionej czcionki do drukowania, ale wyświetla kody kontrolne, aby wskazać pogrubiony tekst na ekranie. W takiej sytuacji należy używać `OnDraw` wyłącznie do wyświetlania ekranu. Podczas przesłonięcia Zastąp `OnPrint` wywołaniem do `OnDraw` odrębnej funkcji rysowania. Ta funkcja rysuje dokument w taki sposób, w jaki pojawia się na papierze, przy użyciu atrybutów, które nie są wyświetlane na ekranie.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Strony drukarki a strony dokumentów

Gdy odwołujesz się do numerów stron, czasami konieczne jest rozróżnienie między koncepcją strony a koncepcją dokumentu. Z punktu widzenia drukarki stroną jest jeden arkusz papieru. Jednak jeden arkusz papieru nie musi być równy jednej stronie dokumentu. Na przykład w przypadku drukowania biuletynu, w którym arkusze mają być składane, jeden arkusz papieru może zawierać zarówno pierwszą, jak i ostatnią stronę dokumentu, obok siebie. Podobnie w przypadku drukowania arkusza kalkulacyjnego dokument nie zawiera żadnych stron. Zamiast tego jeden arkusz papieru może zawierać wiersze od 1 do 20, kolumny od 6 do 10.

Wszystkie numery stron w strukturze [CPrintInfo](reference/cprintinfo-structure.md) odnoszą się do stron drukarki. Struktura wywołuje `OnPrepareDC` i `OnPrint` jeden raz dla każdego arkusza papieru, który przejdzie przez drukarkę. Gdy zastąpisz funkcję [OnPreparePrinting](reference/cview-class.md#onprepareprinting) w celu określenia długości dokumentu, musisz użyć stron drukarki. Jeśli istnieje zgodność jeden-do-jednego (oznacza to, że jedna strona drukarki jest równa jednej stronie dokumentu), to jest to łatwe. Jeśli po drugiej stronie strony dokumentu i strony drukarki nie są bezpośrednio zgodne, należy przetłumaczyć między nimi. Rozważmy na przykład drukowanie arkusza kalkulacyjnego. Podczas zastępowania `OnPreparePrinting` należy obliczyć, ile arkuszy papieru będzie wymaganych do drukowania całego arkusza kalkulacyjnego, a następnie użyć tej wartości podczas wywoływania `SetMaxPage` funkcji składowej `CPrintInfo` . Podobnie w przypadku przesłaniania `OnPrepareDC` należy przetłumaczyć *m_nCurPage* do zakresu wierszy i kolumn, które będą wyświetlane w tym konkretnym arkuszu, a następnie odpowiednio dostosować Źródło okienka ekranu.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Stronicowanie w czasie drukowania

W niektórych sytuacjach Klasa widoku może nie wiedzieć, jak długo dokument jest do momentu wydrukowania. Załóżmy na przykład, że aplikacja nie jest w trybie WYSIWYG, więc długość dokumentu na ekranie nie jest zgodna z długością wydruku.

Powoduje to problem podczas przesłonięcia [OnPreparePrinting](reference/cview-class.md#onprepareprinting) dla klasy widoku: nie można przekazać wartości do `SetMaxPage` funkcji struktury [CPrintInfo](reference/cprintinfo-structure.md) , ponieważ nie jest znana długość dokumentu. Jeśli użytkownik nie określi numeru strony, który ma zostać zatrzymany przy użyciu okna dialogowego Drukuj, struktura nie wie, kiedy należy zatrzymać pętlę drukowania. Jedynym sposobem, aby określić, kiedy należy zatrzymać pętlę drukowania, jest wydrukowanie dokumentu i wyświetlenie go po zakończeniu. Klasa widoku musi sprawdzać koniec dokumentu podczas jego drukowania, a następnie informować platformę, gdy zostanie osiągnięty koniec.

Struktura opiera się na funkcji [OnPrepareDC](reference/cview-class.md#onpreparedc) klasy widoku, aby określić, kiedy ma zostać zatrzymana. Po każdym wywołaniu `OnPrepareDC` , struktura sprawdza element członkowski `CPrintInfo` struktury o nazwie *m_bContinuePrinting*. Wartość domyślna to **true.** Tak długo, jak to pozostanie, struktura kontynuuje pętlę drukowania. Jeśli jest ustawiona na **false**, struktura zostaje zatrzymana. Aby przeprowadzić stronicowanie w czasie drukowania, przesłonić, `OnPrepareDC` Aby sprawdzić, czy osiągnięto koniec dokumentu, i ustawić *M_bContinuePrinting* na **Fałsz** , gdy ma.

Domyślna implementacja `OnPrepareDC` zestawów *M_bContinuePrinting* **wartość false** , jeśli bieżąca strona jest większa niż 1. Oznacza to, że jeśli długość dokumentu nie została określona, struktura zakłada, że dokument jest jednostronicowy. Jedną z konsekwencji jest to, że należy zachować ostrożność, jeśli wywołasz wersję klasy bazowej `OnPrepareDC` . Nie należy zakładać, że *m_bContinuePrinting* będzie **prawdziwe** po wywołaniu wersji klasy bazowej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Nagłówki i stopki](headers-and-footers.md)

- [Alokowanie zasobów GDI](allocating-gdi-resources.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie](printing.md)<br/>
[Klasa CView](reference/cview-class.md)<br/>
[Klasa CDC](reference/cdc-class.md)
