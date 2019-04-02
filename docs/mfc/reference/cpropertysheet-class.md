---
title: Cpropertysheet — klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: 0e5194a356684f2ff86d74a0ed1f37f332bcffeb
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781656"
---
# <a name="cpropertysheet-class"></a>Cpropertysheet — klasa

Przedstawia arkusze właściwości, znane również jako zakładki okna dialogowego.

## <a name="syntax"></a>Składnia

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name|Opis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Konstruuje `CPropertySheet` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Dodaje strony do arkusza właściwości.|
|[CPropertySheet::Construct](#construct)|Konstruuje `CPropertySheet` obiektu.|
|[CPropertySheet::Create](#create)|Wyświetla niemodalnego arkusza właściwości.|
|[CPropertySheet::DoModal](#domodal)|Wyświetla modalny arkusz właściwości.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Wskazuje, czy arkusz właściwości używa kart skumulowany lub przewijania.|
|[CPropertySheet::EndDialog](#enddialog)|Kończy arkusza właściwości.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Pobiera indeks aktywnej strony arkusza właściwości.|
|[CPropertySheet::GetActivePage](#getactivepage)|Zwraca obiekt stroną aktywną.|
|[CPropertySheet::GetPage](#getpage)|Pobiera wskaźnik do określonej strony.|
|[CPropertySheet::GetPageCount](#getpagecount)|Pobiera liczbę stron w arkuszu właściwości.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Pobiera indeks określonej strony arkusza właściwości.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Pobiera wskaźnik do formantu karty.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Należy przesłonić ten element, aby rozszerzyć inicjowanie arkusza właściwości.|
|[CPropertySheet::PressButton](#pressbutton)|Symuluje wybraną określonego przycisku w arkuszu właściwości.|
|[CPropertySheet::RemovePage](#removepage)|Usuwa strony z arkusza właściwości.|
|[CPropertySheet::SetActivePage](#setactivepage)|Programowe ustawia obiekt stroną aktywną.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Ustawia tekst dla przycisku Zakończ.|
|[CPropertySheet::SetTitle](#settitle)|Ustawia podpis arkusza właściwości.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Włącza przyciski kreatora.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Włącza tryb kreatora.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name|Opis|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Windows [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) struktury. Zapewnia dostęp do właściwości podstawowe parametry arkusza.|

## <a name="remarks"></a>Uwagi

Arkusz właściwości składa się z `CPropertySheet` obiektu i co najmniej jeden [CPropertyPage](../../mfc/reference/cpropertypage-class.md) obiektów. Struktura wyświetlany arkusz właściwości w oknie z zestawem karty indeksów i obszar, który zawiera aktualnie wybranej strony. Użytkownik przechodzi do określonej strony za pomocą odpowiedniej karty.

`CPropertySheet` zapewnia obsługę rozwiniętym okienku [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) struktury wprowadzone w programie Windows 98 i Windows NT Windows 2000. Struktura zawiera dodatkowe flagi i elementów członkowskich, które obsługuje tła mapy bitowej "limit".

Aby wyświetlić te nowe obrazy automatycznie obiekt arkusza właściwości, należy przekazać prawidłowe wartości dla obrazy mapy bitowej i palety w wywołaniu [CPropertySheet::Construct](#construct) lub [CPropertySheet::CPropertySheet](#cpropertysheet).

Mimo że `CPropertySheet` nie pochodzi od [CDialog](../../mfc/reference/cdialog-class.md), zarządzanie `CPropertySheet` obiekt jest takie jak zarządzanie `CDialog` obiektu. Na przykład utworzenie arkusza właściwości wymaga konstrukcji legalną dwuczęściową: wywołanie konstruktora, a następnie wywołaj [DoModal](#domodal) dla modalny arkusz właściwości lub [Utwórz](#create) dla niemodalnego arkusza właściwości. `CPropertySheet` ma dwa rodzaje konstruktorów: [CPropertySheet::Construct](#construct) i [CPropertySheet::CPropertySheet](#cpropertysheet).

Podczas konstruowania `CPropertySheet` obiektu niektóre [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) może spowodować wystąpienie wyjątku pierwszej szansy wystąpić. Wynika to z systemu, próbuje zmienić styl arkusza właściwości, przed utworzeniem arkusza. Aby uniknąć tego wyjątku, upewnij się, ustaw następujące style, podczas tworzenia usługi `CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Następujące style są opcjonalne i nie będzie powodował wyjątku pierwszej szansy:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Inne `Window Styles` są zabronione i nie należy włączać.

Wymiana danych między `CPropertySheet` obiektu i obiektu zewnętrznego przypomina wymiana danych z `CDialog` obiektu. Istotną różnicą jest ustawienia arkusza właściwości są zwykle zmienne Członkowskie `CPropertyPage` obiektów, a nie z `CPropertySheet` sam obiekt.

Można utworzyć typu zakładki okna dialogowego o nazwie Kreator, który składa się z arkusza właściwości, za pomocą sekwencji stron właściwości, które prowadzą użytkownika przez kroki operacji, takich jak Konfigurowanie urządzenia lub tworzenia biuletynu. W oknie dialogowym kartę Typ kreatora na stronach właściwości nie ma karty, a tylko jedną właściwość strona jest widoczna w danym momencie. Ponadto, zamiast **OK** i **Zastosuj teraz** ma typ kreatora zakładki okna dialogowego przyciski **ponownie** przycisku **dalej** lub  **Zakończ** przycisku **anulować** przycisku i **pomocy** przycisku.

Aby utworzyć okno dialogowe Typ kreatora, wykonaj te same czynności, które należy wykonać, Utwórz arkusz właściwości standardowych, ale wywołanie [SetWizardMode](#setwizardmode) przed wywołaniem [DoModal](#domodal). Aby włączyć przyciski kreatora, należy wywołać [SetWizardButtons](#setwizardbuttons), aby dostosować wygląd i funkcji przy użyciu flagi. Aby włączyć **Zakończ** przycisk, wywołaj [SetFinishText](#setfinishtext) po użytkownik podjęciu działania na ostatniej stronie kreatora.

Aby uzyskać więcej informacji o sposobie używania `CPropertySheet` obiektów, zobacz artykuł [arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Dodaje podany stronę z kartą po prawej stronie w arkuszu właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Wskazuje stronę, które mają zostać dodane do arkusza właściwości. Nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Dodawanie stron do arkusza właściwości w kolejności od lewej do prawej, w jakiej mają być wyświetlane.

`AddPage` dodaje [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) obiekt `CPropertySheet` obiektu użytkownika listę stron, ale nie powoduje utworzenia okno dla strony. Struktura odłoży tworzenia okna, strony, chyba że użytkownik wybierze tę stronę.

Po dodaniu strony właściwości przy użyciu `AddPage`, `CPropertySheet` jest elementem nadrzędnym `CPropertyPage`. Aby uzyskać dostęp do arkusza właściwości na stronie właściwości, należy wywołać [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Nie jest konieczne czekać do momentu utworzenia okna arkusza właściwości, aby wywołać `AddPage`. Zazwyczaj będzie wywoływać `AddPage` przed wywołaniem [DoModal](#domodal) lub [Utwórz](#create).

Jeśli wywołasz `AddPage` po wyświetleniu strony właściwości, wiersza kart będzie odzwierciedlać nowo dodane strony.

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

*nIDCaption*<br/>
Identyfikator podpis ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskaźnik do nadrzędnego okna arkusza właściwości. Jeśli ma wartość NULL, okno nadrzędne będzie głównego okna aplikacji.

*iSelectPage*<br/>
Indeks strony, która będzie początkowo u góry. Domyślna to pierwsza strona, które są dodawane do arkusza.

*pszCaption*<br/>
Wskaźnik do ciągu zawierającego podpis ma być używany dla arkusza właściwości. Nie może mieć wartości NULL.

*hbmWatermark*<br/>
Dojście do mapy bitowej znaku wodnego strony właściwości.

*hpalWatermark*<br/>
Dojście do palety znaku wodnego mapy bitowej i/lub mapy bitowej nagłówka.

*hbmHeader*<br/>
Dojście do mapy bitowej nagłówek strony właściwości.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, jeśli jeden z konstruktorów klas nie została już wywołana. Na przykład wywołać `Construct` podczas deklarowania lub przydzielania tablic `CPropertySheet` obiektów. W przypadku tablic, należy wywołać `Construct` dla każdego elementu w tablicy.

Aby wyświetlić arkusza właściwości, należy wywołać [DoModal](#domodal) lub [Utwórz](#create). Ciąg znajdujący się w pierwszym parametrze zostaną umieszczone na pasku podpisu dla arkusza właściwości.

Można wyświetlać obrazy znaku wodnego i/lub nagłówek automatycznie, jeśli używasz trzecia i czwarta prototypów `Construct`wymienionych powyżej i przekazujesz prawidłowe wartości dla *hbmWatermark*, *hpalWatermark* , i/lub *hbmHeader* parametrów.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, w obszarze należy okoliczności, w jakich wywoływałby `Construct`.

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

*nIDCaption*<br/>
Identyfikator podpis ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskazuje okno nadrzędne arkusza właściwości. Jeśli ma wartość NULL, okno nadrzędne będzie głównego okna aplikacji.

*iSelectPage*<br/>
Indeks strony, która będzie początkowo u góry. Domyślna to pierwsza strona, które są dodawane do arkusza.

*pszCaption*<br/>
Wskazuje ciąg zawierający podpis ma być używany dla arkusza właściwości. Nie może mieć wartości NULL.

*hbmWatermark*<br/>
Dojście do mapy bitowej tła arkusza właściwości.

*hpalWatermark*<br/>
Dojście do palety znaku wodnego mapy bitowej i/lub mapy bitowej nagłówka.

*hbmHeader*<br/>
Dojście do mapy bitowej nagłówek strony właściwości.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusza właściwości, należy wywołać [DoModal](#domodal) lub [Utwórz](#create). Ciąg znajdujący się w pierwszym parametrze zostaną umieszczone na pasku podpisu dla arkusza właściwości.

Jeśli masz wiele parametrów (na przykład, jeśli używasz tablicy), użyj [konstruowania](#construct) zamiast `CPropertySheet`.

Można wyświetlać obrazy znaku wodnego i/lub nagłówek automatycznie, jeśli używasz trzecia i czwarta prototypów `CPropertySheet`powyżej, i przekaż prawidłowe wartości *hbmWatermark*, *hpalWatermark*, i / lub *hbmHeader* parametrów.

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

*pParentWnd*<br/>
Wskazuje okna nadrzędnego. Jeśli ma wartość NULL, obiekt nadrzędny jest pulpitu.

*dwStyle*<br/>
Style okna ramowego dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Rozszerzone Style okna dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [rozszerzone Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli arkusz właściwości został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie `Create` może znajdować się w konstruktorze lub można też wywołać po wywołaniu konstruktora.

Domyślny styl wyrażona przez przekazanie wartości -1 jako *dwStyle*, jest faktycznie WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Wartość domyślna rozszerzone style okna, wyrażonych przez przekazanie 0 jako *dwExStyle*, jest faktycznie WS_EX_DLGMODALFRAME.

`Create` Funkcja elementu członkowskiego zwraca natychmiast po utworzeniu arkusza właściwości. Aby zniszczyć arkusza właściwości, należy wywołać [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Niemodalne arkusze właściwości wyświetlane w wyniku wywołania `Create` nie mają OK anulowania, Zastosuj teraz przyciski i uzyskać pomoc, tak jak arkusze właściwości modalne. Żądany przyciski musi zostać utworzona przez użytkownika.

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

IDOK lub IDCANCEL, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0 lub -1. Jeśli jako kreatora została ustanowiona arkusza właściwości (zobacz [SetWizardMode](#setwizardmode)), `DoModal` zwraca ID_WIZFINISH lub IDCANCEL.

### <a name="remarks"></a>Uwagi

Zwracana wartość odpowiada identyfikator formantu, który zamknięciu arkusza właściwości. Po powrocie z tej funkcji systemu windows, odpowiadający arkusza właściwości i wszystkie strony będzie została zniszczona. Same obiekty będą nadal istnieć. Zazwyczaj będzie odbierać dane z [CPropertyPage](../../mfc/reference/cpropertypage-class.md) obiektów po `DoModal` zwraca IDOK.

Aby wyświetlić niemodalnego arkusza właściwości, należy wywołać [Utwórz](#create) zamiast tego.

Strona właściwości jest tworzona z jego odpowiedniego zasobu okna dialogowego, może spowodować wyjątek pierwszego rzędu. Powoduje to na stronie właściwości, zmiana stylu zasobu okna dialogowego na wymagany styl, przed utworzeniem strony. Ponieważ zasoby są zwykle tylko do odczytu, powoduje wyjątek. System obsługuje wyjątek i tworzy kopię zmodyfikowanego zasobu. W związku z tym można zignorować wyjątku pierwszej szansy.

> [!NOTE]
>  Ten wyjątek musi być obsługiwane przez system operacyjny, jeśli kompilujesz z model obsługi wyjątków asynchronicznych. Aby uzyskać więcej informacji na temat modele obsługi wyjątków, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md). W tym przypadku nie jest zawijany wywołania `CPropertySheet::DoModal` za pomocą bloku try / catch języka C++ w którym catch obsługiwać wszystkie wyjątki, na przykład `catch (...)`. Ten blok będzie obsługiwać wyjątek przeznaczony dla systemu operacyjnego i przyczynę nieprzewidywalne zachowanie. Jednak można bezpiecznie użyć obsługi przy użyciu określonego wyjątku typów lub strukturalna Obsługa wyjątków, gdzie wyjątek naruszenie zasad dostępu jest przekazywana do systemu operacyjnego wyjątków C++.

Aby uniknąć generowania ten wyjątek pierwszego rzędu, można ręcznie gwarantuje, że arkusz właściwości ma poprawny [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles). Należy ustawić następujące style dla arkusza właściwości:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Bez powodowania wyjątku pierwszej szansy, można użyć następujących stylów opcjonalne:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Wyłącz wszystkie style Windows, ponieważ nie są zgodne z arkuszy właściwości. Ta informacja dotyczy rozszerzone style. Odpowiednie ustawienie te style standardowa gwarantuje, że arkusz właściwości nie ma być modyfikowane i pozwoli uniknąć generowania wyjątku pierwszej szansy.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Wskazuje, czy stosu wierszy kart w arkuszu właściwości.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStacked*<br/>
Wskazuje, czy włączono skumulowany karty w arkuszu właściwości. Wyłącz skumulowany wierszy tagów, ustawiając *bStacked* na wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie jeśli arkusz właściwości ma więcej kart niż mieści się w jednym wierszu w szerokość arkusza właściwości karty będą umieszczane w wielu wierszach. Aby użyć karty przewijania zamiast tabulatorów stosu, należy wywołać `EnableStackedTabs` z *bStacked* ustawiona na wartość FALSE przed wywołaniem [DoModal](#domodal) lub [Utwórz](#create).

Należy wywołać `EnableStackedTabs` podczas tworzenia modalne lub niemodalnego arkusza właściwości. Aby włączyć ten styl w `CPropertySheet`-pochodne klasy, pisanie programu obsługi komunikatów dla WM_CREATE. W wersji zgodnym z przesłoniętą [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), wywołaj `EnableStackedTabs( FALSE )` przed wywołaniem implementacji klasy podstawowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

Kończy arkusza właściwości.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID*<br/>
Identyfikator ma być używany jako wartość zwracaną przez arkusz właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, po naciśnięciu OK, Anuluj lub przycisk Zamknij. Wywołanie, że ta funkcja elementu członkowskiego, jeśli wystąpi zdarzenie, które należy zamknąć arkusza właściwości.

Ta funkcja elementu członkowskiego służy tylko przy użyciu modalne okno dialogowe.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::PressButton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Pobiera numer indeksu stroną aktywną okno Arkusz właściwości, a następnie używa zwracanego numer indeksu jako parametr dla `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer indeksu się stroną aktywną.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Pobiera stroną aktywną okno Arkusz właściwości.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnej strony.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego do wykonywania pewnych akcji na aktywnej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>  CPropertySheet::GetPage

Zwraca wskaźnik do określonej strony, w tym arkuszu właściwości.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Indeks żądanej strony, począwszy od 0. Musi należeć do zakresu od 0 i jeden mniejsza niż liczba stron w arkuszu właściwości, włącznie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strony odpowiadający *nPage* parametru.

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

*pPage*<br/>
Wskazuje stronę z indeksem, który ma zostać odnaleziona. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

Numer indeksu strony.

### <a name="remarks"></a>Uwagi

Na przykład można użyć `GetPageIndex` uzyskać indeks strony, aby można było używać [SetActivePage](#setactivepage) lub [GetPage](#getpage).

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Pobiera wskaźnik do formantu karty, aby zrobić coś, które są specyficzne dla formantu karty (oznacza to, aby użyć dowolnego z interfejsów API w [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do formantu karty.

### <a name="remarks"></a>Uwagi

Na przykład można wywołać tej funkcji elementu członkowskiego, jeśli chcesz dodać map bitowych na poszczególnych kartach podczas inicjowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Struktura, w której członkowie przechowywania właściwości [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2).

### <a name="remarks"></a>Uwagi

Ta struktura jest używana do zainicjowania wygląd arkusza właściwości po jest tworzony, ale przed wyświetleniem go z [DoModal](#domodal) funkcja elementu członkowskiego. Na przykład ustawić *niezerowego* członkiem `m_psh` rozmiar chcesz arkusza właściwości, aby mieć.

Aby uzyskać więcej informacji na temat tej struktury, w tym listę swoich elementów członkowskich Zobacz PROPSHEETHEADER w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Konwertuje jednostki okno dialogowe prostokąta jednostki ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera okno dialogowe służy do koordynowania ma zostać przekonwertowany.

### <a name="remarks"></a>Uwagi

Okno dialogowe jednostki są wyrażony w postaci bieżące okno dialogowe podstawowej jednostce pochodzi od średniej szerokości i wysokości znaków czcionkę tekstu okno dialogowe. Jedna jednostka poziomy to jedna czwarta jednostki podstawowej szerokość okno dialogowe, a jedna jednostka w pionie jest jednej ósmej jednostki podstawowej wysokość okno dialogowe.

[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) Windows funkcja zwraca informacje o rozmiarze do czcionki systemowej, ale można określić inną czcionkę dla każdego arkusza właściwości, jeśli używasz stylu DS_SETFONT w pliku definicji zasobu. [MapDialogRect](/windows/desktop/api/winuser/nf-winuser-mapdialogrect) Windows funkcji opisanych w zestawie Windows SDK używa odpowiednią czcionkę dla tego okna dialogowego.

`MapDialogRect` Funkcji składowej zastępuje jednostki okno dialogowe *lprect —* z ekranu jednostki (w pikselach), dzięki czemu prostokąt można utworzyć okno dialogowe lub położenie formantu w polu.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Zastępuje rozszerzyć inicjowanie arkusza właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Określa, czy aplikacja ma fokus wprowadzania do jednej z kontrolek w arkuszu właściwości. Jeśli `OnInitDialog` zwraca wartość różną od zera, Windows ustawia fokus wprowadzania pierwszą kontrolkę w arkuszu właściwości. Aplikacja może zwrócić 0, tylko wtedy, gdy ma jawnie ustawić fokusu wprowadzania do jednej z kontrolek w arkuszu właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana w odpowiedzi na wiadomość / / Złap. Ta wiadomość jest wysyłana do arkusza właściwości podczas [Utwórz](#create) lub [DoModal](#domodal) wywołania, które występują, natychmiast, przed wyświetleniem arkusza właściwości.

Ta funkcja elementu członkowskiego należy zastąpić, jeśli zachodzi potrzeba wykonania specjalnego przetwarzania, po zainicjowaniu arkusza właściwości. W wersji zastąpione, należy najpierw wywołać klasy bazowej `OnInitDialog` , ale nie brać pod uwagę jego zwracanej wartości. Z funkcji zgodnym z przesłoniętą składową, będzie zwykle zwraca wartość TRUE.

Nie trzeba się wpis mapy komunikatów dla tej funkcji elementu członkowskiego.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Symuluje wybraną określonego przycisku w arkuszu właściwości.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*nButton*<br/>
Nprzycisk: Określa przycisk aby zostać naciśnięte. Ten parametr może być jedną z następujących wartości:

- PSBTN_BACK wybierze przycisk Wstecz.

- PSBTN_NEXT wybierze przycisk Dalej.

- PSBTN_FINISH wybierze przycisk Zakończ.

- PSBTN_OK wybierze przycisk OK.

- PSBTN_APPLYNOW wybierze przycisk Zastosuj teraz.

- PSBTN_CANCEL wybierze przycisk Anuluj.

- PSBTN_HELP wybierze przycisk pomocy.

### <a name="remarks"></a>Uwagi

Zobacz [PSM_PRESSBUTTON](/windows/desktop/Controls/psm-pressbutton) Aby uzyskać więcej informacji na temat wiadomości Pressbutton zestaw SDK Windows.

Wywołanie `PressButton` nie będą wysyłały [PSN_APPLY](/windows/desktop/Controls/psn-apply) powiadomienia na stronie właściwości Framework. Aby wysłać powiadomienie, należy wywołać [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

Usuwa arkusz właściwości stronę i niszczy okno skojarzone.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Wskazuje stronę, która ma zostać usunięty z arkusza właściwości. Nie może mieć wartości NULL.

*nPage*<br/>
Indeks strony do usunięcia. Musi należeć do zakresu od 0 i jeden mniejsza niż liczba stron w arkuszu właściwości, włącznie.

### <a name="remarks"></a>Uwagi

[CPropertyPage](../../mfc/reference/cpropertypage-class.md) sam obiekt nie jest niszczony, aż do właściciela `CPropertySheet` okno zostanie zamknięte.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Zmienia aktywnej strony.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Indeks strony do ustawienia. Musi być między 0 a mniejszy niż liczba stron w arkuszu właściwości, włącznie.

*pPage*<br/>
Wskazuje stronę, aby ustawić w arkuszu właściwości. Nie może być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli arkusz właściwości jest aktywowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład użyć `SetActivePage` Jeśli akcja użytkownika na jednej stronie powinno spowodować innej strony stać się stroną aktywną.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Ustawia tekst w przycisku Zakończ.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Wskazuje tekst, który ma być wyświetlany na przycisku polecenia Zakończ.

### <a name="remarks"></a>Uwagi

Wywołaj `SetFinishText` do wyświetlania tekstu na przycisku polecenia Zakończ i ukryć przyciski Dalej i wstecz po użytkownik wykona akcję na ostatniej stronie kreatora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

Określa podpis arkusza właściwości (tekst wyświetlany na pasku tytułu okna ramki).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Określa styl tytuł arkusza właściwości. Styl musi być określona w lokalizacji 0 lub jako PSH_PROPTITLE. Jeśli styl jest ustawiony jako PSH_PROPTITLE, słowo "Właściwości" pojawia się po tekstem określonym jako podpis. Na przykład, wywołanie `SetTitle`("Simple", PSH_PROPTITLE) spowoduje podpis arkusz właściwości "Proste właściwości."

*lpszText*<br/>
Wskazuje tekst, który ma służyć jako podpis na pasku tytułu w arkuszu właściwości.

### <a name="remarks"></a>Uwagi

Domyślnie arkusz właściwości parametr podpis w Konstruktorze arkusza właściwości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

Włącza lub wyłącza przycisk Wstecz, dalej albo Zakończ w arkuszu właściwości kreatora.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Zestaw flag, umożliwiające dostosowanie funkcji i wygląd przycisków kreatora. Ten parametr może być kombinacją następujących wartości:

- Przycisk Wstecz PSWIZB_BACK

- Przycisk Dalej PSWIZB_NEXT

- Przycisk Zakończ PSWIZB_FINISH

- Przycisk Zakończ wyłączone PSWIZB_DISABLEDFINISH

### <a name="remarks"></a>Uwagi

Wywołaj `SetWizardButtons` tylko wtedy, gdy okno jest otwarte; nie można wywołać `SetWizardButtons` przed wywołaniem [DoModal](#domodal). Zazwyczaj należy wywołać `SetWizardButtons` z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Jeśli chcesz zmienić tekst na przycisku Zakończ lub ukryć następnego i Wstecz przyciski po użytkownik zostało ukończone kreatora wywołanie [SetFinishText](#setfinishtext). Należy pamiętać, że ten sam przycisk został udostępniony do zakończenia i dalej. Można wyświetlać zakończenia lub przycisk Dalej w tym samym czasie, ale nie oba.

### <a name="example"></a>Przykład

A `CPropertySheet` ma trzy strony właściwości kreatora: `CStylePage`, `CColorPage`, i `CShapePage`.  Poniższy fragment kodu pokazuje, jak włączanie i wyłączanie **ponownie** i **dalej** przyciski na stronie kreatora właściwości.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode

Określa stronę właściwości jako kreatora.

```
void SetWizardMode();
```

### <a name="remarks"></a>Uwagi

Jedną z najważniejszych cech Kreator strony właściwości jest, użytkownik nawiguje przy użyciu obok lub zakończenie, tworzenie kopii i przyciski, zamiast tabulatorów "Anuluj".

Wywołaj `SetWizardMode` przed wywołaniem [DoModal](#domodal). Po wywołaniu metody `SetWizardMode`, `DoModal` zwróci ID_WIZFINISH (Jeśli użytkownik zamknie za pomocą przycisku Zakończ) lub IDCANCEL.

`SetWizardMode` Ustawia flagę PSH_WIZARD.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Zobacz także

[MFC Sample CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CMNCTRL2 próbki MFC](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
