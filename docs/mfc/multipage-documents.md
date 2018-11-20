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
ms.openlocfilehash: b4ec9f456443b9cd180f1558946829281bc10a36
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176383"
---
# <a name="multipage-documents"></a>Dokumenty wielostronicowe

W tym artykule opisano protokół drukowania Windows oraz wyjaśniono, jak drukowanie dokumentów, które zawierają więcej niż jedną stronę. Tego artykułu obejmuje następujące tematy:

- [Protokół drukowania](#_core_the_printing_protocol)

- [Zastępowanie funkcji klasy widoku](#_core_overriding_view_class_functions)

- [Podział na strony](#_core_pagination)

- [Strony wydruku a stron dokumentu](#_core_printer_pages_vs.._document_pages)

- [Drukuj w czasie dzielenia na strony](#_core_print.2d.time_pagination)

##  <a name="_core_the_printing_protocol"></a> Protokół drukowania

Aby wydrukować dokument wielostronicowe, framework i widoku wchodzić w interakcje w następujący sposób. Po raz pierwszy wyświetli ramach **drukowania** okno dialogowe, tworzy kontekst urządzenia dla drukarki i wywołania [StartDoc](../mfc/reference/cdc-class.md#startdoc) funkcji składowej typu [CDC](../mfc/reference/cdc-class.md) obiektu. Następnie dla każdej strony dokumentu struktura wywołuje [StartPage](../mfc/reference/cdc-class.md#startpage) funkcji składowej typu `CDC` obiektów, powoduje, że obiekt widoku, aby wydrukować strony i wywołań [EndPage](../mfc/reference/cdc-class.md#endpage) funkcja elementu członkowskiego. Jeśli tryb drukarki, należy zmienić przed rozpoczęciem na danej stronie, wywołuje widok [ResetDC](../mfc/reference/cdc-class.md#resetdc), aktualizacje, które [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury zawierającej nowych informacji o trybie drukarki. Gdy cały dokument został wydrukowany, struktura wywołuje [EndDoc](../mfc/reference/cdc-class.md#enddoc) funkcja elementu członkowskiego.

##  <a name="_core_overriding_view_class_functions"></a> Zastępowanie funkcji klasy widoku

[CView](../mfc/reference/cview-class.md) klasa definiuje kilka funkcji Członkowskich, które są wywoływane przez platformę podczas drukowania. Przez zastąpienie tych funkcji w klasie widoku, musisz podać połączeń między logiki drukowania struktury i klasy widoku logiki drukowania. W poniższej tabeli wymieniono te funkcje elementów członkowskich.

### <a name="cviews-overridable-functions-for-printing"></a>Funkcje z możliwością zastąpienia firmy CView związane z drukowaniem

|Nazwa|Przyczynę zastąpienia|
|----------|---------------------------|
|[Onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting)|Aby wstawić wartości w oknie dialogowym drukowania, szczególnie długość dokumentu|
|[Onbeginprinting —](../mfc/reference/cview-class.md#onbeginprinting)|Aby przydzielić czcionki lub innych zasobów GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|By dostosować atrybuty kontekstu urządzenia dla danej strony można też wykonać wydruku w czasie dzielenia na strony|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Aby wydrukować daną stronę|
|[Onendprinting —](../mfc/reference/cview-class.md#onendprinting)|Można cofnąć alokacji zasobów GDI|

Związane z drukowaniem przetwarzania w innych funkcjach, a także można zrobić, ale te funkcje są tymi, które dysku proces drukowania.

Poniższa ilustracja przedstawia kroki związane z procesem drukowania i wskazuje, gdzie każdy z `CView`na drukowanie Członkowskie, które funkcje są wywoływane. W pozostałej części tego artykułu opisano większość z tych kroków, które bardziej szczegółowo. Dodatkowe elementy proces drukowania są opisane w artykule [alokowanie zasobów GDI](../mfc/allocating-gdi-resources.md).

![Drukowanie procesu pętli](../mfc/media/vc37c71.gif "procesu pętli drukowania") <br/>
Pętla drukowania

##  <a name="_core_pagination"></a> Podział na strony

Struktura przechowuje wiele informacji o zadaniu drukowania w [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury. Niektóre wartości w `CPrintInfo` odnoszą się do dzielenia na strony; te wartości są dostępne, jak pokazano w poniższej tabeli.

### <a name="page-number-information-stored-in-cprintinfo"></a>Numer strony informacji przechowywanych w cprintinfo —

|Zmiennej składowej lub<br /><br /> nazwy funkcji|Numer strony, do których odwołuje się|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Pierwsza strona dokumentów|
|`GetMaxPage`/`SetMaxPage`|Ostatniej strony dokumentu|
|`GetFromPage`|Pierwszą stronę do wydrukowania|
|`GetToPage`|Ostatnią stronę do wydrukowania|
|`m_nCurPage`|Obecnie drukowanej strony|

Start numery strony na 1, czyli pierwszej strony ponumerowane 1, 0 nie. Aby uzyskać więcej informacji na temat tych i innych członków [cprintinfo —](../mfc/reference/cprintinfo-structure.md), zobacz *odwołanie MFC*.

Na początku procesu drukowania, struktura wywołuje widok [onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting) funkcji składowej, wskaźnik do przekazywania `CPrintInfo` struktury. Kreator aplikacji zawiera implementacja `OnPreparePrinting` wywołująca [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), innej funkcji składowej typu `CView`. `DoPreparePrinting` jest funkcją, która wyświetla okno dialogowe drukowania i tworzy kontekst urządzenia drukarki.

Na tym etapie aplikacja nie wie, jak wiele stron znajdują się w dokumencie. Używa wartości domyślnej 1 i 0xFFFF dla numerów pierwszej i ostatniej strony dokumentu. Jeśli wiesz, jak wiele stron dokumentu, zastępują `OnPreparePrinting` i wywołać [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) dla `CPrintInfo` struktury przed wysłaniem go do `DoPreparePrinting`. Dzięki temu można określić długość dokumentu.

`DoPreparePrinting` następnie wyświetla okno dialogowe drukowania. Gdy zwraca ono `CPrintInfo` struktura zawiera wartości podane przez użytkownika. Jeśli użytkownik zamierza drukowanie wybranego zakresu stron, użytkownik można określić początkową i końcową numery stron w oknie dialogowym drukowania. Struktura pobiera te wartości przy użyciu `GetFromPage` i `GetToPage` funkcji [cprintinfo —](../mfc/reference/cprintinfo-structure.md). Jeśli użytkownik nie określono zakres stron, struktura wywołuje `GetMinPage` i `GetMaxPage` i używa wartości zwracanych do drukowania całego dokumentu.

Dla każdej strony dokumentu do wydrukowania struktura wywołuje dwóch funkcji składowych w klasie widoku [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) i [OnPrint](../mfc/reference/cview-class.md#onprint)i przekazuje każda funkcja dwa parametry: wskaźnik do [ Przechwytywanie zmian danych](../mfc/reference/cdc-class.md) obiektu i wskaźnik `CPrintInfo` struktury. Każdym struktura wywołuje `OnPrepareDC` i `OnPrint`, przekazuje on inną wartość w *m_nCurPage* członkiem `CPrintInfo` struktury. W ten sposób ramach informuje widoku strony, na które mają być drukowane.

[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) funkcja elementu członkowskiego służy również do wyświetlania na ekranie. Dzięki temu dostosowań do kontekstu urządzenia przed rozpoczęciem rysowania. `OnPrepareDC` pełni podobną rolę w drukowania, ale istnieje kilka różnic: po pierwsze, `CDC` obiekt reprezentuje kontekst urządzenia drukarki, zamiast kontekstu urządzenia ekranu, a drugi, `CPrintInfo` obiekt jest przekazywany jako drugi parametr. (Ten parametr jest **NULL** podczas `OnPrepareDC` nosi nazwę do wyświetlania na ekranie.) Zastąp `OnPrepareDC` zmiany kontekstu urządzenia oparte na stronę, która jest drukowany. Na przykład można przenieść pochodzenia okienka ekranu i obszaru przycinania, aby upewnić się, że odpowiednie części dokumentu zostanie wydrukowany.

[OnPrint](../mfc/reference/cview-class.md#onprint) funkcja elementu członkowskiego przeprowadza rzeczywiste drukowanie strony. Artykuł [jak domyślne drukowania jest wykonywane](../mfc/how-default-printing-is-done.md) pokazuje, jak struktura wywołuje [OnDraw](../mfc/reference/cview-class.md#ondraw) z kontekstem urządzenia drukarki do wykonania drukowania. Mówiąc ściślej, struktura wywołuje `OnPrint` z `CPrintInfo` struktury i kontekst urządzenia i `OnPrint` przekazuje kontekst urządzenia do `OnDraw`. Zastąp `OnPrint` do wykonania dowolnej renderowania, który ma być przeprowadzane tylko podczas drukowania, a nie do wyświetlania na ekranie. Na przykład, aby wydrukować nagłówków i stopek (zapoznaj się z artykułem [nagłówków i stopek](../mfc/headers-and-footers.md) Aby uzyskać więcej informacji). Następnie wywołaj `OnDraw` z zastępowania metody `OnPrint` do renderowania, które są wspólne dla zarówno wyświetlanie na ekranie i drukowania.

Fakt, `OnDraw` nie renderowania, na ekranie zarówno wyświetlania i drukowanie oznacza, że aplikacja jest w trybie WYSIWYG: "zostanie wyświetlony jest what you get". Jednak Załóżmy, że nie są zapisywanie WYSIWYG aplikacji. Na przykład należy wziąć pod uwagę tekstu edytor, który używa czcionki pogrubionej związane z drukowaniem, ale wyświetla kody sterujące, aby wskazać pogrubioną czcionką na ekranie. W takiej sytuacji należy użyć `OnDraw` wyłącznie do wyświetlania na ekranie. Gdy zastąpisz `OnPrint`, Zastąp wywołanie `OnDraw` wywołaniem to oddzielna funkcja rysowania. Tę funkcję rysuje dokumentu w sposób, który pojawia się w dokumencie przy użyciu atrybutów, które nie będą wyświetlane na ekranie.

##  <a name="_core_printer_pages_vs.._document_pages"></a> Vs stron drukarki. Strony dokumentu

Przy odwoływaniu się numery stron, czasami jest niezbędne do rozróżniania drukarki koncepcji strony i dokumentu koncepcji strony. Z punktu widzenia drukarki strona jest jeden arkusz papieru. Jednak jeden arkusz papieru nie musi być równa się jedną stronę dokumentu. Na przykład podczas drukowania biuletynu, gdzie arkusze mają być składane, jeden arkusz papieru może zawierać imię i nazwisko stron dokumentu, obok siebie. Podobnie jeśli arkusz kalkulacyjny, dokument nie składają się z stron w ogóle. Zamiast tego jeden arkusz papieru może zawierać wiersze od 1 do 20, 6 do 10 kolumn.

Stronie wszystkie liczby w elemencie [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury odnoszą się do strony wydruku. Struktura wywołuje `OnPrepareDC` i `OnPrint` jeden raz dla każdego arkusza dokument, który będzie przekazywał drukarki. Gdy zastąpisz [onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting) funkcji do określenia długość dokumentu, należy użyć strony wydruku. Jeśli ma odpowiednika (oznacza to jedną stronę drukarki jest równa jedną stronę dokumentu), wówczas jest to łatwe. Jeśli z drugiej strony, stron dokumentu a strony wydruku nie są bezpośrednio zgodne, musi przetłumaczyć między nimi. Na przykład należy wziąć pod uwagę drukowanie arkusz kalkulacyjny. Podczas zastępowania `OnPreparePrinting`, musisz obliczyć liczby arkuszy będzie wymagane, aby wydrukować cały arkusz kalkulacyjny, a następnie użycie tej wartości podczas wywoływania `SetMaxPage` funkcji składowej typu `CPrintInfo`. Podobnie podczas zastępowania `OnPrepareDC`, musi przetłumaczyć *m_nCurPage* do zakresu wierszy i kolumn, które będzie wyświetlane w tym określonego arkusza i odpowiednio dostosować pochodzenia okienka ekranu.

##  <a name="_core_print.2d.time_pagination"></a> Drukuj w czasie dzielenia na strony

W niektórych sytuacjach klasy widoku może nie wiedzieć z wyprzedzeniem ile dokument trwa do momentu rzeczywiście został wydrukowany. Na przykład załóżmy, że aplikacja nie jest typu WYSIWYG, dlatego długość dokumentu na ekranie nie odpowiada jego długość po wydrukowaniu.

Powoduje to, że problem podczas zastąpienia [onprepareprinting —](../mfc/reference/cview-class.md#onprepareprinting) dla swojej klasy widoku: nie można przekazać wartość do `SetMaxPage` funkcji [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury, ponieważ nie wiesz, długość dokument. Jeśli użytkownik nie określono numer strony, aby zatrzymać przy użyciu okna dialogowego drukowania, struktura nie może ustalić, kiedy przestać drukowania pętli. Jedynym sposobem ustalenia, kiedy przestać drukowania pętli jest wydrukować dokument i zobaczyć, po jego zakończeniu. Klasa widoku musi sprawdzić do końca dokumentu, podczas drukowania, a następnie poinformować platformę, gdy zostanie osiągnięty koniec.

Struktura opiera się na klasie widoku [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) funkcję, aby ustalić, kiedy przestać. Po każdym wywołaniu `OnPrepareDC`, struktura sprawdza, czy członek `CPrintInfo` strukturę o nazwie *m_bContinuePrinting*. Jego wartość domyślna to **wartość TRUE.** Tak długo, jak długo pozostaje on, więc w ramach kontynuuje drukowania pętli. Jeśli jest równa **FALSE**, zatrzymuje framework. Aby przeprowadzić podział na strony wydruku w czasie, należy zastąpić `OnPrepareDC` do sprawdzenia, czy koniec dokumentu zostały osiągnięte i ustawiać *m_bContinuePrinting* do **FALSE** kiedy ma.

Domyślna implementacja klasy `OnPrepareDC` ustawia *m_bContinuePrinting* do **FALSE** Jeśli bieżąca strona jest większa niż 1. Oznacza to, że jeśli długość dokumentu nie został określony, struktura przyjęto założenie, że dokument jest długo po jednej stronie. W wyniku tego jest, że należy zachować ostrożność, jeśli zostanie wywołana wersja klasy bazowej `OnPrepareDC`. Nie należy zakładać, że *m_bContinuePrinting* będzie **TRUE** po wywołaniu wersją klasy bazowej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Nagłówki i stopki](../mfc/headers-and-footers.md)

- [Alokowanie zasobów GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)<br/>
[Klasa CView](../mfc/reference/cview-class.md)<br/>
[Klasa CDC](../mfc/reference/cdc-class.md)