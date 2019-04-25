---
title: Architektura podglądu wydruku
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: ea80b67b3f6bb6980e4e8f7f12a967cb7bb5b6c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218732"
---
# <a name="print-preview-architecture"></a>Architektura podglądu wydruku

W tym artykule wyjaśniono, jak struktura MFC implementuje funkcje podglądu wydruku. Omawiane tematy to m.in.:

- [Proces podglądu wydruku](#_core_the_print_preview_process)

- [Modyfikowanie podglądu wydruku](#_core_modifying_print_preview)

Podgląd wydruku jest nieznacznie różnić się od wyświetlanie na ekranie i drukowania, ponieważ zamiast bezpośrednio rysowania obrazu na urządzeniu, aplikacja musi symulować drukarki na ekranie. Aby to umożliwić, bibliotekę Microsoft Foundation Class definiuje specjalny (nieudokumentowane) klasy pochodzącej od [klasa CDC](../mfc/reference/cdc-class.md), co jest nazywane `CPreviewDC`. Wszystkie `CDC` obiekty zawierają dwa konteksty urządzenia, ale zazwyczaj są identyczne. W `CPreviewDC` obiektu, są one różne: pierwszy reprezentuje drukarki jest symulowane, a druga — ekranu, na którym dane wyjściowe nie są wyświetlane.

##  <a name="_core_the_print_preview_process"></a> Proces podglądu wydruku

Gdy użytkownik wybierze polecenie Podgląd wydruku **pliku** menu, szablon tworzy `CPreviewDC` obiektu. Zawsze, gdy aplikacja wykonuje operację, która ustawia cechy kontekstu urządzenia drukarki, struktura wykonuje również podobne działania w kontekście urządzenia ekranu. Na przykład aplikacja wybiera czcionkę związane z drukowaniem, struktura wybiera czcionkę dla ekranu, która symuluje czcionka drukarki. Zawsze, gdy aplikacji będzie wysyłać dane wyjściowe do drukarki, struktura zamiast wysyła dane wyjściowe na ekranie.

Podgląd wydruku różni się również drukowanie w kolejności, że każdy rysuje stron dokumentu. Podczas drukowania, struktura nadal drukowania pętli do momentu zostało wyrenderowane zakres stron. Podczas podglądu wydruku jednej lub dwóch stronach są wyświetlane w dowolnym momencie, a następnie aplikacja oczekuje; nie dalszych strony są wyświetlane, dopóki użytkownik nie wykona. W podglądu wydruku aplikacji musi również odpowiadać na komunikaty WM_PAINT, tak jak podczas zwykłej ekranu.

[CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) funkcja jest wywoływana, gdy zostanie wywołana tryb podglądu, dokładnie tak jak na początku zadania drukowania. [Klasa Cprintinfo](../mfc/reference/cprintinfo-structure.md) struktury przekazany do funkcji zawiera kilka składowych, których wartości można ustawić na dostosowanie niektórych parametrów operacji podglądu wydruku. Na przykład można ustawić *m_nNumPreviewPages* członka, aby określić, czy dokument w trybie strony jednego lub dwóch stron w wersji zapoznawczej.

##  <a name="_core_modifying_print_preview"></a> Modyfikowanie podglądu wydruku

Zamiast łatwo można zmodyfikować zachowania i wyglądu podglądu wydruku w na wiele sposobów. Na przykład można, między innymi:

- Spowodować okna podglądu wydruku, aby wyświetlić pasek przewijania, aby mieć łatwy dostęp do dowolnej strony dokumentu.

- Przyczyna podglądu wydruku do zachowania użytkownika pozycji w dokumencie, począwszy od jego wyświetlaną u bieżącej strony.

- Spowodować, że inicjowanie różne do wykonania dla podglądu wydruku i drukowania.

- Przyczyna Podgląd wydruku, aby wyświetlić numery stron w własnych formatów.

Jeśli wiadomo, jak długo trwa dokumentu i wywołania `SetMaxPage` z odpowiednią wartością ramach te informacje mogą posłużyć w wersji zapoznawczej, a także podczas drukowania. Gdy w ramach zna długość dokumentu, zapewniają okno podglądu przy użyciu paska, co pozwala na stronie i z powrotem do dokumentu w trybie podglądu przewijania. Jeśli nie został ustawiony długość dokumentu, struktura nie może się znajdować pole przewijania, aby wskazać bieżące położenie, dzięki czemu w ramach nie dodaje pasek przewijania. W takim przypadku użytkownik musi użyć przycisków poprzedniej strony i następnej strony na pasku sterowania okno podglądu do strony w dokumencie.

Podgląd wydruku, może okazać się przydatne do przypisania wartości do *m_nCurPage* członkiem `CPrintInfo`, nawet jeśli nigdy nie należy czynności związane z drukowaniem zwykłej. Podczas drukowania zwykłych tego elementu członkowskiego niesie ze sobą informacje w ramach klasy widoku. Jest to, jak struktura informuje o widoku strony, na które mają być drukowane.

Z drugiej strony, po uruchomieniu trybu podglądu wydruku, *m_nCurPage* elementu członkowskiego niesie ze sobą informacji w odwrotnym kierunku: z widoku platformy Framework. Środowisko wykorzystuje wartość tego elementu członkowskiego, aby określić strony, na które należy wyświetlić podglądu najpierw. Wartość domyślna tego elementu członkowskiego jest 1, co pierwszej strony dokumentu jest początkowo wyświetlane. Można zastąpić `OnPreparePrinting` ustawić tego elementu członkowskiego na numer strony, można wyświetlać w czasie, o której wywołano polecenie Podgląd wydruku. W ten sposób aplikacja przechowuje pozycji bieżącego użytkownika, podczas przenoszenia z trybu wyświetlania normalne tryb podglądu wydruku.

Czasami możesz chcieć `OnPreparePrinting` przeprowadzić inicjowanie różne w zależności od tego, czy jest to dla zadania drukowania i podglądu wydruku. Można to ustalić, sprawdzając *m_bPreview* zmiennej składowej w `CPrintInfo` struktury. Ten element członkowski jest ustawiona na **TRUE** po wywołaniu podglądu wydruku.

`CPrintInfo` Struktura zawiera także składową o nazwie *m_strPageDesc*, który jest używany do formatowania ciągów wyświetlane u dołu ekranu w trybie jednej strony i wielu stron. Domyślnie te ciągi mają postać "strony *n*" i "stron *n* - *m*,", ale możesz modyfikować *m_strPageDesc* z w ramach `OnPreparePrinting` i ustaw ciągi na coś bardziej rozbudowany. Zobacz [klasa Cprintinfo](../mfc/reference/cprintinfo-structure.md) w *odwołanie MFC* Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Drukowanie i podgląd wydruku](../mfc/printing-and-print-preview.md)<br/>
[Drukowanie](../mfc/printing.md)<br/>
[Klasa CView](../mfc/reference/cview-class.md)<br/>
[Klasa CDC](../mfc/reference/cdc-class.md)
