---
title: 'Kontrolki ActiveX MFC: malowanie kontrolki ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364582"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Kontrolki ActiveX MFC: malowanie kontrolki ActiveX

W tym artykule opisano proces malowania sterowania ActiveX i jak można zmienić kod malowania w celu optymalizacji procesu. (Zobacz [Optymalizacja rysowania sterowania](../mfc/optimizing-control-drawing.md) dla technik optymalizacji rysunku przez brak kontroli indywidualnie przywrócić wcześniej wybrane obiekty GDI. Po narysowaniu wszystkich formantów kontener może automatycznie przywrócić oryginalne obiekty.)

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Przykłady w tym artykule pochodzą z formantu utworzonego przez Kreatora sterowania MFC ActiveX z ustawieniami domyślnymi. Aby uzyskać więcej informacji na temat tworzenia aplikacji kontroli szkieletu za pomocą Kreatora sterowania MFC ActiveX, zobacz artykuł [Kreator sterowania MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Poruszane są następujące tematy:

- [Ogólny proces malowania formantu i kodu utworzonego przez Kreatora sterowania ActiveX w celu obsługi malowania](#_core_the_painting_process_of_an_activex_control)

- [Jak zoptymalizować proces malowania](#_core_optimizing_your_paint_code)

- [Jak malować formant za pomocą metaplików](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Proces malowania formantu ActiveX

Gdy formanty ActiveX są początkowo wyświetlane lub są ponownie rysowane, są one zgodne z procesem malowania podobnym do innych aplikacji opracowanych przy użyciu MFC, z jednym ważnym rozróżnieniem: Formanty ActiveX mogą być w stanie aktywnym lub nieaktywnym.

Aktywny formant jest reprezentowany w kontenerze formantu ActiveX przez okno podrzędne. Podobnie jak inne okna, jest odpowiedzialny za malowanie się po odebraniu wiadomości WM_PAINT. Klasa podstawowa formantu, [COleControl,](../mfc/reference/colecontrol-class.md)obsługuje `OnPaint` ten komunikat w swojej funkcji. Ta domyślna `OnDraw` implementacja wywołuje funkcję formantu.

Nieaktywna kontrolka jest malowana inaczej. Gdy formant jest nieaktywny, jego okno jest niewidoczne lub nie istnieje, więc nie może odbierać komunikat farby. Zamiast tego kontener formantu `OnDraw` bezpośrednio wywołuje funkcję formantu. Różni się to od aktywnego procesu malowania `OnPaint` formantu tym, że funkcja elementu członkowskiego nigdy nie jest wywoływana.

Jak opisano w poprzednich akapitach, jak ActiveX formant jest aktualizowany zależy od stanu formantu. Jednak ponieważ struktura wywołuje `OnDraw` funkcję elementu członkowskiego w obu przypadkach, należy dodać większość kodu malowania w tej funkcji elementu członkowskiego.

Funkcja `OnDraw` elementu członkowskiego obsługuje malowanie sterowania. Gdy formant jest nieaktywny, `OnDraw`wywołuje kontener formantu, przekazując kontekst urządzenia kontenera formantu i współrzędne prostokątnego obszaru zajmowanego przez formant.

Prostokąt przekazany przez strukturę do `OnDraw` funkcji elementu członkowskiego zawiera obszar zajmowany przez formant. Jeśli formant jest aktywny, w lewym górnym rogu jest (0, 0) i kontekst urządzenia przekazywane jest dla okna podrzędnego, który zawiera formant. Jeśli formant jest nieaktywny, lewa górna współrzędna nie jest koniecznie (0, 0), a kontekst urządzenia przekazany jest dla kontenera formantu zawierającego formant.

> [!NOTE]
> Ważne jest, aby `OnDraw` modyfikacje nie zależały od tego, czy lewy górny punkt prostokąta jest równy (0, `OnDraw`0) i aby rysować tylko wewnątrz prostokąta przekazanego do . Nieoczekiwane wyniki mogą wystąpić, jeśli rysujesz poza obszarem prostokąta.

Domyślna implementacja dostarczona przez Kreatora sterowania MFC ActiveX w pliku implementacji formantu (. CPP), pokazany poniżej, maluje prostokąt białym pędzlem i wypełnia elipsę bieżącym kolorem tła.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Podczas malowania formantu nie należy zakładać stanu kontekstu urządzenia, który jest `OnDraw` przekazywany jako parametr *pdc* do funkcji. Od czasu do czasu kontekst urządzenia jest dostarczany przez aplikację kontenera i nie musi być inicjowany do stanu domyślnego. W szczególności jawnie wybierz pióra, pędzle, kolory, czcionki i inne zasoby, od których zależy kod rysunku.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optymalizacja kodu farby

Po pomyślnym malowaniu formantu następnym krokiem `OnDraw` jest optymalizacja funkcji.

Domyślna implementacja malowania formantów ActiveX maluje cały obszar sterowania. Jest to wystarczające dla prostych formantów, ale w wielu przypadkach ponowne malowanie formantu byłoby szybsze, jeśli tylko część, która wymaga aktualizacji została przemalowana, zamiast całego formantu.

Funkcja `OnDraw` zapewnia łatwą metodę optymalizacji poprzez przejście *rcInvalid*, prostokątny obszar sterowania, który wymaga przerysowania. Użyj tego obszaru, zwykle mniejszego niż cały obszar kontrolny, aby przyspieszyć proces malowania.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Malowanie sterowania za pomocą metaplików

W większości przypadków parametr *pdc* do `OnDraw` funkcji wskazuje kontekst urządzenia ekranowego (DC). Jednak podczas drukowania obrazów formantu lub podczas sesji podglądu wydruku kontroler domeny odebrany do renderowania jest specjalnym typem zwanym "metaplikowym kontrolerem domeny". W przeciwieństwie do kontrolera domeny ekranu, który natychmiast obsługuje wysłane do niego żądania, metaplik dc przechowuje żądania do odtworzonego w późniejszym czasie. Niektóre aplikacje kontenera mogą również zdecydować się na renderowanie obrazu sterującego przy użyciu metapliku DC w trybie projektowania.

Żądania rysowania metaplików mogą być składane `IViewObject::Draw` przez kontener za pośrednictwem dwóch funkcji interfejsu: `IDataObject::GetData`(ta funkcja może być również wywoływana dla rysowania nie-metaplikowego) i . Gdy metaplik DC jest przekazywany jako jeden z parametrów, struktura MFC wywołuje [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Ponieważ jest to funkcja wirtualnego elementu członkowskiego, należy zastąpić tę funkcję w klasie formantu, aby wykonać wszelkie specjalne przetwarzanie. Domyślne zachowanie `COleControl::OnDraw`wywołuje .

Aby upewnić się, że formant można narysować w kontekstach urządzenia zarówno na ekranie, jak i w metaplikach, należy używać tylko funkcji członkowskich, które są obsługiwane zarówno na ekranie, jak i w metapliku kontrolera domeny. Należy pamiętać, że układ współrzędnych nie może być mierzony w pikselach.

Ponieważ domyślna `OnDrawMetafile` implementacja wywołuje `OnDraw` funkcję formantu, należy używać tylko funkcji członkowskich, które są odpowiednie zarówno `OnDrawMetafile`dla metapliku, jak i kontekstu urządzenia ekranowego, chyba że zostanie zastąpiona . Poniżej wymieniono podzbiór `CDC` funkcji członkowskich, które mogą być używane zarówno w metapliku, jak i w kontekście urządzenia ekranowego. Aby uzyskać więcej informacji na temat tych funkcji, zobacz klasy [CDC](../mfc/reference/cdc-class.md) w *odwołaniu MFC*.

|Arc|Bibblt (BibBlt)|Chord|
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

Oprócz `CDC` funkcji członkowskich istnieje kilka innych funkcji, które są zgodne w metapliku DC. Należą do nich [CPalette:::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)i trzy `CBrush`funkcje członkowskie: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)i [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funkcje, które nie są rejestrowane w metapliku są: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)i [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Ponieważ metaplik DC nie jest faktycznie skojarzony z urządzeniem, nie można używać SetDIBits, GetDIBits i CreateDIBitmap z metaplikiem DC. Można użyć SetDIBitsToDevice i StretchDIBits z metaplik dc jako miejsce docelowe. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)i [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nie mają znaczenia w przypadku metapliku DC.

Innym punktem, który należy wziąć pod uwagę przy użyciu metapliku DC, jest to, że układ współrzędnych nie może być mierzony w pikselach. Z tego powodu cały kod rysunku powinien być dostosowany `OnDraw` tak, aby zmieścił się w prostokącie przekazanym w parametrze *rcBounds.* Zapobiega to przypadkowemu malowaniu poza formantem, ponieważ *rcBounds* reprezentuje rozmiar okna formantu.

Po zaimplementowaniu renderowania metapliku dla formantu użyj kontenera testowego, aby przetestować metaplik. Zobacz [testowanie właściwości i zdarzenia z kontenerem testowym,](../mfc/testing-properties-and-events-with-test-container.md) aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Aby przetestować metaplik formantu za pomocą kontenera testowego

1. W menu **Edycja** kontenera testowego kliknij polecenie **Wstaw nowy formant**.

1. W polu **Wstaw nowy formant** zaznacz formant i kliknij przycisk **OK**.

   Formant pojawi się w kontenerze testowym.

1. W menu **Sterowanie** kliknij polecenie **Rysuj metaplik**.

   Pojawi się osobne okno, w którym wyświetlany jest metaplik. Można zmienić rozmiar tego okna, aby zobaczyć, jak skalowanie wpływa na metaplik formantu. Okno można zamknąć w dowolnym momencie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
