---
title: Cpropertysheet — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
dev_langs:
- C++
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7b49aba6ea5d2397baa0dc72f36b2693810fbeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cpropertysheet-class"></a>Cpropertysheet — klasa
Reprezentuje arkuszy właściwości, znanej także jako okna dialogowe kart.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPropertySheet : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Konstruuje `CPropertySheet` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertySheet::AddPage](#addpage)|Dodaje strony do arkusza właściwości.|  
|[CPropertySheet::Construct](#construct)|Konstruuje `CPropertySheet` obiektu.|  
|[CPropertySheet::Create](#create)|Wyświetla niemodalnego arkusza właściwości.|  
|[CPropertySheet::DoModal](#domodal)|Wyświetla modalny arkusz właściwości.|  
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Wskazuje, czy arkusz właściwości używa skumulowany lub przewijania.|  
|[CPropertySheet::EndDialog](#enddialog)|Kończy arkusza właściwości.|  
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Pobiera indeks strony aktywnego arkusza właściwości.|  
|[CPropertySheet::GetActivePage](#getactivepage)|Zwraca obiekt aktywnej strony.|  
|[CPropertySheet::GetPage](#getpage)|Pobiera wskaźnik do określonej strony.|  
|[CPropertySheet::GetPageCount](#getpagecount)|Pobiera liczbę stron w arkuszu właściwości.|  
|[CPropertySheet::GetPageIndex](#getpageindex)|Pobiera indeks określonej strony arkusza właściwości.|  
|[CPropertySheet::GetTabControl](#gettabcontrol)|Pobiera wskaźnik do formantu karty.|  
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.|  
|[CPropertySheet::OnInitDialog](#oninitdialog)|Należy przesłonić, aby rozszerzyć inicjowanie arkusza właściwości.|  
|[CPropertySheet::PressButton](#pressbutton)|Symuluje wybór określonego przycisku w arkuszu właściwości.|  
|[CPropertySheet::RemovePage](#removepage)|Usuwa stronę arkusza właściwości.|  
|[CPropertySheet::SetActivePage](#setactivepage)|Programowo ustawia obiekt aktywnej strony.|  
|[CPropertySheet::SetFinishText](#setfinishtext)|Ustawia tekst dla przycisku.|  
|[CPropertySheet::SetTitle](#settitle)|Ustawia tytuł arkusza właściwości.|  
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Włącza przyciski kreatora.|  
|[CPropertySheet::SetWizardMode](#setwizardmode)|Włącza tryb kreatora.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) struktury. Zapewnia dostęp do podstawowych właściwości arkusza parametrów.|  
  
## <a name="remarks"></a>Uwagi  
 Arkusz właściwości składa się z `CPropertySheet` obiektu i co najmniej jeden [cpropertypage —](../../mfc/reference/cpropertypage-class.md) obiektów. Platformę arkusz właściwości będzie wyświetlany jako okno z zestawem kartę indeksy i obszar zawierający aktualnie wybranej strony. Użytkownik przechodzi do określonej strony przy użyciu odpowiedniej karty.  
  
 `CPropertySheet` zapewnia obsługę rozszerzonych [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546) wprowadzone w systemie struktury [!INCLUDE[Win98](../../mfc/reference/includes/win98_md.md)] i 2000 systemu Windows NT. Struktura zawiera dodatkowe flagi i elementów członkowskich, które obsługują przy użyciu mapy bitowej tła "znak wodny".  
  
 Aby automatycznie wyświetlać tych nowych obrazów w obiekt arkusza właściwości, należy przekazać prawidłowe wartości dla obrazów mapy bitowej i palety w wywołaniu [CPropertySheet::Construct](#construct) lub [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 Mimo że `CPropertySheet` nie pochodzi od [cdialog —](../../mfc/reference/cdialog-class.md), zarządzanie `CPropertySheet` obiekt jest takie jak zarządzanie `CDialog` obiektu. Na przykład tworzenie arkusz właściwości wymaga konstrukcja dwie części: wywołanie konstruktora, a następnie wywołać [DoModal](#domodal) dla modalny arkusz właściwości lub [Utwórz](#create) dla niemodalnego arkusza właściwości. `CPropertySheet` ma dwa typy z konstruktorów: [CPropertySheet::Construct](#construct) i [CPropertySheet::CPropertySheet](#cpropertysheet).  
  
 Podczas konstruowania `CPropertySheet` obiekt niektóre [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) może spowodować wyjątek pierwszej szansy występuje. Wynika to z próby Zmień styl arkusza właściwości, przed utworzeniem arkusz systemu. Aby uniknąć tego wyjątku, upewnij się, ustaw następujące style, podczas tworzenia Twojej `CPropertySheet`:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD —  
  
-   WS_TABSTOP —  
  
 Następujące style są opcjonalne, a nie spowoduje wyjątkach pierwszej szansy:  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN —  
  
 Inne `Window Styles` są zabronione i nie należy włączać.  
  
 Wymiana danych między `CPropertySheet` obiektu i obiekt zewnętrzny jest podobny do wymiany danych z `CDialog` obiektu. Istotną różnicą jest ustawienia arkusza właściwości są zwykle zmienne Członkowskie `CPropertyPage` obiektów, a nie z `CPropertySheet` samego obiektu.  
  
 Można utworzyć typu o nazwie kreatora, który składa się z arkusza właściwości z sekwencją strony właściwości, które prowadzą użytkownika przez kroki operacji, takich jak Konfigurowanie urządzenia lub tworzenia biuletynu okno dialogowe kartę. W oknie dialogowym kartę typu Kreator strony właściwości nie ma karty, a tylko jedna właściwość strona jest widoczna w czasie. Ponadto zamiast **OK** i **Zastosuj teraz** przycisków, okno dialogowe Kreator typ ma **ponownie** przycisku **dalej** lub  **Zakończ** przycisku **anulować** przycisk, a **pomocy** przycisku.  
  
 Aby utworzyć okno dialogowe Typ kreatora, wykonaj te same czynności, które należy wykonać, aby utworzyć arkusz właściwości standardowych, ale wywołanie [SetWizardMode](#setwizardmode) przed wywołaniem [DoModal](#domodal). Aby włączyć przyciski kreatora, należy wywołać [SetWizardButtons](#setwizardbuttons), aby dostosować wygląd i funkcji przy użyciu flagi. Aby włączyć **Zakończ** przycisku, należy wywołać [SetFinishText](#setfinishtext) po użytkownika akcja ma być wykonana na ostatniej stronie kreatora.  
  
 Aby uzyskać więcej informacji o sposobie używania `CPropertySheet` obiektów, zobacz artykuł [arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md). Również, zobacz artykuł bazy wiedzy Knowledge Base Q146916: Porada: tworzenie cpropertysheet niemodalny — przyciskami standardowa, a artykuł Q300606: Porada: projekt arkusza właściwości MFC o zmiennym rozmiarze.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPropertySheet`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdlgs.h  
  
##  <a name="addpage"></a>  CPropertySheet::AddPage  
 Dodaje podany strony z kartą po prawej stronie w arkuszu właściwości.  
  
```  
void AddPage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Wskazuje stronę do dodania do arkusza właściwości. Nie może być **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Dodaj arkusz właściwości w kolejności od lewej do prawej, w jakiej mają być wyświetlane strony.  
  
 `AddPage` dodaje [cpropertypage —](../../mfc/reference/cpropertypage-class.md#cpropertypage) do obiektu `CPropertySheet` obiekt do listy stron, ale nie powoduje utworzenia okna dla strony. Platformę odłoży Tworzenie okna dla strony, dopóki użytkownik wybierze tej strony.  
  
 Po dodaniu strony właściwości przy użyciu `AddPage`, `CPropertySheet` jest nadrzędny `CPropertyPage`. Aby uzyskać dostęp do arkusza właściwości na stronie właściwości, należy wywołać [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).  
  
 Nie jest konieczne tworzenie okna arkusza właściwości do wywołania po upływie `AddPage`. Zazwyczaj należy wywołać `AddPage` przed wywołaniem [DoModal](#domodal) lub [Utwórz](#create).  
  
 Jeśli należy wywołać `AddPage` po wyświetleniu strony właściwości, wiersza kart będzie odzwierciedlać nowo dodanego strony.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]  
  
##  <a name="construct"></a>  CPropertySheet::Construct  
 Konstruuje `CPropertySheet` obiektu.  
  
```  
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
void Construct(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
void Construct(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCaption`  
 Identyfikator podpisu ma być używany dla tego arkusza właściwości.  
  
 `pParentWnd`  
 Wskaźnik do nadrzędnego okna arkusza właściwości. Jeśli **NULL**, okno nadrzędne będzie głównego okna aplikacji.  
  
 `iSelectPage`  
 Indeks strony, która będzie początkowo u góry. Domyślny jest pierwszą stroną dodane do arkusza.  
  
 `pszCaption`  
 Wskaźnik do ciąg zawierający podpis, który ma służyć do arkusza właściwości. Nie może być **NULL**.  
  
 `hbmWatermark`  
 Dojście do mapy bitowej znaku wodnego strony właściwości.  
  
 `hpalWatermark`  
 Dojście do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.  
  
 `hbmHeader`  
 Dojście do mapy bitowej nagłówka strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji członkowskiej w przypadku jednego z konstruktorów klas nie już została wywołana. Na przykład wywołać `Construct` po zadeklarować lub przydzielić tablice `CPropertySheet` obiektów. W przypadku tablic, należy wywołać `Construct` dla każdego elementu w tablicy.  
  
 Aby wyświetlić arkusz właściwości, należy wywołać [DoModal](#domodal) lub [Utwórz](#create). Ciąg znajdujący się w pierwszym parametrze zostaną umieszczone w pasku podpisu dla tego arkusza właściwości.  
  
 Można wyświetlać znaków wodnych i/lub nagłówek obrazy automatycznie, jeśli używasz trzeci lub czwarty prototypów `Construct`, wymienione powyżej, i podaj prawidłowe wartości dla `hbmWatermark`, `hpalWatermark`, i/lub `hbmHeader` parametrów.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, w przypadku okoliczności, w jakich spowodowałoby wywołanie `Construct`.  
  
 [!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]  
  
##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet  
 Konstruuje `CPropertySheet` obiektu.  
  
```  
CPropertySheet();

 
explicit CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
explicit CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd = NULL,  
    UINT iSelectPage = 0);

 
CPropertySheet(
    UINT nIDCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);

 
CPropertySheet(
    LPCTSTR pszCaption,  
    CWnd* pParentWnd,  
    UINT iSelectPage,  
    HBITMAP hbmWatermark,  
    HPALETTE hpalWatermark = NULL,  
    HBITMAP hbmHeader = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDCaption`  
 Identyfikator podpisu ma być używany dla tego arkusza właściwości.  
  
 `pParentWnd`  
 Punkty do nadrzędnego okna arkusza właściwości. Jeśli **NULL**, okno nadrzędne będzie głównego okna aplikacji.  
  
 `iSelectPage`  
 Indeks strony, która będzie początkowo u góry. Domyślny jest pierwszą stroną dodane do arkusza.  
  
 `pszCaption`  
 Wskazuje ciąg zawierający podpis, który ma służyć do arkusza właściwości. Nie może być **NULL**.  
  
 `hbmWatermark`  
 Dojście do mapy bitowej tła arkusza właściwości.  
  
 `hpalWatermark`  
 Dojście do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.  
  
 `hbmHeader`  
 Dojście do mapy bitowej nagłówka strony właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić arkusz właściwości, należy wywołać [DoModal](#domodal) lub [Utwórz](#create). Ciąg znajdujący się w pierwszym parametrze zostaną umieszczone w pasku podpisu dla tego arkusza właściwości.  
  
 Jeśli masz wiele parametrów (na przykład, jeśli używasz tablicy), użyj [skonstruować](#construct) zamiast `CPropertySheet`.  
  
 Można wyświetlać znaków wodnych i/lub nagłówek obrazy automatycznie, jeśli używasz trzeci lub czwarty prototypów `CPropertySheet`powyżej, i podaj prawidłowe wartości dla `hbmWatermark`, `hpalWatermark`, i/lub `hbmHeader` parametrów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]  
  
##  <a name="create"></a>  CPropertySheet::Create  
 Wyświetla niemodalnego arkusza właściwości.  
  
```  
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);  
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskazuje okno nadrzędne. Jeśli **NULL**, nadrzędny jest pulpitu.  
  
 `dwStyle`  
 Style okna arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 `dwExStyle`  
 Rozszerzone Style okna arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli arkusz właściwości jest tworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **Utwórz** może znajdować się w konstruktorze lub można ją wywołać po wywołaniu konstruktora.  
  
 Domyślny styl wyrażonych przez przekazanie -1 jako `dwStyle`, jest w rzeczywistości **ws_sysmenu —&#124;**`WS_POPUP`**&#124;ws_caption —&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_ WIDOCZNE**. Wartość domyślna rozszerzone style okna, wyrażonych przez przekazanie 0 jako `dwExStyle`, jest w rzeczywistości **ws_ex_dlgmodalframe —**.  
  
 **Utwórz** funkcji członkowskiej zwraca natychmiast po utworzeniu arkusza właściwości. Aby zniszczyć arkusza właściwości, należy wywołać [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).  
  
 Niemodalne arkusze właściwości wyświetlane w wyniku wywołania **Utwórz** nie mają przyciski OK, Anuluj Zastosuj teraz i pomoc, tak jak arkusze właściwości modalne. Żądany przycisków musi zostać utworzony przez użytkownika.  
  
 Aby wyświetlić modalny arkusz właściwości, należy wywołać [DoModal](#domodal) zamiast tego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]  
  
##  <a name="domodal"></a>  CPropertySheet::DoModal  
 Wyświetla modalny arkusz właściwości.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IDOK` lub `IDCANCEL` Jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie wartość 0 lub wartość-1. Jeśli arkusz właściwości została ustanowiona jako kreatora (zobacz [SetWizardMode](#setwizardmode)), `DoModal` zwraca albo `ID_WIZFINISH` lub `IDCANCEL`.  
  
### <a name="remarks"></a>Uwagi  
 Zwracana wartość odpowiada identyfikator formantu, który zamknął arkusz właściwości. Po powrocie z tej funkcji windows odpowiadający arkusz właściwości i wszystkie strony będzie został zlikwidowany. Samych obiektów będą nadal istnieć. Zazwyczaj pobierze dane z [cpropertypage —](../../mfc/reference/cpropertypage-class.md) obiektów po `DoModal` zwraca `IDOK`.  
  
 Aby wyświetlić niemodalnego arkusza właściwości, należy wywołać [Utwórz](#create) zamiast tego.  
  
 Strony właściwości jest tworzona na podstawie jego odpowiadający jej zasób okna dialogowego, może spowodować wyjątkach pierwszej szansy. Powoduje to na stronie właściwości zmiany stylu zasobu okna dialogowego do wymaganego stylu, przed utworzeniem strony. Ponieważ zasoby są zwykle tylko do odczytu, to powoduje zgłoszenie wyjątku. System obsługuje wyjątek i tworzy kopię zmodyfikowanych zasobów. W związku z tym można zignorować wyjątkach pierwszej szansy.  
  
> [!NOTE]
>  Ten wyjątek musi być obsługiwane przez system operacyjny, jeśli kompilacja model obsługi wyjątków asynchronicznych. Aby uzyskać więcej informacji o modelach obsługi wyjątków, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md). W takim przypadku nie jest zawijany wywołań `CPropertySheet::DoModal` z bloku try-catch C++ w którym catch obsługuje wszystkie wyjątki, na przykład `catch (...)`. Ten blok może obsłużyć wyjątek przeznaczony dla systemu operacyjnego i Przyczyna nieprzewidywalne zachowanie. Jednak można bezpiecznie korzystać wyjątek języka C++, obsługa z typów określonych wyjątków lub obsługa wyjątków strukturalnych, gdzie wyjątek naruszenie zasad dostępu jest przekazywana do systemu operacyjnego.  
  
 Aby uniknąć generowania tego wyjątku pierwszej szansy, użytkownik może ręcznie zagwarantować, że arkusz właściwości jest prawidłowy [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Należy określić następujące style arkusz właściwości:  
  
-   DS_3DLOOK  
  
-   DS_CONTROL  
  
-   WS_CHILD —  
  
-   WS_TABSTOP —  
  
 Możesz użyć następujących stylów opcjonalne bez powodowania wyjątkach pierwszej szansy:  
  
-   DS_SHELLFONT  
  
-   DS_LOCALEDIT  
  
-   WS_CLIPCHILDREN —  
  
 Wyłącz wszystkie style systemu Windows, ponieważ nie są zgodne z arkuszy właściwości. Rozszerzone style nie obejmuje tej porady. Ustawienie tych standardowe style odpowiednio będzie gwarantuje, że arkusza właściwości nie ma być modyfikowane i pozwoli uniknąć generowania wyjątkach pierwszej szansy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::AddPage](#addpage).  
  
##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs  
 Wskazuje, czy stosu wierszy kart w arkuszu właściwości.  
  
```  
void EnableStackedTabs(BOOL bStacked);
```  
  
### <a name="parameters"></a>Parametry  
 `bStacked`  
 Wskazuje, czy karty skumulowany są włączone w arkuszu właściwości. Wyłącz skumulowany wierszy tagów, ustawiając `bStacked` do **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie jeśli w arkuszu właściwości więcej kart niż mieści się w jednym wierszu w szerokość arkusza właściwości kart będą umieszczane w wielu wierszach. Aby użyć karty przewijania zamiast tabulatorów stosu, należy wywołać `EnableStackedTabs` z `bStacked` ustawioną **FALSE** przed wywołaniem [DoModal](#domodal) lub [Utwórz](#create).  
  
 Należy wywołać `EnableStackedTabs` podczas tworzenia modalne lub niemodalnego arkusza właściwości. Włączenie tego stylu w `CPropertySheet`-pochodnej klasy, zapisać program obsługi komunikatów dla `WM_CREATE`. W wersji przesłoniętych [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), wywołaj **EnableStackedTabs (FALSE)** przed wywołaniem klasy podstawowej implementacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]  
  
##  <a name="enddialog"></a>  CPropertySheet::EndDialog  
 Kończy arkusza właściwości.  
  
```  
void EndDialog(int nEndID);
```  
  
### <a name="parameters"></a>Parametry  
 *nEndID*  
 Identyfikator ma być używany jako wartość zwracaną przez arkusz właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę po naciśnięciu OK, Anuluj lub przycisk Zamknij. Za pośrednictwem wywołania tej funkcji członkowskiej, jeśli zdarzenie, które należy zamknąć arkusz właściwości.  
  
 Ta funkcja członkowska jest używana tylko z modalne okno dialogowe.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::PressButton](#pressbutton).  
  
##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex  
 Pobiera numer indeksu strony active okna arkusza właściwości, a następnie używa zwróconych numer indeksu jako parametr `GetPage`.  
  
```  
int GetActiveIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer indeksu aktywnej strony.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage  
 Pobiera okna arkusza właściwości aktywnej strony.  
  
```  
CPropertyPage* GetActivePage() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do aktywnej strony.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska umożliwia wykonanie akcji na stronie aktywne.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]  
  
##  <a name="getpage"></a>  CPropertySheet::GetPage  
 Zwraca wskaźnik do określonej strony w tym arkuszu właściwości.  
  
```  
CPropertyPage* GetPage(int nPage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPage`  
 Indeks żądanej strony, zaczynając od 0. Musi być między 0 a mniejszy niż liczba stron w arkuszu właściwości włącznie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strony odpowiadający `nPage` parametru.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount  
 Określa liczbę stron w arkuszu właściwości.  
  
```  
int GetPageCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba stron w arkuszu właściwości.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).  
  
##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex  
 Pobiera numer indeksu określonej strony w arkuszu właściwości.  
  
```  
int GetPageIndex(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Wskazuje stronę z indeksu, który ma zostać odnaleziona. Nie może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Numer indeksu strony.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład używasz `GetPageIndex` można uzyskać indeksu strony, aby można było używać [SetActivePage](#setactivepage) lub [GetPage](#getpage).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl  
 Pobiera wskaźnik do formantu karty zrobienia czegoś specyficzne dla formantu karty (oznacza to, aby użyć dowolnego z interfejsów API w [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).  
  
```  
CTabCtrl* GetTabControl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do formantu karty.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład można wywołać funkcji członkowskiej, jeśli chcesz dodać map bitowych na poszczególnych kartach podczas inicjowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]  
  
##  <a name="m_psh"></a>  CPropertySheet::m_psh  
 Struktura, której członkowie przechowywania właściwości [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546).  
  
### <a name="remarks"></a>Uwagi  
 Ta struktura jest używana do zainicjowania wygląd arkusza właściwości po go jest tworzony, ale przed wyświetleniem z [DoModal](#domodal) funkcję elementu członkowskiego. Na przykład ustawić `dwSize` członkiem `m_psh` rozmiar ma arkusza właściwości, aby mieć.  
  
 Więcej informacji dotyczących tej struktury, w tym listę jej członków, zobacz **PROPSHEETHEADER** w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]  
  
##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect  
 Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.  
  
```  
void MapDialogRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera okno dialogowe koordynuje do skonwertowania.  
  
### <a name="remarks"></a>Uwagi  
 Okno dialogowe jednostki są wyrażony w postaci bieżące okno dialogowe podstawowa jednostka pochodną średnia wysokość i szerokość znaków czcionki używanej w tekście okno dialogowe. Jedną jednostkę pozioma jest jedna czwarta jednostkę szerokości base okno dialogowe i jedną jednostkę pionową jest ósmego jednej jednostki podstawowej wysokość okno dialogowe.  
  
 [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) systemu Windows funkcja zwraca informacje o rozmiarze czcionki systemu, ale można określić inną czcionkę dla każdego arkusza właściwości, jeśli używasz **DS_SETFONT** stylu w Plik definicji zasobu. [MapDialogRect](http://msdn.microsoft.com/library/windows/desktop/ms645502) funkcji systemu Windows, opisane w zestawie SDK systemu Windows używa odpowiednią czcionkę dla tego okna dialogowego.  
  
 `MapDialogRect` Funkcji członkowskiej zastępuje jednostki okno dialogowe `lpRect` z ekranu jednostki (w pikselach), dzięki czemu prostokąt umożliwia tworzenie okna dialogowego lub ustaw kontrolkę w polu.  
  
##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog  
 Zastąpienia, aby rozszerzyć inicjowanie arkusza właściwości.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa, czy aplikacja ma fokus wprowadzania formantów w arkuszu właściwości. Jeśli **OnInitDialog** zwraca różną od zera, system Windows konfiguruje fokus wprowadzania pierwszą kontrolkę w arkuszu właściwości. Aplikacja może zwrócić 0 tylko wtedy, gdy fokus wprowadzania została jawnie ustawiona do formantów w arkuszu właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana w odpowiedzi na **WM_INITDIALOG** wiadomości. Ten komunikat jest wysyłany do arkusza właściwości podczas [Utwórz](#create) lub [DoModal](#domodal) wywołań, które występują bezpośrednio przed wyświetleniem arkusza właściwości.  
  
 Przesłonić tę funkcję elementu członkowskiego, jeśli zachodzi potrzeba wykonania specjalnego przetwarzania, po zainicjowaniu arkusza właściwości. W wersji przesłonięte, najpierw wywołaj klasę bazową `OnInitDialog` , ale pominąć jego wartości zwracanej. Zwykle zwróci **TRUE** z funkcji zastąpionym elementem członkowskim.  
  
 Nie trzeba wpisu mapy komunikatów dla tej funkcji Członkowskich.  
  
##  <a name="pressbutton"></a>  CPropertySheet::PressButton  
 Symuluje wybór określonego przycisku w arkuszu właściwości.  
  
```  
void PressButton(int nButton);
```  
  
### <a name="parameters"></a>Parametry  
 `nButton`  
 nButton: identyfikuje przycisk jest naciśnięty. Ten parametr może mieć jedną z następujących wartości:  
  
- **PSBTN_BACK** wybierze przycisk Wstecz.  
  
- **PSBTN_NEXT** wybierze przycisk Dalej.  
  
- **PSBTN_FINISH** wybierze przycisk Zakończ.  
  
- **PSBTN_OK** wybierze przycisk OK.  
  
- **PSBTN_APPLYNOW** wybierze przycisk Zastosuj teraz.  
  
- **PSBTN_CANCEL** wybierze przycisk Anuluj.  
  
- **PSBTN_HELP** wybierze przycisk Pomoc.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [PSM_PRESSBUTTON](http://msdn.microsoft.com/library/windows/desktop/bb774597) Aby uzyskać więcej informacji o komunikacie Pressbutton zestawu SDK systemu Windows.  
  
 Wywołanie `PressButton` nie będą wysyłały [PSN_APPLY](http://msdn.microsoft.com/library/windows/desktop/bb774552) powiadomienia na stronie właściwości do struktury. Aby wysłać powiadomienie, należy wywołać [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]  
  
##  <a name="removepage"></a>  CPropertySheet::RemovePage  
 Usuwa stronę arkusz właściwości i niszczy okno skojarzone.  
  
```  
void RemovePage(CPropertyPage* pPage);  
void RemovePage(int nPage);
```  
  
### <a name="parameters"></a>Parametry  
 `pPage`  
 Wskazuje strony, aby były usuwane z arkusza właściwości. Nie może być `NULL`.  
  
 `nPage`  
 Indeks strony do usunięcia. Musi być między 0 a mniejszy niż liczba stron w arkuszu właściwości włącznie.  
  
### <a name="remarks"></a>Uwagi  
 [Cpropertypage —](../../mfc/reference/cpropertypage-class.md) sam obiekt nie jest niszczony do właściciela `CPropertySheet` zamknięcia okna.  
  
##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage  
 Zmienia aktywnej strony.  
  
```  
BOOL SetActivePage(int nPage);  
BOOL SetActivePage(CPropertyPage* pPage);
```  
  
### <a name="parameters"></a>Parametry  
 `nPage`  
 Indeks strony, aby ustawić. Musi być między 0 a mniejszy niż liczba stron w arkuszu właściwości włącznie.  
  
 `pPage`  
 Wskazuje stronę, aby ustawić w arkuszu właściwości. Nie można go **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli arkusz właściwości jest aktywowany pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład użyć `SetActivePage` Jeśli akcja użytkownika na jednej stronie powinno powodować innej strony aktywnej strony.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).  
  
##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText  
 Ustawia tekst w przycisku polecenia.  
  
```  
void SetFinishText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Wskazuje tekst, który będzie wyświetlany na przycisku polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `SetFinishText` do wyświetlania tekstu na przycisku polecenia i Ukryj przycisków Następny i z powrotem po podaniu akcji na ostatniej stronie kreatora.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="settitle"></a>  CPropertySheet::SetTitle  
 Określa podpis arkusza właściwości (tekst wyświetlany w pasku tytułu okna ramki).  
  
```  
void SetTitle(
    LPCTSTR lpszText,  
    UINT nStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nStyle`  
 Określa styl tytuł arkusza właściwości. Styl należy określić w lokalizacji 0 lub jako **PSH_PROPTITLE**. Jeżeli styl jest ustawiony jako **PSH_PROPTITLE**, wyraz "Właściwości" pojawia się po tekście określony jako podpis. Na przykład wywołanie elementu `SetTitle`("Prosta" **PSH_PROPTITLE**) spowoduje podpis arkusz właściwości "Proste właściwości".  
  
 `lpszText`  
 Wskazuje tekst, który ma służyć jako podpisu na pasku tytułu arkusza właściwości.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie arkusz właściwości jest używany parametr podpisu w Konstruktorze arkusza właściwości.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]  
  
##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons  
 Włącza lub wyłącza przycisk Wstecz, dalej lub Zakończ kreator arkusza właściwości.  
  
```  
void SetWizardButtons(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Zestaw flag, które dostosować wygląd przycisków kreatora i funkcji. Ten parametr może mieć kombinację następujących wartości:  
  
- **PSWIZB_BACK** przycisk Wstecz  
  
- **PSWIZB_NEXT** obok przycisku  
  
- **PSWIZB_FINISH** przycisk Zakończ  
  
- **PSWIZB_DISABLEDFINISH** przycisku Zakończ wyłączone  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `SetWizardButtons` dopiero po otwarciu okna dialogowego; nie można wywołać `SetWizardButtons` przed wywołaniem [DoModal](#domodal). Zazwyczaj należy wywołać `SetWizardButtons` z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).  
  
 Jeśli chcesz zmienić tekst przycisku lub ukrywanie następnej i Wstecz raz przyciski użytkownika zostało zakończone kreatora wywołanie [SetFinishText](#setfinishtext). Należy zwrócić uwagę na to, czy ten sam przycisk jest udostępniany Zakończ i dalej. Można wyświetlić zakończenia lub przycisk Dalej w tym samym czasie, ale nie oba.  
  
### <a name="example"></a>Przykład  
 A `CPropertySheet` ma trzy Kreator strony właściwości: `CStylePage`, `CColorPage`, i `CShapePage`.  Poniższy fragment kodu przedstawia sposób włączania i wyłączania **ponownie** i **dalej** przycisków na stronie kreatora właściwości.  
  
 [!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]  
  
##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode  
 Określa stronę właściwości jako kreatora.  
  
```  
void SetWizardMode();
```  
  
### <a name="remarks"></a>Uwagi  
 Klucza cech Kreator strony właściwości jest użytkownika przechodzi dalej przy użyciu lub Zakończ, Utwórz kopię czy anulować przycisków zamiast tabulatorów.  
  
 Wywołanie `SetWizardMode` przed wywołaniem [DoModal](#domodal). Po wywołaniu metody `SetWizardMode`, `DoModal` zwróci albo **ID_WIZFINISH** (Jeśli użytkownik zostanie zamknięta z przycisku) lub **IDCANCEL**.  
  
 `SetWizardMode` Ustawia flagę PSH_WIZARD.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL1 próbki MFC](../../visual-cpp-samples.md)   
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Przykładowe MFC PROPDLG](../../visual-cpp-samples.md)   
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



