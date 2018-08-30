---
title: Klasa CAnimateCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
dev_langs:
- C++
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b8f9f99b38d2878025546379a185aef53bb663
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213772"
---
# <a name="canimatectrl-class"></a>Klasa CAnimateCtrl
Oferuje funkcje kontrolki typowej animacji Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CAnimateCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Konstruuje `CAnimateCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAnimateCtrl::Close](#close)|Zamyka klip AVI.|  
|[CAnimateCtrl::Create](#create)|Tworzy formant animacji i dołącza je do `CAnimateCtrl` obiektu.|  
|[CAnimateCtrl::CreateEx](#createex)|Tworzy formant animacji przy użyciu określonego stylów rozszerzonej Windows i dołącza je do `CAnimateCtrl` obiektu.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Wskazuje, czy jest odtwarzany klip Audio i wideo z przeplotem (AVI).|  
|[CAnimateCtrl::Open](#open)|Otwiera klip AVI z pliku lub zasobu i wyświetla pierwszej ramki.|  
|[CAnimateCtrl::Play](#play)|Odtwarza klip AVI bez dźwięku.|  
|[CAnimateCtrl::Seek](#seek)|Wyświetla wybrany jednej ramki klip AVI.|  
|[CAnimateCtrl::Stop](#stop)|Zatrzymuje odtwarzanie klipu AVI.|  
  
## <a name="remarks"></a>Uwagi  
 Ta kontrolka (i w związku z tym `CAnimateCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95, Windows 98 i Windows NT 3.51 lub nowszej.  
  
 Formantu animacji jest oknem prostokątny, który wyświetla klip AVI (wideo Audio z przeplotem) format — standardowego formatu audio/wideo Windows. Klip AVI to seria ramek mapy bitowej, takie jak film.  
  
 Formanty animacji można odtworzyć tylko proste klipy AVI. W szczególności klipy wideo do odtwarzania przez kontrolki animacji musi spełniać następujące wymagania:  
  
-   Musi być dokładnie jednego strumienia wideo i musi mieć co najmniej jedną klatkę.  
  
-   Może być co najwyżej dwóch strumieni w pliku (zazwyczaj innych strumienia, jeśli jest obecny, jest strumienia audio, chociaż kontrolki animacji ignoruje audio informacji).  
  
-   Klip musi być bez kompresji lub skompresowany za pomocą RLE8 kompresji.  
  
-   Brak zmian palety są dozwolone w strumienia wideo.  
  
 Tylko klip AVI można dodać do aplikacji jako zasób AVI lub jej towarzyszą Twojej aplikacji w postaci oddzielnych plików AVI.  
  
 Ponieważ wątek kontynuuje wykonywanie, gdy jest wyświetlana tylko klip AVI, co spotykanym sposobem wykorzystania formantu animacji jest wskazujący aktywności systemu podczas długotrwałej operacji. Na przykład okno dialogowe znajdowania Eksploratora plików wyświetla przenoszenie szkła powiększającego jako system wyszukuje plik.  
  
 Jeśli tworzysz `CAnimateCtrl` obiektu w obrębie okna dialogowego pole, lub z zasobu okna dialogowego za pomocą edytora okien dialogowych, jej zostaną automatycznie usunięte po użytkownik zamknie okno dialogowe.  
  
 Jeśli tworzysz `CAnimateCtrl` obiekt w tym oknie, konieczne może być zniszczenia. Jeśli tworzysz `CAnimateCtrl` obiektów na stosie, zostanie zniszczony automatycznie. Jeśli tworzysz `CAnimateCtrl` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu do zniszczenia. Przypadku klasy wyprowadzonej z nową klasę `CAnimateCtrl` i przydzielić wszystkie pamięci w tej klasie, Zastąp `CAnimateCtrl` destruktora w celu usunięcia alokacje.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CAnimateCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CAnimateCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl  
 Konstruuje `CAnimateCtrl` obiektu.  
  
