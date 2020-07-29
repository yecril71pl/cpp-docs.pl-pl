---
title: Klasa CEdit
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 1cf195401f74261d3e67d5e8e945d1278ff2f90b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212504"
---
# <a name="cedit-class"></a>Klasa CEdit

Oferuje funkcje kontrolki edycji systemu Windows.

## <a name="syntax"></a>Składnia

```
class CEdit : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit:: CEdit](#cedit)|Konstruuje `CEdit` obiekt Control.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit:: anulowanie](#canundo)|Określa, czy można cofnąć operację edycji kontrolki.|
|[CEdit:: CharFromPos](#charfrompos)|Pobiera indeksy wierszy i znaków dla znaku znajdującego się najbliżej określonego położenia.|
|[CEdit:: Clear](#clear)|Usuwa (czyści) bieżące zaznaczenie (jeśli istnieje) w kontrolce Edycja.|
|[CEdit:: Copy](#copy)|Kopiuje bieżące zaznaczenie (jeśli istnieje) w kontrolce Edycja do Schowka w formacie CF_TEXT.|
|[CEdit:: Create](#create)|Tworzy formant edycji systemu Windows i dołącza go do `CEdit` obiektu.|
|[CEdit:: Wytnij](#cut)|Usuwa (wycina) bieżące zaznaczenie (jeśli istnieje) w kontrolce Edycja i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.|
|[CEdit:: EmptyUndoBuffer](#emptyundobuffer)|Resetuje (czyści) flagę cofania kontrolki edycji.|
|[CEdit:: FmtLines](#fmtlines)|Ustawia włączenie lub wyłączenie znaków miękkiej przerwy liniowej w kontrolce edycji wielowierszowej.|
|[CEdit:: GetCueBanner](#getcuebanner)|Pobiera tekst wyświetlany jako wskaźnik tekstowy lub Porada w kontrolce edycji, gdy kontrolka jest pusta i nie ma fokusu.|
|[CEdit:: GetFirstVisibleLine](#getfirstvisibleline)|Określa skrajny widoczny wiersz w kontrolce edycji.|
|[CEdit:: GetHandle](#gethandle)|Pobiera dojście do pamięci, która jest aktualnie przypisana do wielowierszowej kontrolki edycji.|
|[CEdit:: getpodświetl](#gethighlight)|Pobiera indeksy znaków początkowych i końcowych w zakresie tekstu, który jest wyróżniony w bieżącym formancie edycji.|
|[CEdit:: GetLimitText](#getlimittext)|Pobiera maksymalną ilość tekstu, który `CEdit` może zawierać.|
|[CEdit:: getline](#getline)|Pobiera wiersz tekstu z kontrolki edycji.|
|[CEdit:: GetLineCount](#getlinecount)|Pobiera liczbę wierszy w kontrolce edycji z wieloma wierszami.|
|[CEdit:: GetMargins](#getmargins)|Pobiera lewy i prawy margines dla tego elementu `CEdit` .|
|[CEdit:: GetModify](#getmodify)|Określa, czy zawartość kontrolki edycji została zmodyfikowana.|
|[CEdit:: GetPasswordChar](#getpasswordchar)|Pobiera znak hasła wyświetlany w kontrolce edycji, gdy użytkownik wprowadza tekst.|
|[CEdit:: getRect](#getrect)|Pobiera prostokąt formatowania kontrolki edycji.|
|[CEdit:: GetSel](#getsel)|Pobiera pierwsze i ostatnie znaki z bieżącego zaznaczenia w kontrolce edycji.|
|[CEdit:: HideBalloonTip](#hideballoontip)|Ukrywa wszelką wskazówkę dymkową skojarzoną z bieżącą kontrolką edycji.|
|[CEdit:: LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić do kontrolki edycji.|
|[CEdit:: LineFromChar](#linefromchar)|Pobiera numer wiersza, który zawiera określony indeks znaków.|
|[CEdit:: LineIndex](#lineindex)|Pobiera indeks znaku wiersza w kontrolce edycji wielowierszowej.|
|[CEdit:: LineLength](#linelength)|Pobiera długość wiersza w kontrolce edycji.|
|[CEdit:: LineScroll](#linescroll)|Przewija tekst kontrolki edycji z wieloma wierszami.|
|[CEdit::P Kopiuj](#paste)|Wstawia dane ze schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.|
|[CEdit::P osFromChar](#posfromchar)|Pobiera współrzędne lewego górnego rogu określonego indeksu znaków.|
|[CEdit:: ReplaceSel](#replacesel)|Zastępuje bieżące zaznaczenie w kontrolce edycji określonym tekstem.|
|[CEdit:: SetCueBanner](#setcuebanner)|Ustawia tekst wyświetlany jako wskaźnik tekstowy lub Porada w kontrolce edycji, gdy kontrolka jest pusta i nie ma fokusu.|
|[CEdit:: SetHandle](#sethandle)|Ustawia dojście do pamięci lokalnej, która będzie używana przez wielowierszową kontrolkę edycji.|
|[CEdit:: setpodświetl](#sethighlight)|Podświetla zakres tekstu, który jest wyświetlany w bieżącym formancie edycji.|
|[CEdit:: SetLimitText](#setlimittext)|Ustawia maksymalną ilość tekstu, który `CEdit` może zawierać.|
|[CEdit:: Setmargins](#setmargins)|Ustawia lewy i prawy margines dla tego elementu `CEdit` .|
|[CEdit:: SetModify](#setmodify)|Ustawia lub czyści flagę modyfikacji kontrolki edycji.|
|[CEdit:: SetPasswordChar](#setpasswordchar)|Ustawia lub usuwa znak hasła wyświetlany w kontrolce edycji, gdy użytkownik wprowadza tekst.|
|[CEdit:: SetReadOnly](#setreadonly)|Ustawia stan tylko do odczytu kontrolki edycji.|
|[CEdit:: SetRect](#setrect)|Ustawia prostokąt formatowania kontrolki edycji z wieloma wierszami i aktualizuje formant.|
|[CEdit:: SetRectNP](#setrectnp)|Ustawia prostokąt formatowania kontrolki edycji z wieloma wierszami bez ponownego rysowania okna kontroli.|
|[CEdit:: SetSel](#setsel)|Wybiera zakres znaków w kontrolce edycji.|
|[CEdit:: SetTabStops](#settabstops)|Ustawia tabulator w kontrolce edycji wielowierszowej.|
|[CEdit:: ShowBalloonTip](#showballoontip)|Wyświetla wskazówkę dymkową, która jest skojarzona z bieżącą kontrolką edycji.|
|[CEdit:: Undo](#undo)|Odwraca ostatnią operację edycji.|

## <a name="remarks"></a>Uwagi

Kontrolka edycji jest prostokątnym oknem podrzędnym, w którym użytkownik może wpisać tekst.

Kontrolkę edycji można utworzyć z poziomu szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach najpierw Wywołaj konstruktora `CEdit` w celu skonstruowania `CEdit` obiektu, a następnie wywołaj funkcję [tworzenia](#create) elementu członkowskiego, aby utworzyć kontrolkę Edycja systemu Windows i dołączyć ją do `CEdit` obiektu.

Konstrukcja może być procesem jednoetapowym klasy pochodzącej od `CEdit` . Napisz konstruktora dla klasy pochodnej i Wywołaj `Create` z konstruktora.

`CEdit`dziedziczy znaczące funkcje z `CWnd` . Aby ustawić i pobrać tekst z `CEdit` obiektu, użyj `CWnd` funkcji składowych [SetWindowText](cwnd-class.md#setwindowtext) i [GetWindowText](cwnd-class.md#getwindowtext), które ustawiają lub pobierają całą zawartość kontrolki edycji, nawet jeśli jest to formant wielowierszowy. Wiersze tekstu w kontrolce wielowierszowej są oddzielone sekwencjami znaków "\r\n". Ponadto, Jeśli kontrolka edycji jest wielowierszowa, Pobierz i ustaw część tekstu kontrolki, wywołując `CEdit` element członkowski Functions [getline](#getline), [SetSel](#setsel), [GetSel](#getsel)i [ReplaceSel](#replacesel).

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows wysyłane przez kontrolkę edycji do jej elementu nadrzędnego (zazwyczaj klasy pochodnej `CDialog` ), Dodaj wpis mapy komunikatów i funkcję elementu członkowskiego obsługi komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów przyjmuje następującą formę:

  **Powiadomienie ON_**_NOTIFICATION_**(** _ID_**,** _memberFxn_ **)**

gdzie `id` określa identyfikator okna podrzędnego kontrolki edycji wysyłającej powiadomienie i `memberFxn` jest nazwą nadrzędnej funkcji członkowskiej, która została zapisywana w celu obsługi powiadomienia.

Prototyp funkcji elementu nadrzędnego jest następujący:

**afx_msg** void memberFxn **();**

Poniżej znajduje się lista potencjalnych wpisów mapy komunikatów oraz opis przypadków, w których zostałyby one przesłane do elementu nadrzędnego:

- ON_EN_CHANGE użytkownik podjął akcję, która mogła zmienić tekst w kontrolce edycji. W przeciwieństwie do EN_UPDATE komunikatu powiadomienia, ten komunikat jest wysyłany po zaktualizowaniu przez system Windows ekranu.

- ON_EN_ERRSPACE kontrolka edycji nie może przydzielić wystarczającej ilości pamięci do spełnienia określonego żądania.

- ON_EN_HSCROLL użytkownik klika poziomy pasek przewijania kontrolki edycji. Okno nadrzędne zostanie powiadomione przed zaktualizowaniem ekranu.

- ON_EN_KILLFOCUS kontrolka edycji utraci fokus wprowadzania.

- ON_EN_MAXTEXT bieżąca wstawka przekroczyła określoną liczbę znaków kontrolki edycji i została obcięta. Wysyłany również wtedy, gdy kontrolka edycji nie ma stylu ES_AUTOHSCROLL i liczba znaków do wstawienia będzie przekroczyć szerokość kontrolki edycji. Wysyłane również wtedy, gdy kontrolka edycji nie ma ES_AUTOVSCROLL stylu i całkowita liczba wierszy wynikających z wstawiania tekstu przekroczy wysokość kontrolki edycji.

- ON_EN_SETFOCUS wysyłany, gdy kontrolka edycji odbierze fokus wprowadzania.

- ON_EN_UPDATE kontrolka edycji wyświetli zmieniony tekst. Wysyłany po sformatowaniu przez kontrolkę tekstu, ale przed wyświetleniem tekstu, aby można było zmienić rozmiar okna, w razie potrzeby.

- ON_EN_VSCROLL użytkownik klika pionowy pasek przewijania kontrolki edycji. Okno nadrzędne zostanie powiadomione przed zaktualizowaniem ekranu.

Jeśli utworzysz `CEdit` obiekt w oknie dialogowym, `CEdit` obiekt zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz `CEdit` obiekt z zasobu okna dialogowego przy użyciu edytora okien dialogowych, `CEdit` obiekt zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz `CEdit` obiekt w oknie, może być również konieczne jego zniszczenie. Jeśli utworzysz `CEdit` obiekt na stosie, zostanie on zniszczony automatycznie. Jeśli obiekt jest tworzony `CEdit` na stercie przy użyciu **`new`** funkcji, należy wywołać **`delete`** obiekt, aby zniszczyć go, gdy użytkownik zakończy kontrolkę edycji systemu Windows. W przypadku przydzielenia pamięci w `CEdit` obiekcie Zastąp `CEdit` destruktor, aby usunąć alokacje.

Aby zmodyfikować niektóre style w kontrolce edycji (na przykład ES_READONLY), należy wysłać określone komunikaty do kontrolki zamiast używać polecenia [Modify](cwnd-class.md#modifystyle). Zobacz [Edycja stylów kontrolek](/windows/win32/Controls/edit-control-styles) w Windows SDK.

Aby uzyskać więcej informacji na temat `CEdit` , zobacz [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit:: anulowanie

Wywołaj tę funkcję, aby określić, czy Ostatnia operacja edycji może zostać cofnięta.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli Ostatnia operacja edycji może zostać cofnięta przez wywołanie `Undo` funkcji składowej; 0, jeśli nie można jej cofnąć.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_CANUNDO](/windows/win32/Controls/em-canundo) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit:: CEdit

Konstruuje `CEdit` obiekt.

```
CEdit();
```

### <a name="remarks"></a>Uwagi

Użyj [Create](#create) , aby skonstruować formant edycji systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit:: CharFromPos

Wywołaj tę funkcję, aby pobrać indeksy liniowe i znaki znakowe znaku bliżej określonego punktu w tej `CEdit` kontrolce

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Współrzędne punktu w obszarze klienta tego `CEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Indeks znaku w WYRAZie z małą kolejnością i indeks wiersza w WYRAZie o wysokim poziomie kolejności.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja członkowska jest dostępna od systemu Windows 95 i Windows NT 4,0.

