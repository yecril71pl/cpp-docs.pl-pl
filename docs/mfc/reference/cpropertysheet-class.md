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
ms.openlocfilehash: 167c99f734e4538ff2704e032a6ca98fb1d82004
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363948"
---
# <a name="cpropertysheet-class"></a>Klasa CPropertySheet

Reprezentuje arkusze właściwości, znane również jako okna dialogowe kart.

## <a name="syntax"></a>Składnia

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Konstruuje `CPropertySheet` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Arkusz CPropertySheet::AddPage](#addpage)|Dodaje stronę do arkusza właściwości.|
|[Arkusz CPropertySheet::Konstruuj](#construct)|Konstruuje `CPropertySheet` obiekt.|
|[Arkusz CPropertySheet::Tworzenie](#create)|Wyświetla niemodytowy arkusz właściwości.|
|[CPropertySheet::DoModal](#domodal)|Wyświetla arkusz właściwości modalnych.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Wskazuje, czy arkusz właściwości używa kart skumulowanych czy przewijanych.|
|[Arkusz CPropertySheet::EndDialog](#enddialog)|Kończy arkusz właściwości.|
|[Arkusz CPropertySheet::GetActiveIndex](#getactiveindex)|Pobiera indeks aktywnej strony arkusza właściwości.|
|[Arkusz CPropertySheet::GetActivePage](#getactivepage)|Zwraca aktywny obiekt strony.|
|[Arkusz CPropertySheet::GetPage](#getpage)|Pobiera wskaźnik do określonej strony.|
|[CPropertySheet::GetPageCount](#getpagecount)|Pobiera liczbę stron w arkuszu właściwości.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Pobiera indeks określonej strony arkusza właściwości.|
|[Arkusz CPropertySheet::GetTabControl](#gettabcontrol)|Pobiera wskaźnik do kontrolki karty.|
|[Arkusz CPropertySheet::MapDialogRect](#mapdialogrect)|Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.|
|[Arkusz CPropertySheet::OnInitDialog](#oninitdialog)|Zastąrpnąć, aby zwiększyć inicjowanie arkusza właściwości.|
|[CPropertySheet::PressButton](#pressbutton)|Symuluje wybór określonego przycisku w arkuszu właściwości.|
|[CPropertySheet::RemovePage](#removepage)|Usuwa stronę z arkusza właściwości.|
|[Arkusz CPropertySheet::SetActivePage](#setactivepage)|Programowo ustawia aktywny obiekt strony.|
|[Arkusz CPropertySheet::SetFinishText](#setfinishtext)|Ustawia tekst przycisku Zakończ.|
|[Arkusz CPropertySheet::SetTitle](#settitle)|Ustawia podpis arkusza właściwości.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Włącza przyciski kreatora.|
|[Arkusz CPropertySheet::SetWizardMode](#setwizardmode)|Włącza tryb kreatora.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Struktura Windows [PROPSHEETHEADER.](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) Zapewnia dostęp do podstawowych parametrów arkusza właściwości.|

## <a name="remarks"></a>Uwagi

Arkusz właściwości składa `CPropertySheet` się z obiektu i co najmniej jednego [obiektu CPropertyPage.](../../mfc/reference/cpropertypage-class.md) Struktura wyświetla arkusz właściwości jako okno z zestawem indeksów kart i obszarem zawierającym aktualnie wybraną stronę. Użytkownik przechodzi do określonej strony przy użyciu odpowiedniej karty.

`CPropertySheet`zapewnia obsługę rozszerzonej struktury [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) wprowadzonej w systemach Windows 98 i Windows NT 2000. Struktura zawiera dodatkowe flagi i elementy członkowskie, które obsługują przy użyciu mapy bitowej tła "znak wodny".

Aby automatycznie wyświetlić te nowe obrazy w obiekcie arkusza właściwości, należy przekazać prawidłowe wartości dla obrazów bitmapowych i palet w wywołaniu [CPropertySheet::Construct](#construct) or [CPropertySheet::CPropertySheet](#cpropertysheet).

Mimo `CPropertySheet` że nie pochodzi z [CDialog](../../mfc/reference/cdialog-class.md), zarządzanie `CPropertySheet` `CDialog` obiektem jest jak zarządzanie obiektem. Na przykład utworzenie arkusza właściwości wymaga konstrukcji dwuczęściowej: wywołaj konstruktora, a następnie [wywołaj DoModal](#domodal) dla arkusza właściwości modalnych lub [Utwórz](#create) dla arkusza właściwości bez trybu. `CPropertySheet`Posiada dwa typy konstruktorów: [CPropertySheet::Construct](#construct) i [CPropertySheet::CPropertySheet](#cpropertysheet).

Podczas konstruowania `CPropertySheet` obiektu, niektóre style [okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) może spowodować wyjątek pierwszej szansy występuje. Wynika to z systemu próbuje zmienić styl arkusza właściwości przed utworzeniem arkusza. Aby uniknąć tego wyjątku, podczas `CPropertySheet`tworzenia:

- DS_3DLOOK

- DS_CONTROL

- Ws_child

- Ws_tabstop

Następujące style są opcjonalne i nie powodują wyjątku pierwszej szansy:

- DS_SHELLFONT

- DS_LOCALEDIT

- Ws_clipchildren

Wszelkie `Window Styles` inne są zabronione i nie należy ich włączać.

Wymiana danych między `CPropertySheet` obiektem a obiektem zewnętrznym jest `CDialog` podobna do wymiany danych z obiektem. Ważną różnicą jest to, że ustawienia arkusza właściwości `CPropertyPage` są zazwyczaj zmienne członkowskie obiektów, a nie samego `CPropertySheet` obiektu.

Można utworzyć typ okna dialogowego karty o nazwie kreator, który składa się z arkusza właściwości z sekwencją stron właściwości, które prowadzą użytkownika przez kroki operacji, takie jak konfigurowanie urządzenia lub tworzenie biuletynu. W oknie dialogowym karty typu kreatora strony właściwości nie mają kart, a jednocześnie jest widoczna tylko jedna strona właściwości. Ponadto zamiast przycisków **OK** i **Zastosuj teraz,** okno dialogowe typu kreatora zawiera przycisk **Wstecz,** przycisk **Dalej** lub **Zakończ,** przycisk **Anuluj** i przycisk **Pomoc.**

Aby utworzyć okno dialogowe typu kreatora, wykonaj te same kroki, które należy wykonać, aby utworzyć standardowy arkusz właściwości, ale wywołaj [Polecenie SetWizardMode](#setwizardmode) przed wywołaniem [programu DoModal](#domodal). Aby włączyć przyciski kreatora, wywołaj [Przycisk SetWizardButtons](#setwizardbuttons), używając flag, aby dostosować ich funkcję i wygląd. Aby włączyć przycisk **Zakończ,** po dokonaniu przez użytkownika działania na ostatniej stronie kreatora należy wywołać program [SetFinishText.](#setfinishtext)

Aby uzyskać więcej informacji `CPropertySheet` na temat używania obiektów, zobacz artykuł [Arkusze właściwości i strony właściwości](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>Arkusz CPropertySheet::AddPage

Dodaje dostarczoną stronę z prawą kartę w arkuszu właściwości.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
Wskazuje stronę, która ma zostać dodana do arkusza właściwości. Nie może być null.

### <a name="remarks"></a>Uwagi

Dodaj strony do arkusza właściwości w kolejności od lewej do prawej, które mają być wyświetlane.

`AddPage`dodaje [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) obiektu `CPropertySheet` do listy stron obiektu, ale faktycznie nie tworzy okno dla strony. Struktura odkłada utworzenie okna dla strony, dopóki użytkownik nie wybierze tej strony.

Po dodaniu strony `AddPage`właściwości `CPropertySheet` przy użyciu , `CPropertyPage`jest elementem nadrzędnym . Aby uzyskać dostęp do arkusza właściwości ze strony właściwości, zadzwoń [do CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

Nie trzeba czekać, aż powstanie okna arkusza `AddPage`właściwości, aby wywołać . Zazwyczaj dzwonisz `AddPage` przed wywołaniem [DoModal](#domodal) lub [Create](#create).

Jeśli wywołasz `AddPage` po wyświetleniu strony właściwości, wiersz karty będzie odzwierciedlał nowo dodaną stronę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>Arkusz CPropertySheet::Konstruuj

Konstruuje `CPropertySheet` obiekt.

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

*nIDCaption (nIDCaption)*<br/>
Identyfikator podpisu, który ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego arkusza właściwości. Jeśli null, okno nadrzędne będzie głównym oknem aplikacji.

*Strona iSelectPage*<br/>
Indeks strony, która początkowo będzie na górze. Domyślnie jest to pierwsza strona dodana do arkusza.

*pszCaption*<br/>
Wskaźnik do ciągu zawierającego podpis, który ma być używany dla arkusza właściwości. Nie może być null.

*hbmWodekwodny*<br/>
Dojście do mapy bitowej znaku wodnego strony właściwości.

*hpalWodek*<br/>
Uchwyt do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.

*hbmHeader (głowica)*<br/>
Dojście do mapy bitowej nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, jeśli jeden z konstruktorów klasy nie został już wywołany. Na przykład `Construct` wywołać podczas deklarowania `CPropertySheet` lub przydzielić tablice obiektów. W przypadku tablic, należy wywołać `Construct` dla każdego elementu członkowskiego w tablicy.

Aby wyświetlić arkusz właściwości, wywołanie [DoModal](#domodal) lub [Utwórz](#create). Ciąg zawarty w pierwszym parametrze zostanie umieszczony na pasku podpisu dla arkusza właściwości.

Obrazy znaku wodnego i/lub nagłówka można wyświetlać automatycznie, `Construct`jeśli używasz trzeciego lub czwartego prototypu , wymienionych powyżej, i przekazujesz prawidłowe wartości dla parametrów *hbmWatermark*, *hpalWatermark*i/lub *hbmHeader.*

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, w jakich `Construct`okolicznościach można wywołać .

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>CPropertySheet::CPropertySheet

Konstruuje `CPropertySheet` obiekt.

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

*nIDCaption (nIDCaption)*<br/>
Identyfikator podpisu, który ma być używany dla arkusza właściwości.

*pParentWnd*<br/>
Wskazuje okno nadrzędne arkusza właściwości. Jeśli null, okno nadrzędne będzie głównym oknem aplikacji.

*Strona iSelectPage*<br/>
Indeks strony, która początkowo będzie na górze. Domyślnie jest to pierwsza strona dodana do arkusza.

*pszCaption*<br/>
Wskazuje ciąg zawierający podpis, który ma być używany dla arkusza właściwości. Nie może być null.

*hbmWodekwodny*<br/>
Dojście do mapy bitowej tła arkusza właściwości.

*hpalWodek*<br/>
Dojście do palety mapy bitowej znaku wodnego i/lub mapy bitowej nagłówka.

*hbmHeader (głowica)*<br/>
Dojście do mapy bitowej nagłówka strony właściwości.

### <a name="remarks"></a>Uwagi

Aby wyświetlić arkusz właściwości, wywołanie [DoModal](#domodal) lub [Utwórz](#create). Ciąg zawarty w pierwszym parametrze zostanie umieszczony na pasku podpisu dla arkusza właściwości.

Jeśli masz wiele parametrów (na przykład, jeśli używasz tablicy), użyj [Construct](#construct) zamiast `CPropertySheet`.

Obrazy znaku wodnego i/lub nagłówka można wyświetlać automatycznie, `CPropertySheet`jeśli używasz trzeciego lub czwartego prototypu powyżej, a także przekazujesz prawidłowe wartości dla parametrów *hbmWatermark*, *hpalWatermark*i/lub *hbmHeader.*

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>Arkusz CPropertySheet::Tworzenie

Wyświetla niemodytowy arkusz właściwości.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskazuje okno nadrzędne. Jeśli null, nadrzędny jest pulpit.

*Dwstyle*<br/>
Style okien dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Dwexstyle*<br/>
Rozszerzone style okien dla arkusza właściwości. Aby uzyskać pełną listę dostępnych stylów, zobacz [Rozszerzone style okien](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli arkusz właściwości został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie `Create` może znajdować się wewnątrz konstruktora lub można wywołać go po wywołaniu konstruktora.

Domyślny styl, wyrażony przez przejście -1 jako *dwStyle*, jest w rzeczywistości WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. Domyślny styl rozszerzonego okna, wyrażony przez przekazanie 0 jako *dwExStyle*, jest w rzeczywistości WS_EX_DLGMODALFRAME.

Funkcja `Create` elementu członkowskiego zwraca natychmiast po utworzeniu arkusza właściwości. Aby zniszczyć arkusz właściwości, zadzwoń [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Niemodalne arkusze właściwości wyświetlane `Create` z wywołaniem, aby nie mieć przycisków OK, Anuluj, Zastosuj teraz i Pomoc, jak robią to arkusze właściwości modalnych. Żądane przyciski muszą być tworzone przez użytkownika.

Aby wyświetlić arkusz właściwości modalnych, wywołanie [DoModal](#domodal) zamiast.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>CPropertySheet::DoModal

Wyświetla arkusz właściwości modalnych.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Wartość zwracana

IDOK lub IDCANCEL, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0 lub -1. Jeśli arkusz właściwości został ustanowiony jako kreator (zobacz [SetWizardMode),](#setwizardmode) `DoModal` zwraca ID_WIZFINISH lub IDCANCEL.

### <a name="remarks"></a>Uwagi

Zwracana wartość odpowiada identyfikatorowi formantu, który zamknął arkusz właściwości. Po powrocie tej funkcji okna odpowiadające arkuszowi właściwości i wszystkie strony zostaną zniszczone. Same obiekty nadal będą istnieć. Zazwyczaj będzie pobierać dane z [CPropertyPage](../../mfc/reference/cpropertypage-class.md) obiektów `DoModal` po zwraca IDOK.

Aby wyświetlić arkusz właściwości bez trybu, wywołanie [Create](#create) zamiast tego.

Gdy strona właściwości jest tworzona z odpowiedniego zasobu okna dialogowego, może to spowodować wyjątek pierwszej szansy. Wynika to ze strony właściwości, zmieniając styl zasobu okna dialogowego na wymagany styl przed utworzeniem strony. Ponieważ zasoby są zazwyczaj tylko do odczytu, powoduje to wyjątek. System obsługuje wyjątek i tworzy kopię zmodyfikowanego zasobu. W związku z tym można zignorować wyjątek pierwszej szansy.

> [!NOTE]
> Ten wyjątek musi być obsługiwany przez system operacyjny, jeśli kompilujesz z modelem obsługi wyjątków asynchronicznych. Aby uzyskać więcej informacji na temat modeli obsługi wyjątków, zobacz [/EH (Model obsługi wyjątków)](../../build/reference/eh-exception-handling-model.md). W takim przypadku nie należy `CPropertySheet::DoModal` zawijać wywołań za pomocą bloku try-catch języka C++, w którym catch obsługuje wszystkie wyjątki, `catch (...)`na przykład . Ten blok będzie obsługiwać wyjątek przeznaczony dla systemu operacyjnego i spowodować nieprzewidywalne zachowanie. Można jednak bezpiecznie używać obsługi wyjątków języka C++ z określonymi typami wyjątków lub obsługi wyjątków strukturalnych, w przypadku gdy wyjątek naruszenia zasad dostępu jest przekazywany do systemu operacyjnego.

Aby uniknąć generowania tego wyjątku pierwszej szansy, można ręcznie zagwarantować, że arkusz właściwości ma poprawne [style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Należy ustawić następujące style dla arkusza właściwości:

- DS_3DLOOK

- DS_CONTROL

- Ws_child

- Ws_tabstop

Można użyć następujących stylów opcjonalnych bez powodowania wyjątku pierwszej szansy:

- DS_SHELLFONT

- DS_LOCALEDIT

- Ws_clipchildren

Wyłącz wszystkie inne style systemu Windows, ponieważ nie są one zgodne z arkuszami właściwości. Ta rada nie ma zastosowania do rozszerzonych stylów. Odpowiednie ustawienie tych standardowych stylów zagwarantuje, że arkusz właściwości nie musi być modyfikowany i uniknie generowania wyjątku pierwszej szansy.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::AddPage](#addpage).

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Wskazuje, czy wiersze kart mają być ułożone w arkuszu właściwości.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parametry

*bStacked*<br/>
Wskazuje, czy w arkuszu właściwości są włączone zakładki skumulowane. Wyłącz ułożone wiersze znaczników, ustawiając *bStacked* na FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie, jeśli arkusz właściwości ma więcej kart niż zmieści się w jednym wierszu w szerokości arkusza właściwości, karty będą ułożone w wielu wierszach. Aby użyć kart przewijania zamiast kart `EnableStackedTabs` układania, zadzwoń z *bStacked ustawioną* na FALSE przed wywołaniem [DoModal](#domodal) lub [Create](#create).

Należy wywołać `EnableStackedTabs` podczas tworzenia modalnego lub niemodalnego arkusza właściwości. Aby włączyć ten styl `CPropertySheet`do klasy pochodnej, napisz program obsługi wiadomości dla WM_CREATE. W zastąpiona wersja [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), `EnableStackedTabs( FALSE )` wywołać przed wywołaniem implementacji klasy podstawowej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>Arkusz CPropertySheet::EndDialog

Kończy arkusz właściwości.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parametry

*nEndID (nEndID)*<br/>
Identyfikator, który ma być używany jako wartość zwracana arkusza właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez platformę po naciśnięciu przycisku OK, Anuluj lub Zamknij. Wywołanie tej funkcji elementu członkowskiego, jeśli wystąpi zdarzenie, które powinno zamknąć arkusz właściwości.

Ta funkcja elementu członkowskiego jest używana tylko z modalnym oksem.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::PressButton](#pressbutton).

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>Arkusz CPropertySheet::GetActiveIndex

Pobiera numer indeksu aktywnej strony okna arkusza właściwości, a następnie używa `GetPage`zwracanego numeru indeksu jako parametru dla .

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Numer indeksu aktywnej strony.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>Arkusz CPropertySheet::GetActivePage

Pobiera aktywną stronę okna arkusza właściwości.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnej strony.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego służy do wykonywania niektórych akcji na aktywnej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>Arkusz CPropertySheet::GetPage

Zwraca wskaźnik do określonej strony w tym arkuszu właściwości.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parametry

*strona nPage*<br/>
Indeks żądanej strony, zaczynając od 0. Musi być od 0 do jednego mniej niż liczba stron w arkuszu właściwości, włącznie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do strony odpowiadającej parametrowi *nPage.*

### <a name="example"></a>Przykład

Zobacz przykład [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>CPropertySheet::GetPageCount

Określa liczbę stron aktualnie w arkuszu właściwości.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba stron w arkuszu właściwości.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>CPropertySheet::GetPageIndex

Pobiera numer indeksu określonej strony w arkuszu właściwości.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
Wskazuje stronę z indeksem, który ma zostać znaleziony. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

Numer indeksu strony.

### <a name="remarks"></a>Uwagi

Na przykład można `GetPageIndex` użyć, aby uzyskać indeks strony w celu użycia [SetActivePage](#setactivepage) lub [GetPage](#getpage).

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>Arkusz CPropertySheet::GetTabControl

Pobiera wskaźnik do kontrolki karty, aby zrobić coś specyficznego dla kontrolki karty (czyli do użycia dowolnego z interfejsów API w [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do kontrolki karty.

### <a name="remarks"></a>Uwagi

Na przykład wywołać tę funkcję elementu członkowskiego, jeśli chcesz dodać mapy bitowe do każdej z kart podczas inicjowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>CPropertySheet::m_psh

Struktura, której członkowie przechowują cechy [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Uwagi

Ta struktura służy do inicjowania wyglądu arkusza właściwości po jego skonstruowaniu, ale przed wyświetleniem go za pomocą funkcji elementu członkowskiego [DoModal.](#domodal) Na przykład ustaw element członkowski `m_psh` *dwSize* do rozmiaru, który ma mieć arkusz właściwości.

Aby uzyskać więcej informacji na temat tej struktury, w tym listę jej członków, zobacz PROPSHEETHEADER w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>Arkusz CPropertySheet::MapDialogRect

Konwertuje jednostki okna dialogowego prostokąta na jednostki ekranu.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę [RECT](/previous-versions/dd162897\(v=vs.85\)) lub obiekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) który zawiera współrzędne okna dialogowego do przekonwertowania.

### <a name="remarks"></a>Uwagi

Jednostki okna dialogowego są podane w kategoriach bieżącej jednostki bazowej okna dialogowego pochodzącej od średniej szerokości i wysokości znaków w czcionce używanej dla tekstu okna dialogowego. Jedna jednostka pozioma to jedna czwarta jednostki szerokości podstawy okna dialogowego, a jedna jednostka pionowa to jedna ósma jednostki wysokości podstawy okna dialogowego.

Funkcja [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows zwraca informacje o rozmiarze czcionki systemowej, ale można określić inną czcionkę dla każdego arkusza właściwości, jeśli w pliku definicji zasobów jest używany styl DS_SETFONT. [Funkcja MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) Windows, opisana w programie Windows SDK, używa odpowiedniej czcionki dla tego okna dialogowego.

Funkcja `MapDialogRect` elementu członkowskiego zastępuje jednostki okna dialogowego w *lpRect* jednostkami ekranu (pikselami), dzięki czemu prostokąt może być użyty do utworzenia okna dialogowego lub umieszczenia formantu w polu.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>Arkusz CPropertySheet::OnInitDialog

Zastępuje, aby zwiększyć inicjowanie arkusza właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Określa, czy aplikacja ustawiła fokus wejściowy na jeden z formantów w arkuszu właściwości. Jeśli `OnInitDialog` zwraca wartość niezerową, system Windows ustawia fokus wejściowy na pierwszy formant w arkuszu właściwości. Aplikacja może zwrócić 0 tylko wtedy, gdy jawnie ustawić fokus wejściowy do jednego z formantów w arkuszu właściwości.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana w odpowiedzi na komunikat WM_INITDIALOG. Ten komunikat jest wysyłany do arkusza właściwości podczas [tworzenia](#create) lub [domodalnych](#domodal) wywołań, które występują bezpośrednio przed wyświetleniem arkusza właściwości.

Zastąpokaj tę funkcję elementu członkowskiego, jeśli konieczne jest wykonanie specjalnego przetwarzania podczas inicjowania arkusza właściwości. W wersji zastąpione najpierw wywołać `OnInitDialog` klasę podstawową, ale pominąć jego wartość zwracaną. Zwykle zwracasz wartość TRUE z funkcji nadrzędnego elementu członkowskiego.

Nie potrzebujesz wpisu mapy wiadomości dla tej funkcji członkowskiej.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>CPropertySheet::PressButton

Symuluje wybór określonego przycisku w arkuszu właściwości.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parametry

*nButton (przycisk)*<br/>
nButton : Identyfikuje przycisk do naciśnięcia. Ten parametr może być jedną z następujących wartości:

- PSBTN_BACK Wybierz przycisk Wstecz.

- PSBTN_NEXT Wybierz przycisk Dalej.

- PSBTN_FINISH Wybierz przycisk Zakończ.

- PSBTN_OK Wybierz przycisk OK.

- PSBTN_APPLYNOW wybierz przycisk Zastosuj teraz.

- PSBTN_CANCEL wybierz przycisk Anuluj.

- PSBTN_HELP Wybierz przycisk Pomoc.

### <a name="remarks"></a>Uwagi

Zobacz [PSM_PRESSBUTTON,](/windows/win32/Controls/psm-pressbutton) aby uzyskać więcej informacji na temat komunikatu Windows SDK Pressbutton.

Wywołanie `PressButton` nie wyśle [powiadomienia PSN_APPLY](/windows/win32/Controls/psn-apply) ze strony właściwości do struktury. Aby wysłać to powiadomienie, zadzwoń [do CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>CPropertySheet::RemovePage

Usuwa stronę z arkusza właściwości i niszczy skojarzone okno.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parametry

*strona pPage*<br/>
Wskazuje stronę do usunięcia z arkusza właściwości. Nie może być null.

*strona nPage*<br/>
Indeks strony do usunięcia. Musi być od 0 do jednego mniej niż liczba stron w arkuszu właściwości, włącznie.

### <a name="remarks"></a>Uwagi

Sam obiekt [CPropertyPage](../../mfc/reference/cpropertypage-class.md) nie jest niszczony, `CPropertySheet` dopóki właściciel okna nie zostanie zamknięty.

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>Arkusz CPropertySheet::SetActivePage

Zmienia aktywną stronę.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parametry

*strona nPage*<br/>
Indeks strony do ustawienia. Musi być od 0 do jednego mniej niż liczba stron w arkuszu właściwości, włącznie.

*strona pPage*<br/>
Wskazuje stronę ustawioną w arkuszu właściwości. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli arkusz właściwości jest pomyślnie aktywowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład `SetActivePage` użyj, jeśli akcja użytkownika na jednej stronie powinna spowodować, że inna strona stanie się aktywną stroną.

### <a name="example"></a>Przykład

Zobacz przykład [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>Arkusz CPropertySheet::SetFinishText

Ustawia tekst w przycisku polecenia Zakończ.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskazuje tekst wyświetlany na przycisku polecenia Zakończ.

### <a name="remarks"></a>Uwagi

Wywołanie, `SetFinishText` aby wyświetlić tekst na przycisku polecenia Zakończ i ukryć przyciski Dalej i Wstecz po zakończeniu akcji przez użytkownika na ostatniej stronie kreatora.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>Arkusz CPropertySheet::SetTitle

Określa podpis arkusza właściwości (tekst wyświetlany na pasku tytułu okna ramki).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parametry

*styl nStyle*<br/>
Określa styl tytułu arkusza właściwości. Styl musi być określony na 0 lub jako PSH_PROPTITLE. Jeśli styl jest ustawiony jako PSH_PROPTITLE, wyraz "Właściwości" pojawia się po tekście określonym jako podpis. Na przykład `SetTitle`wywołanie ("Proste", PSH_PROPTITLE) spowoduje podpis arkusza właściwości "Właściwości proste".

*lpszText (tekst)*<br/>
Wskazuje tekst, który ma być używany jako podpis na pasku tytułu arkusza właściwości.

### <a name="remarks"></a>Uwagi

Domyślnie arkusz właściwości używa parametru caption w konstruktorze arkusza właściwości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons

Włącza lub wyłącza przycisk Wstecz, Dalej lub Zakończ w arkuszu właściwości kreatora.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Dwflags*<br/>
Zestaw flag, które dostosowują funkcję i wygląd przycisków kreatora. Ten parametr może być kombinacją następujących wartości:

- przycisk PSWIZB_BACK Wstecz

- PSWIZB_NEXT przycisk Dalej

- PSWIZB_FINISH przycisk Zakończ

- PSWIZB_DISABLEDFINISH przycisk Zakończ wyłączona

### <a name="remarks"></a>Uwagi

Wywołanie `SetWizardButtons` dopiero po otwarciu okna dialogowego; nie można zadzwonić `SetWizardButtons` przed wywołaniem [DoModal](#domodal). Zazwyczaj należy wywołać `SetWizardButtons` z [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Jeśli chcesz zmienić tekst na przycisku Zakończ lub ukryć przyciski Dalej i Wstecz po zakończeniu pracy kreatora przez użytkownika, zadzwoń do [setfinishtext](#setfinishtext). Należy zauważyć, że ten sam przycisk jest udostępniony dla Zakończ i Dalej. Przycisk Zakończ lub Następny można wyświetlić jednocześnie, ale nie oba.

### <a name="example"></a>Przykład

A `CPropertySheet` ma trzy strony `CStylePage` `CColorPage`właściwości `CShapePage`kreatora: , , i .  Poniższy fragment kodu pokazuje, jak włączyć i wyłączyć przyciski **Wstecz** i **Dalej** na stronie właściwości kreatora.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>Arkusz CPropertySheet::SetWizardMode

Ustanawia stronę właściwości jako kreatora.

```
void SetWizardMode();
```

### <a name="remarks"></a>Uwagi

Kluczową cechą strony właściwości kreatora jest to, że użytkownik nawiguje za pomocą przycisków Dalej lub Zakończ, Wstecz i Anuluj zamiast kart.

Zadzwoń `SetWizardMode` przed wywołaniem [DoModal](#domodal). Po `SetWizardMode`wywołaniu `DoModal` , zwróci ID_WIZFINISH (jeśli użytkownik zamknie się za pomocą przycisku Zakończ) lub IDCANCEL.

`SetWizardMode`ustawia flagę PSH_WIZARD.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