```  
CAnimateCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [Utwórz](#create) funkcja elementu członkowskiego, aby można było wykonać żadnych innych operacji na obiekcie tworzenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>  CAnimateCtrl::Close  
 Zamyka klip AVI, który był wcześniej otwarty w formancie animacji (jeśli istnieje) i usuwa go z pamięci.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>  CAnimateCtrl::Create  
 Tworzy formant animacji i dołącza je do `CAnimateCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl kontrolki animacji. Zastosuj dowolnej kombinacji systemu windows, opisane w poniższej sekcji uwag i style kontrolki animacji style opisanego w [style kontrolki animacji](/windows/desktop/Controls/animation-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Określa położenie i rozmiar kontrolki animacji. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](../../mfc/reference/rect-structure1.md) struktury.  
  
 *pParentWnd*  
 Określa okno nadrzędne kontrolki animacji, zwykle `CDialog`. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CAnimateCtrl` w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołaj `Create`, który tworzy kontrolki animacji i dołącza go do `CAnimateCtrl` obiektu.  
  
 Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu animacji.  
  
- WS_CHILD zawsze  
  
- WS_VISIBLE zwykle  
  
- WS_DISABLED rzadko  
  
 Style rozszerzone systemu windows za pomocą kontrolki animacji należy wywołać [CreateEx](#createex) zamiast `Create`.  
  
 Oprócz Style okna wymienionych powyżej można zastosować co najmniej jeden style kontrolki animacji do kontrolki animacji. Zobacz zestaw SDK Windows, aby uzyskać więcej informacji na [style kontrolki animacji](/windows/desktop/Controls/animation-control-styles).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="createex"></a>  CAnimateCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CAnimateCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl kontrolki animacji. Zastosuj dowolną kombinację okna i style kontrolki animacji opisane w [style kontrolki animacji](/windows/desktop/Controls/animation-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying  
 Wskazuje, czy jest odtwarzany klip Audio i wideo z przeplotem (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli jest odtwarzany klip AVI; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="open"></a>  CAnimateCtrl::Open  
 Wywołaj tę funkcję, aby otworzyć klip AVI i wyświetlić jego pierwszej ramki.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFileName*  
 A `CString` obiekt lub wskaźnik zawiera nazwę pliku AVI albo nazwa zasobu AVI ciąg zakończony znakiem null. Jeśli ten parametr ma wartość NULL, system zamyka klip AVI, który był wcześniej otwarty dla formantu animacji, jeśli istnieje.  
  
 *nID*  
 Identyfikator zasobu AVI. Jeśli ten parametr ma wartość NULL, system zamyka klip AVI, który był wcześniej otwarty dla formantu animacji, jeśli istnieje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Zasób AVI jest ładowany z modułu, który utworzył już formant animacji.  
  
 `Open` nie obsługuje dźwięk w klip AVI; można otworzyć tylko dyskretnej AVI klipów.  
  
 Jeśli ma kontrolki animacji `ACS_AUTOPLAY` stylu kontrolki animacji zostanie automatycznie uruchomiony, odtwarzanie klipu, natychmiast po zakończeniu zostanie otwarty. Nadal będzie odtwarzania klipu w tle, podczas gdy wątek kontynuuje wykonywanie. Po zakończeniu klip odtwarzany, jego automatycznie powtarza się.  
  
 Jeśli ma kontrolki animacji `ACS_CENTER` stylu klip AVI zostanie wyśrodkowany w kontrolce i nie zmienia rozmiar formantu. Jeśli nie ma kontrolki animacji `ACS_CENTER` stylu, formant będzie można zmienić rozmiar, gdy klip AVI zostanie otworzony do rozmiaru obrazów w klip AVI. Pozycja w lewym górnym rogu formantu nie ulegną zmianie, tylko rozmiar formantu.  
  
 Jeśli ma kontrolki animacji `ACS_TRANSPARENT` stylów, pierwsza ramka będą pobierane przy użyciu przezroczyste tło zamiast kolor tła określone w klipu animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>  CAnimateCtrl::Play  
 Wywołaj tę funkcję, aby odtworzyć klip AVI w formantu animacji.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parametry  
 *nZe*  
 Liczony od zera indeks ramki, w którym rozpoczyna się odtwarzanie. Wartość musi być mniejsza niż 65536. Wartość 0 oznacza, że zaczynają się od pierwszej ramki w klip AVI.  
  
 *nAby*  
 Liczony od zera indeks ramki, gdzie odtwarzanie kończy się. Wartość musi być mniejsza niż 65536. Wartość - 1 oznacza, że kończy się ostatniej ramki w klip AVI.  
  
 *nRep*  
 Liczba tylko klip AVI oparte na metodzie powtórzeń. Wartość - 1 oznacza nieokreśloną pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolki animacji będzie odtwarzany klip w tle, podczas gdy wątek kontynuuje wykonywanie. Jeśli ma kontrolki animacji `ACS_TRANSPARENT` stylu klip AVI będą odtwarzane przy użyciu przezroczyste tło, a nie kolor tła, określone w klipie animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>  CAnimateCtrl::Seek  
 Wywołaj tę funkcję, aby wyświetlić statycznie jednej ramki klip AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parametry  
 *nAby*  
 Liczony od zera indeks ramki do wyświetlenia. Wartość musi być mniejsza niż 65536. Wartość 0 oznacza wyświetlenie pierwszej ramki w klip AVI. Wartość -1 oznacza wyświetlenie ostatniej ramki w klip AVI.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ma kontrolki animacji `ACS_TRANSPARENT` stylu klip AVI będą pobierane przy użyciu przezroczyste tło, a nie kolor tła określone w klipu animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>  CAnimateCtrl::Stop  
 Wywołaj tę funkcję, aby zatrzymać odtwarzanie klip AVI w kontrolce animacji.  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL](message-map-macros-mfc.md#on_control)

