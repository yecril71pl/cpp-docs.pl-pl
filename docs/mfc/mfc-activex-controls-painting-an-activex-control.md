---
title: 'Kontrolki ActiveX MFC: malowanie kontrolki ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: 4a7cff57213cf9ba234ead9880207fd93592614f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549529"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Kontrolki ActiveX MFC: malowanie kontrolki ActiveX

W tym artykule opisano proces malowanie kontrolki ActiveX i jak może zmienić kod malowania, aby zoptymalizować proces. (Zobacz [Optymalizacja rysowania kontrolki](../mfc/optimizing-control-drawing.md) dla techniki dotyczące optymalizacji rysowania przez nie formantów indywidualnie Przywróć wcześniej wybrane obiekty GDI. Po zostały wystawione wszystkich formantów, kontener automatycznie przywrócić oryginalnych obiektów.)

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Przykłady w tym artykule pochodzą z kontrolki utworzone przez kreatora kontrolek ActiveX MFC przy użyciu ustawień domyślnych. Aby uzyskać więcej informacji na temat tworzenia aplikacji szkielet kontrolek przy użyciu Kreatora kontrolek ActiveX MFC, zobacz artykuł [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).

Omówiono następujące tematy:

- [Ogólny proces malowanie kontrolki i kod utworzony przez kreatora kontrolek ActiveX do obsługi rysowania](#_core_the_painting_process_of_an_activex_control)

- [Jak zoptymalizować proces rysowania](#_core_optimizing_your_paint_code)

- [Jak malować kontrolki przy użyciu metapliki](#_core_painting_your_control_using_metafiles)

##  <a name="_core_the_painting_process_of_an_activex_control"></a> Proces malowanie kontrolki ActiveX

Kontrolki ActiveX początkowo są wyświetlane lub są rysowane, należy wykonać proces rysowania, podobnie jak inne aplikacje opracowane przy użyciu biblioteki MFC, z jedną istotną różnicę: formanty ActiveX może być aktywny lub nieaktywny.

Aktywny formant jest reprezentowany w kontenerze kontrolek ActiveX, okno podrzędne. Podobnie jak inne okna jest odpowiedzialny za malowanie sam po odebraniu komunikat WM_PAINT. Klasa bazowa dla formantu, [COleControl](../mfc/reference/colecontrol-class.md), obsługuje ten komunikat jest jego `OnPaint` funkcji. Ta domyślna implementacja wywołuje `OnDraw` funkcja kontrolki.

Kontrolka w postaci nieaktywny jest malowane inaczej. Gdy kontrolka jest nieaktywny, okno jest niewidoczne lub nie istnieje, więc nie może ona odbierać komunikat malowania. Zamiast tego kontenera kontrolek bezpośrednio wywołuje `OnDraw` funkcja formantu. To różni się od procesu malowania aktywną kontrolkę w tym `OnPaint` nigdy nie jest wywoływana funkcja elementu członkowskiego.

Zgodnie z opisem w poprzednich akapitach, jak kontrolki ActiveX jest aktualizowany zależy od stanu kontrolki. Jednakże ponieważ struktura wywołuje `OnDraw` funkcja elementu członkowskiego w obu przypadkach możesz dodać większość kodu rysowania w tej funkcji elementu członkowskiego.

`OnDraw` Funkcja elementu członkowskiego obsługuje malowania kontroli. Gdy formant jest nieaktywny, kontener formantu wywołuje `OnDraw`, przekazując kontekst urządzenia kontenera kontrolki i współrzędne prostokątny obszar zajmowany przez kontrolkę.

Prostokąt przekazywane przez platformę, by `OnDraw` funkcja elementu członkowskiego zawiera obszar zajmowany przez kontrolkę. Jeśli kontrolka jest aktywny, jest lewego górnego rogu (0, 0) i kontekst urządzenia przekazany do okna podrzędnego, który zawiera formant. Jeśli kontrolka jest nieaktywny, Współrzędna lewej górnej niekoniecznie jest (0, 0) a kontekst urządzenia przekazany do kontenera kontrolki zawierająca formant.

> [!NOTE]
>  Ważne jest, że modyfikacje w `OnDraw` nie są zależne od prostokąta górnego punktu po lewej stronie jest równa (0, 0) i rysowania tylko wewnątrz prostokąta przekazane do `OnDraw`. Jeśli narysujesz poza obszar prostokąta, mogą wystąpić nieoczekiwane rezultaty.

Domyślna implementacja dostarczone przez Kreator kontrolek ActiveX MFC w pliku implementacji (. CPP), pokazano poniżej, rysują prostokąt pędzlem biały i wypełnia elipsę z bieżącym kolorem tła.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
>  Gdy malowanie kontrolki, nie powinna dokonywać założeń dotyczących stan kontekstu urządzenia, który jest przekazywany jako *kontrolera pdc* parametr `OnDraw` funkcji. Od czasu do czasu kontekstu urządzenia jest dostarczany przez aplikację kontenera i nie zostaną niekoniecznie zainicjowane do stanu domyślnego. W szczególności należy jawnie wybrać pióra, pędzle, kolory, czcionki i inne zasoby, które zależy od kodu rysowania.

##  <a name="_core_optimizing_your_paint_code"></a> Optymalizacja kodu malowania

Formant jest pomyślnie malowanie sam, następnym krokiem po zoptymalizować `OnDraw` funkcji.

Domyślna implementacja klasy kontrolki ActiveX malowanie Malowanie obszaru całego kontroli. Jest to wystarczające dla prostych kontrolek, ale w wielu przypadkach odświeżenie formant będzie szybciej, jeśli tylko część wymaganej aktualizacji była odświeżana, zamiast całego kontroli.

`OnDraw` Funkcja zapewnia prostą metodę optymalizacji, przekazując *rcInvalid*, prostokątny obszar formantu, który wymaga ponownego narysowania. Umożliwia ten obszar zwykle mniejsze niż obszar kontroli cały proces rysowania.

##  <a name="_core_painting_your_control_using_metafiles"></a> Malowanie przy użyciu metapliki kontrolki

W większości przypadków *kontrolera pdc* parametr `OnDraw` funkcji wskazuje na ekranie kontekstu urządzenia (DC). Jednak podczas drukowania obrazów formantu lub podczas sesji podglądu wydruku, kontroler domeny otrzymał renderowanie to specjalny typ o nazwie "metaplik DC". W przeciwieństwie do ekranu kontrolera domeny, która od razu obsługuje żądania wysyłane do niej, metaplik kontroler domeny przechowuje żądania do odtworzenia w późniejszym czasie. Niektóre aplikacje kontenera mają także możliwość renderowania obrazu sterowania przy użyciu metaplik kontrolera domeny w trybie projektowania.

Metaplik rysowania żądań będzie możliwe przez kontener za pośrednictwem dwóch funkcji interfejsu: `IViewObject::Draw` (tej funkcji mogą być również wywoływane dla innych metaplik rysowania) i `IDataObject::GetData`. Gdy metaplik kontroler domeny jest przekazywany jako jeden z parametrów, struktura MFC sprawia, że wywołanie [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Ponieważ jest to funkcja wirtualna elementu członkowskiego, należy zastąpić tę funkcję w klasie kontrolki, aby wykonywać żadnych specjalnych przetwarzanie. Domyślne zachowanie wywołania `COleControl::OnDraw`.

Aby upewnić się, że formant może znajdować się na środku ekranu i metaplik konteksty urządzenia, należy użyć tylko funkcji elementów członkowskich, które są obsługiwane zarówno w ekran i metaplik kontrolera domeny. Należy pamiętać, że w układzie współrzędnych nie może być (w pikselach).

Ponieważ domyślną implementację elementu `OnDrawMetafile` wywołuje formantu `OnDraw` funkcji, należy użyć tylko funkcji Członkowskich, które są odpowiednie na potrzeby metaplik i kontekstu urządzenia ekranu, chyba że przesłonisz `OnDrawMetafile`. Poniższa lista zawiera podzbiór `CDC` funkcji Członkowskich, które mogą być używane w metaplik i kontekst urządzenia ekranu. Aby uzyskać więcej informacji na temat tych funkcji, zobacz klasy [CDC](../mfc/reference/cdc-class.md) w *odwołanie MFC*.

|Łuk|BibBlt|Skrót|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Oprócz `CDC` funkcji elementów członkowskich, istnieje kilka funkcji, które są zgodne w metaplik kontrolera domeny. Obejmują one [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)i trzy funkcje elementów członkowskich `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), i [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funkcje, które nie są rejestrowane w metaplik: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)i [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Ponieważ metaplik kontrolera domeny nie jest faktycznie skojarzony z urządzeniem, nie można używać SetDIBits GetDIBits i CreateDIBitmap metaplik kontrolera domeny. SetDIBitsToDevice i StretchDIBits z metaplik kontrolera domeny można użyć jako miejsca docelowego. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), i [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nie są istotne przy użyciu metaplik kontrolera domeny.

Inny należy wziąć pod uwagę podczas korzystania z metaplik kontroler domeny jest czy współrzędnych nie może być (w pikselach). Z tego powodu przekazywane do wszystkich swój kod rysowania powinny być dostosowane do mieści się w prostokącie `OnDraw` w *rcBounds* parametru. Zapobiega to przypadkowym malowania poza kontrolą, ponieważ *rcBounds* reprezentuje rozmiar okna formantu.

Po udało Ci się wdrożyć metaplik renderowania dla formantu, należy użyć kontenera testu do testowania metaplik. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Aby przetestować metaplik formantu za pomocą kontenera testu

1. W kontenerze testów **Edytuj** menu, kliknij przycisk **Wstaw nową kontrolkę**.

1. W **Wstaw nową kontrolkę** polu, wybierz kontrolkę i kliknij przycisk **OK**.

   Kontrolka pojawi się w kontenerze testowym.

1. Na **kontroli** menu, kliknij przycisk **Rysowanie metaplik**.

   Oddzielne okno pojawia się, w którym jest wyświetlany metaplik. Można zmienić rozmiar tego okna, aby zobaczyć, jak skalowanie wpływa na metaplik formantu. Możesz zamknąć to okno, w dowolnym momencie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

