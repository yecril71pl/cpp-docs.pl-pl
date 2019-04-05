---
title: 'Instrukcje: Użyj narzędzia do rysowania'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: 7b362749c9a5cb1c7ec77e5cac8625aa7eb260f0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037792"
---
# <a name="how-to-use-a-drawing-tool"></a>Instrukcje: Użyj narzędzia do rysowania

**Edytora obrazów** Rysowanie odręczne i wymazywanie narzędzia, które współpracują w taki sam sposób. Wybierz narzędzie i, jeśli to konieczne, [wybierz kolory pierwszego planu i tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) i opcje rozmiaru i kształtu. Następnie przesuń wskaźnik do obrazu i kliknięciu lub przeciągnij, aby narysować i wymazać.

## <a name="drawing-tools"></a>Narzędzia do rysowania

Możesz wybrać narzędzi do rysowania za pomocą albo **edytora obrazów** paska narzędzi lub **obraz** menu. Po wybraniu **Gumka** narzędzia **pędzla** narzędzia lub **Aerograf** narzędzia Selektor opcji Wyświetla opcje tego narzędzia.

> [!TIP]
>  Etykietki narzędzi są wyświetlane po umieszczeniu kursora przyciski na [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md). Te wskazówki pomoże zidentyfikować określone przyciski zostały tu wymienione.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Aby wybrać i użyj narzędzia do rysowania na pasku narzędzi edytora obrazów

1. Wybierz przycisk na **edytora obrazów** paska narzędzi.

   - **Gumka** narzędzie farby obraz z bieżącym kolorem tła po naciśnięciu lewego przycisku myszy.

      > [!TIP]
      > Zamiast używania **Gumka** narzędzia, może okazać się bardziej wygodne do rysowania w kolor tła z jednym z narzędzi do rysowania.

   - **Ołówka** narzędzie freehand rysuje stałej szerokości jednego piksela.

   - **Pędzla** narzędzie ma różnych typów i rozmiarów.

   - **Aerograf** narzędzie losowo dystrybuuje kolorów pikseli wokół środka pędzla.

1. Jeśli to konieczne, wybierz kolory i pędzla:

   - W [paleta kolorów](../windows/colors-window-image-editor-for-icons.md), wybierz przycisk myszy po lewej stronie, aby wybrać kolor pierwszego planu lub prawego przycisku myszy, aby zmienić kolor tła.

   - W [Selektor opcji](../windows/toolbar-image-editor-for-icons.md), wybierz kształt reprezentujący pędzla, którego chcesz użyć.

1. Wskaż miejsce na obrazu, w którym chcesz uruchomić, rysowania lub malowania. Kursor zmienia kształt zgodnie z wybranego narzędzia.

1. Naciśnij klawisze lewy przycisk myszy (kolor pierwszego planu) lub prawym przyciskiem myszy (na kolor tła) i przytrzymaj go podczas rysowania.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Aby wybrać i użyj narzędzia do rysowania menu obrazu

1. Przejdź do menu **obraz** > **narzędzia**.

1. Kaskadowe podmenu wybierz narzędzie którego chcesz użyć.

## <a name="lines-or-closed-figures"></a>Linie lub zamkniętych figur

**Edytora obrazów** narzędzia do rysowania linii i zamkniętych figur wszystkie działają tak samo jak: Umieść punkt wstawiania w jednym punkcie i przeciągnij pola do innego. W przypadku wierszy te punkty są punkty końcowe. W przypadku zamkniętych figur te punkty są przeciwny narożników prostokąta blokujących na rysunku.

Wiersze są rysowane w szerokości ustalany na podstawie bieżącego zaznaczenia pędzla, a ramce rysunki są rysowane w szerokości ustalany na podstawie bieżącego zaznaczenia szerokość. Linie i wszystkie dane, zarówno w ramce, jak i wypełnione, są rysowane w bieżącym kolorem po naciśnięciu lewego przycisku myszy, lub w bieżącym kolorem tła po naciśnięciu prawego przycisku myszy.

