---
title: Klasa CPropertySheet
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
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421010"
---
# <a name="cpropertysheet-class"></a>Klasa CPropertySheet

Reprezentuje arkusze właściwości, znane również jako okna dialogowe kart.

## <a name="syntax"></a>Składnia

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Konstruuje obiekt `CPropertySheet`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CPropertySheet:: addPage](#addpage)|Dodaje stronę do arkusza właściwości.|
|[CPropertySheet:: konstrukcja](#construct)|Konstruuje obiekt `CPropertySheet`.|
|[CPropertySheet:: Create](#create)|Wyświetla niemodalny arkusz właściwości.|
|[CPropertySheet::D oModal](#domodal)|Wyświetla modalny arkusz właściwości.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Wskazuje, czy arkusz właściwości używa kart skumulowanych czy przewijanych.|
|[CPropertySheet:: zdarzenie EndDialog](#enddialog)|Kończy arkusz właściwości.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Pobiera indeks aktywnej strony arkusza właściwości.|
|[CPropertySheet::GetActivePage](#getactivepage)|Zwraca obiekt aktywnej strony.|
|[CPropertySheet:: GetPage](#getpage)|Pobiera wskaźnik do określonej strony.|
|[CPropertySheet:: getpagecount](#getpagecount)|Pobiera liczbę stron w arkuszu właściwości.|
|[CPropertySheet:: GetPageIndex](#getpageindex)|Pobiera indeks określonej strony arkusza właściwości.|
|[CPropertySheet:: GetTabControl](#gettabcontrol)|Pobiera wskaźnik do kontrolki karta.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.|
|[CPropertySheet:: OnInitDialog](#oninitdialog)|Przesłoń, aby rozszerzyć zainicjowanie arkusza właściwości.|
|[CPropertySheet::P ressButton](#pressbutton)|Symuluje wybór określonego przycisku w arkuszu właściwości.|
|[CPropertySheet:: Wywołaj RemovePage](#removepage)|Usuwa stronę z arkusza właściwości.|
|[CPropertySheet::SetActivePage](#setactivepage)|Program programowo ustawia obiekt aktywnej strony.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Ustawia tekst dla przycisku Zakończ.|
|[CPropertySheet:: settitle](#settitle)|Ustawia podpis arkusza właściwości.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Włącza przyciski kreatora.|
|[CPropertySheet:: SetWizardMode](#setwizardmode)|Włącza tryb kreatora.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CPropertySheet:: m_psh](#m_psh)|Struktura [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) systemu Windows. Zapewnia dostęp do podstawowych parametrów arkusza właściwości.|

## <a name="remarks"></a>Uwagi

Arkusz właściwości składa się z obiektu `CPropertySheet` i jednego lub większej liczby obiektów [CPropertyPage](../../mfc/reference/cpropertypage-class.md) . Struktura Wyświetla arkusz właściwości jako okno z zestawem indeksów kart i obszarem zawierającym aktualnie wybraną stronę. Użytkownik przechodzi do określonej strony przy użyciu odpowiedniej karty.

`CPropertySheet` zapewnia obsługę rozwiniętej struktury [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) wprowadzonej w systemach Windows 98 i windows NT 2000. Struktura zawiera dodatkowe flagi i składowe, które obsługują użycie mapy bitowej "znaku wodnego".

Aby automatycznie wyświetlić te nowe obrazy w obiekcie arkusza właściwości, Przekaż prawidłowe wartości obrazów mapy bitowej i palety w wywołaniu [CPropertySheet:: konstrukcja](#construct) lub [CPropertySheet:: CPropertySheet](#cpropertysheet).

Mimo że `CPropertySheet` nie pochodzi od [CDialog](../../mfc/reference/cdialog-class.md), Zarządzanie obiektem `CPropertySheet` jest podobne do zarządzania obiektem `CDialog`. Na przykład utworzenie arkusza właściwości wymaga konstrukcji dwuczęściowej: Wywołaj konstruktora, a następnie Wywołaj [DoModal](#domodal) dla modalnego arkusza właściwości lub [Utwórz](#create) dla niemodalnego arkusza właściwości. `CPropertySheet` ma dwa typy konstruktorów: [CPropertySheet:: konstrukcja](#construct) i [CPropertySheet:: CPropertySheet](#cpropertysheet).

Podczas konstruowania obiektu `CPropertySheet` niektóre [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) mogą spowodować wystąpienie wyjątku pierwszej szansy. Powoduje to, że system próbuje zmienić styl arkusza właściwości przed utworzeniem arkusza. Aby uniknąć tego wyjątku, upewnij się, że podczas tworzenia `CPropertySheet`ustawisz następujące style:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Następujące style są opcjonalne i nie spowodują wyjątku pierwszej szansy:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Wszystkie inne `Window Styles` są zabronione i nie należy ich włączać.

Wymiana danych między obiektem `CPropertySheet` a obiektem zewnętrznym przypomina wymianę danych z obiektem `CDialog`. Istotną różnicą jest to, że ustawienia arkusza właściwości są zwykle zmiennymi składowymi obiektów `CPropertyPage`, a nie samego obiektu `CPropertySheet`.

Można utworzyć typ okna dialogowego o nazwie Kreator, który składa się z arkusza właściwości z sekwencją stron właściwości, które prowadzą użytkownika przez kroki operacji, takie jak Konfigurowanie urządzenia lub tworzenie biuletynu. W oknie dialogowym karta typ Kreatora strony właściwości nie mają kart i widoczna jest tylko jedna strona właściwości jednocześnie. Ponadto zamiast przyciski **OK** i **Zastosuj teraz** , okno dialogowe karta typu Kreator zawiera przycisk **Wstecz** , przycisk **dalej** lub **Zakończ** , przycisk **Anuluj** i przycisk **Pomoc** .

Aby utworzyć okno dialogowe typ kreatora, wykonaj te same czynności, które należy wykonać w celu utworzenia standardowego arkusza właściwości, ale Wywołaj metodę [SetWizardMode](#setwizardmode) przed wywołaniem [DoModal](#domodal). Aby włączyć przyciski kreatora, wywołaj [SetWizardButtons](#setwizardbuttons), używając flag w celu dostosowania ich funkcji i wyglądu. Aby włączyć przycisk **Zakończ** , wywołaj [SetFinishText](#setfinishtext) po wykonaniu czynności przez użytkownika na ostatniej stronie kreatora.

Aby uzyskać więcej informacji o sposobach korzystania z obiektów `CPropertySheet`, zobacz [arkusze właściwości artykułów i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs. h

##  <a name="addpage"></a>CPropertySheet:: addPage

Dodaje podaną stronę ze skrajną prawą kartę w arkuszu właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Wskazuje stronę, która ma zostać dodana do arkusza właściwości. Nie może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Dodaj strony do arkusza właściwości w kolejności od lewej do prawej, które mają być wyświetlane.

`AddPage` dodaje obiekt [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) do listy stron `CPropertySheet` obiektu, ale nie tworzy w rzeczywistości okna dla strony. Struktura opóźnia tworzenie okna dla strony do momentu, gdy użytkownik wybierze Tę stronę.

Po dodaniu strony właściwości przy użyciu `AddPage`, `CPropertySheet` jest elementem nadrzędnym `CPropertyPage`. Aby uzyskać dostęp do arkusza właściwości na stronie właściwości, wywołaj [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent).

Nie trzeba czekać do momentu utworzenia okna arkusza właściwości w celu wywołania `AddPage`. Zwykle przed wywołaniem [DoModal](#domodal) lub [Create](#create)należy wywołać `AddPage`.

Jeśli wywołasz `AddPage` po wyświetleniu strony właściwości, wiersz karty będzie odzwierciedlał nowo dodaną stronę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet:: konstrukcja

Konstruuje obiekt `CPropertySheet`.

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
Identyfikator podpisu, który ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego arkusza właściwości. Jeśli wartość jest równa NULL, okno nadrzędne będzie głównym oknem aplikacji.

*iSelectPage*<br/>
Indeks strony, która początkowo będzie znajdować się na górze. Wartość domyślna to pierwsza strona dodana do arkusza.

*pszCaption*<br/>
Wskaźnik na ciąg zawierający podpis, który ma być używany dla arkusza właściwości. Nie może mieć wartości NULL.

*hbmWatermark*<br/>
Dojście do mapy bitowej znaku wodnego strony właściwości.

*hpalWatermark*<br/>
Dojście do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.

*hbmHeader*<br/>
Dojście do mapy bitowej nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, jeśli jeden z konstruktorów klas nie został jeszcze wywołany. Na przykład Wywołaj `Construct` przy deklarowaniu lub przydzieleniu tablic obiektów `CPropertySheet`. W przypadku tablic należy wywoływać `Construct` dla każdego elementu członkowskiego tablicy.

Aby wyświetlić arkusz właściwości, wywołaj [DoModal](#domodal) lub [Utwórz](#create). Ciąg zawarty w pierwszym parametrze zostanie umieszczony na pasku podpisu arkusza właściwości.

W przypadku używania trzech lub czwartych prototypów `Construct`i/lub obrazów nagłówka można automatycznie wyświetlać obrazy ze znakami wodnymi i/lub, a także przekazywać prawidłowe wartości parametrów *hbmWatermark*, *hpalWatermark*i/lub *hbmHeader* .

### <a name="example"></a>Przykład

Poniższy przykład ilustruje, jakie okoliczności należy wywołać `Construct`.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet::CPropertySheet

Konstruuje obiekt `CPropertySheet`.

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
Identyfikator podpisu, który ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskazuje okno nadrzędne arkusza właściwości. Jeśli wartość jest równa NULL, okno nadrzędne będzie głównym oknem aplikacji.

*iSelectPage*<br/>
Indeks strony, która początkowo będzie znajdować się na górze. Wartość domyślna to pierwsza strona dodana do arkusza.

*pszCaption*<br/>
Wskazuje ciąg zawierający podpis, który ma być używany dla arkusza właściwości. Nie może mieć wartości NULL.

*hbmWatermark*<br/>
Uchwyt mapy bitowej w tle arkusza właściwości.

*hpalWatermark*<br/>
Uchwyt do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.

*hbmHeader*<br/>
Uchwyt mapy bitowej nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusz właściwości, wywołaj [DoModal](#domodal) lub [Utwórz](#create). Ciąg zawarty w pierwszym parametrze zostanie umieszczony na pasku podpisu arkusza właściwości.

Jeśli masz wiele parametrów (na przykład jeśli używasz tablicy), użyj [konstrukcji](#construct) zamiast `CPropertySheet`.

W przypadku używania trzech lub czwartych prototypów `CPropertySheet`i/lub obrazów nagłówka można automatycznie wyświetlać *obrazy ze*znakami wodnymi i */lub.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet:: Create

Wyświetla niemodalny arkusz właściwości.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskazuje okno nadrzędne. Jeśli wartość jest równa NULL, element nadrzędny jest pulpitem.

*dwStyle*<br/>
Style okna dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Rozszerzone style okna dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Rozszerzone style okien](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli arkusz właściwości został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie `Create` może znajdować się wewnątrz konstruktora lub można wywołać go po wywołaniu konstruktora.

Domyślny styl wyrażony przez przekazywanie-1 jako *dwStyle*jest w rzeczywistości WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Domyślny styl okna rozszerzonego wyrażony przez przekazanie wartości 0 jako *dwExStyle*, jest w rzeczywistości WS_EX_DLGMODALFRAME.

Funkcja członkowska `Create` zwraca natychmiast po utworzeniu arkusza właściwości. Aby zniszczyć arkusz właściwości, wywołaj [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow).

Niemodalne arkusze właściwości wyświetlane z wywołaniem `Create` nie mają przycisków OK, Anuluj, Zastosuj teraz i pomoc jako modalne arkusze właściwości. Żądane przyciski muszą zostać utworzone przez użytkownika.

Aby wyświetlić modalny arkusz właściwości, wywołaj [DoModal](#domodal) zamiast.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>CPropertySheet::D oModal

Wyświetla modalny arkusz właściwości.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwrócona

IDOK lub IDCANCEL, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0 lub-1. Jeśli arkusz właściwości został ustanowiony jako Kreator (zobacz [SetWizardMode](#setwizardmode)), `DoModal` zwraca albo ID_WIZFINISH lub IDCANCEL.

### <a name="remarks"></a>Uwagi

Wartość zwracana odpowiada IDENTYFIKATORowi kontrolki, która zamknęła arkusz właściwości. Po powrocie tej funkcji okna odpowiadające arkuszowi właściwości i wszystkie strony zostaną zniszczone. Obiekty nadal będą istnieć. Zwykle dane z obiektów [CPropertyPage](../../mfc/reference/cpropertypage-class.md) są pobierane po `DoModal` zwraca IDOK.

Aby wyświetlić niemodalny arkusz właściwości, zamiast tego wywołaj metodę [Create](#create) .

Gdy strona właściwości jest tworzona na podstawie odpowiedniego zasobu okna dialogowego, może to spowodować wyjątek pierwszej szansy. Powoduje to zmianę stylu zasobu okna dialogowego do wymaganego stylu przed utworzeniem strony. Ponieważ zasoby są zwykle tylko do odczytu, powoduje to wyjątek. System obsługuje wyjątek i tworzy kopię zmodyfikowanego zasobu. Wyjątek pierwszej szansy może zostać zignorowany.

> [!NOTE]
>  Ten wyjątek musi być obsługiwany przez system operacyjny w przypadku kompilowania z modelem obsługi wyjątków asynchronicznych. Aby uzyskać więcej informacji na temat modeli obsługi wyjątków, zobacz [/EH (model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md). W tym przypadku nie należy zawijać wywołań do `CPropertySheet::DoModal` przy użyciu C++ bloku try-catch, w którym catch obsługuje wszystkie wyjątki, na przykład `catch (...)`. Ten blok mógłby obsłużyć wyjątek przeznaczony dla systemu operacyjnego i spowodować nieprzewidywalne zachowanie. Można jednak bezpiecznie korzystać C++ z obsługi wyjątków z określonymi typami wyjątków lub z obsługą wyjątków strukturalnych, w przypadku których wyjątek naruszenia dostępu jest przenoszona do systemu operacyjnego.

Aby uniknąć generowania tego wyjątku pierwszej szansy, można ręcznie zagwarantować, że arkusz właściwości ma poprawne [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Należy ustawić następujące style dla arkusza właściwości:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Możesz użyć następujących opcjonalnych stylów bez powodowania wyjątku pierwszej szansy:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Wyłącz wszystkie inne style systemu Windows, ponieważ nie są one zgodne z arkuszami właściwości. Te porady nie dotyczą stylów rozszerzonych. Odpowiednie ustawienie standardowych stylów zagwarantuje, że arkusz właściwości nie musi być modyfikowany i nie spowoduje generowania wyjątku pierwszej szansy.

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertySheet:: AddPage](#addpage).

##  <a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Wskazuje, czy wiersze kart mają być ułożone w arkuszu właściwości.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStacked*<br/>
Wskazuje, czy skumulowane karty są włączone w arkuszu właściwości. Wyłącz skumulowane wiersze tagów, ustawiając *bStacked* na false.

### <a name="remarks"></a>Uwagi

Domyślnie, jeśli arkusz właściwości zawiera więcej kart, niż mieści się w pojedynczym wierszu szerokości arkusza właściwości, karty stosują się do wielu wierszy. Aby korzystać z kart przewijanych zamiast kart stosów, przed wywołaniem [DoModal](#domodal) lub [Create](#create)należy wywoływać `EnableStackedTabs` *bStacked* z ustawionym na wartość false.

Należy wywołać `EnableStackedTabs` podczas tworzenia modalnego lub niemodalnego arkusza właściwości. Aby uwzględnić ten styl w klasie pochodnej `CPropertySheet`, napisz procedurę obsługi komunikatów dla WM_CREATE. W zastąpionej wersji elementu [CWnd:: OnCreate](../../mfc/reference/cwnd-class.md#oncreate), wywołaj `EnableStackedTabs( FALSE )` przed wywołaniem implementacji klasy bazowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet:: zdarzenie EndDialog

Kończy arkusz właściwości.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID*<br/>
Identyfikator, który ma być używany jako wartość zwracana arkusza właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę po naciśnięciu przycisku OK, Anuluj lub Zamknij. Wywołaj tę funkcję elementu członkowskiego, jeśli wystąpi zdarzenie, które powinno zamknąć arkusz właściwości.

Ta funkcja członkowska jest używana tylko w przypadku modalnego okna dialogowego.

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertySheet::P ressbutton](#pressbutton).

##  <a name="getactiveindex"></a>CPropertySheet::GetActiveIndex

Pobiera numer indeksu aktywnej strony okna arkusza właściwości, a następnie używa zwróconego numeru indeksu jako parametru `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Wartość zwrócona

Numer indeksu aktywnej strony.

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>CPropertySheet::GetActivePage

Pobiera aktywną stronę okna arkusza właściwości.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do aktywnej strony.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego, aby wykonać akcję na aktywnej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet:: GetPage

Zwraca wskaźnik do określonej strony w tym arkuszu właściwości.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Indeks żądanej strony, zaczynając od 0. Musi zawierać się w przedziale od 0 do mniej niż liczba stron w arkuszu właściwości włącznie.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do strony odpowiadającej parametrowi *nPage* .

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>CPropertySheet:: getpagecount

Określa liczbę stron znajdujących się obecnie w arkuszu właściwości.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba stron w arkuszu właściwości.

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>CPropertySheet:: GetPageIndex

Pobiera numer indeksu określonej strony z arkusza właściwości.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Wskazuje na stronę z indeksem, który ma zostać znaleziony. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwrócona

Numer indeksu strony.

### <a name="remarks"></a>Uwagi

Na przykład można użyć `GetPageIndex`, aby uzyskać indeks strony, aby można było użyć [SetActivePage](#setactivepage) lub [GetPage](#getpage).

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>CPropertySheet:: GetTabControl

Pobiera wskaźnik do kontrolki karta, aby wykonać coś specyficznego dla kontrolki karta (czyli do używania dowolnych z interfejsów API w [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do kontrolki karta.

### <a name="remarks"></a>Uwagi

Na przykład Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz dodać mapy bitowe do każdej karty podczas inicjowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>CPropertySheet:: m_psh

Struktura, której członkowie przechowują cechy [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Uwagi

Użyj tej struktury, aby zainicjować wygląd arkusza właściwości po jego zbudowaniu, ale przed wyświetleniem go przy użyciu funkcji składowej [DoModal](#domodal) . Na przykład Ustaw element członkowski *dwSize* `m_psh` na rozmiar, który ma mieć arkusz właściwości.

Aby uzyskać więcej informacji na temat tej struktury, łącznie z listą jej elementów członkowskich, zobacz PROPSHEETHEADER w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>CPropertySheet::MapDialogRect

Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje strukturę [Rect](/previous-versions/dd162897\(v=vs.85\)) lub obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który zawiera współrzędne okna dialogowego do przekonwertowania.

### <a name="remarks"></a>Uwagi

Jednostki okna dialogowego są określane jako bieżąca jednostka bazowa okna dialogowego, która pochodzi od średniej szerokości i wysokości znaków w czcionce używanej dla tekstu okna dialogowego. Jedna jednostka w poziomie jest jedną czwartą jednostkowej szerokości okna dialogowego, a jedna jednostka pionowa to jedna ósma jednostki podstawowej wysokości okna dialogowego.

Funkcja [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) systemu Windows zwraca informacje o rozmiarze dla czcionki systemowej, ale można określić inną czcionkę dla każdego arkusza właściwości, jeśli używasz stylu DS_SETFONT w pliku definicji zasobu. Funkcja [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) systemu Windows opisana w Windows SDK używa odpowiedniej czcionki dla tego okna dialogowego.

Funkcja członkowska `MapDialogRect` zastępuje jednostki okna dialogowego w *lpRect* za pomocą jednostek ekranu (pikseli), dzięki czemu prostokąt może służyć do tworzenia okna dialogowego lub umieszczania kontrolki w obrębie pola.

##  <a name="oninitdialog"></a>CPropertySheet:: OnInitDialog

Przesłania do inicjowania arkusza właściwości rozszerzonego.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwrócona

Określa, czy aplikacja ustawi fokus wprowadzania na jeden z kontrolek w arkuszu właściwości. Jeśli `OnInitDialog` zwraca wartość różną od zera, system Windows ustawia fokus wprowadzania na pierwszy formant w arkuszu właściwości. Aplikacja może zwrócić 0 tylko wtedy, gdy jawnie ustawił fokus wprowadzania na jeden z kontrolek w arkuszu właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana w odpowiedzi na komunikat WM_INITDIALOG. Ten komunikat jest wysyłany do arkusza właściwości podczas wywołań [Create](#create) lub [DoModal](#domodal) , które występują bezpośrednio przed wyświetleniem arkusza właściwości.

Przesłoń tę funkcję elementu członkowskiego, jeśli trzeba przeprowadzić przetwarzanie specjalne po zainicjowaniu arkusza właściwości. W zastąpionej wersji, najpierw Wywołaj klasę bazową `OnInitDialog` ale zignoruj jej wartość zwracaną. Zwykle zwracasz wartość TRUE ze zastąpionej funkcji członkowskiej.

Nie jest potrzebny wpis mapy komunikatów dla tej funkcji elementu członkowskiego.

##  <a name="pressbutton"></a>CPropertySheet::P ressButton

Symuluje wybór określonego przycisku w arkuszu właściwości.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*Nprzycisk*<br/>
Nprzycisk: identyfikuje przycisk, który ma zostać naciśnięty. Ten parametr może mieć jedną z następujących wartości:

- PSBTN_BACK wybiera przycisk Wstecz.

- PSBTN_NEXT wybiera przycisk Dalej.

- PSBTN_FINISH wybiera przycisk Zakończ.

- PSBTN_OK wybiera przycisk OK.

- PSBTN_APPLYNOW wybiera przycisk Zastosuj teraz.

- PSBTN_CANCEL wybiera przycisk Anuluj.

- PSBTN_HELP wybiera przycisk Pomoc.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat Windows SDK komunikatu PressButton, zobacz [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) .

Wywołanie `PressButton` nie wyśle powiadomienia [PSN_APPLY](/windows/win32/Controls/psn-apply) ze strony właściwości do struktury. Aby wysłać to powiadomienie, wywołaj [CPropertyPage:: OnOK —](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>CPropertySheet:: Wywołaj RemovePage

Usuwa stronę z arkusza właściwości i niszczy skojarzone okno.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*pPage*<br/>
Wskazuje stronę, która ma zostać usunięta z arkusza właściwości. Nie może mieć wartości NULL.

*nPage*<br/>
Indeks strony, która ma zostać usunięta. Musi zawierać się w przedziale od 0 do mniej niż liczba stron w arkuszu właściwości włącznie.

### <a name="remarks"></a>Uwagi

Sam obiekt [CPropertyPage](../../mfc/reference/cpropertypage-class.md) nie jest niszczony, dopóki nie zostanie zamknięty właściciel okna `CPropertySheet`.

##  <a name="setactivepage"></a>CPropertySheet::SetActivePage

Zmienia aktywną stronę.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*nPage*<br/>
Indeks strony do ustawienia. Musi zawierać się w przedziale od 0 do mniej niż liczba stron w arkuszu właściwości włącznie.

*pPage*<br/>
Wskazuje stronę, która ma zostać ustawiona w arkuszu właściwości. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli arkusz właściwości został aktywowany pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład użyj `SetActivePage`, jeśli akcja użytkownika na jednej stronie powinna spowodować, że inna strona stanie się stroną aktywną.

### <a name="example"></a>Przykład

Zobacz przykład dla [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>CPropertySheet::SetFinishText

Ustawia tekst na przycisku polecenia zakończenia.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Wskazuje tekst, który będzie wyświetlany na przycisku polecenia Zakończ.

### <a name="remarks"></a>Uwagi

Wywołaj `SetFinishText`, aby wyświetlić tekst na przycisku Zakończ polecenie i ukryć przyciski Dalej i wstecz po zakończeniu działania przez użytkownika na ostatniej stronie kreatora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet:: settitle

Określa podpis arkusza właściwości (tekst wyświetlany na pasku tytułu okna ramki).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Określa styl tytułu arkusza właściwości. Styl musi być określony jako 0 lub jako PSH_PROPTITLE. Jeśli styl jest ustawiony jako PSH_PROPTITLE, słowo "właściwości" pojawia się po tekście określonym jako napis. Na przykład wywołanie `SetTitle`("Simple", PSH_PROPTITLE) spowoduje podpis arkusza właściwości "proste właściwości".

*lpszText*<br/>
Wskazuje tekst, który ma być używany jako podpis na pasku tytułu arkusza właściwości.

### <a name="remarks"></a>Uwagi

Domyślnie arkusz właściwości używa parametru Caption w konstruktorze arkusza właściwości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons

Włącza lub wyłącza przycisk Wstecz, dalej lub Zakończ w arkuszu właściwości kreatora.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*flagiDW*<br/>
Zestaw flag, które dostosowują funkcję i wygląd przycisków kreatora. Ten parametr może być kombinacją następujących wartości:

- Przycisk PSWIZB_BACK wstecz

- Przycisk PSWIZB_NEXT dalej

- Przycisk Zakończ PSWIZB_FINISH

- PSWIZB_DISABLEDFINISH wyłączony przycisk Zakończ

### <a name="remarks"></a>Uwagi

Wywołaj `SetWizardButtons` tylko po otwarciu okna dialogowego; nie można wywołać `SetWizardButtons` przed wywołaniem [DoModal](#domodal). Zazwyczaj należy wywołać `SetWizardButtons` z [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Jeśli chcesz zmienić tekst na przycisku Zakończ lub ukryć przyciski Dalej i wstecz, gdy użytkownik ukończy pracę kreatora, wywołaj [SetFinishText](#setfinishtext). Należy pamiętać, że ten sam przycisk jest udostępniony do zakończenia i następny. Możesz w jednym momencie wyświetlić przycisk Zakończ lub następny, ale nie oba.

### <a name="example"></a>Przykład

`CPropertySheet` ma trzy strony właściwości kreatora: `CStylePage`, `CColorPage`i `CShapePage`.  Poniższy fragment kodu pokazuje, jak włączyć i wyłączyć przyciski **Wstecz** i **dalej** na stronie właściwości kreatora.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet:: SetWizardMode

Ustanawia stronę właściwości jako kreatora.

```
void SetWizardMode();
```

### <a name="remarks"></a>Uwagi

Kluczową cechą strony właściwości kreatora jest to, że użytkownik nawiguje przy użyciu przycisków dalej lub Zakończ, wstecz i Anuluj zamiast tabulatorów.

Wywołaj `SetWizardMode` przed wywołaniem [DoModal](#domodal). Po wywołaniu `SetWizardMode`, `DoModal` zwróci albo ID_WIZFINISH (Jeśli użytkownik zostanie zamknięty przy użyciu przycisku Zakończ) lub IDCANCEL.

`SetWizardMode` ustawia flagę PSH_WIZARD.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CMNCTRL1 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład CMNCTRL2 MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład PROPDLG MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład SNAPVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
