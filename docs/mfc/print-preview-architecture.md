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
ms.openlocfilehash: 1956313d4e904255ba59e79690fe3d7144669a29
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623937"
---
# <a name="print-preview-architecture"></a>Architektura podglądu wydruku

W tym artykule wyjaśniono, jak platforma MFC implementuje funkcję podglądu wydruku. Omawiane tematy to m.in.:

- [Proces podglądu wydruku](#_core_the_print_preview_process)

- [Modyfikowanie podglądu wydruku](#_core_modifying_print_preview)

Podgląd wydruku jest nieco różny od wyświetlania ekranu i drukowania, ponieważ zamiast bezpośredniego rysowania obrazu na urządzeniu aplikacja musi symulować drukarkę przy użyciu ekranu. Aby to umożliwić, biblioteka MFC definiuje specjalną (nieudokumentowaną) klasę pochodną [klasy przechwytywania](reference/cdc-class.md)o nazwie `CPreviewDC` . Wszystkie `CDC` obiekty zawierają dwa konteksty urządzenia, ale zazwyczaj są identyczne. W `CPreviewDC` obiekcie są różne: pierwszy reprezentuje symulowaną drukarkę, a drugi reprezentuje ekran, na którym są wyświetlane dane wyjściowe.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Proces podglądu wydruku

Gdy użytkownik wybierze polecenie Drukuj podgląd z menu **plik** , struktura utworzy `CPreviewDC` obiekt. Za każdym razem, gdy aplikacja wykonuje operację, która ustawia charakterystykę kontekstu urządzenia drukarki, struktura wykonuje także podobną operację w kontekście urządzenia ekranu. Na przykład jeśli aplikacja wybierze czcionkę do drukowania, struktura wybiera czcionkę na potrzeby wyświetlania ekranu, która symuluje czcionkę drukarki. Za każdym razem, gdy aplikacja wyśle dane wyjściowe do drukarki, struktura wysyła dane wyjściowe do ekranu.

Podgląd wydruku różni się także od drukowania w kolejności, w której każda rysuje strony dokumentu. Podczas drukowania środowisko kontynuuje pętlę drukowania do momentu renderowania określonego zakresu stron. W podglądzie wydruku w dowolnym momencie jest wyświetlana jedna lub dwie strony, a następnie aplikacja czeka; żadne dalsze strony nie są wyświetlane, dopóki użytkownik nie odpowie. W podglądzie wydruku aplikacja musi również odpowiadać na WM_PAINT komunikatów, tak jak podczas normalnego wyświetlania ekranu.

Funkcja [CView:: OnPreparePrinting](reference/cview-class.md#onprepareprinting) jest wywoływana w przypadku wywołania trybu podglądu, podobnie jak na początku zadania drukowania. Struktura [struktury CPrintInfo](reference/cprintinfo-structure.md) przeniesiona do funkcji zawiera kilka elementów członkowskich, których wartości można ustawić w celu dostosowania określonych cech operacji podglądu wydruku. Na przykład można ustawić składową *m_nNumPreviewPages* , aby określić, czy dokument ma być wyświetlany w trybie jednej strony, czy na dwie strony.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Modyfikowanie podglądu wydruku

Możesz łatwo modyfikować zachowanie i wygląd podglądu wydruku na wiele sposobów. Można na przykład, między innymi:

- Wyświetlenie okna podglądu wydruku w celu uzyskania łatwego dostępu do dowolnej strony dokumentu.

- Powoduje, że Podgląd wydruku zachowuje położenie użytkownika w dokumencie, rozpoczynając jego wyświetlanie na bieżącej stronie.

- Należy wykonać inne inicjalizacje dla podglądu wydruku i drukowania.

- Wyświetl podgląd wydruku, aby wyświetlić numery stron we własnych formatach.

Jeśli wiesz, jak długo dokument jest i wywołuje `SetMaxPage` odpowiednią wartość, struktura może używać tych informacji w trybie podglądu oraz podczas drukowania. Gdy struktura zna długość dokumentu, może udostępnić okno podglądu z paskiem przewijania, umożliwiając użytkownikowi przechodzenie do tyłu i do przodu dokumentu w trybie podglądu. Jeśli nie ustawiono długości dokumentu, struktura nie może umieścić pola przewijania, aby wskazać bieżącą pozycję, więc struktura nie dodaje paska przewijania. W takim przypadku użytkownik musi użyć przycisków Następna strona i Poprzednia strona na pasku sterowania okna podglądu, aby wyświetlić stronę w dokumencie.

W przypadku wersji zapoznawczej drukowania przydatne może być przypisanie wartości do *m_nCurPage* elementu członkowskiego `CPrintInfo` , nawet mimo tego, że w przypadku zwykłego drukowania nie trzeba tego robić. Podczas zwykłego drukowania ten element członkowski przenosi informacje z struktury do klasy widoku. Jest to sposób, w jaki struktura informuje widok, która strona powinna zostać wydrukowana.

Z drugiej strony, gdy zostanie uruchomiony tryb Podgląd wydruku, element członkowski *m_nCurPage* przenosi informacje w odwrotnym kierunku: od widoku do struktury. Struktura używa wartości tego elementu członkowskiego, aby określić, która strona powinna być wyświetlana w pierwszej kolejności. Wartość domyślna tego elementu członkowskiego to 1, więc pierwsza strona dokumentu jest wyświetlana na początku. Można przesłonić, `OnPreparePrinting` Aby ustawić dla tego elementu członkowskiego liczbę wyświetlanej strony w momencie wywołania polecenia Podgląd wydruku. W ten sposób aplikacja zachowuje bieżącą pozycję użytkownika podczas przechodzenia z trybu wyświetlania normalnego do trybu podglądu wydruku.

Czasami możesz chcieć `OnPreparePrinting` wykonać inne inicjalizacje w zależności od tego, czy jest wywoływana dla zadania drukowania czy w podglądzie wydruku. Można to ustalić, sprawdzając zmienną elementu członkowskiego *m_bPreview* w `CPrintInfo` strukturze. Ten element członkowski ma **wartość true** , gdy zostanie wywołana wersja zapoznawcza wydruku.

`CPrintInfo`Struktura zawiera również element członkowski o nazwie *m_strPageDesc*, który służy do formatowania ciągów wyświetlanych w dolnej części ekranu w trybach jednostronicowych i wielostronicowych. Domyślnie te ciągi mają postać "Strona *n*" i "strony *n*  -  *m*", ale można modyfikować *m_strPageDesc* z poziomu `OnPreparePrinting` i ustawiać ciągi na bardziej rozbudowane. Aby uzyskać więcej informacji, zobacz [CPrintInfo Structure](reference/cprintinfo-structure.md) w *dokumentacji MFC* .

## <a name="see-also"></a>Zobacz też

[Drukowanie i podgląd wydruku](printing-and-print-preview.md)<br/>
[Drukowanie](printing.md)<br/>
[Klasa CView](reference/cview-class.md)<br/>
[Klasa CDC](reference/cdc-class.md)
