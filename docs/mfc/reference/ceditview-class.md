---
title: Klasa elementu CEditView
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
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506729"
---
# <a name="ceditview-class"></a>Klasa elementu CEditView

Typ klasy widoku, która udostępnia funkcje kontrolki edycji systemu Windows i może służyć do implementowania prostych funkcji edytora tekstu.

## <a name="syntax"></a>Składnia

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Elementu CEditView:: elementu CEditView](#ceditview)|Konstruuje obiekt typu `CEditView`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Elementu CEditView:: ciąg FindText](#findtext)|Wyszukuje ciąg w tekście.|
|[Elementu CEditView:: GetBufferLength](#getbufferlength)|Uzyskuje długość buforu znaków.|
|[Elementu CEditView:: GetEditCtrl](#geteditctrl)|Zapewnia dostęp do `CEdit` części `CEditView` obiektu (kontrolki edycji systemu Windows).|
|[Elementu CEditView:: GetPrinterFont](#getprinterfont)|Pobiera bieżącą czcionkę drukarki.|
|[Elementu CEditView:: GetSelectedText](#getselectedtext)|Pobiera bieżący wybór tekstu.|
|[Elementu CEditView:: LockBuffer](#lockbuffer)|Blokuje bufor.|
|[Elementu CEditView::P rintInsideRect](#printinsiderect)|Renderuje tekst wewnątrz danego prostokąta.|
|[Elementu CEditView:: SerializeRaw](#serializeraw)|`CEditView` Serializować obiekt na dysk jako nieprzetworzony tekst.|
|[Elementu CEditView:: SetPrinterFont](#setprinterfont)|Ustawia nową czcionkę drukarki.|
|[Elementu CEditView:: SetTabStops](#settabstops)|Ustawia tabulatory dla wyświetlania ekranu i drukowania.|
|[Elementu CEditView:: UnlockBuffer](#unlockbuffer)|Odblokowuje bufor.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Elementu CEditView:: OnFindNext](#onfindnext)|Znajduje następne wystąpienie ciągu tekstowego.|
|[Elementu CEditView:: OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia danego ciągu z nowym ciągiem.|
|[Elementu CEditView:: OnReplaceSel](#onreplacesel)|Zastępuje bieżące zaznaczenie.|
|[Elementu CEditView:: OnTextNotFound](#ontextnotfound)|Wywołuje się, gdy nie można dopasować żadnego dodatkowego tekstu do operacji find.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Elementu CEditView::d wStyleDefault](#dwstyledefault)|Styl domyślny dla obiektów typu `CEditView`.|

## <a name="remarks"></a>Uwagi

`CEditView` Klasa udostępnia następujące dodatkowe funkcje:

- Drukowany.

- Znajdź i Zamień.

Ponieważ Klasa `CEditView` jest pochodną klasy `CView`, obiekty klasy `CEditView` mogą być używane z szablonami dokumentów i dokumentów.

Tekst `CEditView` każdego formantu jest przechowywany w jego własnym globalnym obiekcie pamięci. Aplikacja może mieć dowolną liczbę `CEditView` obiektów.

Utwórz obiekty typu `CEditView` , jeśli chcesz, aby okno edycji miało dodane funkcje wymienione powyżej, lub jeśli chcesz mieć prostą funkcję edytora tekstu. `CEditView` Obiekt może zajmować cały obszar klienta okna. Utwórz własne klasy z `CEditView` programu, aby dodać lub zmodyfikować podstawowe funkcje lub zadeklarować klasy, które można dodać do szablonu dokumentu.

Domyślna implementacja klasy `CEditView` obsługuje następujące polecenia: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT i ID_FILE_PRINT.

Domyślny limit znaków dla `CEditView` jest (1024 \* 1024-1 = 1048575). Można to zmienić, wywołując funkcję EM_LIMITTEXT bazowej kontrolki edycji. Jednak limity są różne w zależności od systemu operacyjnego i typu kontrolki edycji (pojedyncze lub wielowierszowe). Aby uzyskać więcej informacji na temat tych limitów, zobacz [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Aby zmienić ten limit w kontrolce, Przesłoń `OnCreate()` funkcję `CEditView` dla klasy i Wstaw następujący wiersz kodu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Obiekty typu `CEditView` (lub typy pochodne od `CEditView`) mają następujące ograniczenia:

- `CEditView`nie implementuje prawdziwej informacji o tym, co jest widoczne (WYSIWYG). Tam, gdzie istnieje wybór między możliwością czytelności na ekranie i dopasowanie wydruków `CEditView` , program umożliwia odczytywanie ekranu.

- `CEditView`może wyświetlać tekst tylko w jednej czcionce. Nie jest obsługiwane formatowanie znaków specjalnych. Zobacz klasy [CRichEditView](../../mfc/reference/cricheditview-class.md) , aby uzyskać więcej możliwości.

- Ilość tekstu, który może `CEditView` zawierać, jest ograniczona. Limity są takie same jak dla `CEdit` kontrolki.

Aby uzyskać więcej informacji `CEditView`na temat, zobacz [pochodne klasy widoków dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="ceditview"></a>Elementu CEditView:: elementu CEditView

Konstruuje obiekt typu `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy wywołać funkcję [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) przed użyciem kontrolki edycji. Jeśli dziedziczysz klasę z `CEditView` i dodasz ją do szablonu przy użyciu `CWinApp::AddDocTemplate`, struktura wywołuje `Create` zarówno ten Konstruktor, jak i funkcję.

##  <a name="dwstyledefault"></a>Elementu CEditView::d wStyleDefault

Zawiera domyślny styl `CEditView` obiektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Uwagi

Przekaż ten statyczny element członkowski jako parametr `Create` dwStyle funkcji, aby uzyskać styl `CEditView` domyślny dla obiektu.

##  <a name="findtext"></a>Elementu CEditView:: ciąg FindText

Wywołaj `FindText` funkcję, aby `CEditView` przeszukać bufor tekstu obiektu.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać znaleziony.

*bNext*<br/>
Określa kierunek wyszukiwania. W przypadku wartości TRUE kierunek wyszukiwania jest skierowany ku końcu buforu. W przypadku wartości FALSE kierunek wyszukiwania jest skierowany do początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku wartości TRUE wyszukiwanie uwzględnia wielkość liter. W przypadku wartości FALSE wyszukiwanie nie uwzględnia wielkości liter.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zostanie znaleziony tekst wyszukiwania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja przeszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, rozpoczynając od bieżącego zaznaczenia, w kierunku określonym przez *bNext*i z rozróżnianiem wielkości liter określonym przez *bCase*. Jeśli tekst zostanie znaleziony, ustawia zaznaczenie na znaleziony tekst i zwraca wartość różną od zera. Jeśli tekst nie zostanie znaleziony, funkcja zwróci wartość 0.

Zwykle nie trzeba wywoływać `FindText` funkcji, chyba że przesłonisz `OnFindNext`, które wywołania. `FindText`

##  <a name="getbufferlength"></a>Elementu CEditView:: GetBufferLength

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać liczbę znaków w buforze edycji, bez uwzględnienia terminatora wartości null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w buforze.

##  <a name="geteditctrl"></a>Elementu CEditView:: GetEditCtrl

Wywołaj `GetEditCtrl` , aby pobrać odwołanie do kontrolki edycji używanej przez widok edycji.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CEdit` obiektu.

### <a name="remarks"></a>Uwagi

Ten formant jest typu [CEdit](../../mfc/reference/cedit-class.md), więc można manipulować formantem edycji systemu Windows bezpośrednio przy użyciu `CEdit` funkcji Członkowskich.

> [!CAUTION]
>  `CEdit` Użycie obiektu może zmienić stan podstawowej kontrolki edycji systemu Windows. Na przykład nie należy zmieniać ustawień karty przy użyciu funkcji [CEdit:: SetTabStops](../../mfc/reference/cedit-class.md#settabstops) , ponieważ `CEditView` buforuje te ustawienia do użycia zarówno w kontrolce edycji, jak i w drukowaniu. Zamiast tego należy użyć [elementu CEditView:: SetTabStops](#settabstops).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>Elementu CEditView:: GetPrinterFont

Wywołaj `GetPrinterFont` , aby uzyskać wskaźnik do obiektu [CFont](../../mfc/reference/cfont-class.md) , który opisuje bieżącą czcionkę drukarki.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFont` obiektu, który określa bieżącą czcionkę drukarki; Wartość NULL, Jeśli czcionka drukarki nie została ustawiona. Wskaźnik może być tymczasowy i nie powinien być przechowywany do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Jeśli czcionka drukarki nie została ustawiona, domyślnym zachowaniem `CEditView` drukowania klasy jest Drukowanie przy użyciu tej samej czcionki, która jest używana do wyświetlania.

Użyj tej funkcji, aby określić bieżącą czcionkę drukarki. Jeśli nie jest to wymagana czcionka drukarki, użyj [elementu CEditView:: SetPrinterFont](#setprinterfont) , aby ją zmienić.

##  <a name="getselectedtext"></a>Elementu CEditView:: GetSelectedText

Wywołanie `GetSelectedText` kopiowania zaznaczonego tekstu `CString` do obiektu, do końca zaznaczenia lub znaku poprzedzającego pierwszy znak powrotu karetki w zaznaczeniu.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strResult*<br/>
Odwołanie do `CString` obiektu, który ma odebrać zaznaczony tekst.

##  <a name="lockbuffer"></a>Elementu CEditView:: LockBuffer

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do buforu. Bufor nie powinien być modyfikowany.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu kontrolki edycji.

##  <a name="onfindnext"></a>Elementu CEditView:: OnFindNext

Wyszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, w kierunku określonym przez *bNext*, z rozróżnianiem wielkości liter określoną przez *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać znaleziony.

*bNext*<br/>
Określa kierunek wyszukiwania. W przypadku wartości TRUE kierunek wyszukiwania jest skierowany ku końcu buforu. W przypadku wartości FALSE kierunek wyszukiwania jest skierowany do początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku wartości TRUE wyszukiwanie uwzględnia wielkość liter. W przypadku wartości FALSE wyszukiwanie nie uwzględnia wielkości liter.

### <a name="remarks"></a>Uwagi

Wyszukiwanie rozpoczyna się od początku bieżącego wyboru i jest realizowane przez wywołanie [ciąg FindText](#findtext). W implementacji domyślnej program wywołuje `OnFindNext` [OnTextNotFound](#ontextnotfound) , jeśli tekst nie zostanie znaleziony.

Przesłoń `OnFindNext` , aby zmienić sposób `CEditView`wyszukiwania tekstu przez obiekt pochodny. `CEditView`wywołuje `OnFindNext` się, gdy użytkownik wybierze przycisk Znajdź dalej w oknie dialogowym Wyszukiwanie standardowe.

##  <a name="onreplaceall"></a>Elementu CEditView:: OnReplaceAll

`CEditView`wywołuje `OnReplaceAll` się, gdy użytkownik wybierze przycisk Zamień wszystko w oknie dialogowym zastąpienie standardowe.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać znaleziony.

*lpszReplace*<br/>
Tekst, w którym ma zostać zamieniony tekst wyszukiwania.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku wartości TRUE wyszukiwanie uwzględnia wielkość liter. W przypadku wartości FALSE wyszukiwanie nie uwzględnia wielkości liter.

### <a name="remarks"></a>Uwagi

`OnReplaceAll`Przeszukuje tekst w buforze dla tekstu określonego przez *lpszFind*, z rozróżnianiem wielkości liter określonego przez *bCase*. Wyszukiwanie rozpoczyna się na początku bieżącego zaznaczenia. Za każdym razem, gdy wyszukiwany tekst zostanie znaleziony, ta funkcja zamienia to wystąpienie tekstu na tekst określony przez *lpszReplace*. Wyszukiwanie jest realizowane przez wywołanie [ciąg FindText](#findtext). W implementacji domyślnej [OnTextNotFound](#ontextnotfound) jest wywoływana, jeśli tekst nie zostanie znaleziony.

Jeśli bieżące zaznaczenie nie jest zgodne z *lpszFind*, zaznaczenie zostanie zaktualizowane do pierwszego wystąpienia tekstu określonego przez *lpszFind* , a zastąpienie nie zostanie wykonane. Dzięki temu użytkownik może potwierdzić, że jest to co chcesz zrobić, gdy zaznaczenie nie jest zgodne z tekstem, który ma zostać zastąpiony.

Przesłoń `OnReplaceAll` , aby zmienić sposób `CEditView`zamieniania tekstu przez obiekt pochodny.

##  <a name="onreplacesel"></a>Elementu CEditView:: OnReplaceSel

`CEditView`wywołuje `OnReplaceSel` się, gdy użytkownik wybierze przycisk Zamień w oknie dialogowym zastąpienie standardowe.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać znaleziony.

*bNext*<br/>
Określa kierunek wyszukiwania. W przypadku wartości TRUE kierunek wyszukiwania jest skierowany ku końcu buforu. W przypadku wartości FALSE kierunek wyszukiwania jest skierowany do początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku wartości TRUE wyszukiwanie uwzględnia wielkość liter. W przypadku wartości FALSE wyszukiwanie nie uwzględnia wielkości liter.

*lpszReplace*<br/>
Tekst, który ma zastąpić znaleziony tekst.

### <a name="remarks"></a>Uwagi

Po zamianie zaznaczenia ta funkcja przeszukuje tekst w buforze dla następnego wystąpienia tekstu określonego przez *lpszFind*, w kierunku określonym przez *bNext*, z rozróżnianiem wielkości liter określoną przez *bCase*. Wyszukiwanie jest realizowane przez wywołanie [ciąg FindText](#findtext). Jeśli tekst nie zostanie znaleziony, [OnTextNotFound](#ontextnotfound) jest wywoływana.

Przesłoń `OnReplaceSel` , aby zmienić `CEditView`sposób zamieniania zaznaczonego tekstu przez obiekt pochodny.

##  <a name="ontextnotfound"></a>Elementu CEditView:: OnTextNotFound

Zastąp tę funkcję, aby zmienić implementację domyślną, która wywołuje funkcję `MessageBeep`systemu Windows.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać znaleziony.

##  <a name="printinsiderect"></a>Elementu CEditView::P rintInsideRect

Wywołanie `PrintInsideRect` do drukowania tekstu w prostokącie określonym przez *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*rectLayout*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktury Rect](/windows/win32/api/windef/ns-windef-rect) określające prostokąt, w którym ma być renderowany tekst.

*nIndexStart*<br/>
Indeks w buforze pierwszego znaku, który ma być renderowany.

*nIndexStop*<br/>
Indeks w buforze znaku następującego po ostatnim znaku do renderowania.

### <a name="return-value"></a>Wartość zwracana

Indeks następnego znaku do wydrukowania (oznacza to, że znak następujący po ostatnim znaku jest renderowany).

### <a name="remarks"></a>Uwagi

`CEditView` Jeśli kontrolka nie ma stylu ES_AUTOHSCROLL, tekst jest zawijany w obrębie prostokąta renderowania. Jeśli kontrolka ma styl ES_AUTOHSCROLL, tekst zostanie przycięty do prawej krawędzi prostokąta.

Element obiektu rectLayout został zmieniony tak, aby wymiary prostokąta definiują część oryginalnego prostokąta, który jest zajmowany przez tekst. `rect.bottom`

##  <a name="serializeraw"></a>Elementu CEditView:: SerializeRaw

Wywołanie `SerializeRaw` w celu `CArchive` odczytania obiektu lub `CEditView` zapisanie tekstu w obiekcie do pliku tekstowego.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
Odwołanie do `CArchive` obiektu, który przechowuje Zserializowany tekst.

### <a name="remarks"></a>Uwagi

`SerializeRaw`różni się `CEditView`od wewnętrznej `Serialize` implementacji w programie, który odczytuje i zapisuje tylko tekst, bez poprzedzających danych opisu obiektu.

##  <a name="setprinterfont"></a>Elementu CEditView:: SetPrinterFont

Wywołaj `SetPrinterFont` , aby ustawić czcionkę drukarki na czcionkę określoną przez *pfont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do obiektu typu `CFont`. Jeśli wartość jest równa NULL, czcionka używana do drukowania jest zależna od czcionki wyświetlania.

### <a name="remarks"></a>Uwagi

Jeśli chcesz, aby widok zawsze używał określonej czcionki do drukowania, Uwzględnij wywołanie `SetPrinterFont` w `OnPreparePrinting` funkcji klasy. Ta funkcja wirtualna jest wywoływana przed rozpoczęciem drukowania, więc zmiana czcionki odbywa się przed wydrukowaniem zawartości widoku.

##  <a name="settabstops"></a>Elementu CEditView:: SetTabStops

Wywołaj tę funkcję, aby ustawić tabulatory używane do wyświetlania i drukowania.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops*<br/>
Szerokość każdego tabulatora w jednostkach okna dialogowego.

### <a name="remarks"></a>Uwagi

Obsługiwana jest tylko jedna szerokość tabulatora. ( `CEdit` obiekty obsługują wiele szerokości tabulacji). Szerokości znajdują się w jednostkach okna dialogowego, co jest równe jednej czwartej średniej szerokości znaków (w oparciu o wielkie i małe litery alfabetu) czcionki używanej w czasie drukowania lub wyświetlania. Nie należy używać `CEdit::SetTabStops` , ponieważ `CEditView` należy buforować wartość tabulatora.

Ta funkcja modyfikuje tylko karty obiektu, dla którego jest wywoływana. Aby zmienić tabulatory dla każdego `CEditView` obiektu w aplikacji, wywołaj `SetTabStops` funkcję każdego obiektu.

### <a name="example"></a>Przykład

Ten fragment kodu ustawia tabulatory w kontrolce na każdy czwarty znak, starannie mierząc czcionkę używaną przez kontrolkę.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>Elementu CEditView:: UnlockBuffer

Wywołaj tę funkcję elementu członkowskiego, aby odblokować bufor.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Uwagi

Wywołaj `UnlockBuffer` po zakończeniu korzystania ze wskaźnika zwróconego przez [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Zobacz także

[Przykład SUPERPAD MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
