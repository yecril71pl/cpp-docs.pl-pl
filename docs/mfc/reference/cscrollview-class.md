---
title: Klasa CScrollView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
dev_langs:
- C++
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82ffdb26c5766a0ff7cbada511c9bc9c82ebfd93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375545"
---
# <a name="cscrollview-class"></a>Klasa CScrollView
A [CView](../../mfc/reference/cview-class.md) dzięki możliwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CScrollView : public CView  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CScrollView::CScrollView](#cscrollview)|Konstruuje `CScrollView` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](#checkscrollbars)|Wskazuje, czy widok przewijania paski przewijania w poziomie i w pionie.|  
|[CScrollView::FillOutsideRect](#filloutsiderect)|Wypełnia obszar poza obszarem przewijania widoku.|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Pobiera bieżące położenie przewijania w jednostkach urządzenia.|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Pobiera bieżący tryb mapowania, łączny rozmiar i rozmiary wiersza i strony przewijanego widoku. Rozmiary są w jednostkach urządzenia.|  
|[CScrollView::GetScrollPosition](#getscrollposition)|Pobiera bieżące położenie przewijania w jednostkach logicznych.|  
|[CScrollView::GetTotalSize](#gettotalsize)|Pobiera całkowity rozmiar widoku przewijania w jednostkach logicznych.|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Powoduje, że rozmiar widoku dyktowania rozmiar ramki.|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|Przewija widok do danego punktu, określona w jednostkach logicznych.|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Umieszcza przewijania widoku w trybie skalowanie do dopasowania.|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|Ustawia tryb mapowania widoku przewijania, łączny rozmiar i kwoty przewijania w poziomie i w pionie.|  
  
## <a name="remarks"></a>Uwagi  
 Można obsługiwać standard przewijanie samodzielnie w dowolnej klasy pochodne `CView` przez zastąpienie mapowanych komunikat [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funkcji elementów członkowskich. Ale `CScrollView` dodaje następujące funkcje do jego `CView` możliwości:  
  
-   Zarządza rozmiarów okna i okienka ekranu i tryby mapowania.  
  
-   Automatycznie przewija w odpowiedzi na komunikaty paska przewijania.  
  
-   Automatycznie przewija w odpowiedzi na wiadomości z klawiatury, bez przewijania myszy i kółka myszy IntelliMouse.  
  
 Aby przewijać automatycznie w odpowiedzi na wiadomości z klawiatury, Dodaj komunikat WM_KEYDOWN i przetestowania VK_DOWN, VK_PREV i wywołanie [SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597).  
  
 Może obsłużyć kółka myszy przewijanie się przez zastąpienie mapowanych komunikat [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) i [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) funkcji elementów członkowskich. Jak w przypadku `CScrollView`, zalecane zachowania obsługuje te funkcje Członkowskie [WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617), komunikat obrotu kółka.  
  
 Aby skorzystać z automatycznego przewijania, pochodzi z klasy widoku `CScrollView` zamiast z `CView`. Widok najpierw utworzenia, aby obliczyć rozmiar przewijanego widok, w oparciu o rozmiar dokumentu, wywołanie `SetScrollSizes` funkcji członkowskiej z zastąpienia albo [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) lub [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Musi pisania kodu do badania rozmiar dokumentu. Na przykład zobacz [próbki bazgrołów](../../visual-cpp-samples.md).)  
  
 Wywołanie `SetScrollSizes` funkcji członkowskiej Ustawia tryb mapowania widoku, całkowita liczba wymiarów widoku przewijania i kwoty przewijanie w poziomie i w pionie. Wszystkie rozmiary są w jednostkach logicznych. Rozmiar logiczny widoku zwykle jest obliczana na podstawie danych przechowywanych w dokumencie, ale w niektórych przypadkach możesz określić o stałym rozmiarze. Przykłady z obu metod można znaleźć [CScrollView::SetScrollSizes](#setscrollsizes).  
  
 Należy określić ilości przewijanie w poziomie i w pionie w jednostkach logicznych. Domyślnie, gdy użytkownik kliknie wale paska przewijania, poza pole przewijania `CScrollView` Przewija "page". Jeśli użytkownik kliknie strzałkę przewijania na końcu paska przewijania, `CScrollView` Przewija "wiersz". Domyślnie strony jest 1/10 całkowitego rozmiaru widoku. wiersz jest 1/10 rozmiaru strony. Zastąp te wartości domyślne przez przekazanie rozmiarów niestandardowych w `SetScrollSizes` funkcję elementu członkowskiego. Na przykład może ustawienie rozmiaru na poziomie niektórych część szerokość całkowity rozmiar i pionowe rozmiaru wysokość wiersza w bieżącej czcionki.  
  
 Zamiast przewijania, `CScrollView` może automatycznie skalować widoku do bieżącego rozmiaru okna. W tym trybie widoku nie ma pasków przewijania i widok logiczny jest rozciągany tak, lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Aby używać tej możliwości skalowania do dopasowania, należy wywołać [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Wywołania albo `SetScaleToFitSize` lub `SetScrollSizes`, ale nie oba.)  
  
 Przed `OnDraw` po wywołaniu funkcji członkowskiej klasy pochodnej widoku `CScrollView` automatycznie dopasowuje początek okienka ekranu dla `CPaintDC` obiektu kontekstu urządzenia, przesyłanego do `OnDraw`.  
  
 Aby dostosować okienka ekranu początkowego okno przewijania `CScrollView` zastępuje [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Dostosowanie to odbywa się automatycznie dla `CPaintDC` kontekstu urządzenia który `CScrollView` przekazuje do `OnDraw`, ale należy wywołać **CScrollView::OnPrepareDC** samodzielnie dla innych kontekstach urządzenia należy użyć, np. `CClientDC`. Można zastąpić **CScrollView::OnPrepareDC** ustawić pióra, kolor tła i inne atrybuty rysowania, ale Wywołaj klasę bazową do skalowania.  
  
 Paski przewijania mogą być wyświetlane w trzech miejscach względem widoku, jak pokazano w następujących przypadkach:  
  
-   Paski przewijania standardowe styl okna można ustawić dla widoku za pomocą **ws_hscroll —** i **ws_vscroll —**[style Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
-   Formanty paska przewijania można również dodać do ramki zawierający widok, przesyła dalej przypadku platformę `WM_HSCROLL` i `WM_VSCROLL` komunikaty z ramkę okna do aktualnie aktywnego widoku.  
  
-   Platformę również przekazuje przewiń komunikaty z `CSplitterWnd` splitter — formant (Widok) w okienku podziału obecnie aktywne. Po umieszczeniu w [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) pasków przewijania udostępnionego `CScrollView` obiektu będzie używać udostępnionego te zamiast tworzenia własnego.  
  
 Aby uzyskać więcej informacji na temat używania `CScrollView`, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md) i [pochodnych widoku klasy dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cview —](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars  
 Wywołanie tej funkcji Członkowskich, aby określić, czy poziome i pionowe paski przewijania widoku.  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *bHasHorzBar*  
 Wskazuje, że aplikacja ma poziomy pasek przewijania.  
  
 *bHasVertBar*  
 Wskazuje, że aplikacja ma pionowy pasek przewijania.  
  
##  <a name="cscrollview"></a>  CScrollView::CScrollView  
 Konstruuje `CScrollView` obiektu.  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `SetScrollSizes` lub `SetScaleToFitSize` przed przewijania widoku są wykorzystywane.  
  
##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect  
 Wywołanie `FillOutsideRect` aby wypełnił obszar widoku, który pojawi się poza obszarem przewijania.  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Kontekst urządzenia, w którym ma zostać wykonane wypełniania.  
  
 `pBrush`  
 Pędzel, z którym ma zostać wypełniony obszaru.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `FillOutsideRect` w danym widoku przewijania `OnEraseBkgnd` funkcji obsługi, aby uniknąć nadmiernego tła ponownego rysowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition  
 Wywołanie `GetDeviceScrollPosition` potrzebne bieżącym poziomie i w pionie położenie pola przewijania pasków przewijania.  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Położenie poziome i pionowe (w jednostkach urządzenia) pola przewijania jako `CPoint` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tej pary współrzędnych odnosi się do lokalizacji w dokumencie, do którego zostały przewijane lewego górnego rogu widoku. Jest to przydatne dla przesunięcie pozycji myszy urządzenia do położenia urządzenia przewijania widoku.  
  
 `GetDeviceScrollPosition` Zwraca wartości w jednostkach urządzenia. Jednostki logiczne, należy użyć `GetScrollPosition` zamiast tego.  
  
##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes` Pobiera bieżący tryb mapowania, łączny rozmiar i rozmiary wiersza i strony przewijanego widoku.  
  
```  
void GetDeviceScrollSizes(
    int& nMapMode,  
    SIZE& sizeTotal,  
    SIZE& sizePage,  
    SIZE& sizeLine) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMapMode`  
 Zwraca bieżący tryb mapowania dla tego widoku. Aby uzyskać listę możliwych wartości, zobacz `SetScrollSizes`.  
  
 `sizeTotal`  
 Zwraca bieżący łączny rozmiar widoku przewijania w jednostkach urządzenia.  
  
 `sizePage`  
 Zwraca bieżący kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy kliknij wale paska przewijania. **Cx** elementu członkowskiego zawiera kwotę poziomej. **Cy** elementu członkowskiego zawiera kwotę pionowej.  
  
 `sizeLine`  
 Zwraca bieżący kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy, kliknij strzałkę przewijania. **Cx** elementu członkowskiego zawiera kwotę poziomej. **Cy** elementu członkowskiego zawiera kwotę pionowej.  
  
### <a name="remarks"></a>Uwagi  
 Rozmiary są w jednostkach urządzenia. Ta funkcja elementu członkowskiego rzadko jest wywoływana.  
  
##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition  
 Wywołanie `GetScrollPosition` potrzebne bieżącym poziomie i w pionie położenie pola przewijania pasków przewijania.  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Położenie poziome i pionowe (w jednostkach logicznych) pola przewijania jako `CPoint` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tej pary współrzędnych odnosi się do lokalizacji w dokumencie, do którego zostały przewijane lewego górnego rogu widoku.  
  
 `GetScrollPosition` Zwraca wartości w jednostkach logicznych. Jednostki urządzenia, należy użyć `GetDeviceScrollPosition` zamiast tego.  
  
##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize  
 Wywołanie `GetTotalSize` można pobrać bieżącego rozmiary poziome i pionowe przewijania widoku.  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowity rozmiar widoku przewijania w jednostkach logicznych. Poziomy rozmiar jest **cx** członkiem `CSize` zwracają wartość. Jest pionowy rozmiar **cy** elementu członkowskiego.  
  
##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit  
 Wywołanie `ResizeParentToFit` aby umożliwić rozmiar widoku dyktowania rozmiar ramki okna.  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShrinkOnly*  
 Rodzaj operacji zmiany rozmiaru do wykonania. Wartość domyślna to **TRUE**, zmniejsza okno ramowe w razie potrzeby. Paski przewijania będzie wyświetlany dla widoków duże lub małe ramka okna. Wartość **FALSE** powoduje, że widok, aby zawsze dokładnie zmiany rozmiaru okna ramki. Może to być nieco niebezpieczne, ponieważ okno ramowe można pobrać zbyt duży, aby zmieścił się wewnątrz okno ramowe interfejsu (MDI) wielu dokumentów lub ekranu.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zalecane tylko dla widoków w oknach ramowych podrzędnych MDI. Użyj `ResizeParentToFit` w `OnInitialUpdate` funkcji obsługi sieci pochodnej `CScrollView` klasy. Na przykład funkcji członkowskiej zobacz [CScrollView::SetScrollSizes](#setscrollsizes).  
  
 `ResizeParentToFit` zakłada się, czy rozmiar okna widok został ustawiony. Jeśli rozmiar okna widoku nie została ustawiona podczas `ResizeParentToFit` jest wywoływana, otrzymasz potwierdzenia. Aby upewnić się, że tak nie jest, należy wykonać następujące wywołanie przed wywołaniem `ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition  
 Wywołanie `ScrollToPosition` przewiń do danego punktu w widoku.  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Punkt przewinięcia w jednostkach logicznych. **x** elementu członkowskiego musi być wartością dodatnią (większa lub równa 0, maksymalnie całkowity rozmiar widoku). Dotyczy to także **y** elementu członkowskiego, gdy tryb mapowania jest `MM_TEXT`. **y** element członkowski ma ujemną wartość w innych niż mapowania tryby `MM_TEXT`.  
  
### <a name="remarks"></a>Uwagi  
 Widok będzie przewijane, tak aby ten punkt znajduje się w lewym górnym rogu okna. Nie można wywołać funkcji członkowskiej, jeśli widok jest skalowane w celu dopasowania.  
  
##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize  
 Wywołanie `SetScaleToFitSize` Jeśli chcesz automatycznie skalować rozmiaru okienka ekranu do bieżącego rozmiaru okna.  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>Parametry  
 `sizeTotal`  
 Poziome i pionowe rozmiary, do których ma być skalowana w widoku. Rozmiar widoku przewijania jest mierzony w jednostkach logicznych. Rozmiar poziomych znajduje się w **cx** elementu członkowskiego. Rozmiar pionowy znajduje się w **cy** elementu członkowskiego. Zarówno **cx** i **cy** musi być większa lub równa 0.  
  
### <a name="remarks"></a>Uwagi  
 Pasków przewijania tylko część widoku logicznym może być widoczny w dowolnym momencie. Z możliwością Skaluj do rozmiaru widoku nie ma pasków przewijania a widok logiczny jest rozciągany tak, lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Gdy zmieniany jest rozmiar okna, widok rysuje jego danych w nowej skali, zależnie od rozmiaru okna.  
  
 Zwykle będzie Umieść wywołanie `SetScaleToFitSize` w zastąpienia widoku `OnInitialUpdate` funkcję elementu członkowskiego. Jeśli nie chcesz, automatyczne skalowanie, wywołanie `SetScrollSizes` zamiast funkcji członkowskiej.  
  
 `SetScaleToFitSize` może służyć do zaimplementowania operację "Powiększenie Dopasuj". Użyj `SetScrollSizes` może ponownie zainicjować przewijania.  
  
 `SetScaleToFitSize` zakłada się, czy rozmiar okna widok został ustawiony. Jeśli rozmiar okna widoku nie została ustawiona podczas `SetScaleToFitSize` jest wywoływana, otrzymasz potwierdzenia. Aby upewnić się, że tak nie jest, należy wykonać następujące wywołanie przed wywołaniem `SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes  
 Wywołanie `SetScrollSizes` po widok ma być aktualizowane.  
  
```  
void SetScrollSizes(
    int nMapMode,  
    SIZE sizeTotal,  
    const SIZE& sizePage = sizeDefault,  
    const SIZE& sizeLine = sizeDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `nMapMode`  
 Tryb mapowania, które można ustawić dla tego widoku. Możliwe wartości:  
  
|Tryb mapowania|Jednostka logiczna|Rozszerzenie dodatnią osi y...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 piksela|W dół|  
|`MM_HIMETRIC`|0,01 mm|W górę|  
|`MM_TWIPS`|1/1440 w|W górę|  
|`MM_HIENGLISH`|0,001 in|W górę|  
|`MM_LOMETRIC`|0,1 mm|W górę|  
|`MM_LOENGLISH`|0,01 in|W górę|  
  
 Wszystkie te tryby są definiowane przez system Windows. Dwa tryby mapowania standardowe, `MM_ISOTROPIC` i `MM_ANISOTROPIC`, nie są używane do `CScrollView`. Biblioteka klas zawiera `SetScaleToFitSize` funkcji członkowskiej skalowania widok do rozmiaru okna. Kolumna trzech w powyższej tabeli opisano współrzędnych orientacji.  
  
 `sizeTotal`  
 Całkowity rozmiar przewijania widoku. **Cx** elementu członkowskiego zawiera poziome zakresu. **Cy** elementu członkowskiego zawiera pionowego. Rozmiary są w jednostkach logicznych. Zarówno **cx** i **cy** musi być większa lub równa 0.  
  
 `sizePage`  
 Kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy kliknij wale paska przewijania. **Cx** elementu członkowskiego zawiera kwotę poziomej. **Cy** elementu członkowskiego zawiera kwotę pionowej.  
  
 `sizeLine`  
 Kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy kliknij strzałkę przewijania. **Cx** elementu członkowskiego zawiera kwotę poziomej. **Cy** elementu członkowskiego zawiera kwotę pionowej.  
  
### <a name="remarks"></a>Uwagi  
 Telefonować zastąpienia z `OnUpdate` funkcji członkowskiej, aby dostosować właściwości przewijania, gdy na przykład początkowo wyświetlana jest dokumentu lub zmiany rozmiaru.  
  
 Będą zazwyczaj uzyskiwać informacje o rozmiarze z widoku skojarzonego dokumentu, przez wywołanie funkcji członkowskiej dokumentu, być może wywołać `GetMyDocSize`, wprowadzona z klasy pochodnej dokumentu. Poniższy kod przedstawia tego podejścia:  
  
 [!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 Można również czasami konieczne może być ustawiona o stałym rozmiarze, zgodnie z poniższym kodem:  
  
 [!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 Musisz ustawić tryb mapowania na dowolnym trybie mapowania systemu Windows z wyjątkiem `MM_ISOTROPIC` lub `MM_ANISOTROPIC`. Jeśli chcesz używać trybu nieograniczonego mapowania wywołanie `SetScaleToFitSize` funkcji członkowskiej zamiast `SetScrollSizes`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
