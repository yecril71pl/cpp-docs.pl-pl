---
title: 'Jak: Korzystanie z narzędzia do rysowania'
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
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359851"
---
# <a name="how-to-use-a-drawing-tool"></a>Jak: Korzystanie z narzędzia do rysowania

**Edytor obrazów** ma narzędzia do rysowania odręcznego i wymazywania, które działają w ten sam sposób. Wybierz narzędzie i, jeśli to konieczne, [wybierz kolory pierwszego planu i tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) oraz opcje rozmiaru i kształtu. Następnie przenieś wskaźnik do obrazu i kliknij lub przeciągnij, aby rysować i wymazywać.

## <a name="drawing-tools"></a>Narzędzia do rysowania

Narzędzia do rysowania można wybrać z paska narzędzi **Edytora obrazów** lub z menu **Obraz.** Po wybraniu narzędzia **Gumka,** **Narzędzia Pędzel** lub **Aerografu** selektor opcji wyświetla opcje tego narzędzia.

> [!TIP]
> Porady dotyczące narzędzi pojawiają się po najechaniu kursorem na przyciski na [pasku narzędzi Edytor obrazów](../windows/toolbar-image-editor-for-icons.md). Te wskazówki pomogą Ci zidentyfikować konkretne przyciski wymienione tutaj.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>Aby zaznaczyć i użyć narzędzia do rysowania z paska narzędzi Edytora obrazów

1. Wybierz przycisk na pasku narzędzi **Edytor obrazów.**

   - Narzędzie **Gumka** maluje obraz bieżącym kolorem tła po naciśnięciu lewego przycisku myszy.

      > [!TIP]
      > Zamiast używać narzędzia **Gumka,** wygodniej jest rysować kolor tła za pomocą jednego z narzędzi do rysowania.

   - Narzędzie **Ołówek** rysuje odręcznie o stałej szerokości jednego piksela.

   - **Narzędzie Pędzel** ma różne kształty i rozmiary.

   - Narzędzie **Airbrush** losowo rozmieszcza kolorowe piksele wokół środka pędzla.

1. W razie potrzeby wybierz kolory i pędzel:

   - W [palecie Kolory](../windows/colors-window-image-editor-for-icons.md)wybierz lewy przycisk myszy, aby wybrać kolor pierwszego planu lub prawy przycisk myszy, aby wybrać kolor tła.

   - W [selektorze Opcje](../windows/toolbar-image-editor-for-icons.md)zaznacz kształt reprezentujący pędzel, którego chcesz użyć.

1. Wskaż miejsce na obrazie, w którym chcesz rozpocząć rysowanie lub malowanie. Wskaźnik zmieni kształt zgodnie z wybranym narzędziem.

1. Naciśnij lewy przycisk myszy (dla koloru pierwszego planu) lub prawy przycisk myszy (dla koloru tła) i przytrzymaj go podczas rysowania.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>Aby zaznaczyć i użyć narzędzia do rysowania z menu Obraz

1. Przejdź do menu **Narzędzia** > **obrazów**.

1. W podmenu kaskadowych wybierz narzędzie, którego chcesz użyć.

## <a name="lines-or-closed-figures"></a>Linie lub liczby zamknięte

Narzędzia **Edytor obrazów** do rysowania linii i zamkniętych figurek działają w ten sam sposób: punkt wstawiania umieszcza się w jednym punkcie i przeciąga się do drugiego. W przypadku wierszy te punkty są punktami końcowymi. W przypadku liczb zamkniętych punkty te są przeciwległymi narożnikami prostokąta ograniczającego rysunek.

Linie są rysowane w szerokości określonej przez bieżące zaznaczenie pędzla, a rysunki w ramkach są rysowane w szerokości określonej przez bieżący wybór szerokości. Linie i wszystkie figury, zarówno w ramkach, jak i napełnionych, są rysowane w bieżącym kolorze pierwszego planu po naciśnięciu lewego przycisku myszy lub w bieżącym kolorze tła po naciśnięciu prawego przycisku myszy.

### <a name="to-draw-a-line"></a>Aby narysować linię

