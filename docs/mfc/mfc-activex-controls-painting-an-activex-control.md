---
title: 'Formanty MFC ActiveX: Malowanie formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de12a21c4b411f3cd1fe25d7d6badd8d26318351
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929815"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Kontrolki ActiveX MFC: malowanie kontrolki ActiveX
W tym artykule opisano proces malowanie formantu ActiveX i jak można zmienić kod farby, aby zoptymalizować proces. (Zobacz [Optymalizacja rysowania kontroli](../mfc/optimizing-control-drawing.md) dla techniki dotyczące optymalizacji rysunku, ponieważ nie ma pojedynczych formantów Przywróć wcześniej wybrane obiekty GDI. Po zostały wystawione wszystkie formanty, kontener może automatycznie Przywracanie oryginalnych obiektów.)  
  
 Przykłady w tym artykule pochodzą z formantu tworzone przez Kreator kontrolek ActiveX MFC z ustawieniami domyślnymi. Aby uzyskać więcej informacji na temat tworzenia aplikacji szkielet formantów przy użyciu kreator kontrolek ActiveX MFC, zobacz artykuł [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Omówiono następujące tematy:  
  
-   [Ogólny proces malowanie formantu i kod utworzonych przez Kreator kontrolek ActiveX do obsługi rysowania](#_core_the_painting_process_of_an_activex_control)  
  
-   [Jak zoptymalizować proces rysowania](#_core_optimizing_your_paint_code)  
  
-   [Jak namalować formantu przy użyciu metapliki](#_core_painting_your_control_using_metafiles)  
  
##  <a name="_core_the_painting_process_of_an_activex_control"></a> Proces malowanie formantu ActiveX  
 Formanty ActiveX są początkowo wyświetlane lub są rysowane, należy wykonać procedurę rysowania podobnie jak inne aplikacje opracowane za pomocą MFC, z jedną istotną różnicę: formantów ActiveX może być aktywny lub nieaktywny.  
  
 Aktywny formant jest reprezentowana w kontenerze formantów ActiveX przez okna podrzędnego. Podobnie jak inne okna jest odpowiedzialny za malowanie się, gdy zostaje otrzymany komunikat WM_PAINT. Klasa podstawowa dla formantu, [colecontrol —](../mfc/reference/colecontrol-class.md), obsługuje tę wiadomość w jego `OnPaint` funkcji. Ta domyślna implementacja wywołuje `OnDraw` funkcja formantu.  
  
 Formant nieaktywne jest rysowane inaczej. Gdy formant jest nieaktywny, okna jest niewidoczne lub nie istnieje, więc może nie odbierać wiadomości malowania. Zamiast tego formantu kontenera bezpośrednio wywołuje `OnDraw` funkcja formantu. Ta różni się od procesu rysowania aktywny formant w tym `OnPaint` nigdy nie została wywołana funkcja elementu członkowskiego.  
  
 Zgodnie z opisem w akapitów, sposób aktualizowania formantu ActiveX zależny od stanu formantu. Jednak ponieważ struktura wywołuje `OnDraw` funkcji członkowskiej w obu przypadkach należy dodać większość kodu malowania w funkcji członkowskiej.  
  
 `OnDraw` Funkcji członkowskiej obsługuje malowanie formantu. Gdy formant jest nieaktywny, wywołuje kontenera formantu `OnDraw`, przekazanie kontekstu urządzenia formantu kontenera i współrzędne prostokątny obszar zajmowane przez formant.  
  
 Prostokąt przekazany przez platformę, by `OnDraw` funkcji członkowskiej zawiera obszar zajęty przez formant. Jeśli formant jest aktywny, lewego górnego rogu jest (0, 0) i kontekst urządzenia przekazany do okna podrzędnego z formantem. Jeśli formant jest nieaktywny, Współrzędna lewej górnej niekoniecznie (0, 0) i kontekst urządzenia przekazany dla formantu kontenera zawierająca formant.  
  
> [!NOTE]
>  Ważne jest, że modyfikacje `OnDraw` nie zależą od prostokąta górnego punktu po lewej stronie jest równa (0, 0) i rysowania tylko wewnątrz prostokąta przekazywane do `OnDraw`. Po narysowaniu poza obszarem prostokąta, mogą wystąpić nieoczekiwane rezultaty.  
  
 Domyślna implementacja udostępniane przez Kreator kontrolek ActiveX MFC w pliku implementacji (. CPP), pokazano poniżej, prostokąt z białym znakiem pędzla do malowania i wypełnia elipsy bieżący kolor tła.  
  
 [!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]  
  
> [!NOTE]
>  Gdy malowanie formantu, nie należy podejmować założenia dotyczące stan kontekstu urządzenia, który jest przekazywany jako *kontrolera pdc* parametr `OnDraw` funkcji. Czasami kontekstu urządzenia jest dostarczany przez aplikację kontenera i nie zostaną niekoniecznie zainicjowane do stanu domyślnego. W szczególności należy jawnie wybrać pióra, pędzle, kolory, czcionki i inne zasoby, które zależy od swój kod rysowania.  
  
##  <a name="_core_optimizing_your_paint_code"></a> Optymalizacja kodu malowania  
 Po formantu jest pomyślnie malowanie samego, następnym krokiem jest zoptymalizować `OnDraw` funkcji.  
  
 Domyślna implementacja malowanie formantu ActiveX umożliwia malowanie obszar całego kontroli. To jest wystarczająca dla formantów prostego, ale w wielu przypadkach ponownego rysowania formant będzie szybciej, jeśli tylko część wymaganej aktualizacji zostało odowieżany zamiast całego formantu.  
  
 `OnDraw` Funkcja zapewnia to łatwa metoda optymalizacji przez przekazanie *rcInvalid*, prostokątny obszar kontrolkę, która wymaga ponownego narysowania. Umożliwia ten obszar zwykle mniejsze niż obszar kontroli cały proces rysowania.  
  
##  <a name="_core_painting_your_control_using_metafiles"></a> Malowanie formantu przy użyciu metapliki  
 W większości przypadków *kontrolera pdc* parametr `OnDraw` funkcji wskazuje ekranu kontekstu urządzenia (DC). Jednak podczas drukowania obrazów formantu lub podczas sesji podglądu wydruku, kontroler domeny otrzymał celu renderowania jest specjalny typ o nazwie "metaplik kontrolera domeny". W przeciwieństwie do ekranu kontrolera domeny, która natychmiast obsługuje żądania wysyłane do niego, metaplików kontroler domeny przechowuje żądań, aby go odtworzyć w późniejszym czasie. Niektóre aplikacje kontener może też renderować obraz kontrolki za pomocą metaplik kontrolera domeny w trybie projektowania.  
  
 Metaplik rysowania żądań jest możliwe przez kontener za pośrednictwem dwóch funkcji interfejsu: `IViewObject::Draw` (Ta funkcja także dla może zostać wywołany z systemem innym niż metaplik rysowania) i `IDataObject::GetData`. Gdy metaplik kontrolera domeny jest przekazywany jako jeden z parametrów, struktura MFC nawiązuje połączenie [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Ponieważ jest to funkcja wirtualny element członkowski, należy przesłonić tę funkcję w klasie formantu do dowolnego specjalnego przetwarzania. Wywołania zachowanie domyślne `COleControl::OnDraw`.  
  
 Upewnij się, że formant może znajdować się na środku zarówno ekranu, a metaplików konteksty urządzenia, możesz korzystać tylko funkcji elementów członkowskich, które są obsługiwane zarówno ekranu i metaplik kontrolera domeny. Należy pamiętać, że współrzędnych nie może być podawana w pikselach.  
  
 Ponieważ domyślna implementacja `OnDrawMetafile` wywołuje formantu `OnDraw` funkcji, należy użyć tylko funkcje Członkowskie, które są odpowiednie dla zarówno metaplik, jak i kontekst urządzenia ekranu, chyba że nadpiszesz `OnDrawMetafile`. Poniższa lista zawiera podzbiór `CDC` funkcji elementów członkowskich, których można użyć w metaplik i kontekst urządzenia ekranu. Aby uzyskać więcej informacji na temat tych funkcji, zobacz klasy [CDC](../mfc/reference/cdc-class.md) w *odwołania MFC*.  
  
|Łuk|BibBlt|Akordu|  
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
  
 Oprócz `CDC` funkcji członkowskiej, istnieje kilka funkcji, które są zgodne w metaplik kontrolera domeny. Obejmują one [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)i trzy funkcje Członkowskie `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), i [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).  
  
 Funkcje, które nie są rejestrowane w metaplik są: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)i [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Ponieważ metaplik kontrolera domeny nie jest rzeczywiście skojarzone z urządzeniem, nie można używać SetDIBits, GetDIBits i CreateDIBitmap metaplik kontrolera domeny. Umożliwia SetDIBitsToDevice i StretchDIBits z metaplik kontrolera domeny jako miejsca docelowego. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), i [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nie są znaczące z metaplik kontrolera domeny.  
  
 Inny punkt do uwzględnienia przy użyciu metaplik kontrolera domeny jest, że współrzędnych nie może być podawana w pikselach. Z tego powodu wszystkie swój kod rysowania powinny być dostosowane do mieści się w prostokącie przekazany do `OnDraw` w *rcBounds* parametru. Zapobiega przypadkowemu rysowania poza kontrolą, ponieważ *rcBounds* reprezentuje rozmiar okna formantu.  
  
 Po wdrożeniu metaplik renderowania dla formantu, przetestuj metaplik za pomocą kontenera testu. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
#### <a name="to-test-the-controls-metafile-using-test-container"></a>Aby przetestować metaplik formantu za pomocą kontenera testu  
  
1.  W kontenerze testowym **Edytuj** menu, kliknij przycisk **Wstaw nowy formant**.  
  
2.  W **Wstaw nowy formant** wybierz formantu a kliknij **OK**.  
  
     Formant pojawią się w kontenerze testowym.  
  
3.  Na **kontroli** menu, kliknij przycisk **rysowania metaplik**.  
  
     Osobne okno jest wyświetlane, w którym jest wyświetlany metaplik. Można zmienić rozmiar tego okna, aby zobaczyć wpływ skalowania formantu metaplik. W dowolnej chwili możesz zamknąć to okno.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

