---
title: Klasa CEditView
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: 8fbb2dc569e675ecff4ce04758a4eced40505bf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373971"
---
# <a name="ceditview-class"></a>Klasa CEditView

Typ klasy widoku, który zapewnia funkcjonalność formantu edycji systemu Windows i może służyć do implementowania prostych funkcji edytora tekstu.

## <a name="syntax"></a>Składnia

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Konstruuje obiekt `CEditView`typu .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::ZnajdźTekst](#findtext)|Wyszukuje ciąg w tekście.|
|[CEditView::GetBufferLength](#getbufferlength)|Uzyskuje długość buforu znaków.|
|[CEditView::GetEditCtrl](#geteditctrl)|Zapewnia dostęp `CEdit` do części `CEditView` obiektu (kontrolki edycji systemu Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Pobiera bieżącą czcionkę drukarki.|
|[CEditView::GetSelectedText](#getselectedtext)|Pobiera bieżące zaznaczenie tekstu.|
|[CEditView::LockBuffer](#lockbuffer)|Blokuje bufor.|
|[CEditView::PrintInsideRect](#printinsiderect)|Renderuje tekst wewnątrz danego prostokąta.|
|[CEditView::SerializeRaw](#serializeraw)|Serializuje obiekt `CEditView` na dysku jako tekst nieprzetworzony.|
|[CEditView::SetPrinterFont](#setprinterfont)|Ustawia nową czcionkę drukarki.|
|[CEditView::SetTabStops](#settabstops)|Ustawia tabulatory zarówno do wyświetlania na ekranie, jak i drukowania.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Odblokowuje bufor.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie ciągu tekstowego.|
|[CEditView::OnReplaceAll](#onreplaceall)|Zastępuje wszystkie wystąpienia danego ciągu nowym ciągiem.|
|[CEditView::OnReplaceSel](#onreplacesel)|Zastępuje bieżący wybór.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Wywoływana, gdy operacja find nie pasuje do dalszego tekstu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Domyślny styl obiektów `CEditView`typu .|

## <a name="remarks"></a>Uwagi

Klasa `CEditView` zawiera następujące dodatkowe funkcje:

- Drukowania.

- Znajdź i wymień.

Ponieważ `CEditView` klasa jest pochodną `CView`klasy, `CEditView` obiekty klasy mogą być używane z dokumentami i szablonami dokumentów.

Tekst `CEditView` każdego formantu jest przechowywany w jego własnym obiekcie pamięci globalnej. Aplikacja może mieć dowolną `CEditView` liczbę obiektów.

Utwórz obiekty `CEditView` typu, jeśli chcesz okno edycji z dodanymi funkcjami wymienionymi powyżej lub jeśli chcesz proste funkcje edytora tekstu. Obiekt `CEditView` może zajmować cały obszar klienta okna. Wyprowadzić własne klasy `CEditView` z dodać lub zmodyfikować podstawowe funkcje lub zadeklarować klasy, które mogą być dodawane do szablonu dokumentu.

Domyślna implementacja `CEditView` klasy obsługuje następujące polecenia: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT i ID_FILE_PRINT.

Domyślny limit `CEditView` znaków to (1024 \* 1024 - 1 = 1048575). Można to zmienić, wywołując funkcję EM_LIMITTEXT podstawowej kontroli edycji. Jednak limity różnią się w zależności od systemu operacyjnego i typu kontroli edycji (jedno- lub wielowierszowe). Aby uzyskać więcej informacji na temat tych limitów, zobacz [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Aby zmienić ten limit w formancie, należy zastąpić `OnCreate()` funkcję `CEditView` dla klasy i wstawić następujący wiersz kodu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Obiekty typu `CEditView` (lub typów pochodzących z `CEditView`) mają następujące ograniczenia:

- `CEditView`nie implementuje prawdziwego tego, co widzisz, jest to, co dostajesz (WYSIWYG) edycja. W przypadku wyboru między czytelnością na ekranie a `CEditView` pasującymi wydrukami, decyduje się na czytelność ekranu.

- `CEditView`tekst można wyświetlić tylko w jednej czcionce. Nie jest obsługiwane formatowanie znaków specjalnych. Zobacz klasy [CRichEditView](../../mfc/reference/cricheditview-class.md) większe możliwości.

- Ilość tekstu, `CEditView` który może zawierać, jest ograniczona. Limity są takie same `CEdit` jak dla formantu.

Aby uzyskać `CEditView`więcej informacji na temat , zobacz [Klasy widoku pochodnego dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

[Cctrlview](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="ceditviewceditview"></a><a name="ceditview"></a>CEditView::CEditView

Konstruuje obiekt `CEditView`typu .

```
CEditView();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy wywołać [CWnd::Create,](../../mfc/reference/cwnd-class.md#create) zanim zostanie użyty formant edycji. Jeśli pochodzisz klasy `CEditView` i dodać go do `CWinApp::AddDocTemplate`szablonu przy użyciu , `Create` ramach wywołuje zarówno tego konstruktora i funkcji.

## <a name="ceditviewdwstyledefault"></a><a name="dwstyledefault"></a>CEditView::dwStyleDefault

Zawiera domyślny styl `CEditView` obiektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Uwagi

Przekaż ten statyczny element członkowski jako `Create` parametr *dwStyle* funkcji, aby uzyskać domyślny `CEditView` styl dla obiektu.

## <a name="ceditviewfindtext"></a><a name="findtext"></a>CEditView::ZnajdźTekst

Wywołanie `FindText` funkcji, `CEditView` aby przeszukać bufor tekstu obiektu.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który należy znaleźć.

*bNastępna*<br/>
Określa kierunek wyszukiwania. Jeśli true, kierunek wyszukiwania znajduje się na końcu buforu. Jeśli FAŁDa, kierunek wyszukiwania znajduje się w kierunku początku buforu.

*bKasze*<br/>
Określa, czy w wyszukiwaniu jest rozróżniana wielkość liter. Jeśli wartość TRUE, w wyszukiwaniu rozróżniana jest wielkość liter. Jeśli FAŁDa, w wyszukiwaniu nie jest rozróżniana wielkość liter.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli tekst wyszukiwania zostanie znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja przeszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, zaczynając od bieżącego zaznaczenia, w kierunku określonym przez *bNext*i z czułością wielkości liter określoną przez *bCase*. Jeśli tekst zostanie znaleziony, ustawia zaznaczenie na znaleziony tekst i zwraca wartość niezerową. Jeśli tekst nie zostanie znaleziony, funkcja zwraca wartość 0.

Zwykle nie trzeba wywoływać `FindText` funkcji, chyba że `OnFindNext`zastąpisz `FindText`, który wywołuje .

## <a name="ceditviewgetbufferlength"></a><a name="getbufferlength"></a>CEditView::GetBufferLength

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać liczbę znaków aktualnie w buforze formantu edycji, z wyłączeniem zerowego terminatora.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w buforze.

## <a name="ceditviewgeteditctrl"></a><a name="geteditctrl"></a>CEditView::GetEditCtrl

Wywołanie, `GetEditCtrl` aby uzyskać odwołanie do formantu edycji używanego przez widok edycji.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CEdit` obiektu.

### <a name="remarks"></a>Uwagi

Ten formant jest typu [CEdit](../../mfc/reference/cedit-class.md), dzięki czemu można manipulować formantem edycji systemu Windows bezpośrednio za pomocą funkcji `CEdit` członkowskich.

> [!CAUTION]
> Za `CEdit` pomocą obiektu można zmienić stan podstawowej kontroli edycji systemu Windows. Na przykład nie należy zmieniać ustawień karty za pomocą funkcji [CEdit::SetTabStops,](../../mfc/reference/cedit-class.md#settabstops) ponieważ `CEditView` buforuje te ustawienia do użycia zarówno w formancie edycji, jak i podczas drukowania. Zamiast tego należy użyć [funkcji CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

## <a name="ceditviewgetprinterfont"></a><a name="getprinterfont"></a>CEditView::GetPrinterFont

Wywołanie, `GetPrinterFont` aby uzyskać wskaźnik do obiektu [CFont,](../../mfc/reference/cfont-class.md) który opisuje bieżącą czcionkę drukarki.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFont` obiektu określającego bieżącą czcionkę drukarki; NULL, jeśli czcionka drukarki nie została ustawiona. Wskaźnik może być tymczasowy i nie powinny być przechowywane do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Jeśli czcionka drukarki nie została ustawiona, `CEditView` domyślnym zachowaniem klasy jest drukowanie przy użyciu tej samej czcionki, która jest używana do wyświetlania.

Ta funkcja służy do określania bieżącej czcionki drukarki. Jeśli nie jest to żądana czcionka drukarki, użyj [CEditView::SetPrinterFont,](#setprinterfont) aby ją zmienić.

## <a name="ceditviewgetselectedtext"></a><a name="getselectedtext"></a>CEditView::GetSelectedText

Wywołanie `GetSelectedText` skopiowania zaznaczonego `CString` tekstu do obiektu, do końca zaznaczenia lub znaku poprzedzającego pierwszy znak powrotu karetki w zaznaczeniu.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strResult (wynik)*<br/>
Odwołanie do `CString` obiektu, który ma otrzymać zaznaczony tekst.

## <a name="ceditviewlockbuffer"></a><a name="lockbuffer"></a>CEditView::LockBuffer

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do buforu. Bufor nie powinien być modyfikowany.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu formantu edycji.

## <a name="ceditviewonfindnext"></a><a name="onfindnext"></a>CEditView::OnFindNext

Przeszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, w kierunku określonym przez *bNext*, z czułością wielkości literą określoną przez *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który należy znaleźć.

*bNastępna*<br/>
Określa kierunek wyszukiwania. Jeśli true, kierunek wyszukiwania znajduje się na końcu buforu. Jeśli FAŁDa, kierunek wyszukiwania znajduje się w kierunku początku buforu.

*bKasze*<br/>
Określa, czy w wyszukiwaniu jest rozróżniana wielkość liter. Jeśli wartość TRUE, w wyszukiwaniu rozróżniana jest wielkość liter. Jeśli FAŁDa, w wyszukiwaniu nie jest rozróżniana wielkość liter.

### <a name="remarks"></a>Uwagi

Wyszukiwanie rozpoczyna się na początku bieżącego zaznaczenia i odbywa się za pomocą wywołania [FindText](#findtext). W domyślnej `OnFindNext` implementacji wywołuje [OnTextNotFound,](#ontextnotfound) jeśli tekst nie zostanie znaleziony.

`OnFindNext` Zastąpić, aby `CEditView`zmienić sposób wyszukiwania tekstu przez obiekt pochodny. `CEditView`podczas `OnFindNext` wybierania przez użytkownika przycisku Znajdź następny w standardowym oknie dialogowym Znajdowanie.

## <a name="ceditviewonreplaceall"></a><a name="onreplaceall"></a>CEditView::OnReplaceAll

`CEditView`podczas `OnReplaceAll` wybierania przycisku Zamień wszystko w standardowym oknie dialogowym Zamień.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który należy znaleźć.

*lpszReplace (miejsce)*<br/>
Tekst zastępujący wyszukiwany tekst.

*bKasze*<br/>
Określa, czy w wyszukiwaniu jest rozróżniana wielkość liter. Jeśli wartość TRUE, w wyszukiwaniu rozróżniana jest wielkość liter. Jeśli FAŁDa, w wyszukiwaniu nie jest rozróżniana wielkość liter.

### <a name="remarks"></a>Uwagi

`OnReplaceAll`przeszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, z rozróżniaczem wielkości liter określoną przez *bCase*. Wyszukiwanie rozpoczyna się na początku bieżącego zaznaczenia. Za każdym razem, gdy zostanie znaleziony wyszukiwany tekst, ta funkcja zastępuje to wystąpienie tekstu tekstem określonym przez *lpszReplace*. Wyszukiwanie odbywa się za pomocą połączenia z [FindText](#findtext). W domyślnej implementacji [OnTextNotFound](#ontextnotfound) jest wywoływana, jeśli tekst nie zostanie znaleziony.

Jeśli bieżące zaznaczenie nie jest zgodne z *lpszFind*, zaznaczenie jest aktualizowane do pierwszego wystąpienia tekstu określonego przez *lpszFind* i zastema nie jest wykonywane. Dzięki temu użytkownik może potwierdzić, że jest to, co chce zrobić, gdy zaznaczenie nie pasuje do tekstu, który ma zostać zastąpiony.

`OnReplaceAll` Zastąp, aby `CEditView`zmienić sposób, w jaki obiekt pochodny zastępuje tekst.

## <a name="ceditviewonreplacesel"></a><a name="onreplacesel"></a>CEditView::OnReplaceSel

`CEditView`podczas `OnReplaceSel` wybierania przez użytkownika przycisku Zamień w standardowym oknie dialogowym Zamień.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który należy znaleźć.

*bNastępna*<br/>
Określa kierunek wyszukiwania. Jeśli true, kierunek wyszukiwania znajduje się na końcu buforu. Jeśli FAŁDa, kierunek wyszukiwania znajduje się w kierunku początku buforu.

*bKasze*<br/>
Określa, czy w wyszukiwaniu jest rozróżniana wielkość liter. Jeśli wartość TRUE, w wyszukiwaniu rozróżniana jest wielkość liter. Jeśli FAŁDa, w wyszukiwaniu nie jest rozróżniana wielkość liter.

*lpszReplace (miejsce)*<br/>
Tekst zastępujący znaleziony tekst.

### <a name="remarks"></a>Uwagi

Po zastąpieniu zaznaczenia funkcja ta przeszukuje tekst w buforze w celu następnego wystąpienia tekstu określonego przez *lpszFind*, w kierunku określonym przez *bNext*, z czułością wielkości liter określoną przez *bCase*. Wyszukiwanie odbywa się za pomocą połączenia z [FindText](#findtext). Jeśli tekst nie zostanie znaleziony, [OnTextNotFound](#ontextnotfound) jest wywoływana.

`OnReplaceSel` Zastąp, aby `CEditView`zmienić sposób, w jaki obiekt pochodny zastępuje zaznaczony tekst.

## <a name="ceditviewontextnotfound"></a><a name="ontextnotfound"></a>CEditView::OnTextNotFound

Zastąd w tej funkcji należy zmienić `MessageBeep`domyślną implementację, która wywołuje funkcję systemu Windows .

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*Lpszfind*<br/>
Tekst, który należy znaleźć.

## <a name="ceditviewprintinsiderect"></a><a name="printinsiderect"></a>CEditView::PrintInsideRect

Wywołanie `PrintInsideRect` drukowania tekstu w prostokącie określonym przez *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*reectLayout*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktury RECT](/windows/win32/api/windef/ns-windef-rect) określającej prostokąt, w którym ma być renderowany tekst.

*nIndexStart (Początek)*<br/>
Indeks w buforze pierwszego znaku, który ma być renderowany.

*nIndexStop (Stop)*<br/>
Indeks w buforze znaku następującego po ostatnim znaku do renderowania.

### <a name="return-value"></a>Wartość zwracana

Indeks następnego znaku do wydrukowania (czyli znak następujący po ostatnim renderowanym znaku).

### <a name="remarks"></a>Uwagi

Jeśli `CEditView` formant nie ma stylu ES_AUTOHSCROLL, tekst jest zawijany w prostokąt renderowania. Jeśli formant ma styl ES_AUTOHSCROLL, tekst jest przycięty na prawej krawędzi prostokąta.

Element `rect.bottom` obiektu *rectLayout* jest zmieniany w taki sposób, że wymiary prostokąta definiują część oryginalnego prostokąta zajmowaną przez tekst.

## <a name="ceditviewserializeraw"></a><a name="serializeraw"></a>CEditView::SerializeRaw

Wywołanie, `SerializeRaw` `CArchive` aby obiekt został odczytany `CEditView` lub wpisany tekst w obiekcie do pliku tekstowego.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
Odwołanie do `CArchive` obiektu, który przechowuje tekst seryjny.

### <a name="remarks"></a>Uwagi

`SerializeRaw`różni się `CEditView`od wewnętrznej `Serialize` implementacji w tym, że odczytuje i zapisuje tylko tekst, bez poprzednich danych opisu obiektu.

## <a name="ceditviewsetprinterfont"></a><a name="setprinterfont"></a>CEditView::SetPrinterFont

Wywołanie, `SetPrinterFont` aby ustawić czcionkę drukarki do czcionki określonej przez *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont (pFont)*<br/>
Wskaźnik do obiektu typu `CFont`. Jeśli null, czcionka używana do drukowania jest oparta na czcionce wyświetlanej.

### <a name="remarks"></a>Uwagi

Jeśli chcesz, aby widok zawsze używał określonej czcionki `SetPrinterFont` do drukowania, `OnPreparePrinting` dołącz wywołanie do funkcji klasy. Ta funkcja wirtualna jest wywoływana przed wystąpieniem drukowania, więc zmiana czcionki ma miejsce przed wydrukowaniem zawartości widoku.

## <a name="ceditviewsettabstops"></a><a name="settabstops"></a>CEditView::SetTabStops

Wywołanie tej funkcji, aby ustawić tabulatory używane do wyświetlania i drukowania.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops (Niem.*<br/>
Szerokość każdego tabulatora w jednostkach dialogowych.

### <a name="remarks"></a>Uwagi

Obsługiwane jest tylko pojedyncze szerokoście tabulatora. (obiekty `CEdit` obsługują wiele szerokości kart). Szerokości znajdują się w jednostkach dialogowych, które są równe jednej czwartej średniej szerokości znaku (tylko na podstawie wielkich i małych liter alfabetycznych) czcionki używanej w czasie drukowania lub wyświetlania. Nie należy `CEdit::SetTabStops` używać, ponieważ `CEditView` musi buforować wartość tabulatora.

Ta funkcja modyfikuje tylko karty obiektu, dla którego jest wywoływana. Aby zmienić tabulatory dla każdego `CEditView` obiektu w `SetTabStops` aplikacji, należy wywołać funkcję każdego obiektu.

### <a name="example"></a>Przykład

Ten fragment kodu ustawia tabulatora zatrzymuje się w formancie do co czwartego znaku, dokładnie mierząc czcionkę używa formant.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

## <a name="ceditviewunlockbuffer"></a><a name="unlockbuffer"></a>CEditView::UnlockBuffer

Wywołanie tej funkcji elementu członkowskiego, aby odblokować bufor.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Uwagi

Wywołanie `UnlockBuffer` po zakończeniu korzystania ze wskaźnika zwróconego przez [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Zobacz też

[Próbka MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