1. Użyj [paska narzędzi Edytor obrazów](../windows/toolbar-image-editor-for-icons.md) lub przejdź do menu **Narzędzia**> **obrazów** i wybierz narzędzie **Linia.**

1. W razie potrzeby wybierz kolory i pędzel:

   - W [palecie Kolory](../windows/colors-window-image-editor-for-icons.md)wybierz lewy przycisk myszy, aby wybrać kolor pierwszego planu lub prawy przycisk myszy, aby wybrać kolor tła.

   - W [selektorze Opcje](../windows/toolbar-image-editor-for-icons.md)zaznacz kształt reprezentujący pędzel, którego chcesz użyć.

1. Umieść wskaźnik w punkcie początkowym linii.

1. Przeciągnij do punktu końcowego linii.

### <a name="to-draw-a-closed-figure"></a>Aby narysować zamkniętą figurę

1. Użyj **paska** narzędzi Edytor obrazów lub przejdź do menu **Narzędzia** > **obrazów** i wybierz narzędzie **Rysunek zamknięty.**

   Narzędzia **do rysowania z postaciami zamkniętymi** tworzą figury wskazane na odpowiednich przyciskach.

1. W razie potrzeby wybierz kolory i szerokość linii.

1. Przesuń wskaźnik do jednego rogu prostokątnego obszaru, w którym chcesz narysować rysunek.

1. Przeciągnij wskaźnik do przeciwległego narożnika po przekątnej.

## <a name="custom-brushes"></a>Pędzle niestandardowe

Niestandardowy pędzel to prostokątna część obrazu, którą można podnieść i używać, podobnie jak jedna z gotowych pędzli **edytora obrazów.** Wszystkie operacje, które można wykonać na zaznaczeniu, można wykonać na niestandardowym pędzlu, jak również.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Aby utworzyć niestandardowy pędzel z części obrazu

1. Zaznacz część obrazu, której chcesz użyć dla pędzla.

1. Przytrzymaj klawisz **Shift** w dół, wybierz zaznaczenie i przeciągnij go po obrazie lub przejdź do menu **Obraz** > **Użyj zaznaczenia jako pędzel**.

   Zaznaczenie staje się pędzlem niestandardowym, który rozmieszcza kolory zaznaczenia na obrazie. Kopie zaznaczenia pozostają wzdłuż ścieżki przeciągania. Im wolniej przeciągasz, tym więcej kopii.

   > [!NOTE]
   > Wybranie **opcji Użyj zaznaczenia jako pędzla** bez uprzedniego zaznaczenia części obrazu spowoduje użycie całego obrazu jako pędzla. Wynik użycia pędzla niestandardowego będzie również zależeć od tego, czy wybrano [tło nieprzezroczyste czy przezroczyste.](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)

Piksele w pędzlu niestandardowym, które pasują do bieżącego koloru tła, są zwykle przezroczyste: nie malują istniejącego obrazu. Można zmienić to zachowanie, tak aby piksele koloru tła malować na istniejącym obrazie.

Można użyć pędzla niestandardowego, takiego jak stempel lub wzornik, aby utworzyć różne efekty specjalne.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Aby narysować niestandardowe kształty pędzli w kolorze tła

1. Wybierz nieprzezroczyste lub przezroczyste tło.

1. Ustaw kolor tła na kolor, w którym chcesz rysować.

1. Umieść pędzel niestandardowy w miejscu, w którym chcesz narysować.

1. Wybierz prawy przycisk myszy. Wszystkie nieprzezroczyste obszary pędzla niestandardowego są rysowane w kolorze tła.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Aby podwoić lub zmniejszyć rozmiar pędzla niestandardowego lub o połowę

Naciśnij klawisz Plus**+** **Sign** ( ), aby podwoić rozmiar**-** pędzla, lub klawisz **Minus Sign** ( ), aby zmniejszyć go o połowę.

### <a name="to-cancel-the-custom-brush"></a>Aby anulować niestandardowy pędzel

Naciśnij **klawisz Esc** lub wybierz inne narzędzie do rysowania.

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)<br/>
[Jak: Tworzenie ikony lub innego obrazu](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Jak: Edytowanie obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Jak: Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
