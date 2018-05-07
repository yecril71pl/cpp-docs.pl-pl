---
title: Ctoolbar — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
dev_langs:
- C++
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a80ea4cb188d879b9af0a7901ffbe89b8673df6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ctoolbar-class"></a>Ctoolbar — klasa
Paski sterowania mających wiersz przycisków mapy bitowej i opcjonalnie separatorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|Konstruuje `CToolBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|Zwraca indeks przycisk o tym identyfikatorze danego polecenia.|  
|[CToolBar::Create](#create)|Tworzy narzędzi systemu Windows i dołącza go do `CToolBar` obiektu.|  
|[CToolBar::CreateEx](#createex)|Tworzy `CToolBar` obiektu o dodatkowe style osadzonego `CToolBarCtrl` obiektu.|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Pobiera identyfikator, stylu i numer obrazu przycisku.|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Pobiera styl przycisku.|  
|[CToolBar::GetButtonText](#getbuttontext)|Pobiera tekst, który będzie wyświetlany na przycisku.|  
|[CToolBar::GetItemID](#getitemid)|Zwraca identyfikator polecenia przycisku lub separatora pod danym indeksem.|  
|[CToolBar::GetItemRect](#getitemrect)|Pobiera prostokątny obszar wyświetlania elementu pod danym indeksem.|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umożliwia bezpośredni dostęp do podstawowych formant.|  
|[CToolBar::LoadBitmap](#loadbitmap)|Ładuje mapę bitową zawierający obrazy dla przycisków mapy bitowej.|  
|[CToolBar::LoadToolBar](#loadtoolbar)|Ładuje zasobu paska narzędzi utworzone za pomocą edytora zasobów.|  
|[CToolBar::SetBitmap](#setbitmap)|Ustawia obraz mapy bitowej.|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Określa identyfikator, stylu i numer obrazu przycisku.|  
|[CToolBar::SetButtons](#setbuttons)|Ustawia przycisk style i indeks obrazy dla przycisków w mapy bitowej.|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku.|  
|[CToolBar::SetButtonText](#setbuttontext)|Ustawia tekst, który będzie wyświetlany na przycisku.|  
|[CToolBar::SetHeight](#setheight)|Określa wysokość paska narzędzi.|  
|[CToolBar::SetSizes](#setsizes)|Ustawia przycisków i ich map bitowych.|  
  
## <a name="remarks"></a>Uwagi  
 Przyciski może działać tak jak przyciski, przyciski pola wyboru lub przycisków radiowych. `CToolBar` obiekty są zwykle osadzonych członkami okno ramowe obiektów pochodzących od klasy [cframewnd —](../../mfc/reference/cframewnd-class.md) lub [cmdiframewnd —](../../mfc/reference/cmdiframewnd-class.md).  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl), funkcji członkowskiej nowych 4.0 MFC pozwala korzystać z obsługi systemu Windows formantu wspólnego pasków narzędzi i dodatkowe funkcje. `CToolBar` Funkcje Członkowskie zapewniają większość funkcjonalności formanty standardowe systemu Windows; Jednak jeśli wywołasz `GetToolBarCtrl`, pasków narzędzi można nadać jeszcze więcej właściwości paski narzędzi Windows 95/98. Podczas wywoływania `GetToolBarCtrl`, zwróci odwołanie do `CToolBarCtrl` obiektu. Zobacz [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) uzyskać więcej informacji o projektowaniu paski narzędzi przy użyciu formanty standardowe systemu Windows. Więcej ogólnych informacji na temat typowych formantów, zobacz [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493) w zestawie Windows SDK.  
  
 Visual C++ udostępnia dwie metody tworzenia paska narzędzi. Aby utworzyć zasób paska narzędzi edytora zasobów, wykonaj następujące kroki:  
  
1.  Utwórz zasób paska narzędzi.  
  
2.  Utworzyć `CToolBar` obiektu.  
  
3.  Wywołanie [Utwórz](#create) (lub [CreateEx](#createex)) funkcja Utwórz pasek narzędzi systemu Windows i dołączenie go do `CToolBar` obiektu.  
  
4.  Wywołanie [LoadToolBar](#loadtoolbar) można załadować zasobu paska narzędzi.  
  
 W przeciwnym razie wykonaj następujące kroki:  
  
1.  Utworzyć `CToolBar` obiektu.  
  
2.  Wywołanie [Utwórz](#create) (lub [CreateEx](#createex)) funkcja Utwórz pasek narzędzi systemu Windows i dołączenie go do `CToolBar` obiektu.  
  
3.  Wywołanie [LoadBitmap](#loadbitmap) załadować mapy bitowej, który zawiera obrazy dla przycisków paska narzędzi.  
  
4.  Wywołanie [SetButtons](#setbuttons) styl przycisku i skojarzyć z obrazem w mapie bitowej każdego przycisku.  
  
 Wszystkie obrazy dla przycisków na pasku narzędzi są brane z jednej bitmapy, który musi zawierać jeden obraz dla każdego przycisku. Wszystkie obrazy muszą być takie same wymiary. Wartość domyślna to 16 pikseli szerokości i wysokości 15 pikseli. Obrazy muszą być jednocześnie w mapy bitowej.  
  
 `SetButtons` Funkcja przyjmuje wskaźnika do tablicy sterowania identyfikatorów i liczba całkowita określająca liczbę elementów w tablicy. Funkcja Ustawia identyfikator każdego przycisku do wartości odpowiadającego mu elementu tablicy i przypisuje każdego przycisku Indeks obrazu, który określa położenie obrazu przycisku w pliku mapy bitowej. Jeśli element tablicy ma wartość **ID_SEPARATOR**, nie przypisano żadnych indeksu obrazu.  
  
 Kolejność obrazów w pliku mapy bitowej jest zwykle kolejność, w którym są one pobierane na ekranie, ale może użyć [SetButtonInfo](#setbuttoninfo) funkcja zmiana relacji między kolejności obrazu i kolejności rysowania.  
  
 Wszystkie przycisków na pasku narzędzi mają taki sam rozmiar. Wartość domyślna to 24 x 22 piksele zgodnie z *Windows interfejsu wskazówki dotyczące projektowania oprogramowania*. Każde dodatkowe miejsce między wymiarami obrazu i przycisk służy do obramowania wokół obrazu.  
  
 Każdy przycisk ma jeden obraz. Przycisk różnych stanów i style (naciśniętego, Strzałka w dół, wyłączone, wyłączona w dół i nieokreślony) są generowane na podstawie jednego obrazu. Mimo że mapy bitowe mogą być dowolnego koloru, można uzyskać najlepsze wyniki z obrazów w czerni i odcieni szarości.  
  
> [!WARNING]
> `CToolBar` obsługuje map bitowych z maksymalnie 16 kolorów. Podczas ładowania obrazu w edytorze paska narzędzi, Visual Studio automatycznie konwertuje obraz mapy bitowej 16 kolorów, jeśli to konieczne i wyświetla ostrzeżenie, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (przy użyciu edytora zewnętrznego do edycji obraz), może być nieoczekiwane zachowanie aplikacji.  
  
 Przyciski paska narzędzi naśladującej przycisków domyślnie. Przyciski paska narzędzi można również jednak naśladującej przycisków pola wyboru lub przycisków radiowych. Przyciski pole wyboru ma trzy stany: zaznaczone, wyczyszczone i nieokreślony. Przyciski radiowe mają tylko dwa stany: zaznaczone i wyczyszczone.  
  
 Aby ustawić separatora stylu lub przycisk poszczególnych bez wskazujące na tablicę, należy wywołać [GetButtonStyle](#getbuttonstyle) do pobrania stylu, a następnie wywołać [SetButtonStyle](#setbuttonstyle) zamiast `SetButtons`. `SetButtonStyle` jest najbardziej przydatna, gdy chcesz zmienić styl przycisku w czasie wykonywania.  
  
 Aby przypisać tekst wyświetlany na przycisku, należy wywołać [GetButtonText](#getbuttontext) można pobrać tekst wyświetlany na przycisku, a następnie wywołać [SetButtonText](#setbuttontext) można ustawić tekst.  
  
 Aby utworzyć przycisk pole wyboru, należy przypisać mu styl **TBBS_CHECKBOX** lub użyj `CCmdUI` obiektu `SetCheck` funkcji członkowskiej we `ON_UPDATE_COMMAND_UI` obsługi. Wywoływanie `SetCheck` włącza przycisk w przycisk pola wyboru. Przekaż `SetCheck` argumentu o wartości 0 nie jest zaznaczona, 1 dla zaznaczone lub 2 dla nieokreślony.  
  
 Aby utworzyć przycisk radiowy, należy wywołać [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektu [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) funkcji członkowskiej z `ON_UPDATE_COMMAND_UI` obsługi. Przekaż `SetRadio` argument 0 niezaznaczone lub niezerowe dla zaznaczone. Aby zapewnić zachowanie wykluczają się wzajemnie grupie opcji, należy skonfigurować `ON_UPDATE_COMMAND_UI` programy obsługi dla wszystkich przycisków w grupie.  
  
 Aby uzyskać więcej informacji na temat używania `CToolBar`, zapoznaj się z artykułem [MFC — implementacja paska narzędzi](../../mfc/mfc-toolbar-implementation.md) i [techniczna 31 Uwaga: paski sterowania](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar —](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex  
 Ta funkcja członkowska zwraca indeks pierwszego przycisku paska narzędzi, zaczynając od pozycji 0, którego identyfikator polecenia jest zgodna `nIDFind`.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFind`  
 Identyfikator polecenia przycisku paska narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks przycisku lub -1, jeśli żaden przycisk nie uzyskał identyfikator danego polecenia.  
  
