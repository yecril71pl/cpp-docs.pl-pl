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
ms.openlocfilehash: e853a770dd1f98b1e7f06afd814962f3b3805ceb
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177878"
---
# <a name="ceditview-class"></a>Klasa CEditView

Typ widoku klasy, która udostępnia funkcje Windows formantu edycyjnego i może służyć do implementowania prostego edytora tekstu.

## <a name="syntax"></a>Składnia

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Tworzy obiekt typu `CEditView`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Wyszukuje ciąg w tekście.|
|[CEditView::GetBufferLength](#getbufferlength)|Pobiera długość buforu znaków.|
|[CEditView::GetEditCtrl](#geteditctrl)|Zapewnia dostęp do `CEdit` część `CEditView` obiektu (Windows formantu edycyjnego,).|
|[CEditView::GetPrinterFont](#getprinterfont)|Pobiera bieżącą czcionkę drukarki.|
|[CEditView::GetSelectedText](#getselectedtext)|Pobiera aktualnie zaznaczonego tekstu.|
|[CEditView::LockBuffer](#lockbuffer)|Blokuje buforu.|
|[CEditView::PrintInsideRect](#printinsiderect)|Wyświetla tekst wewnątrz danego prostokąta.|
|[CEditView::SerializeRaw](#serializeraw)|Serializuje `CEditView` obiektu na dysku jako nieprzetworzony tekst.|
|[CEditView::SetPrinterFont](#setprinterfont)|Ustawia czcionkę nowe drukarki.|
|[CEditView::SetTabStops](#settabstops)|Ustawia tabulatora drukowanie i wyświetlanie na ekranie.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Odblokowuje buforu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Znajduje następne wystąpienie ciągu tekstowego.|
|[CEditView::OnReplaceAll](#onreplaceall)|Zamienia wszystkie wystąpienia podanego ciągu nowy ciąg.|
|[CEditView::OnReplaceSel](#onreplacesel)|Zamienia bieżące zaznaczenie.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Wywołuje się, gdy operacja wyszukiwania nie powiedzie się dopasować dowolny tekst dalszych.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Domyślny styl dla obiektów typu `CEditView`.|

## <a name="remarks"></a>Uwagi

`CEditView` Klasa oferuje następujące dodatkowe funkcje:

- Drukowanie.

- Znajdź i Zamień.

Ponieważ klasa `CEditView` jest pochodną klasy `CView`, obiekty klasy `CEditView` mogą być używane z dokumentów i szablonów dokumentów.

Każdy `CEditView` tekst kontrolki jest przechowywana w obiekcie własnej globalnej pamięci. Twoja aplikacja może mieć dowolną liczbę `CEditView` obiektów.

Tworzenie obiektów typu `CEditView` okno edycji o dodatkowe funkcje wymienione powyżej, lub jeśli chcesz, aby funkcje prostego edytora tekstu. Element `CEditView` obiektu mogą zajmować całego obszaru klienta okna. Pochodzi własnych klas z `CEditView` do dodawania lub modyfikowania podstawowych funkcji lub aby zadeklarować klasy, które można dodać do szablonu dokumentu.

Domyślna implementacja klasy `CEditView` obsługuje następujące polecenia: Id_edit_select_all — id_edit_find —, id_edit_replace —, id_edit_repeat — i ID_FILE_PRINT.

Domyślny limit znaków `CEditView` jest (1024 \* 1024-1 = 1048575). Można to zmienić, wywołując funkcję EM_LIMITTEXT podstawowej kontrolki edycji. Jednak ograniczenia są różne w zależności od systemu operacyjnego i typu pole edycji (pojedyncze lub wielowierszowy). Aby uzyskać więcej informacji na temat tych ograniczeń, zobacz [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext).

Aby zmienić ten limit w kontrolce, należy zastąpić `OnCreate()` funkcji dla Twojego `CEditView` klasy i Wstaw następujący wiersz kodu:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Obiekty typu `CEditView` (lub typy pochodzące z `CEditView`) mają następujące ograniczenia:

- `CEditView` nie implementuje true zostanie wyświetlony jest w ofercie edytowania (WYSIWYG). W przypadku, gdy ma możliwość wyboru między czytelność na ekranie i dopasowania wydruku `CEditView` zdecyduje się na ekranie czytelności.

- `CEditView` można wyświetlić tekst w jednej czcionki. Formatowanie znaków specjalnych nie jest obsługiwane. Można znaleźć klasy [CRichEditView](../../mfc/reference/cricheditview-class.md) większe możliwości.

- Ilość tekstu `CEditView` może zawierać jest ograniczona. Ograniczenia są takie same jak w przypadku `CEdit` kontroli.

Aby uzyskać więcej informacji na temat `CEditView`, zobacz [pochodne Widok klas dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="ceditview"></a>  CEditView::CEditView

Tworzy obiekt typu `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, należy wywołać [CWnd::Create](../../mfc/reference/cwnd-class.md#create) działać, zanim zostaną użyte kontrolki edycji. Jeśli wyprowadzić klasę z `CEditView` i dodaj go do szablonu, za pomocą `CWinApp::AddDocTemplate`, struktura wywołuje zarówno ten konstruktor i `Create` funkcji.

##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault

Zawiera domyślny styl `CEditView` obiektu.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Uwagi

Przekaż ten statyczny element członkowski jako *dwStyle* parametru `Create` funkcję, aby uzyskać domyślny styl `CEditView` obiektu.

##  <a name="findtext"></a>  CEditView::FindText

Wywołaj `FindText` funkcję, aby wyszukać `CEditView` bufor tekstowy tego obiektu.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać odnaleziona.

*bDalej*<br/>
Określa kierunek wyszukiwania. W przypadku opcji TRUE kierunek wyszukiwania jest pod koniec buforu. W przypadku wartości FAŁSZ kierunek wyszukiwania jest kierunku początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku opcji TRUE wyszukiwania jest uwzględniana wielkość liter. W przypadku wartości FAŁSZ wyszukiwania nie jest uwzględniana wielkość liter.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zostanie znaleziony tekst wyszukiwania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja wyszukuje tekst w buforze tekstu określonego przez *lpszFind*, począwszy od bieżącego zaznaczenia, w kierunku określony przez *bDalej*i uwzględniając wielkość liter, określonej przez *bCase*. Jeśli zostanie znaleziony tekst, ustawia zaznaczenie znaleziony tekst i zwraca wartość różną od zera. Jeśli tekst nie zostanie znaleziony, funkcja zwraca 0.

Zwykle nie trzeba wywoływać `FindText` działać, chyba że przesłonisz `OnFindNext`, która wywołuje metodę `FindText`.

##  <a name="getbufferlength"></a>  CEditView::GetBufferLength

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać liczbę znaków, obecnie w buforze kontrolki edycji, nie wliczając terminator o wartości null.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w buforze.

##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl

Wywołaj `GetEditCtrl` można pobrać odwołania do kontrolki edycji używane przez widok edycji.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CEdit` obiektu.

### <a name="remarks"></a>Uwagi

Ten formant jest typu [CEdit](../../mfc/reference/cedit-class.md), dzięki czemu można manipulować bezpośrednio przy użyciu kontrolki edycji Windows `CEdit` funkcji elementów członkowskich.

> [!CAUTION]
>  Za pomocą `CEdit` obiektu, Zmień stan bazowego Windows można edytować kontrolkę. Na przykład nie należy zmieniać ustawień karty przy użyciu [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) działać, ponieważ `CEditView` buforuje te ustawienia do użycia zarówno w formancie edycji w drukowania. Zamiast tego należy użyć [CEditView::SetTabStops](#settabstops).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont

Wywołaj `GetPrinterFont` uzyskać wskaźnik do [CFont](../../mfc/reference/cfont-class.md) obiekt, który opisuje bieżącą czcionkę drukarki.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFont` obiektu, który określa bieżącą czcionkę drukarki; Wartość NULL, jeśli nie zostało ustawione na czcionkę drukarki. Wskaźnik mogą być tymczasowe i nie powinny być przechowywane do późniejszego użycia.

### <a name="remarks"></a>Uwagi

Jeśli czcionka drukarki nie została ustawiona, domyślne zachowanie drukowanie `CEditView` klasa jest drukowanie przy użyciu tego samego czcionki używanej do wyświetlania.

Aby określić bieżącą czcionkę drukarki, należy użyć tej funkcji. Jeśli nie jest czcionka żądaną drukarki, użyj [CEditView::SetPrinterFont](#setprinterfont) go zmienić.

##  <a name="getselectedtext"></a>  CEditView::GetSelectedText

Wywołaj `GetSelectedText` do zaznaczonego tekstu do skopiowania `CString` obiektu, aż do końca zaznaczenia lub znak poprzedzający pierwszy znak powrotu karetki w zaznaczeniu.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parametry

*strResult*<br/>
Odwołanie do `CString` obiektu, który ma otrzymać zaznaczony tekst.

##  <a name="lockbuffer"></a>  CEditView::LockBuffer

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do buforu. Bufor nie powinien być modyfikowany.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu kontrolki edycji.

##  <a name="onfindnext"></a>  CEditView::OnFindNext

Wyszukuje tekst w buforze tekstu określonego przez *lpszFind*, w kierunku określony przez *bDalej*, uwzględniając wielkość liter, określonej przez *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać odnaleziona.

*bDalej*<br/>
Określa kierunek wyszukiwania. W przypadku opcji TRUE kierunek wyszukiwania jest pod koniec buforu. W przypadku wartości FAŁSZ kierunek wyszukiwania jest kierunku początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku opcji TRUE wyszukiwania jest uwzględniana wielkość liter. W przypadku wartości FAŁSZ wyszukiwania nie jest uwzględniana wielkość liter.

### <a name="remarks"></a>Uwagi

Wyszukiwanie rozpoczyna się od początku bieżącego zaznaczenia i odbywa się za pomocą wywołania [FindText](#findtext). W implementacji domyślnej `OnFindNext` wywołania [OnTextNotFound](#ontextnotfound) Jeśli tekst nie zostanie znaleziony.

Zastąp `OnFindNext` zmianę sposobu `CEditView`-pochodnego obiektu wyszukiwania tekstu. `CEditView` wywołania `OnFindNext` kiedy użytkownik naciśnie przycisk Znajdź następny standardowe okno dialogowe Znajdź.

##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll

`CEditView` wywołania `OnReplaceAll` gdy użytkownik wybierze przycisk Zastąp wszystkie standardowe okno dialogowe Zastąp.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać odnaleziona.

*lpszReplace*<br/>
Tekst, aby zamienić tekst wyszukiwania.

*bCase*<br/>
Określa, czy wyszukiwanie uwzględnia wielkość liter. W przypadku opcji TRUE wyszukiwania jest uwzględniana wielkość liter. W przypadku wartości FAŁSZ wyszukiwania nie jest uwzględniana wielkość liter.

### <a name="remarks"></a>Uwagi

`OnReplaceAll` Wyszukuje tekst w buforze tekstu określonego przez *lpszFind*, uwzględniając wielkość liter, określonej przez *bCase*. Wyszukiwanie rozpoczyna się od początku bieżącego zaznaczenia. Każdorazowo zostanie znaleziony tekst wyszukiwania, ta funkcja zastępuje to wystąpienie tekstu z tekstem określonym przez *lpszReplace*. Wyszukiwanie odbywa się za pomocą wywołania [FindText](#findtext). W implementacji domyślnej [OnTextNotFound](#ontextnotfound) jest wywoływana, gdy tekst nie zostanie odnaleziony.

Jeśli bieżące zaznaczenie jest niezgodny *lpszFind*, wybór jest aktualizowany do pierwszego wystąpienia tekstu określonego przez *lpszFind* i Zastąp nie jest wykonywane. Dzięki temu użytkownik upewnić się, że to mają wykonać, jeśli zaznaczenie jest niezgodna z tekst, który ma zostać zastąpione.

Zastąp `OnReplaceAll` zmianę sposobu `CEditView`— obiekt pochodnej zamienia tekst.

##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel

`CEditView` wywołania `OnReplaceSel` gdy użytkownik wybierze przycisk Zastąp standardowe okno dialogowe Zastąp.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać odnaleziona.

*bDalej*<br/>
Określa kierunek wyszukiwania. W przypadku opcji TRUE kierunek wyszukiwania jest pod koniec buforu. W przypadku wartości FAŁSZ kierunek wyszukiwania jest kierunku początku buforu.

*bCase*<br/>
Określa, czy w wyszukiwaniu jest uwzględniana wielkość liter. W przypadku opcji TRUE wyszukiwania jest uwzględniana wielkość liter. W przypadku wartości FAŁSZ wyszukiwania nie jest uwzględniana wielkość liter.

*lpszReplace*<br/>
Tekst do zastąpienia znaleziony tekst.

### <a name="remarks"></a>Uwagi

Po zastąpieniu zaznaczenia, ta funkcja wyszukuje tekst w buforze na następne wystąpienie tekstu określonego przez *lpszFind*, w kierunku określony przez *bDalej*, uwzględniając wielkość liter określony przez *bCase*. Wyszukiwanie odbywa się za pomocą wywołania [FindText](#findtext). Jeśli tekst nie zostanie znaleziony, [OnTextNotFound](#ontextnotfound) jest wywoływana.

Zastąp `OnReplaceSel` zmianę sposobu `CEditView`— obiekt pochodnej zastępuje zaznaczonego tekstu.

##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound

Przesłonić tę funkcję, aby zmienić domyślną implementację, która wywołuje funkcję Windows `MessageBeep`.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parametry

*lpszFind*<br/>
Tekst, który ma zostać odnaleziona.

##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect

Wywołaj `PrintInsideRect` do drukowania tekstu w prostokącie określonego przez *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskaźnik do kontekstu urządzenia drukarki.

*rectLayout*<br/>
Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [struktura RECT](/windows/desktop/api/windef/ns-windef-tagrect) Określanie prostokąt, w którym ma być renderowany tekstu.

*nIndexStart*<br/>
Indeks w buforze pierwszego znaku do renderowania.

*nIndexStop*<br/>
Indeks w buforze znak po ostatnim znaku do renderowania.

### <a name="return-value"></a>Wartość zwracana

Indeks następny znak do wydrukowania (czyli znak po ostatnim znaku renderowania).

### <a name="remarks"></a>Uwagi

Jeśli `CEditView` formant nie ma stylu ES_AUTOHSCROLL, opakowaniu tekstu w prostokącie renderowania. Jeśli kontrolka ma styl ES_AUTOHSCROLL, zostanie obcięta przy prawej krawędzi prostokąta.

`rect.bottom` Elementu *rectLayout* jest zmiany obiektu, dzięki czemu wymiary prostokąta zdefiniować część oryginalnego prostokąt, który jest zajęta przez tekst.

##  <a name="serializeraw"></a>  CEditView::SerializeRaw

Wywołaj `SerializeRaw` mieć `CArchive` obiektu odczytu lub wpisać tekst `CEditView` obiektu do pliku tekstowego.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Odwołanie do `CArchive` obiekt, który przechowuje serializowane tekstu.

### <a name="remarks"></a>Uwagi

`SerializeRaw` różni się od `CEditView`firmy wewnętrzną implementację `Serialize` , odczytuje i zapisuje tylko tekst, bez poprzedzającej opis obiektu danych.

##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont

Wywołaj `SetPrinterFont` można ustawić czcionkę drukarki na czcionkę, określony przez *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Wskaźnik do obiektu typu `CFont`. Jeśli ma wartość NULL, czcionka używana na potrzeby drukowania opiera się na wyświetlanie czcionek.

### <a name="remarks"></a>Uwagi

Widok, aby zawsze używać wybranej czcionki do drukowania, można dołączyć wywołanie `SetPrinterFont` w swojej klasie `OnPreparePrinting` funkcji. Ta wirtualna funkcja jest wywoływana, zanim nastąpi drukowania, więc zmiana czcionki, ma miejsce przed jego treść, wydrukowaniu.

##  <a name="settabstops"></a>  CEditView::SetTabStops

Wywołaj tę funkcję, aby ustawienie pozycji tabulatorów używane do wyświetlania i drukowania.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parametry

*nTabStops*<br/>
Szerokość każdego tabulatora w jednostkach okna dialogowego.

### <a name="remarks"></a>Uwagi

Tylko pojedynczy szerokość tabulatora, jest obsługiwane. ( `CEdit` obiekty obsługują wiele szerokości karty.) Szerokości znajdują się w jednostkach okna dialogowego, które równa jednej czwartej średnia szerokość znaków (oparte na wielkie i małe litery alfabetu tylko) czcionki używanej w czasie drukowania lub wyświetlanie. Nie należy używać `CEdit::SetTabStops` ponieważ `CEditView` musi buforowania wartości tabulatora.

Ta funkcja modyfikuje tylko karty obiektu, dla którego jest wywoływana. Można zmienić na karcie zatrzymuje działanie dla każdego `CEditView` obiektów w aplikacji, wywołaj każdy obiekt `SetTabStops` funkcji.

### <a name="example"></a>Przykład

Ten fragment kodu ustawia pozycji tabulatorów w kontrolce do każdego znaku czwartego mierząc dokładnie czcionkę, której używa kontrolki.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>  CEditView::UnlockBuffer

Wywołaj tę funkcję elementu członkowskiego, aby odblokować buforu.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Uwagi

Wywołaj `UnlockBuffer` po zakończeniu przy użyciu wskaźnika zwrócony przez [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Zobacz też

[Próbki MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Klasa CRichEditView](../../mfc/reference/cricheditview-class.md)