### <a name="to-draw-a-line"></a>Aby narysować linię

1. Użyj [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub przejdź do menu **obraz**> **narzędzia** i wybierz polecenie **wiersza** narzędzia.

1. Jeśli to konieczne, wybierz kolory i pędzla:

   - W [paleta kolorów](../windows/colors-window-image-editor-for-icons.md), wybierz przycisk myszy po lewej stronie, aby wybrać kolor pierwszego planu lub prawego przycisku myszy, aby zmienić kolor tła.

   - W [Selektor opcji](../windows/toolbar-image-editor-for-icons.md), wybierz kształt reprezentujący pędzla, którego chcesz użyć.

1. Umieść wskaźnik myszy na punkt początkowy dla wiersza.

1. Przeciągnij do endpoint dla wiersza.

### <a name="to-draw-a-closed-figure"></a>Aby narysować figurę zamkniętą

1. Użyj **edytora obrazów** paska narzędzi lub przejdź do menu **obraz** > **narzędzia** i wybierz **rysunek rysunek zamknięte** narzędzia.

   **Rysunek rysunek zamknięte** narzędzia Tworzenie figur zgodnie z informacjami zawartymi w ich odpowiednich przycisków.

1. Jeśli to konieczne, zaznacz kolorów i szerokości linii.

1. Przesuń wskaźnik do jednego rogu prostokątny obszar, w którym chcesz rysować na rysunku.

1. Przeciągnij kursor po przekątnej przeciwległego rogu.

## <a name="custom-brushes"></a>Pędzle niestandardowe

Niestandardowy obiekt brush jest prostokątny fragment obrazu, które przejmą i używać jak jeden z **edytora obrazów**firmy pędzle gotowych do użycia. Wszystkie operacje, które można wykonywać na wybranych, można wykonywać na niestandardowy obiekt brush także.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Aby utworzyć niestandardowy obiekt brush z części obrazu

1. Wybierz część obrazu, który chcesz używać dla pędzla.

1. Przytrzymaj **Shift** klucza w dół, wybierz w zaznaczeniu i przeciągnij go na obrazie lub przejdź do menu **obraz** > **Użyj zaznaczenia jako pędzla**.

   Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone.

   > [!NOTE]
   > Wybieranie **Użyj zaznaczenia jako pędzla** bez polega na wybraniu część obrazu użyje całego obrazu jako pędzla. Wynik za pomocą niestandardowy obiekt brush również będzie zależeć od tego, czy wybrano [tła nieprzezroczyste lub przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Niestandardowy obiekt brush pikseli, które odpowiadają bieżącym kolorem tła są zwykle przezroczyste: nie malowanie istniejącego obrazu. Można zmienić to zachowanie, tak aby pikseli kolor tła malować przez istniejący obraz.

Niestandardowy obiekt brush sygnaturę lub wzornika umożliwia tworzenie różnych efekty specjalne.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Do rysowania kształtów niestandardowy obiekt brush kolor tła

1. Wybierz tło nieprzezroczyste lub przezroczyste.

1. Ustaw kolor tła na kolor, w której chcemy narysować.

1. Ustaw niestandardowy obiekt brush, w której chcemy narysować.

1. Wybierz prawego przycisku myszy. Wszelkie nieprzezroczyste regionów niestandardowy obiekt brush są rysowane w kolor tła.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Dwukrotnie lub połowę rozmiar niestandardowy obiekt brush

Naciśnij klawisz **znak Plus** (**+**) klucz dwukrotnie rozmiar pędzla lub **znak Minus** (**-**) kluczem o połowę go .

### <a name="to-cancel-the-custom-brush"></a>Aby anulować niestandardowy obiekt brush

Naciśnij klawisz **Esc** lub innego narzędzia do rysowania.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz także

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Instrukcje: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Instrukcje: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Instrukcje: Praca z kolorami](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>