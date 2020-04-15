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
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370733"
---
# <a name="multipage-documents"></a>Dokumenty wielostronicowe

W tym artykule opisano protokół drukowania systemu Windows i wyjaśniono, jak drukować dokumenty zawierające więcej niż jedną stronę. Artykuł obejmuje następujące tematy:

- [Protokół drukowania](#_core_the_printing_protocol)

- [Nadrzędne funkcje klasy widoku](#_core_overriding_view_class_functions)

- [Dzielenie na strony](#_core_pagination)

- [Strony drukarki a strony dokumentów](#_core_printer_pages_vs.._document_pages)

- [Podział na strony w czasie drukowania](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Protokół drukowania

Aby wydrukować wielostronicowy dokument, struktura i widok współdziałają w następujący sposób. Najpierw w ramach jest wyświetlane okno dialogowe **Drukowanie,** tworzy kontekst urządzenia dla drukarki i wywołuje funkcję elementu członkowskiego [StartDoc](../mfc/reference/cdc-class.md#startdoc) obiektu [CDC.](../mfc/reference/cdc-class.md) Następnie dla każdej strony dokumentu, framework wywołuje funkcję elementu `CDC` członkowskiego [StartPage](../mfc/reference/cdc-class.md#startpage) obiektu, instruuje obiekt widoku, aby wydrukować stronę i wywołuje [endpage](../mfc/reference/cdc-class.md#endpage) funkcji elementu członkowskiego. Jeśli tryb drukarki musi zostać zmieniony przed rozpoczęciem określonej strony, widok wywołuje [ResetDC](../mfc/reference/cdc-class.md#resetdc), który aktualizuje strukturę [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) zawierającą nowe informacje o trybie drukarki. Po wydrukowaniu całego dokumentu, framework wywołuje [EndDoc](../mfc/reference/cdc-class.md#enddoc) funkcji elementu członkowskiego.

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Zastępowanie funkcji klasy widoku

[CView](../mfc/reference/cview-class.md) Klasa definiuje kilka funkcji członkowskich, które są wywoływane przez platformę podczas drukowania. Zastępując te funkcje w klasie widoku, należy podać połączenia między logiką drukowania struktury i logiki drukowania klasy widoku. W poniższej tabeli wymieniono te funkcje członkowskie.

### <a name="cviews-overridable-functions-for-printing"></a>Przesąwalalne funkcje CView do drukowania

|Nazwa|Powód zastąpienia|
|----------|---------------------------|
|[Onprepareprinting](../mfc/reference/cview-class.md#onprepareprinting)|Aby wstawić wartości w oknie dialogowym Drukowanie, zwłaszcza długość dokumentu|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Aby przydzielić czcionki lub inne zasoby GDI|
|[Onpreparedc](../mfc/reference/cview-class.md#onpreparedc)|Aby dostosować atrybuty kontekstu urządzenia dla danej strony lub wykonać podział na strony w czasie drukowania|
|[Onprint](../mfc/reference/cview-class.md#onprint)|Aby wydrukować daną stronę|
|[Drukowanie onend](../mfc/reference/cview-class.md#onendprinting)|Aby zdyskontować alokację zasobów GDI|

Można również przetwarzać związane z drukowaniem w innych funkcjach, ale te funkcje są tymi, które napędzają proces drukowania.

Na poniższym rysunku przedstawiono kroki związane z `CView`procesem drukowania i pokazano, gdzie wywoływane są funkcje każdego z elementów członkowskich drukowania. W dalszej części tego artykułu opisano większość z tych kroków bardziej szczegółowo. Dodatkowe części procesu drukowania opisano w artykule [Przydzielanie zasobów GDI](../mfc/allocating-gdi-resources.md).

![Proces pętli drukowania](../mfc/media/vc37c71.gif "Proces pętli drukowania") <br/>
Pętla drukowania

## <a name="pagination"></a><a name="_core_pagination"></a>Paginacja

Struktura przechowuje wiele informacji o zadaniu drukowania w strukturze [CPrintInfo.](../mfc/reference/cprintinfo-structure.md) Kilka wartości `CPrintInfo` w odniesieniu do podziałów na strony; wartości te są dostępne, jak pokazano w poniższej tabeli.

### <a name="page-number-information-stored-in-cprintinfo"></a>Informacje o numerze strony przechowywane w CPrintInfo

|Zmienna elementu członkowskiego lub<br /><br /> nazwa(y) funkcji|Numer strony, do którego się odwołuje|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Pierwsza strona dokumentu|
|`GetMaxPage`/`SetMaxPage`|Ostatnia strona dokumentu|
|`GetFromPage`|Pierwsza strona do wydrukowania|
|`GetToPage`|Ostatnia strona do wydrukowania|
|`m_nCurPage`|Strona aktualnie drukowana|

Numery stron zaczynają się od 1, czyli pierwsza strona jest ponumerowana 1, a nie 0. Aby uzyskać więcej informacji na temat tych i innych członków [CPrintInfo,](../mfc/reference/cprintinfo-structure.md)zobacz *odwołanie MFC*.

Na początku procesu drukowania ramach wywołuje [onprepareprinting](../mfc/reference/cview-class.md#onprepareprinting) funkcji elementu członkowskiego widoku, `CPrintInfo` przekazując wskaźnik do struktury. Kreator aplikacji zapewnia implementację tego `OnPreparePrinting` wywołania [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), innej funkcji członkowskiej `CView`. `DoPreparePrinting`jest funkcją, która wyświetla okno dialogowe Drukowanie i tworzy kontekst urządzenia drukarki.

W tym momencie aplikacja nie wie, ile stron znajduje się w dokumencie. Używa wartości domyślnych 1 i 0xFFFF dla numerów pierwszej i ostatniej strony dokumentu. Jeśli wiesz, ile stron ma dokument, `OnPreparePrinting` należy zastąpić i wywołać [SetMaxPage] --brokenlink--(reference/cprintinfo-class.md#setmaxpage) dla `CPrintInfo` struktury przed wysłaniem go do `DoPreparePrinting`. Dzięki temu można określić długość dokumentu.

`DoPreparePrinting`następnie wyświetli okno dialogowe Drukowanie. Po powrocie `CPrintInfo` struktura zawiera wartości określone przez użytkownika. Jeśli użytkownik chce wydrukować tylko wybrany zakres stron, może określić numery stron początkowych i kończących w oknie dialogowym Drukowanie. Struktura pobiera te wartości `GetFromPage` przy `GetToPage` użyciu funkcji i [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Jeśli użytkownik nie określi zakresu stron, struktura `GetMinPage` `GetMaxPage` wywołuje i używa wartości zwróconych do wydrukowania całego dokumentu.

Dla każdej strony dokumentu do wydrukowania, ramach wywołuje dwie funkcje członkowskie w klasie widoku, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) i [OnPrint](../mfc/reference/cview-class.md#onprint)i przekazuje każdej `CPrintInfo` funkcji dwa parametry: wskaźnik do obiektu [CDC](../mfc/reference/cdc-class.md) i wskaźnik do struktury. Za każdym `OnPrepareDC` razem, `OnPrint`gdy struktura wywołuje i , przekazuje inną `CPrintInfo` wartość w *m_nCurPage* element członkowski struktury. W ten sposób struktura informuje widok, która strona powinna być drukowana.

Funkcja elementu członkowskiego [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) jest również używana do wyświetlania ekranu. Wprowadza zmiany w kontekście urządzenia przed rozpoczęciem rysowania. `OnPrepareDC`pełni podobną rolę w drukowaniu, ale istnieje kilka `CDC` różnic: po pierwsze, obiekt reprezentuje kontekst urządzenia drukarki `CPrintInfo` zamiast kontekstu urządzenia ekranu, a po drugie, obiekt jest przekazywany jako drugi parametr. (Ten parametr ma `OnPrepareDC` **wartość NULL,** gdy jest wywoływana do wyświetlania ekranu). Zastądeń, `OnPrepareDC` aby wprowadzić zmiany w kontekście urządzenia na podstawie strony, która jest drukowana. Można na przykład przenieść początek rzutni i obszar przycinania, aby upewnić się, że odpowiednia część dokumentu zostanie wydrukowana.

Funkcja elementu członkowskiego [OnPrint](../mfc/reference/cview-class.md#onprint) wykonuje rzeczywiste drukowanie strony. Artykuł [Jak domyślne drukowanie jest wykonywane](../mfc/how-default-printing-is-done.md) pokazuje, jak framework wywołuje [OnDraw](../mfc/reference/cview-class.md#ondraw) z kontekstu urządzenia drukarki do wykonywania drukowania. Dokładniej, struktura wywołuje `OnPrint` ze `CPrintInfo` strukturą i kontekstem urządzenia `OnPrint` i `OnDraw`przekazuje kontekst urządzenia do . Zastąd, aby wykonać renderowanie, `OnPrint` które powinno być wykonywane tylko podczas drukowania, a nie do wyświetlania ekranu. Na przykład, aby wydrukować nagłówki lub stopki (więcej informacji można znaleźć w [artykule Nagłówki i stopki).](../mfc/headers-and-footers.md) Następnie `OnDraw` wywołać z zastąpienia `OnPrint` do renderowania wspólnego do wyświetlania na ekranie i drukowania.

Fakt, `OnDraw` że renderowanie zarówno do wyświetlania na ekranie, jak i drukowania oznacza, że aplikacja jest WYSIWYG: "To, co widzisz, jest tym, co dostajesz". Załóżmy jednak, że nie piszesz aplikacji WYSIWYG. Rozważmy na przykład edytor tekstu, który używa pogrubionej czcionki do drukowania, ale wyświetla kody sterujące wskazujące pogrubiony tekst na ekranie. W takiej sytuacji używasz `OnDraw` wyłącznie do wyświetlania ekranu. Po zastąpieniu `OnPrint`zastąp `OnDraw` wywołanie wywołaniem oddzielnej funkcji rysowania. Ta funkcja rysuje dokument w sposób, w jaki pojawia się na papierze, używając atrybutów, które nie są wyświetlane na ekranie.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Strony drukarki a strony dokumentów

W przypadku odwoływania się do numerów stron czasami konieczne jest rozróżnienie między koncepcją strony drukarki a koncepcją strony dokumentu. Z punktu widzenia drukarki strona to jeden arkusz papieru. Jednak jeden arkusz papieru nie musi być równy jednej stronie dokumentu. Na przykład w przypadku drukowania biuletynu, w którym arkusze mają być składane, jeden arkusz papieru może zawierać zarówno pierwszą, jak i ostatnią stronę dokumentu obok siebie. Podobnie, jeśli drukujesz arkusz kalkulacyjny, dokument nie składa się w ogóle ze stron. Zamiast tego jeden arkusz papieru może zawierać wiersze od 1 do 20, kolumny od 6 do 10.

Wszystkie numery stron w strukturze [CPrintInfo](../mfc/reference/cprintinfo-structure.md) odnoszą się do stron drukarki. Struktura wywołuje `OnPrepareDC` `OnPrint` i raz dla każdego arkusza papieru, który przejdzie przez drukarkę. Podczas zastępowania funkcji [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) w celu określenia długości dokumentu należy użyć stron drukarki. Jeśli istnieje korespondencja jeden do jednego (to znaczy jedna strona drukarki jest równa jednej stronie dokumentu), to jest to łatwe. Jeśli natomiast strony dokumentów i strony drukarki nie odpowiadają bezpośrednio, należy przetłumaczyć między nimi. Rozważmy na przykład wydrukowanie arkusza kalkulacyjnego. Podczas zastępowania `OnPreparePrinting`należy obliczyć, ile arkuszy papieru będzie wymaganych do wydrukowania całego `SetMaxPage` arkusza `CPrintInfo`kalkulacyjnego, a następnie użyć tej wartości podczas wywoływania funkcji elementu członkowskiego . Podobnie podczas zastępowania `OnPrepareDC`należy przetłumaczyć *m_nCurPage* na zakres wierszy i kolumn, które pojawią się na danym arkuszu, a następnie odpowiednio dostosować początek rzutni.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Podział na strony w czasie drukowania

W niektórych sytuacjach klasa widoku może nie wiedzieć z wyprzedzeniem, jak długo dokument jest, dopóki nie został faktycznie wydrukowany. Załóżmy na przykład, że aplikacja nie jest WYSIWYG, więc długość dokumentu na ekranie nie odpowiada jego długości podczas drukowania.

Powoduje to problem podczas [zastępowania OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) dla klasy widoku: nie można `SetMaxPage` przekazać wartość do funkcji [CPrintInfo](../mfc/reference/cprintinfo-structure.md) struktury, ponieważ nie znasz długości dokumentu. Jeśli użytkownik nie określi numeru strony, aby zatrzymać się przy użyciu okna dialogowego Drukowanie, struktura nie wie, kiedy zatrzymać pętlę drukowania. Jedynym sposobem określenia, kiedy zatrzymać pętlę drukowania, jest wydrukowanie dokumentu i sprawdzenie, kiedy się kończy. Klasa widoku musi sprawdzić koniec dokumentu podczas drukowania, a następnie poinformować o ramach po osiągnięciu końca.

Struktura opiera się na funkcji [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) klasy view, aby poinformować ją, kiedy należy go zatrzymać. Po każdym `OnPrepareDC`wywołaniu , ramy sprawdza `CPrintInfo` element członkowski struktury o nazwie *m_bContinuePrinting*. Jego wartością domyślną jest **PRAWDA.** Tak długo, jak pozostaje tak, framework kontynuuje pętli drukowania. Jeśli jest ustawiona na **FALSE**, struktura zatrzymuje. Aby wykonać podział na strony w `OnPrepareDC` czasie drukowania, należy zastąpić, aby sprawdzić, czy osiągnięto koniec dokumentu, i ustawić *m_bContinuePrinting* na **FAŁSZ,** gdy ma.

Domyślna implementacja zestawów `OnPrepareDC` *m_bContinuePrinting* **fałsz,** jeśli bieżąca strona jest większa niż 1. Oznacza to, że jeśli długość dokumentu nie została określona, struktura zakłada, że dokument jest o długości jednej strony. Jedną z konsekwencji jest to, że należy zachować `OnPrepareDC`ostrożność, jeśli wywołasz wersję klasy podstawowej . Nie należy zakładać, że *m_bContinuePrinting* będzie **true** po wywołaniu wersji klasy podstawowej.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Nagłówki i stopki](../mfc/headers-and-footers.md)

- [Przydzielanie zasobów GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)<br/>
[Klasa CView](../mfc/reference/cview-class.md)<br/>
[Klasa CDC](../mfc/reference/cdc-class.md)
