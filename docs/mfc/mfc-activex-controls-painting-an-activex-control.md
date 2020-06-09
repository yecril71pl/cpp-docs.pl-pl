---
title: 'Kontrolki ActiveX MFC: malowanie kontrolki ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: a01a66402471b295a6e57af8af265c50685b4a1f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618223"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Kontrolki ActiveX MFC: malowanie kontrolki ActiveX

W tym artykule opisano proces malowania kontrolek ActiveX oraz sposób zmiany kodu programu Paint w celu optymalizacji procesu. (Zobacz [Optymalizacja rysowania formantów](optimizing-control-drawing.md) pod kątem technik optymalizacji rysowania przez nieposiadanie formantów indywidualnie przywraca poprzednio wybrane obiekty GDI. Po narysowaniu wszystkich kontrolek kontener może automatycznie przywrócić oryginalne obiekty.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Przykłady w tym artykule pochodzą z formantu utworzonego przez kreatora kontrolek ActiveX MFC z ustawieniami domyślnymi. Aby uzyskać więcej informacji na temat tworzenia aplikacji do sterowania szkieletem za pomocą Kreatora kontrolek ActiveX MFC, zobacz artykuł [Kreator formantów ActiveX MFC](reference/mfc-activex-control-wizard.md).

Omówiono następujące tematy:

- [Ogólny proces malowania kontrolki i kodu utworzonego przez kreatora kontrolek ActiveX do obsługi rysowania](#_core_the_painting_process_of_an_activex_control)

- [Jak zoptymalizować proces malowania](#_core_optimizing_your_paint_code)

- [Jak malować swój formant przy użyciu plików.](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Proces rysowania kontrolki ActiveX

Gdy kontrolki ActiveX są początkowo wyświetlane lub odświeżane, postępują zgodnie z procesem malowania podobnym do innych aplikacji opracowanych przy użyciu MFC, z jedną ważną różnicą: formanty ActiveX mogą znajdować się w stanie aktywnym lub nieaktywnym.

Aktywna kontrolka jest reprezentowana w kontenerze kontrolki ActiveX przez okno podrzędne. Podobnie jak w przypadku innych okien, jest on odpowiedzialny za malowanie po odebraniu komunikatu WM_PAINT. Klasa bazowa formantu, [COleControl](reference/colecontrol-class.md), obsługuje ten komunikat w `OnPaint` funkcji. Ta domyślna implementacja wywołuje `OnDraw` funkcję kontrolki.

Nieaktywny formant jest malowany inaczej. Gdy kontrolka jest nieaktywna, jej okno jest niewidoczne lub nieistniejące, dlatego nie może odebrać komunikatu z programu Paint. Zamiast tego kontener sterowania bezpośrednio wywołuje `OnDraw` funkcję formantu. Różni się to od procesu malowania aktywnej kontrolki, w którym `OnPaint` funkcja członkowska nie jest nigdy wywoływana.

Jak opisano w poprzednich akapitach, w jaki sposób formant ActiveX jest aktualizowany, zależy od stanu formantu. Jednak ponieważ struktura wywołuje `OnDraw` funkcję składową w obu przypadkach, należy dodać większość kodu malarskiego w tej funkcji składowej.

`OnDraw`Funkcja członkowska obsługuje malowanie kontrolek. Gdy kontrolka jest nieaktywna, kontener kontrolny jest wywoływany `OnDraw` przez przekazanie kontekstu urządzenia kontenera kontroli i współrzędnych prostokątnego obszaru, który jest zajęty przez formant.

Prostokąt przesłany przez platformę do `OnDraw` funkcji członkowskiej zawiera obszar zajmowany przez formant. Jeśli kontrolka jest aktywna, lewy górny róg to (0, 0), a kontekst urządzenia przeszedł do okna podrzędnego zawierającego kontrolkę. Jeśli formant jest nieaktywny, Współrzędna najwyższego poziomu nie jest konieczna (0, 0), a kontekst urządzenia przeszedł dla kontenera sterowania zawierającego kontrolkę.

> [!NOTE]
> Należy pamiętać, że modyfikacje `OnDraw` nie zależą od lewego górnego punktu prostokąta równego (0, 0) i rysowany tylko wewnątrz prostokąta przenoszonego do `OnDraw` . Nieoczekiwane wyniki mogą wystąpić, jeśli nastąpi przeciągnięcie poza obszar prostokąta.

Domyślna implementacja udostępniona przez kreatora kontrolek ActiveX MFC w pliku implementacji kontroli (. CPP), pokazany poniżej, maluje prostokąt z białym pędzlem i wypełnia elipsę bieżącym kolorem tła.

[!code-cpp[NVC_MFC_AxUI#1](codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Podczas malowania kontrolki nie należy tworzyć założeń dotyczących stanu kontekstu urządzenia, który jest przesyłany jako parametr *podstawowego kontrolera domeny* do `OnDraw` funkcji. Czasami kontekst urządzenia jest dostarczany przez aplikację kontenera i niekoniecznie zostanie zainicjowany do stanu domyślnego. W szczególności, jawnie wybierz pióra, pędzle, kolory, czcionki i inne zasoby, od których zależy kod rysowania.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optymalizowanie kodu programu Paint

Po pomyślnym narysowaniu kontrolki, następnym krokiem jest zoptymalizowanie `OnDraw` funkcji.

Domyślna implementacja kontrolki ActiveX maluje cały obszar kontroli. Jest to wystarczające dla prostych kontrolek, ale w wielu przypadkach odmalowanie kontrolki będzie szybsze, jeśli tylko część, którą wymagała aktualizacji, została odgotowana, a nie w całej kontrolce.

`OnDraw`Funkcja zapewnia łatwą metodę optymalizacji poprzez przekazanie *rcInvalid*, prostokątnego obszaru kontrolki, która wymaga rerysowania. Użyj tego obszaru, zazwyczaj mniejszego niż cały obszar kontroli, aby przyspieszyć proces malowania.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Malowanie kontrolki przy użyciu plików.

W większości przypadków parametr *PDC* do `OnDraw` funkcji wskazuje kontekst urządzenia ekranu. Jednak podczas drukowania obrazów kontrolki lub podczas sesji podglądu wydruku kontroler domeny otrzymany do renderowania jest specjalnym typem o nazwie "metaplik DC". W przeciwieństwie do kontrolera domeny ekranu, który natychmiast obsługuje wysłane do niego żądania, kontroler domeny metaplik zapisuje żądania w późniejszym czasie. Niektóre aplikacje kontenera mogą również wybrać renderowanie obrazu kontrolki przy użyciu metapliku DC w trybie projektowania.

Żądania rysowania metaplików mogą być tworzone przez kontener za pomocą dwóch funkcji interfejsu: `IViewObject::Draw` (Ta funkcja może być również wywoływana dla rysowania bez metaplików) i `IDataObject::GetData` . Gdy kontroler domeny metaplik jest przenoszona jako jeden z parametrów, struktura MFC wykonuje wywołanie [COleControl:: OnDrawMetafile](reference/colecontrol-class.md#ondrawmetafile). Ponieważ jest to wirtualna funkcja członkowska, Przesłoń tę funkcję w klasie kontrolki, aby wykonać dowolne specjalne przetwarzanie. Domyślne wywołania zachowań `COleControl::OnDraw` .

Aby upewnić się, że formant może być rysowany zarówno w kontekście ekranu, jak i metapliku, należy używać tylko funkcji Członkowskich, które są obsługiwane zarówno na ekranie, jak i metapliku domeny. Należy pamiętać, że układ współrzędnych może nie być mierzony w pikselach.

Ponieważ domyślna implementacja `OnDrawMetafile` wywołania funkcji kontrolki, należy `OnDraw` używać tylko funkcji Członkowskich, które są odpowiednie dla metapliku i dla kontekstu urządzenia ekranu, chyba że zostanie przesłonięte `OnDrawMetafile` . Poniżej wymieniono podzestaw `CDC` funkcji Członkowskich, które mogą być używane zarówno w kontekście metaplików, jak i na ekranie. Aby uzyskać więcej informacji na temat tych funkcji, zobacz Klasa [przechwytywania](reference/cdc-class.md) danych w *dokumentacji MFC*.

|Arc|BibBlt|Chord|
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

Oprócz `CDC` funkcji Członkowskich istnieje kilka innych funkcji, które są zgodne z kontrolerem domeny typu metaplik. Obejmują one [CPalette:: AnimatePalette](reference/cpalette-class.md#animatepalette), [CFont:: CreateFontIndirect](reference/cfont-class.md#createfontindirect)oraz trzy funkcje składowe `CBrush` : [CreateBrushIndirect](reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](reference/cbrush-class.md#createdibpatternbrush)i [CreatePatternBrush](reference/cbrush-class.md#createpatternbrush).

Funkcje, które nie są rejestrowane w metapliku, to: [DrawFocusRect](reference/cdc-class.md#drawfocusrect), [DrawIcon](reference/cdc-class.md#drawicon), [DrawText](reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](reference/cdc-class.md#excludeupdatergn), [FillRect](reference/cdc-class.md#fillrect), [FrameRect](reference/cdc-class.md#framerect), [GrayString](reference/cdc-class.md#graystring), [InvertRect](reference/cdc-class.md#invertrect), [ScrollDC](reference/cdc-class.md#scrolldc)i [TabbedTextOut](reference/cdc-class.md#tabbedtextout). Ponieważ kontroler domeny metaplik nie jest faktycznie skojarzony z urządzeniem, nie można używać SetDIBits, GetDIBits i CreateDIBitmap z kontrolerem domeny metapliku. Jako miejsca docelowego można użyć SetDIBitsToDevice i StretchDIBits z graficznym kontrolerem domeny. [CreateCompatibleDC](reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](reference/cbitmap-class.md#createcompatiblebitmap)i [CreateDiscardableBitmap](reference/cbitmap-class.md#creatediscardablebitmap) nie mają znaczenia w przypadku metapliku DC.

Innym punktem, który należy wziąć pod uwagę podczas korzystania z metapliku DC, jest to, że układ współrzędnych nie jest mierzony w pikselach. Z tego powodu cały kod rysowania powinien zostać dostosowany do rozmiaru w prostokącie przekazaną do `OnDraw` w parametrze *rcBounds* . Zapobiega to przypadkowemu malowaniu poza formantem, ponieważ *rcBounds* reprezentuje rozmiar okna kontrolki.

Po zaimplementowaniu renderowania metaplików dla kontrolki Użyj kontenera testów do przetestowania metapliku. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów,](testing-properties-and-events-with-test-container.md) Aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Aby przetestować metaplik kontrolki za pomocą kontenera testów

1. W menu **Edycja** kontenera testowego kliknij polecenie **Wstaw nową kontrolkę**.

1. W polu **Wstaw nowy formant** zaznacz kontrolkę i kliknij przycisk **OK**.

   Kontrolka zostanie wyświetlona w kontenerze testów.

1. W menu **sterowania** kliknij polecenie **Rysuj metaplik**.

   Zostanie wyświetlone oddzielne okno, w którym jest wyświetlany metaplik. Można zmienić rozmiar tego okna, aby zobaczyć, jak skalowanie ma wpływ na metaplik kontrolki. To okno można zamknąć w dowolnym momencie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
