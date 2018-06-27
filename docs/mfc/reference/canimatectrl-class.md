---
title: Canimatectrl — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 48c431ecbcc415776ff9accfb68004c7c8e46d34
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952329"
---
# <a name="canimatectrl-class"></a>Canimatectrl — klasa
Udostępnia funkcje formantu animacji wspólne systemu Windows.  
  
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
|[CAnimateCtrl::Create](#create)|Tworzy formantu animacji i dołącza go do `CAnimateCtrl` obiektu.|  
|[CAnimateCtrl::CreateEx](#createex)|Tworzy formantu animacji w określonym stylu rozszerzonej systemu Windows i dołącza go do `CAnimateCtrl` obiektu.|  
|[CAnimateCtrl::IsPlaying](#isplaying)|Wskazuje, czy jest odtwarzanie klipów Audio i wideo z przeplotem (AVI).|  
|[CAnimateCtrl::Open](#open)|Otwiera klip AVI z pliku lub zasobu i wyświetla pierwszej ramki.|  
|[CAnimateCtrl::Play](#play)|Klip AVI bez dźwięk jest odtwarzany.|  
|[CAnimateCtrl::Seek](#seek)|Wyświetla wybrany jedną ramkę klip AVI.|  
|[CAnimateCtrl::Stop](#stop)|Zatrzymuje odtwarzanie klip AVI.|  
  
## <a name="remarks"></a>Uwagi  
 Ten formant (i w związku z tym `CAnimateCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95, Windows 98 i Windows NT 3.51 lub nowszej.  
  
 Formantu animacji jest prostokątny okno wyświetla klip AVI (Audio wideo przeplatana) format — standardowy format audio/wideo systemu Windows. Klip AVI jest szereg ramki mapy bitowej, takich jak filmu.  
  
 Formanty animacji można odtworzyć tylko proste klipy AVI. W szczególności klipów odtwarzane za pomocą formantu animacji musi spełniać następujące wymagania:  
  
-   Musi być dokładnie jednego strumienia wideo i musi mieć co najmniej jedną ramkę.  
  
-   Może istnieć co najwyżej dwóch strumieni w pliku (zazwyczaj innego strumienia, jeśli jest dostępna jest strumieniem audio, mimo że formantu animacji ignoruje informacji audio).  
  
-   Klip musi być nieskompresowane lub skompresowane RLE8 kompresji.  
  
-   Wprowadzanie zmian palety jest niedozwolone w strumieniu wideo.  
  
 Klip AVI można dodać do aplikacji jako zasób AVI lub może towarzyszyć aplikacji jako osobny plik AVI.  
  
 Ponieważ wykonywania podczas klip AVI zostanie wyświetlony w wątku sieci będzie nadal występował, jednym z typowych zastosowań formantu animacji jest wskazać działania systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdź Eksploratora plików wyświetla przenoszenie Lupa jako system wyszukuje plik.  
  
 W przypadku utworzenia `CAnimateCtrl` obiektów w oknie dialogowym wpisz lub z zasobu okna dialogowego za pomocą edytora okien dialogowych, jego zostaną automatycznie usunięte gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CAnimateCtrl` obiektów w ramach okna, konieczne może być zniszczenia. W przypadku utworzenia `CAnimateCtrl` obiektów na stosie, zostanie zniszczony automatycznie. W przypadku utworzenia `CAnimateCtrl` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** na obiekt do zniszczenia. Jeśli pochodzi z nową klasę `CAnimateCtrl` i Przydziel wszystkie pamięci przez tę klasę, Zastąp `CAnimateCtrl` destruktora zlikwidować alokacje.  
  
 Aby uzyskać więcej informacji na temat używania `CAnimateCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CAnimateCtrl](../../mfc/using-canimatectrl.md).  
  
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
 Należy wywołać [Utwórz](#create) funkcji członkowskiej, zanim będzie można wykonać żadnych innych operacji tworzenia obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]  
  
##  <a name="close"></a>  CAnimateCtrl::Close  
 Zamyka klip AVI, który został uprzednio otwarty w formantu animacji (jeśli istnieje) i usuwa go z pamięci.  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="create"></a>  CAnimateCtrl::Create  
 Tworzy formantu animacji i dołącza go do `CAnimateCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa styl formantu animacji. Zastosuj dowolną kombinację windows szczegółowo opisane w poniższej sekcji uwag i stylów formantu animacji style [stylów formantu animacji](http://msdn.microsoft.com/library/windows/desktop/bb761886) w zestawie Windows SDK.  
  
 *Rect*  
 Określa położenie i rozmiar formantu animacji. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 *pParentWnd*  
 Określa okno nadrzędne kontrolki animacji, zwykle `CDialog`. Nie może być **NULL**.  
  
 *nID*  
 Określa identyfikator formantu animacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CAnimateCtrl` w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać `Create`, która tworzy kontrolkę animacji i dołącza go do `CAnimateCtrl` obiektu.  
  
 Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu animacji.  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
 Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu animacji, wywołanie [CreateEx](#createex) zamiast `Create`.  
  
 Oprócz Style okna wymienionych powyżej możesz zastosować przynajmniej jednej stylów formantu animacji do formantu animacji. Zobacz Windows SDK, aby uzyskać więcej informacji na [stylów formantu animacji](http://msdn.microsoft.com/library/windows/desktop/bb761886).  
  
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
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz *dwExStyle* parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa styl formantu animacji. Zastosuj dowolną kombinację okna i stylów formantu animacji opisanych w [stylów formantu animacji](http://msdn.microsoft.com/library/windows/desktop/bb761886) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying  
 Wskazuje, czy jest odtwarzanie klipów Audio i wideo z przeplotem (AVI).  
  
```  
BOOL IsPlaying() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli jest odtwarzany klip AVI; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [ACM_ISPLAYING](http://msdn.microsoft.com/library/windows/desktop/bb761895) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="open"></a>  CAnimateCtrl::Open  
 Wywołanie tej funkcji, aby otworzyć klip AVI i wyświetlić jej pierwszej ramki.  
  
```  
BOOL Open(LPCTSTR lpszFileName);  
BOOL Open(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszFileName*  
 A `CString` obiekt lub wskaźnik do zerem ciąg, który zawiera nazwę pliku AVI albo nazwa zasobu AVI. Jeśli ten parametr ma **NULL**, system zamyka klip AVI, który został uprzednio otwarty dla formantu animacji, jeśli istnieje.  
  
 *nID*  
 Identyfikator zasobu AVI. Jeśli ten parametr ma **NULL**, system zamyka klip AVI, który został uprzednio otwarty dla formantu animacji, jeśli istnieje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 AVI zasobów są ładowane z modułu, który go utworzył animacji.  
  
 **Otwórz** klip AVI; nie obsługuje dźwięk można otwierać tylko dyskretnej klipy AVI.  
  
 Jeśli z formantem animacji `ACS_AUTOPLAY` styl formantu animacji zostaną automatycznie uruchomione odtwarzanie klip natychmiast po jej otwarciu. Nadal będzie odtwarzać klip w tle, gdy Twoje wątku kontynuuje wykonywanie. Po zakończeniu klip odtwarzania go automatycznie powtarza się.  
  
 Jeśli z formantem animacji `ACS_CENTER` styl klip AVI zostanie wyśrodkowany w formancie i nie zmienia rozmiar formantu. Jeśli nie ma formantu animacji `ACS_CENTER` styl formantu będzie zmieniany, gdy klip AVI zostanie otworzony rozmiar obrazów w klip AVI. Pozycja w lewym górnym rogu formantu nie spowoduje zmiany, tylko rozmiar formantu.  
  
 Jeśli ma formantu animacji `ACS_TRANSPARENT` styl pierwszej ramki będzie rysowany przy użyciu przezroczyste tło zamiast kolor tła określone w klipie animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="play"></a>  CAnimateCtrl::Play  
 Wywołanie tej funkcji, aby odtworzyć klip AVI w formantu animacji.  
  
```  
BOOL Play(
    UINT nFrom,  
    UINT nTo,  
    UINT nRep);
```  
  
### <a name="parameters"></a>Parametry  
 *NZ*  
 Liczony od zera indeks ramki, w którym rozpoczyna się odtwarzanie. Wartość musi być mniejsza niż 65536. Wartość 0 oznacza, że rozpoczynać się od pierwszej ramki w klip AVI.  
  
 *nAby*  
 Liczony od zera indeks klatki którym odtwarzanie kończy się. Wartość musi być mniejsza niż 65536. Wartość - 1 oznacza kończyć ostatniej ramki w klip AVI.  
  
 *nRep*  
 Liczba powtarzania klip AVI. Wartość - 1 oznacza nieokreśloną pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Formantu animacji odtwarzania klipu w tle z wątku kontynuuje wykonywanie. Jeśli z formantem animacji `ACS_TRANSPARENT` styl klip AVI wykonywanej przy użyciu przezroczyste tło zamiast kolor tła określony w klipie animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="seek"></a>  CAnimateCtrl::Seek  
 Wywołanie tej funkcji, aby wyświetlić statycznie jedną ramkę klip AVI.  
  
```  
BOOL Seek(UINT nTo);
```  
  
### <a name="parameters"></a>Parametry  
 *nAby*  
 Liczony od zera indeks ramki do wyświetlenia. Wartość musi być mniejsza niż 65536. Wartość 0 oznacza wyświetlenie pierwszej ramki w klip AVI. Wartość -1 oznacza wyświetlenie ramki ostatniego w klip AVI.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ma formantu animacji `ACS_TRANSPARENT` styl klip AVI będzie rysowany przy użyciu przezroczyste tło zamiast kolor tła określone w klipie animacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
##  <a name="stop"></a>  CAnimateCtrl::Stop  
 Wywołanie tej funkcji, aby zatrzymać odtwarzanie klip AVI formantu animacji.  
  
```  
BOOL Stop();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CAnimateCtrl::CAnimateCtrl](#canimatectrl).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CAnimateCtrl::Create](#create)   
 [ON_CONTROL —](message-map-macros-mfc.md#on_control)