##  <a name="create"></a>  CToolBar::Create  
 Ta funkcja członkowska tworzy pasek narzędzi (okno podrzędne) systemu Windows i kojarzy ją z `CToolBar` obiektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do okna, który jest elementem nadrzędnym w pasku narzędzi.  
  
 `dwStyle`  
 Styl toolbar. Style dodatkowych narzędzi obsługiwane są następujące:  
  
- `CBRS_TOP` Pasek sterowania jest u góry okna ramki.  
  
- `CBRS_BOTTOM` Pasek sterowania jest w dolnej części okna ramki.  
  
- `CBRS_NOALIGN` Pasek sterowania nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.  
  
- `CBRS_TOOLTIPS` Pasek sterowania Wyświetla etykietki narzędzi.  
  
- **Cbrs_size_dynamic —** pasek sterowania jest dynamiczny.  
  
- **Cbrs_size_fixed —** pasek sterowania został rozwiązany.  
  
- **CBRS_FLOATING** zmiennoprzecinkową jest pasek sterowania.  
  
- `CBRS_FLYBY` Pasek stanu wyświetla informacje o przycisku.  
  
- **CBRS_HIDE_INPLACE** pasek sterowania jest niewidoczny dla użytkownika.  
  
 `nID`  
 Identyfikator paska narzędzi okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia również wysokość paska narzędzi do wartości domyślnej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>  CToolBar::CreateEx  
 Wywołanie tej funkcji do tworzenia paska narzędzi (okno podrzędne) systemu Windows i skojarzyć go z `CToolBar` obiektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,  
    CRect rcBorders = CRect(
    0, 
    0, 
    0, 
    0), 
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do okna, który jest elementem nadrzędnym w pasku narzędzi.  
  
 `dwCtrlStyle`  
 Dodatkowe style w celu utworzenia osadzonego [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) obiektu. Domyślnie ta wartość jest równa **TBSTYLE_FLAT**. Aby uzyskać pełną listę narzędzi style, zobacz `dwStyle`.  
  
 `dwStyle`  
 Styl toolbar. Zobacz [formantu paska narzędzi oraz style przycisku](http://msdn.microsoft.com/library/windows/desktop/bb760439) w zestawie SDK systemu Windows lista odpowiednie style.  
  
 *rcBorders*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który definiuje szerokość obramowania okna narzędzi. Te granice są ustawioną 0,0,0,0 domyślnie, powodując w oknie narzędzi z bez obramowania.  
  
 `nID`  
 Identyfikator paska narzędzi okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia również wysokość paska narzędzi do wartości domyślnej.  
  
 Użyj `CreateEx`, zamiast [Utwórz](#create)w przypadku niektórych style musi być obecny podczas tworzenia formantu paska narzędzi osadzony. Na przykład ustawić `dwCtrlStyle` do **TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT** można utworzyć paska narzędzi podobny paski narzędzi programu Internet Explorer 4.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>  CToolBar::CToolBar  
 Konstruuje funkcji członkowskiej `CToolBar` obiektu i ustawia domyślne rozmiary.  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [Utwórz](#create) funkcji członkowskiej można utworzyć okna narzędzi.  
  
##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo  
 Ta funkcja elementu członkowskiego pobiera identyfikator formantu, stylu i indeks obrazu przycisku paska narzędzi lub separator w lokalizacji określonej przez *nIndex.*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks przycisku paska narzędzi lub separatora, którego informacje ma być pobrana.  
  
 `nID`  
 Odwołanie do **UINT** który ma ustawioną identyfikator polecenia przycisku.  
  
 `nStyle`  
 Odwołanie do **UINT** który ustawiono styl przycisku.  
  
 `iImage`  
 Odwołanie do liczba całkowita, która ma ustawioną wartość indeksu obrazu przycisku w mapy bitowej.  
  
### <a name="remarks"></a>Uwagi  
 Wartości te są przypisane do zmiennych odwołuje się `nID`, `nStyle`, i `iImage`. Indeks obrazu jest położenia obrazu w zawierający obrazy dla przycisków paska mapy bitowej. Pierwszy obraz jest na pozycji 0.  
  
 Jeśli `nIndex` Określa separator, `iImage` ustawiono szerokość separatora w pikselach.  
  
##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle  
 Wywołanie tej funkcji Członkowskich pobrać styl przycisku lub separatora na pasku narzędzi.  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks styl przycisku lub separatora narzędzi do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Styl przycisku lub separatora określonego przez `nIndex`.  
  
### <a name="remarks"></a>Uwagi  
 Styl przycisku określa wygląd przycisku i sposobu odpowiedzi na dane wejściowe użytkownika. Zobacz [SetButtonStyle](#setbuttonstyle) przykłady style przycisku.  
  
##  <a name="getbuttontext"></a>  CToolBar::GetButtonText  
 Wywołanie tej funkcji Członkowskich pobrać tekst wyświetlany na przycisku.  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks tekstu do pobrania.  
  
 `rString`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który będzie zawierać tekst, który ma zostać pobrane.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt zawierający tekst przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Drugi formularz tego elementu członkowskiego funkcji wypełnienia `CString` obiekt z ciągu tekstowego.  
  
##  <a name="getitemid"></a>  CToolBar::GetItemID  
 Ta funkcja elementu członkowskiego zwraca identyfikator polecenia przycisku lub separatora określonego przez `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu o identyfikatorze ma być pobrana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia przycisku lub separatora określonego przez `nIndex`.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca separatorów **ID_SEPARATOR**.  
  
##  <a name="getitemrect"></a>  CToolBar::GetItemRect  
 Wypełnia tę funkcję elementu członkowskiego `RECT` struktury, którego adres znajduje się w `lpRect` z współrzędne przycisku lub separatora określonego przez `nIndex`.  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks elementu (przycisk lub separatora) współrzędnych prostokąta, których mają zostać pobrane.  
  
 `lpRect`  
 Adres [RECT](../../mfc/reference/rect-structure1.md) struktury, która będzie zawierać współrzędne elementu.  
  
### <a name="remarks"></a>Uwagi  
 Współrzędne są podawane w pikselach względem lewego górnego rogu paska narzędzi.  
  
 Użyj `GetItemRect` by uzyskać współrzędne separator, który chcesz zastąpić pola kombi lub inny formant.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CToolBar::SetSizes](#setsizes).  
  
##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl  
 Ta funkcja członkowska umożliwia bezpośredni dostęp do podstawowych formant.  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CToolBarCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `GetToolBarCtrl` korzystanie z funkcji formantu typowych narzędzi systemu Windows i korzystać z obsługi [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) zapewnia pasków narzędzi.  
  
 Aby uzyskać więcej informacji na temat używanie formantów wspólnych, zobacz artykuł [formanty](../../mfc/controls-mfc.md) i [formanty standardowe](http://msdn.microsoft.com/library/windows/desktop/bb775493) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap  
 Wywołanie tej funkcji Członkowskich załadować mapy bitowej określony przez `lpszResourceName` lub `nIDResource`.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Wskaźnik do nazwy zasobu mapy bitowej do załadowania.  
  
 `nIDResource`  
 Identyfikator zasobu mapy bitowej do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Mapa bitowa powinna zawierać jednego obrazu dla przycisku paska narzędzi. Jeśli obrazy nie są rozmiaru standard (16 pikseli szerokości i wysokości 15 pikseli), wywołanie [SetSizes](#setsizes) rozmiar przycisku i obrazów.  
  
> [!WARNING]
> `CToolBar` obsługuje map bitowych z maksymalnie 16 kolorów. Podczas ładowania obrazu w edytorze paska narzędzi, Visual Studio automatycznie konwertuje obraz mapy bitowej 16 kolorów, jeśli to konieczne i wyświetla ostrzeżenie, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (przy użyciu edytora zewnętrznego do edycji obraz), może być nieoczekiwane zachowanie aplikacji.  
  
##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar  
 Wywołanie tej funkcji Członkowskich załadować narzędzi określony przez `lpszResourceName` lub `nIDResource`.  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Wskaźnik do nazwy zasobu paska narzędzi do załadowania.  
  
 `nIDResource`  
 Identyfikator zasobu paska narzędzi do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [paska narzędzi edytora](../../windows/toolbar-editor.md) w Aby uzyskać więcej informacji na temat tworzenia zasobu paska narzędzi.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CToolBar::CreateEx](#createex).  
  
##  <a name="setbitmap"></a>  CToolBar::SetBitmap  
 Wywołanie tej funkcji członkowskich można ustawić obraz mapy bitowej na pasku narzędzi.  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>Parametry  
 *hbmImageWell*  
 Dojście do mapy bitowej, który jest skojarzony z paska narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład wywołać `SetBitmap` zmiany obrazu mapy bitowej, po użytkownik wykona akcję w dokumencie, który zmienia Akcja przycisku.  
  
##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo  
 Wywołanie tej funkcji elementu członkowskiego, aby ustawić identyfikator polecenia, stylu i numer obrazu przycisku.  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks przycisku lub separatora, dla którego ma być utworzony informacji.  
  
 `nID`  
 Wartość, do którego jest ustawiony identyfikator polecenia przycisku.  
  
 `nStyle`  
 Styl przycisku Nowy. Obsługiwane są następujące style przycisku:  
  
- **TBBS_BUTTON** przycisk standardowe (ustawienie domyślne)  
  
- **TBBS_SEPARATOR** separatora  
  
- **TBBS_CHECKBOX** przycisk pole wyboru automatycznie  
  
- **TBBS_GROUP** oznacza początek grupy przycisków  
  
- **TBBS_CHECKGROUP** oznacza początek grupy przycisków pola wyboru  
  
- **TBBS_DROPDOWN** tworzy przycisk listy rozwijanej.  
  
- **TBBS_AUTOSIZE** szerokość przycisku będzie obliczana na podstawie na tekst przycisku, a nie na rozmiar obrazu.  
  
- **TBBS_NOPREFIX** tekst przycisku nie będzie miał prefiks akceleratora skojarzonych z nim.  
  
 `iImage`  
 Nowy indeks obrazu przycisku w mapy bitowej.  
  
### <a name="remarks"></a>Uwagi  
 Separatorami, które mają styl **TBBS_SEPARATOR**, ta funkcja Ustawia szerokość separatora w pikselach do wartości przechowywanej w `iImage`.  
  
> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu `nStyle` parametru, ale ponieważ Stany przycisku są kontrolowane przez [on_update_command_ui —](message-map-macros-mfc.md#on_update_command_ui) obsługi, o podać można ustawić za pomocą `SetButtonInfo` zostaną utracone podczas następnej bezczynności przetwarzanie. Zobacz [jak obiekty interfejsu użytkownika aktualizacji](../../mfc/how-to-update-user-interface-objects.md) i [TN031: paski sterowania](../../mfc/tn031-control-bars.md) Aby uzyskać więcej informacji.  
  
 Informacje dotyczące bitmapy i przyciski, zobacz [ctoolbar —](../../mfc/reference/ctoolbar-class.md) Przegląd i [CToolBar::LoadBitmap](#loadbitmap).  
  
##  <a name="setbuttons"></a>  CToolBar::SetButtons  
 Ta funkcja członkowska Ustawia identyfikator polecenia przycisku paska narzędzi do wartości określonej przez odpowiadający mu element w tablicy `lpIDArray`.  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpIDArray`  
 Wskaźnik do tablicy identyfikatorów poleceń. Można ją **NULL** przydzielić pusty przycisków.  
  
 `nIDCount`  
 Liczba elementów w tablicy wskazywana przez `lpIDArray`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element tablicy ma wartość **ID_SEPARATOR**, separator jest tworzony w odpowiednim miejscu paska narzędzi. Ta funkcja także ustawia styl każdego przycisku **TBBS_BUTTON** i styl każdego separatora **TBBS_SEPARATOR**i przypisuje indeks obrazu do każdego przycisku. Indeks obrazu Określa położenie obrazu przycisku w mapy bitowej.  
  
 Nie trzeba przeprowadzać konta dla separatorów w mapie bitowej, ponieważ ta funkcja nie ma przypisanego indeksów obrazu dla separatorów. Jeśli pasek narzędzi z przyciskami na pozycji 0, 1 i 3 oraz separatora na pozycji nr 2, obrazów na pozycji 0, 1 i 2 w Twojej mapy bitowej są przypisane do przycisków w pozycji 0, 1 i 3, odpowiednio.  
  
 Jeśli `lpIDArray` jest **NULL**, ta funkcja przydziela miejsce dla liczby określone przez elementy `nIDCount`. Użyj [SetButtonInfo](#setbuttoninfo) można ustawić atrybutów każdego elementu.  
  
##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle  
 Wywołanie funkcji członkowskiej na ustawienie stylu przycisku lub separatora lub do grupy przycisków.  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks przycisku lub separatora, którego informacje ma być utworzony.  
  
 `nStyle`  
 Styl przycisku. Obsługiwane są następujące style przycisku:  
  
- **TBBS_BUTTON** przycisk standardowe (ustawienie domyślne)  
  
- **TBBS_SEPARATOR** separatora  
  
- **TBBS_CHECKBOX** przycisk pole wyboru automatycznie  
  
- **TBBS_GROUP** oznacza początek grupy przycisków  
  
- **TBBS_CHECKGROUP** oznacza początek grupy przycisków pola wyboru  
  
- **TBBS_DROPDOWN** tworzy przycisk listy rozwijanej  
  
- **TBBS_AUTOSIZE** szerokość przycisku będzie obliczana na podstawie na tekst przycisku, a nie na rozmiar obrazu  
  
- **TBBS_NOPREFIX** tekst przycisku nie będzie miał prefiks akceleratora skojarzonych z nim  
  
### <a name="remarks"></a>Uwagi  
 Styl przycisku określa wygląd przycisku i sposobu odpowiedzi na dane wejściowe użytkownika.  
  
 Przed wywołaniem `SetButtonStyle`, wywołaj [GetButtonStyle](#getbuttonstyle) funkcji członkowskiej pobrać styl przycisku lub separatora.  
  
> [!NOTE]
>  Można również ustawić Stany przycisku przy użyciu `nStyle` parametru, ale ponieważ Stany przycisku są kontrolowane przez [on_update_command_ui —](message-map-macros-mfc.md#on_update_command_ui) obsługi, o podać można ustawić za pomocą `SetButtonStyle` zostaną utracone podczas następnej bezczynności przetwarzanie. Zobacz [jak obiekty interfejsu użytkownika aktualizacji](../../mfc/how-to-update-user-interface-objects.md) i [TN031: paski sterowania](../../mfc/tn031-control-bars.md) Aby uzyskać więcej informacji.  
  
##  <a name="setbuttontext"></a>  CToolBar::SetButtonText  
 Wywołanie tej funkcji, aby ustawić tekst na przycisku.  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks przycisk, którego tekst jest do ustawienia.  
  
 `lpszText`  
 Wskazuje tekst, który ma być ustawiony na przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CToolBar::GetToolBarCtrl](#gettoolbarctrl).  
  
##  <a name="setheight"></a>  CToolBar::SetHeight  
 Ta funkcja członkowska Ustawia wysokość paska narzędzi wartość w pikselach, określona w `cyHeight`.  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `cyHeight`  
 Wysokość w pikselach paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu [SetSizes](#setsizes), użyj funkcji członkowskiej, aby przesłonić wysokość standardowym pasku narzędzi. Gdy wysokość jest za mały, przyciski zostaną przycięte u dołu.  
  
 Jeśli ta funkcja nie jest wywoływana, platformę używa rozmiaru przycisku do ustalenia wysokość paska narzędzi.  
  
##  <a name="setsizes"></a>  CToolBar::SetSizes  
 Wywołanie tej funkcji Członkowskich ustawioną przycisków paska narzędzi rozmiar w pikselach, określona w *sizeButton*.  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>Parametry  
 *sizeButton*  
 Rozmiar w pikselach każdego przycisku.  
  
 `sizeImage`  
 Rozmiar każdego obrazu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 `sizeImage` Parametr może zawierać rozmiar w pikselach obrazów w pasku narzędzi mapy bitowej. Wymiary w *sizeButton* musi być wystarczająca do przechowywania obrazu oraz 7 pikseli dodatkowe szerokości i 6 pikseli dodatkowe w wysokości. Ta funkcja także Ustawia wysokość paska narzędzi do przycisków.  
  
 Wywołanie tej funkcji Członkowskich tylko dla pasków narzędzi, które nie są zgodne *Windows interfejsu wskazówki dotyczące projektowania oprogramowania* zalecenia dotyczące rozmiarów button i image.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLBARS](../../visual-cpp-samples.md)   
 [DLGCBR32 próbki MFC](../../visual-cpp-samples.md)   
 [Przykładowe MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Ctoolbarctrl — klasa](../../mfc/reference/ctoolbarctrl-class.md)   
 [Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