Aby uzyskać więcej informacji, zobacz [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit:: Clear

Wywołaj tę funkcję, aby usunąć (wyczyścić) bieżące zaznaczenie (jeśli istnieje) w kontrolce Edycja.

```cpp
void Clear();
```

### <a name="remarks"></a>Uwagi

Usunięcie wykonane przez `Clear` można cofnąć przez wywołanie funkcji [cofnięcia](#undo) elementu członkowskiego.

Aby usunąć bieżące zaznaczenie i umieścić zawartość w schowku, wywołaj funkcję [wycinania](#cut) elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [WM_CLEAR](/windows/win32/dataxchg/wm-clear) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit:: Copy

Wywołaj tę funkcję, aby Coy bieżący wybór (jeśli istnieje) w kontrolce Edycja do Schowka w formacie CF_TEXT.

```cpp
void Copy();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [WM_COPY](/windows/win32/dataxchg/wm-copy) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit:: Create

Tworzy formant edycji systemu Windows i dołącza go do `CEdit` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki edycji. Zastosuj dowolną kombinację [stylów edycji](styles-used-by-mfc.md#edit-styles) do kontrolki.

*cinania*<br/>
Określa rozmiar i położenie kontrolki edycji. Może być `CRect` obiektem lub `RECT` strukturą.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki edycji (zazwyczaj a `CDialog` ). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki edycji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany `CEdit` w dwóch krokach. Najpierw Wywołaj `CEdit` konstruktora, a następnie Wywołaj `Create` , który tworzy formant edycji systemu Windows i dołącza go do `CEdit` obiektu.

Gdy `Create` jest wykonywane, system Windows wysyła wiadomości [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)i [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) do kontrolki edycji.

Te komunikaty są domyślnie obsługiwane przez funkcje członkowskie [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)i [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) w `CWnd` klasie bazowej. Aby zwiększyć domyślną obsługę komunikatów, należy utworzyć klasę z `CEdit` , dodać do nowej klasy mapę komunikatów i zastąpić powyższe funkcje składowe programu obsługi komunikatów. Przesłoń `OnCreate` , na przykład, aby wykonać wymaganą inicjalizację dla nowej klasy.

Zastosuj następujące [Style okna](styles-used-by-mfc.md#window-styles) do kontrolki edycji.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP do grup formantów

- WS_TABSTOP do uwzględnienia kontrolki edycji w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit:: Wytnij

Wywołaj tę funkcję, aby usunąć (wyciąć) bieżące zaznaczenie (jeśli istnieje) w kontrolce Edycja i skopiować usunięty tekst do Schowka w formacie CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Uwagi

Usunięcie wykonane przez `Cut` można cofnąć przez wywołanie funkcji [cofnięcia](#undo) elementu członkowskiego.

Aby usunąć bieżące zaznaczenie bez umieszczania w schowku usuniętego tekstu, wywołaj funkcję [czyszczenia](#clear) elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [WM_CUT](/windows/win32/dataxchg/wm-cut) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit:: EmptyUndoBuffer

Wywołaj tę funkcję, aby zresetować (wyczyścić) flagę cofania kontrolki edycji.

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Uwagi

Kontrolka edycji nie będzie teraz mogła cofnąć ostatniej operacji. Flaga Cofnij jest ustawiana za każdym razem, gdy operacja w kontrolce edycji może zostać cofnięta.

Flaga Cofnij jest automatycznie czyszczona za każdym razem, gdy wywoływana jest funkcja członkowska [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) lub [SetHandle](#sethandle) `CWnd` .

Aby uzyskać więcej informacji, zobacz [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit:: FmtLines

Wywołaj tę funkcję, aby ustawić włączanie lub wyłączanie znaków miękkiej przerwy liniowej w kontrolce edycji wielowierszowej.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Określa, czy znaki łamania wiersza są wstawiane. Wartość TRUE wstawia znaki; wartość FALSE usuwa je.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli występują jakiekolwiek formatowanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Miękki przerwa w wierszu składa się z dwóch znaków powrotu karetki i znaku wysuwu wiersza wstawionego na końcu wiersza, który jest przerwany z powodu zawijania wyrazów. Twarda przerwa linia składa się z jednego powrotu karetki i wysuwu wiersza. Nie ma to wpływ na linie, które kończą się znakiem końca wiersza `FmtLines` .

System Windows będzie odpowiadał tylko wtedy, gdy `CEdit` obiekt jest formantem edycji wielokrotnej.

`FmtLines`ma wpływ tylko na bufor zwracany przez [GetHandle](#gethandle) i tekst zwracany przez [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Nie ma to wpływu na wyświetlanie tekstu w kontrolce edycji.

Aby uzyskać więcej informacji, zobacz [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit:: GetCueBanner

Pobiera tekst wyświetlany jako wskaźnik tekstowy lub Porada w kontrolce edycji, gdy kontrolka jest pusta.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
określoną Wskaźnik do ciągu, który zawiera tekst wskaźnika.

*cchText*<br/>
podczas Liczba znaków, które mogą zostać odebrane. Ta liczba zawiera kończący znak NULL.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszego przeciążenia, wartość TRUE, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

W przypadku drugiego przeciążenia [CString](../../atl-mfc-shared/using-cstring.md) , który zawiera tekst wskaźnika, jeśli metoda zakończy się pomyślnie; w przeciwnym razie, pusty ciąg ("").

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) , który jest opisany w Windows SDK. Aby uzyskać więcej informacji, zobacz makro [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) .

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit:: GetFirstVisibleLine

Wywołaj tę funkcję, aby określić najwyższy widoczny wiersz w kontrolce edycji.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) w górnym widocznym wierszu. W przypadku kontrolek edycji jednowierszowej wartość zwracana wynosi 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit:: GetHandle

Wywołaj tę funkcję, aby pobrać dojście do pamięci, która jest aktualnie przypisana do wielowierszowej kontrolki edycji.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt pamięci lokalnej, który identyfikuje bufor przechowujący zawartość kontrolki edycji. Jeśli wystąpi błąd, na przykład wysłanie komunikatu do kontrolki edycji pojedynczej, wartość zwracana wynosi 0.

### <a name="remarks"></a>Uwagi

Dojście jest dojściem do pamięci lokalnej i może być używane przez dowolną z **lokalnych** funkcji pamięci systemu Windows, która przyjmuje jako parametr obsługę pamięci lokalnej.

`GetHandle`jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Wywołaj `GetHandle` kontrolkę edycji wielowierszowej w oknie dialogowym tylko wtedy, gdy okno dialogowe zostało utworzone z ustawioną flagą stylu DS_LOCALEDIT. Jeśli styl DS_LOCALEDIT nie jest ustawiony, nadal otrzymasz niezerową wartość zwrotną, ale nie będzie można użyć zwracanej wartości.

> [!NOTE]
> `GetHandle`nie będzie działał z systemem Windows 95/98. Wywołanie `GetHandle` w systemie Windows 95/98 spowoduje zwrócenie wartości null. `GetHandle`Program będzie działał zgodnie z opisem w systemie Windows NT, wersjami 3,51 i nowszych.

Aby uzyskać więcej informacji, zobacz [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit:: getpodświetl

Pobiera indeksy pierwszego i ostatniego znaku w zakresie tekstu, który jest wyróżniony w bieżącym formancie edycji.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pichStart*|określoną Indeks (liczony od zera) pierwszego znaku z wyróżnionego zakresu tekstu.|
|*pichEnd*|określoną Indeks (liczony od zera) ostatniego znaku w zakresie wyróżnionego tekstu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_GETHILITE](/windows/win32/Controls/em-gethilite) , który jest opisany w Windows SDK. Oba `SetHighlight` i `GetHighlight` są obecnie włączone tylko dla kompilacji Unicode.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit:: GetLimitText

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać limit tekstu dla tego `CEdit` obiektu.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący limit tekstu w TCHARs dla tego `CEdit` obiektu.

### <a name="remarks"></a>Uwagi

Limit tekstu to maksymalna ilość tekstu w TCHARs, którą może zaakceptować kontrolka edycji.

> [!NOTE]
> Ta funkcja członkowska jest dostępna od systemu Windows 95 i Windows NT 4,0.

Aby uzyskać więcej informacji, zobacz [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit:: getline

Wywołaj tę funkcję, aby pobrać wiersz tekstu z kontrolki edycji i umieścić go w *lpszBuffer*.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa numer wiersza, który ma zostać pobrany z wielowierszowej kontrolki edycji. Numery wierszy są zależne od zera. wartość 0 Określa pierwszy wiersz. Ten parametr jest ignorowany przez jednowierszową kontrolkę edycji.

*lpszBuffer*<br/>
Wskazuje bufor, który otrzymuje kopię wiersza. Pierwszy wyraz bufora musi określać maksymalną liczbę TCHARs, które można skopiować do buforu.

*nMaxLength*<br/>
Określa maksymalną liczbę znaków używanie TCHAR, które można skopiować do buforu. `GetLine`umieszcza tę wartość w pierwszym słowie *lpszBuffer* przed wywołaniem do systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych. Wartość zwracana jest równa 0, jeśli numer wiersza określony przez *nIndex* jest większy niż liczba wierszy w kontrolce edycji.

### <a name="remarks"></a>Uwagi

Skopiowany wiersz nie zawiera znaku zakończenia o wartości null.

Aby uzyskać więcej informacji, zobacz [EM_GETLINE](/windows/win32/Controls/em-getline) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit:: GetLineCount

Wywołaj tę funkcję, aby pobrać liczbę wierszy w kontrolce edycji z wieloma wierszami.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita zawierająca liczbę wierszy w kontrolce edycji wielowierszowej. Jeśli tekst nie został wprowadzony do kontrolki edycji, wartość zwracana to 1.

### <a name="remarks"></a>Uwagi

`GetLineCount`jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit:: GetMargins

Wywołaj tę funkcję elementu członkowskiego, aby pobrać lewy i prawy margines tej kontrolki edycji.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość lewego marginesu w SŁOWie o niskim porządku i szerokość prawego marginesu w SŁOWie o wysokiej kolejności.

### <a name="remarks"></a>Uwagi

Marginesy są mierzone w pikselach.

> [!NOTE]
> Ta funkcja członkowska jest dostępna od systemu Windows 95 i Windows NT 4,0.

Aby uzyskać więcej informacji, zobacz [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [elementu CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit:: GetModify

Wywołaj tę funkcję, aby określić, czy zawartość kontrolki edycji została zmodyfikowana.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli zawartość kontrolki edycji została zmodyfikowana; 0, jeśli nie zostały zmienione.

### <a name="remarks"></a>Uwagi

System Windows utrzymuje wewnętrzną flagę wskazującą, czy zawartość kontrolki edycji została zmieniona. Ta flaga jest czyszczona po pierwszym utworzeniu kontrolki edycji i może być również wyczyszczona przez wywołanie funkcji elementu członkowskiego [SetModify](#setmodify) .

Aby uzyskać więcej informacji, zobacz [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit:: GetPasswordChar

Wywołaj tę funkcję, aby pobrać znak hasła, który jest wyświetlany w kontrolce edycji, gdy użytkownik wprowadzi tekst.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa znak, który ma być wyświetlany zamiast znaku, który wpisano użytkownik. Wartość zwracana ma wartość NULL, jeśli nie istnieje żaden znak hasła.

### <a name="remarks"></a>Uwagi

Jeśli utworzysz kontrolkę Edycja z stylem ES_PASSWORD, biblioteka DLL, która obsługuje formant określa domyślny znak hasła. Manifest lub metoda [Funkcja InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) określa, która Biblioteka DLL obsługuje kontrolkę edycji. Jeśli user32.dll obsługuje kontrolkę edycji, domyślnym znakiem hasła jest GWIAZDka ("*", U + 002A). Jeśli comctl32.dll w wersji 6 obsługuje kontrolkę Edycja, domyślnym znakiem jest czarny okrąg ("●", U + 25CF). Aby uzyskać więcej informacji o tym, która Biblioteka DLL i wersja obsługuje formanty standardowe, zobacz [wersje powłoki shell i Common Controls](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Ta metoda wysyła komunikat [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit:: getRect

Wywołaj tę funkcję, aby uzyskać prostokąt formatowania kontrolki edycji.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` strukturę, która otrzymuje prostokąt formatowania.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna edycji kontrolki.

Prostokąt formatowania kontrolki edycji wielowierszowej może być modyfikowany przez funkcje elementów członkowskich [SetRect](#setrect) i [SetRectNP](#setrectnp) .

Aby uzyskać więcej informacji, zobacz [EM_GETRECT](/windows/win32/Controls/em-getrect) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit:: GetSel

Wywołaj tę funkcję, aby uzyskać początkowe i końcowe znaki w bieżącym zaznaczeniu (jeśli istnieją) w kontrolce edycji, używając wartości zwracanej lub parametrów.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odwołanie do liczby całkowitej, która otrzyma pozycję pierwszego znaku w bieżącym zaznaczeniu.

*nEndChar*<br/>
Odwołanie do liczby całkowitej, która otrzyma pozycję pierwszego niezaznaczonego znaku poza końcem bieżącego zaznaczenia.

### <a name="return-value"></a>Wartość zwracana

Wersja, która zwraca element DWORD, zwraca wartość zawierającą pozycję początkową w słowie o niskim porządku i położenie pierwszego niezaznaczonego znaku po zakończeniu zaznaczania w wyrazie o wysokiej kolejności.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETSEL](/windows/win32/Controls/em-getsel) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit:: HideBalloonTip

Ukrywa wszelką wskazówkę dymkową skojarzoną z bieżącą kontrolką edycji.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła komunikat [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) , który jest opisany w Windows SDK.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit:: LimitText

Wywołaj tę funkcję, aby ograniczyć długość tekstu, który użytkownik może wprowadzić do kontrolki edycji.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Określa długość (w TCHARs) tekstu, który użytkownik może wprowadzić. Jeśli ten parametr ma wartość 0, długość tekstu jest ustawiana na UINT_MAX bajtów. Jest to zachowanie domyślne.

### <a name="remarks"></a>Uwagi

Zmiana limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma wpływu na żaden tekst, który znajduje się już w kontrolce edycji, ani nie ma wpływu na długość tekstu skopiowanego do kontrolki edycji przez funkcję elementu członkowskiego [SetWindowText](cwnd-class.md#setwindowtext) w `CWnd` . Jeśli aplikacja używa funkcji, `SetWindowText` Aby umieścić więcej tekstu w kontrolce edycji niż określona w wywołaniu `LimitText` , użytkownik może usunąć dowolny tekst w kontrolce edycji. Jednak limit tekstu uniemożliwi użytkownikowi zastąpienie istniejącego tekstu nowym tekstem, chyba że usunięcie bieżącego zaznaczenia spowoduje, że tekst spadnie poniżej limitu tekstu.

> [!NOTE]
> W systemie Win32 (Windows NT i Windows 95/98), [SetLimitText](#setlimittext) zastępuje tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit:: LineFromChar

Wywołaj tę funkcję, aby pobrać numer wiersza, który zawiera określony indeks znaków.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera wartość indeksu (liczony od zera) dla żądanego znaku w tekście kontrolki edycji lub zawiera-1. Jeśli *nIndex* ma wartość-1, określa bieżący wiersz, czyli wiersz zawierający karetkę.

### <a name="return-value"></a>Wartość zwracana

Numer wiersza (liczony od zera) zawierający indeks znaków określony przez *nIndex*. Jeśli *nIndex* ma wartość-1, zwracana jest liczba wierszy zawierających pierwszy znak zaznaczenia. Jeśli nie ma zaznaczenia, zostanie zwrócony bieżący numer wiersza.

### <a name="remarks"></a>Uwagi

Indeks znaku jest liczbą znaków od początku kontrolki edycji.

Ta funkcja członkowska jest używana tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit:: LineIndex

Wywołaj tę funkcję, aby pobrać indeks znaku wiersza w kontrolce edycji wielowierszowej.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Zawiera wartość indeksu żądanego wiersza w tekście kontrolki edycji lub zawiera-1. Jeśli *nline* ma wartość-1, określa bieżący wiersz, czyli wiersz zawierający karetkę.

### <a name="return-value"></a>Wartość zwracana

Indeks znaku określony w *nline* lub-1, jeśli określony numer wiersza jest większy niż liczba wierszy w kontrolce edycji.

### <a name="remarks"></a>Uwagi

Indeks znaku jest liczbą znaków od początku kontrolki edycji do określonego wiersza.

Ta funkcja członkowska jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_LINEINDEX](/windows/win32/controls/em-lineindex) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit:: LineLength

Pobiera długość wiersza w kontrolce edycji.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Liczony od zera indeks znaku w wierszu, którego długość ma zostać pobrana. Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

W przypadku kontrolek edycji jednowierszowej wartość zwracana jest długością TCHARs tekstu w kontrolce edycji.

W przypadku wielowierszowych kontrolek edycji wartość zwracana jest długością w TCHARs, w wierszu określonym przez parametr *nline* . W przypadku tekstu ANSI długość jest liczbą bajtów w wierszu; w przypadku tekstu Unicode długość jest liczbą znaków w wierszu. Długość znaku powrotu karetki nie jest uwzględniana na końcu wiersza.

Jeśli parametr *nline* jest większy niż liczba znaków w kontrolce, wartość zwracana wynosi zero.

Jeśli parametr *nline* to-1, wartość zwracana jest liczbą niezaznaczonych znaków w wierszach, które zawierają wybrane znaki. Na przykład, jeśli zaznaczenie rozciąga się od czwartego znaku z jednego wiersza przez osiem znaków od końca następnego wiersza, wartość zwracana wynosi 10. Oznacza to, że trzy znaki pierwszego wiersza i siedem na następnej.

Aby uzyskać więcej informacji na temat typu używanie TCHAR, zobacz wiersz używanie TCHAR w tabeli w obszarze [typy danych systemu Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Uwagi

Ta metoda jest obsługiwana przez komunikat [EM_LINELENGTH](/windows/win32/Controls/em-linelength) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: lineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit:: LineScroll

Wywołaj tę funkcję, aby przewinąć tekst kontrolki edycji z wieloma wierszami.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nLines*<br/>
Określa liczbę wierszy do przewinięcia w pionie.

*nChar*<br/>
Określa liczbę pozycji znaków, które mają być przewijane w poziomie. Ta wartość jest ignorowana, Jeśli kontrolka edycji ma styl ES_RIGHT lub ES_CENTER.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

Kontrolka edycji nie przewija w pionie poza ostatnim wierszem tekstu w kontrolce edycji. Jeśli bieżący wiersz i liczba wierszy określonych przez *nlines* przekraczają łączną liczbę wierszy w kontrolce edycji, wartość jest dostosowywana, tak aby Ostatnia linia kontrolki edycji została przesunięta w górę okna Edycja kontrolki.

`LineScroll`może służyć do przewijania w poziomie po ostatnim znaku dowolnego wiersza.

Aby uzyskać więcej informacji, zobacz [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::P Kopiuj

Wywołaj tę funkcję, aby wstawić dane ze schowka do `CEdit` punktu wstawiania.

```cpp
void Paste();
```

### <a name="remarks"></a>Uwagi

Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.

Aby uzyskać więcej informacji, zobacz [WM_PASTE](/windows/win32/dataxchg/wm-paste) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::P osFromChar

Wywołaj tę funkcję, aby pobrać pozycję (lewy górny róg) danego znaku w tym `CEdit` obiekcie.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Indeks (liczony od zera) określonego znaku.

### <a name="return-value"></a>Wartość zwracana

Współrzędne lewego górnego rogu znaku określonego przez *nchar*.

### <a name="remarks"></a>Uwagi

Znak jest określony przez nadanie wartości indeksu liczony od zera. Jeśli *nchar* jest większy niż indeks ostatniego znaku w tym `CEdit` obiekcie, wartość zwracana określa współrzędne pozycji znaku tylko po ostatnim znaku w tym `CEdit` obiekcie.

> [!NOTE]
> Ta funkcja członkowska jest dostępna od systemu Windows 95 i Windows NT 4,0.

Aby uzyskać więcej informacji, zobacz [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit:: ReplaceSel

Wywołaj tę funkcję, aby zamienić bieżące zaznaczenie w kontrolce edycji na tekst określony przez *lpszNewText*.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText*<br/>
Wskazuje ciąg zakończony znakiem null zawierający tekst zastępujący.

*bCanUndo*<br/>
Aby określić, że ta funkcja może zostać cofnięta, ustaw wartość tego parametru na TRUE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

Zamienia tylko część tekstu w kontrolce edycji. Jeśli chcesz zastąpić cały tekst, użyj funkcji składowej [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) .

Jeśli nie ma bieżącego zaznaczenia, tekst zastępczy zostanie wstawiony w bieżącej lokalizacji kursora.

Aby uzyskać więcej informacji, zobacz [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: lineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit:: SetCueBanner

Ustawia tekst wyświetlany jako wskaźnik tekstowy lub Porada w kontrolce edycji, gdy kontrolka jest pusta.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
podczas Wskaźnik do ciągu, który zawiera wskaźnik do wyświetlenia w kontrolce edycji.

*fDrawWhenFocused*<br/>
podczas Jeśli wartość jest równa FALSE, transparent wskaźnika nie jest rysowany, gdy użytkownik kliknie kontrolkę Edycja i nadaje kontrolce fokus.

W przypadku wartości TRUE transparent jest rysowany nawet wtedy, gdy kontrolka ma fokus. Baner podpowiedzi znika, gdy użytkownik zacznie pisać w kontrolce.

Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończy się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) , który jest opisany w Windows SDK. Aby uzyskać więcej informacji, zobacz makro [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) .

### <a name="example"></a>Przykład

Poniższy przykład demonstruje metodę [CEdit:: SetCueBanner](#setcuebanner) .

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit:: SetHandle

Wywołaj tę funkcję, aby ustawić dojście do pamięci lokalnej, która będzie używana przez wielowierszową kontrolkę edycji.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hBuffer*<br/>
Zawiera dojście do pamięci lokalnej. To dojście musi zostać utworzone przez poprzednie wywołanie funkcji [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) systemu Windows przy użyciu flagi LMEM_MOVEABLE. Przyjęto, że pamięć zawiera ciąg zakończony znakiem null. Jeśli tak nie jest, pierwszy bajt przydzieloną pamięć powinien mieć ustawioną wartość 0.

### <a name="remarks"></a>Uwagi

Kontrolka edycji będzie używać tego buforu do przechowywania aktualnie wyświetlanego tekstu zamiast alokowania własnego buforu.

Ta funkcja członkowska jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

Zanim aplikacja ustawi nowe dojście do pamięci, powinno użyć funkcji elementu członkowskiego [GetHandle](#gethandle) , aby uzyskać uchwyt do bieżącego buforu pamięci i zwolnić tę pamięć przy użyciu `LocalFree` funkcji systemu Windows.

`SetHandle`Czyści bufor cofania (po [cofnięciu](#canundo) funkcja członkowska zwraca 0) i flagę modyfikacji wewnętrznej (funkcja [GetModify](#getmodify) member zwraca 0). Okno Edycja kontrolki jest ponownie narysowane.

Można użyć tej funkcji elementu członkowskiego w kontrolce edycji wielowierszowej w oknie dialogowym tylko wtedy, gdy utworzono okno dialogowe z ustawioną flagą DS_LOCALEDIT stylu.

> [!NOTE]
> `GetHandle`nie będzie działał z systemem Windows 95/98. Wywołanie `GetHandle` w systemie Windows 95/98 spowoduje zwrócenie wartości null. `GetHandle`Program będzie działał zgodnie z opisem w systemie Windows NT, wersjami 3,51 i nowszych.

Aby uzyskać więcej informacji, zobacz [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)i [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit:: setpodświetl

Podświetla zakres tekstu, który jest wyświetlany w bieżącym formancie edycji.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ichStart*|podczas Indeks (liczony od zera) pierwszego znaku w zakresie tekstu do wyróżnienia.|
|*ichEnd*|podczas Indeks (liczony od zera) ostatniego znaku w zakresie tekstu do wyróżnienia.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , który jest opisany w Windows SDK.  Ta metoda wysyła komunikat [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , który jest opisany w Windows SDK. Oba `SetHighlight` i `GetHighlight` są włączone tylko dla kompilacji Unicode.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit:: SetLimitText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić limit tekstu dla tego `CEdit` obiektu.

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*Nmaks.*<br/>
Nowy limit tekstu w znakach.

### <a name="remarks"></a>Uwagi

Limit tekstu jest maksymalną ilością tekstu (w znakach), którą może zaakceptować kontrolka edycji.

Zmiana limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma wpływu na żaden tekst, który znajduje się już w kontrolce edycji, ani nie ma wpływu na długość tekstu skopiowanego do kontrolki edycji przez funkcję elementu członkowskiego [SetWindowText](cwnd-class.md#setwindowtext) w `CWnd` . Jeśli aplikacja używa funkcji, `SetWindowText` Aby umieścić więcej tekstu w kontrolce edycji niż określona w wywołaniu `LimitText` , użytkownik może usunąć dowolny tekst w kontrolce edycji. Jednak limit tekstu uniemożliwi użytkownikowi zastąpienie istniejącego tekstu nowym tekstem, chyba że usunięcie bieżącego zaznaczenia spowoduje, że tekst spadnie poniżej limitu tekstu.

Ta funkcja zastępuje [LimitText](#limittext) w systemie Win32.

Aby uzyskać więcej informacji, zobacz [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [elementu CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit:: Setmargins

Wywołaj tę metodę, aby ustawić lewy i prawy margines tej kontrolki edycji.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nLeft*<br/>
Szerokość nowego lewego marginesu (w pikselach).

*nRight*<br/>
Szerokość nowego marginesu (w pikselach).

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja członkowska jest dostępna od systemu Windows 95 i Windows NT 4,0.

Aby uzyskać więcej informacji, zobacz [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [elementu CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit:: SetModify

Wywołaj tę funkcję, aby ustawić lub wyczyścić modyfikowaną flagę kontrolki edycji.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Wartość TRUE wskazuje, że tekst został zmodyfikowany, a wartość FALSE wskazuje, że nie jest modyfikowana. Domyślnie flaga zmodyfikowano jest ustawiona.

### <a name="remarks"></a>Uwagi

Zmodyfikowano flagę wskazuje, czy tekst w kontrolce edycji został zmodyfikowany. Jest ona ustawiana automatycznie za każdym razem, gdy użytkownik zmieni tekst. Jego wartość może zostać pobrana za pomocą elementu członkowskiego [GetModify](#getmodify) .

Aby uzyskać więcej informacji, zobacz [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit:: SetPasswordChar

Wywołaj tę funkcję, aby ustawić lub usunąć znak hasła wyświetlany w kontrolce edycji, gdy użytkownik wpisze tekst.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Określa znak, który ma być wyświetlany zamiast znaku wpisanego przez użytkownika. Jeśli *ch* ma wartość 0, wyświetlane są rzeczywiste znaki wpisane przez użytkownika.

### <a name="remarks"></a>Uwagi

Gdy jest ustawiony znak hasła, ten znak jest wyświetlany dla każdego znaku typu użytkownika.

Ta funkcja członkowska nie ma wpływu na kontrolkę edycji wielowierszowej.

Gdy `SetPasswordChar` wywoływana jest funkcja członkowska, `CEdit` program ponownie narysuje wszystkie widoczne znaki przy użyciu znaku określonego przez *ch*.

Jeśli kontrolka edycji jest tworzona z stylem [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) , jako domyślny znak hasła jest ustawiana gwiazdka ( <strong>\*</strong> ). Ten styl jest usuwany `SetPasswordChar` , jeśli jest wywoływany z *ch* o wartości 0.

Aby uzyskać więcej informacji, zobacz [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit:: SetReadOnly

Wywołuje tę funkcję, aby ustawić stan tylko do odczytu kontrolki edycji.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bReadOnly*<br/>
Określa, czy ma zostać ustawiony lub usunięty stan tylko do odczytu kontrolki edycji. Wartość TRUE ustawia stan na tylko do odczytu; wartość FALSE ustawia stan na odczyt/zapis.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli operacja zakończyła się pomyślnie, lub 0, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Bieżące ustawienie można znaleźć, testując flagę [ES_READONLY](styles-used-by-mfc.md#edit-styles) w zwracanej wartości [CWnd:: GetStyle](cwnd-class.md#getstyle).

Aby uzyskać więcej informacji, zobacz [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit:: SetRect

Wywołaj tę funkcję, aby ustawić wymiary prostokąta przy użyciu określonych współrzędnych.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` strukturę lub `CRect` obiekt, który określa nowe wymiary prostokąta formatowania.

### <a name="remarks"></a>Uwagi

Ten element członkowski jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Użyj `SetRect` , aby ustawić prostokąt formatowania kontrolki edycji wielowierszowej. Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna edycji kontrolki. Po pierwszym utworzeniu kontrolki Edycja prostokąt formatowania jest taki sam, jak obszar klienta okna Edycja kontrolki. Za pomocą `SetRect` funkcji składowej, aplikacja może sprawić, że prostokąt formatowania jest większy lub mniejszy od okna edycji kontrolki.

Jeśli kontrolka edycji nie ma paska przewijania, tekst zostanie przycięty, a nie opakowany, jeśli prostokąt formatowania jest większy niż okno. Jeśli kontrolka edycji zawiera obramowanie, prostokąt formatowania jest zmniejszany o rozmiar obramowania. Jeśli dostosowujesz Prostokąt zwracany przez `GetRect` funkcję członkowską, musisz usunąć rozmiar obramowania przed przekazaniem prostokąta do `SetRect` .

Gdy `SetRect` jest wywoływana, tekst kontrolki edycji jest również ponownie formatowany i wyświetlona.

Aby uzyskać więcej informacji, zobacz [EM_SETRECT](/windows/win32/Controls/em-setrect) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit:: SetRectNP

Wywołaj tę funkcję, aby ustawić prostokąt formatowania kontrolki edycji z wieloma wierszami.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` strukturę lub `CRect` obiekt, który określa nowe wymiary prostokąta.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna edycji kontrolki.

`SetRectNP`jest taka sama jak `SetRect` funkcja członkowska, z tą różnicą, że okno Edycja kontrolki nie jest ponownie rysowane.

Po pierwszym utworzeniu kontrolki Edycja prostokąt formatowania jest taki sam, jak obszar klienta okna Edycja kontrolki. Wywołując `SetRectNP` funkcję członkowską, aplikacja może sprawić, że prostokąt formatowania jest większy lub mniejszy od okna edycji kontrolki.

Jeśli kontrolka edycji nie ma paska przewijania, tekst zostanie przycięty, a nie opakowany, jeśli prostokąt formatowania jest większy niż okno.

Ten element członkowski jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit:: SetSel

Wywołaj tę funkcję, aby wybrać zakres znaków w kontrolce edycji.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parametry

*dwSelection*<br/>
Określa pozycję początkową w wyrazie z małą kolejnością i końcową w wyrazie o wysokiej kolejności. Jeśli słowo o niskim porządku jest równe 0, a słowo o wysokim porządku to-1, zaznaczony jest cały tekst w kontrolce Edycja. Jeśli wyraz o niskim porządku to-1, wszystkie bieżące zaznaczenie zostanie usunięte.

*bNoScroll*<br/>
Wskazuje, czy karetka ma być przewijana do widoku. W przypadku wartości FALSE karetka jest przewijana do widoku. W przypadku wartości TRUE karetka nie jest przewijana do widoku.

*nStartChar*<br/>
Określa pozycję początkową. Jeśli *nStartChar* ma wartość 0, a *nEndChar* to-1, zaznaczony jest cały tekst w kontrolce Edycja. Jeśli *nStartChar* jest-1, wszelkie bieżące zaznaczenie zostanie usunięte.

*nEndChar*<br/>
Określa pozycję końcową.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_SETSEL](/windows/win32/Controls/em-setsel) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CEdit:: GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit:: SetTabStops

Wywołaj tę funkcję, aby ustawić tabulatory w kontrolce edycji wielowierszowej.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Określa, że tabulatory mają być ustawiane w każdej jednostce okna dialogowego *cxEachStop* .

*nTabStops*<br/>
Określa liczbę tabulatorów zawartych w *rgTabStops*. Ta wartość musi być większa niż 1.

*rgTabStops*<br/>
Wskazuje tablicę liczb całkowitych bez znaku określającą tabulatory w jednostkach okna dialogowego. Jednostka okna dialogowego to odległość pozioma lub pionowa. Jedna pozioma jednostka okna dialogowego jest równa jednej czwartej bieżącej jednostki szerokości okna dialogowego i 1 jednostka okna dialogowego w pionie jest równa jednej ósmej aktualnej jednostki wysokości okna dialogowego. Jednostki bazowe okna dialogowego są obliczane na podstawie wysokości i szerokości bieżącej czcionki systemowej. `GetDialogBaseUnits`Funkcja systemu Windows zwraca bieżące jednostki bazowe okna dialogowego w pikselach.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli karty zostały ustawione; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy tekst jest kopiowany do kontrolki edycji wielu wierszy, każdy znak tabulacji w tekście spowoduje wygenerowanie miejsca do następnego tabulatora.

Aby ustawić tabulatory do domyślnego rozmiaru jednostek okna dialogowego 32, wywołaj bezparametrową wersję tej funkcji elementu członkowskiego. Aby ustawić przetrzymywanie tabulatorów o rozmiarze innym niż 32, wywołaj wersję za pomocą parametru *cxEachStop* . Aby ustawić przetrzymywanie tabulatorów na tablicę rozmiarów, użyj wersji z dwoma parametrami.

Ta funkcja członkowska jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

`SetTabStops`nie odświeża automatycznie okna Edycja. Jeśli zmienisz tabulatory dla tekstu, który znajduje się już w kontrolce Edycja, wywołaj [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect) , aby ponownie narysować okno edycji.

Aby uzyskać więcej informacji, zobacz [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) i [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [elementu CEditView:: SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit:: ShowBalloonTip

Wyświetla wskazówkę dymkową, która jest skojarzona z bieżącą kontrolką edycji.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pEditBalloonTip*|podczas Wskaźnik do struktury [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) , która opisuje wskazówkę dymka.|
|*lpszTitle*|podczas Wskaźnik na ciąg Unicode, który zawiera tytuł porady dymkowej.|
|*lpszText*|podczas Wskaźnik na ciąg Unicode, który zawiera tekst porady dymkowej.|
|*ttiIcon*|podczas Liczba **całkowita** określająca typ ikony, która ma zostać skojarzona z końcówką dymka. Wartość domyślna to TTI_NONE. Aby uzyskać więcej informacji, zobacz `ttiIcon` element członkowski struktury [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) .|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła komunikat [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) , który jest opisany w Windows SDK. Aby uzyskać więcej informacji, zobacz makro [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) .

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną, `m_cedit` , która jest używana do uzyskiwania dostępu do bieżącej kontrolki edycji. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wyświetla wskazówkę dymkową dla kontrolki edycji. [CEdit:: ShowBalloonTip](#showballoontip) Metoda określa tytuł i tekst porady dymkowej.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit:: Undo

Wywołaj tę funkcję, aby cofnąć ostatnią operację edycji.

```
BOOL Undo();
```

### <a name="return-value"></a>Wartość zwracana

Dla kontrolki edycji jednowierszowej wartość zwracana jest zawsze różna od zera. W przypadku kontrolki edycji wielowierszowej wartość zwracana jest różna od zera, jeśli operacja cofnięcia zakończyła się powodzeniem, lub 0, jeśli operacja cofania zakończy się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Operację cofania można także cofnąć. Można na przykład przywrócić usunięty tekst z pierwszym wywołaniem do `Undo` . O ile nie istnieje interwencja operacji edycji, można usunąć ten tekst ponownie z drugim wywołaniem do `Undo` .

Aby uzyskać więcej informacji, zobacz [EM_UNDO](/windows/win32/Controls/em-undo) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład CALCDRIV MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład CMNCTRL2 MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](cwnd-class.md)<br/>
[Klasa CButton](cbutton-class.md)<br/>
[Klasa CComboBox](ccombobox-class.md)<br/>
[Klasa CListBox](clistbox-class.md)<br/>
[Klasa CScrollBar](cscrollbar-class.md)<br/>
[Klasa CStatic](cstatic-class.md)<br/>
[Klasa CDialog](cdialog-class.md)
