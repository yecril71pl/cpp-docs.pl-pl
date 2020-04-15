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
ms.openlocfilehash: 3ca2fe4486ae0751f37d046ef28ed11e60e776ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373984"
---
# <a name="cedit-class"></a>Klasa CEdit

Udostępnia funkcje kontrolki edycji systemu Windows.

## <a name="syntax"></a>Składnia

```
class CEdit : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit::CEdytuj](#cedit)|Konstruuje `CEdit` obiekt kontrolny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Określa, czy można cofnąć operację kontroli edycji.|
|[CEdit::CharFromPos](#charfrompos)|Pobiera indeksy wiersza i znaków dla znaku najbliższego określonej pozycji.|
|[CEdit::Wyczyść](#clear)|Usuwa (czyści) bieżący wybór (jeśli istnieje) w formancie edycji.|
|[CEdit::Kopiowanie](#copy)|Kopiuje bieżące zaznaczenie (jeśli istnieje) w formancie edycji do Schowka w formacie CF_TEXT.|
|[CEdit::Tworzenie](#create)|Tworzy formant edycji systemu Windows `CEdit` i dołącza go do obiektu.|
|[CEdit::Wytnij](#cut)|Usuwa (wycina) bieżące zaznaczenie (jeśli istnieje) w formancie edycji i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Resetuje (czyści) flagę cofania formantu edycji.|
|[CEdit::FmtLines](#fmtlines)|Ustawia włączenie lub wyłączenie znaków miękkich podziałów wiersza w ramach wielowierszowej kontrolki edycji.|
|[CEdit::GetCueBanner](#getcuebanner)|Pobiera tekst, który jest wyświetlany jako sygnał tekstowy lub wskazówka, w formancie edycji, gdy formant jest pusty i nie ma fokusu.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Określa najbardziej widoczną linię u góry w formancie edycji.|
|[CEdit::GetHandle](#gethandle)|Pobiera dojście do pamięci, która jest obecnie przydzielona dla kontrolki edycji wielowierszowej.|
|[CEdit::GetHighlight](#gethighlight)|Pobiera indeksy znaków początkowych i kończących w zakresie tekstu, który jest wyróżniony w bieżącym formancie edycji.|
|[CEdit::GetLimitText](#getlimittext)|Pobiera maksymalną ilość `CEdit` tekstu, który może zawierać.|
|[CEdit::GetLine](#getline)|Pobiera wiersz tekstu z kontrolki edycji.|
|[CEdit::GetLineCount](#getlinecount)|Pobiera liczbę wierszy w formancie edycji wielowierszowej.|
|[CEdit::GetMargins](#getmargins)|Pobiera do tego `CEdit`lewy i prawy margines .|
|[CEdit::GetModify](#getmodify)|Określa, czy zawartość formantu edycji została zmodyfikowana.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Pobiera znak hasła wyświetlany w formancie edycji, gdy użytkownik wprowadza tekst.|
|[CEdit::GetRect](#getrect)|Pobiera prostokąt formatowania formantu edycji.|
|[CEdit::GetSel](#getsel)|Pobiera pierwsze i ostatnie pozycje znaków bieżącego zaznaczenia w formancie edycji.|
|[CEdit::HideBalloonTip](#hideballoontip)|Ukrywa każdą końcówkę dymka skojarzoną z bieżącą kontrolą edycji.|
|[CEdit::Tekst limit](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić w formancie edycji.|
|[CEdit::LineFromChar](#linefromchar)|Pobiera numer wiersza wiersza zawierającego określony indeks znaków.|
|[CEdit::LineIndex](#lineindex)|Pobiera indeks znaków wiersza w ramach wielowierszowego formantu edycji.|
|[CEdit::Długość linii](#linelength)|Pobiera długość wiersza w formancie edycji.|
|[CEdit::LineScroll](#linescroll)|Przewija tekst wielowierszowego formantu edycji.|
|[CEdit::Paste](#paste)|Wstawia dane ze Schowka do formantu edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.|
|[CEdit::PosFromChar](#posfromchar)|Pobiera współrzędne lewego górnego rogu określonego indeksu znaków.|
|[CEdit::ReplaceSel](#replacesel)|Zastępuje bieżące zaznaczenie w formancie edycji określonym tekstem.|
|[CEdit::SetCueBanner](#setcuebanner)|Ustawia tekst wyświetlany jako sygnał tekstowy lub wskazówka w formancie edycji, gdy formant jest pusty i nie ma fokusu.|
|[CEdit::SetHandle](#sethandle)|Ustawia dojście do pamięci lokalnej, która będzie używana przez kontrolkę edycji wielowierszowej.|
|[CEdit::SetHighlight](#sethighlight)|Wyróżnia zakres tekstu wyświetlany w bieżącym formancie edycji.|
|[CEdit::SetLimitText](#setlimittext)|Ustawia maksymalną ilość `CEdit` tekstu, jaką może zawierać.|
|[CEdit::SetMargins](#setmargins)|Ustawia dla tego `CEdit`lewy i prawy margines .|
|[CEdit::SetModify](#setmodify)|Ustawia lub czyści flagę modyfikacji dla formantu edycji.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Ustawia lub usuwa znak hasła wyświetlany w formancie edycji, gdy użytkownik wprowadza tekst.|
|[CEdit::SetReadOnly](#setreadonly)|Ustawia stan tylko do odczytu kontrolki edycji.|
|[CEdit::SetRect](#setrect)|Ustawia prostokąt formatowania wielowierszowego formantu edycji i aktualizuje formant.|
|[CEdit::SetRectNP](#setrectnp)|Ustawia prostokąt formatowania wielowierszowego formantu edycji bez ponownego rysowania okna sterowania.|
|[CEdit::SetSel](#setsel)|Wybiera zakres znaków w formancie edycji.|
|[CEdit::SetTabStops](#settabstops)|Ustawia tabulatory w wielowierszowym formancie edycji.|
|[CEdit::ShowBalloonTip](#showballoontip)|Wyświetla końcówkę odnośnika skojarzoną z bieżącą kontrolką edycji.|
|[CEdit::Cofnij](#undo)|Odwraca ostatnią operację kontroli edycji.|

## <a name="remarks"></a>Uwagi

Formant edycji to prostokątne okno podrzędne, w którym użytkownik może wprowadzać tekst.

Formant edycji można utworzyć z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach najpierw `CEdit` wywołać konstruktora do konstruowania `CEdit` obiektu, a następnie [wywołać Create](#create) funkcji elementu członkowskiego, aby utworzyć formant edycji systemu Windows i dołączyć go do `CEdit` obiektu.

Budowa może być procesem jednoetapowym w `CEdit`klasie wywodzącej się z . Napisz konstruktora dla klasy `Create` pochodnej i wywołać z wewnątrz konstruktora.

`CEdit`dziedziczy znaczną `CWnd`funkcjonalność z . Aby ustawić i pobrać `CEdit` tekst z `CWnd` obiektu, należy użyć funkcji członkowskich [SetWindowText](cwnd-class.md#setwindowtext) i [GetWindowText](cwnd-class.md#getwindowtext), które ustawiają lub pobierają całą zawartość formantu edycji, nawet jeśli jest to kontrolka wielowierszowa. Wiersze tekstu w formancie wielowierszowym są oddzielone sekwencjami znaków '\r\n'. Ponadto jeśli formant edycji jest wielowierszowy, pobierz i ustaw `CEdit` część tekstu formantu, wywołując funkcje członkowskie [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)i [ReplaceSel](#replacesel).

Jeśli chcesz obsługiwać wiadomości powiadomień systemu Windows wysyłane przez formant `CDialog`edycji do jego elementu nadrzędnego (zwykle klasy pochodnej), dodaj wpis mapy wiadomości i funkcję elementu członkowskiego obsługi wiadomości do klasy nadrzędnej dla każdej wiadomości.

Każdy wpis mapy wiadomości ma następującą formę:

  **ON_**_POWIADOMIENIE_**(** _id_**,** _memberFxn_ **)**

gdzie `id` określa identyfikator okna podrzędnego formantu edycji `memberFxn` wysyłającego powiadomienie i jest nazwą funkcji elementu członkowskiego nadrzędnego, która została napisana w celu obsługi powiadomienia.

Prototyp funkcji rodzica jest następujący:

**afx_msg** void memberFxn **( );**

Poniżej znajduje się lista potencjalnych wpisów mapy wiadomości i opis przypadków, w których będą one wysyłane do rodzica:

- ON_EN_CHANGE Użytkownik podjął akcję, która mogła zmienić tekst w formancie edycji. W przeciwieństwie do EN_UPDATE komunikat powiadomienia, ten komunikat powiadomienia jest wysyłany po aktualizacji wyświetlania przez system Windows.

- ON_EN_ERRSPACE Formant edycji nie może przydzielić wystarczającej ilości pamięci, aby spełnić określone żądanie.

- ON_EN_HSCROLL Użytkownik klika poziomy pasek przewijania formantu edycji. Okno nadrzędne zostanie powiadomione przed zaktualizowaniem ekranu.

- ON_EN_KILLFOCUS Kontrolka edycji traci fokus wejściowy.

- ON_EN_MAXTEXT Bieżące wstawianie przekroczyło określoną liczbę znaków dla formantu edycji i zostało obcięty. Również wysyłane, gdy formant edycji nie ma stylu ES_AUTOHSCROLL i liczba znaków do wstawienia przekroczy szerokość formantu edycji. Również wysyłane, gdy formant edycji nie ma stylu ES_AUTOVSCROLL i całkowita liczba wierszy wynikających z wstawiania tekstu przekroczy wysokość formantu edycji.

- ON_EN_SETFOCUS Wysyłane, gdy formant edycji odbiera fokus wejściowy.

- ON_EN_UPDATE Formant edycji ma zamiar wyświetlić zmieniony tekst. Wysłane po sformatowanie formantu, ale przed jego ekranem tekst, tak aby rozmiar okna można było zmienić, jeśli to konieczne.

- ON_EN_VSCROLL Użytkownik klika pionowy pasek przewijania formantu edycji. Okno nadrzędne zostanie powiadomione przed zaktualizowaniem ekranu.

Jeśli obiekt `CEdit` zostanie utworzony w oknie `CEdit` dialogowym, obiekt zostanie automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli obiekt `CEdit` zostanie utworzony z zasobu okna `CEdit` dialogowego za pomocą edytora dialogów dialogowych, obiekt zostanie automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli utworzysz `CEdit` obiekt w oknie, może być również konieczne jego zniszczenie. Jeśli utworzysz `CEdit` obiekt na stosie, zostanie on automatycznie zniszczony. Jeśli `CEdit` obiekt zostanie utworzony na stercie przy użyciu **nowej** funkcji, należy wywołać **delete** na obiekcie, aby go zniszczyć, gdy użytkownik zakończy formant edycji systemu Windows. Jeśli przydzielić dowolną `CEdit` pamięć w obiekcie, zastąpić `CEdit` destruktora do usuwania alokacji.

Aby zmodyfikować niektóre style w formancie edycji (na przykład ES_READONLY) należy wysłać określone wiadomości do formantu zamiast korzystać z [modifystyle](cwnd-class.md#modifystyle). Zobacz [Edytowanie stylów sterowania](/windows/win32/Controls/edit-control-styles) w programie Windows SDK.

Aby uzyskać `CEdit`więcej informacji na temat , zobacz [Formanty](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](cobject-class.md)

[Ccmdtarget](ccmdtarget-class.md)

[Cwnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo

Wywołanie tej funkcji, aby ustalić, czy ostatnia operacja edycji można cofnąć.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli ostatnia operacja edycji można `Undo` cofnąć przez wywołanie funkcji elementu członkowskiego; 0, jeśli nie można go cofnąć.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_CANUNDO](/windows/win32/Controls/em-canundo) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::Cofnij](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit::CEdytuj

Konstruuje `CEdit` obiekt.

```
CEdit();
```

### <a name="remarks"></a>Uwagi

Użyj [funkcji Utwórz,](#create) aby utworzyć kontrolka edycji systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos

Wywołanie tej funkcji w celu pobrania indeksów linii i znaków opartych `CEdit` na wartości zerowej znaku najbliższego określonej pozycji w tym formancie

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Współrzędne punktu w obszarze `CEdit` klienta tego obiektu.

### <a name="return-value"></a>Wartość zwracana

Indeks znaków w programie WORD niskiego rzędu oraz indeks wiersza w programie WORD wysokiego rzędu.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja elementu członkowskiego jest dostępna począwszy od systemów Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit::Wyczyść

Wywołanie tej funkcji, aby usunąć (wyczyścić) bieżący wybór (jeśli istnieje) w formancie edycji.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Usunięcie wykonywane przez `Clear` można cofnąć, wywołując funkcję [Cofnij element członkowski.](#undo)

Aby usunąć bieżące zaznaczenie i umieścić usuniętą zawartość w Schowku, należy wywołać funkcję [wytnij](#cut) element członkowski.

Aby uzyskać więcej informacji, zobacz [WM_CLEAR](/windows/win32/dataxchg/wm-clear) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit::Kopiowanie

Wywołanie tej funkcji, aby coy bieżącego zaznaczenia (jeśli istnieje) w formancie edycji do Schowka w formacie CF_TEXT.

```
void Copy();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [WM_COPY](/windows/win32/dataxchg/wm-copy) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit::Tworzenie

Tworzy formant edycji systemu Windows `CEdit` i dołącza go do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu edycji. Zastosuj dowolną kombinację [stylów edycji](styles-used-by-mfc.md#edit-styles) do formantu.

*Rect*<br/>
Określa rozmiar i położenie formantu edycji. Może być `CRect` obiektem lub `RECT` strukturą.

*pParentWnd*<br/>
Określa okno nadrzędne formantu edycji (zwykle ). `CDialog` Nie może być null.

*Nid*<br/>
Określa identyfikator formantu edycji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CEdit` obiektu w dwóch krokach. Najpierw wywołaj `CEdit` konstruktora, a następnie wywołaj `Create`, co `CEdit` tworzy formant edycji systemu Windows i dołącza go do obiektu.

Podczas `Create` wykonywania system Windows wysyła [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)i [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) wiadomości do formantu edycji.

Te komunikaty są obsługiwane domyślnie przez Funkcje członkowskie [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)i [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) w klasie podstawowej. `CWnd` Aby rozszerzyć domyślną obsługę wiadomości, `CEdit`należy wyprowadzić klasę z , dodać mapę wiadomości do nowej klasy i zastąpić powyższe funkcje członkowskie programu message-handler. Zastądnie `OnCreate`, na przykład, aby wykonać wymagane inicjowanie dla nowej klasy.

Zastosuj następujące [style okien](styles-used-by-mfc.md#window-styles) do formantu edycji.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP Do grupowanie formantów

- WS_TABSTOP Aby uwzględnić formant edycji w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit::Wytnij

Wywołanie tej funkcji, aby usunąć (wyciąć) bieżące zaznaczenie (jeśli istnieje) w formancie edycji i skopiować usunięty tekst do Schowka w formacie CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Uwagi

Usunięcie wykonywane przez `Cut` można cofnąć, wywołując funkcję [Cofnij element członkowski.](#undo)

Aby usunąć bieżące zaznaczenie bez umieszczania usuniętego tekstu w Schowku, należy wywołać funkcję [Wyczyść](#clear) element członkowski.

Aby uzyskać więcej informacji, zobacz [WM_CUT](/windows/win32/dataxchg/wm-cut) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Wywołanie tej funkcji, aby zresetować (wyczyść) flagę cofania formantu edycji.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Uwagi

Formant edycji nie będzie teraz mógł cofnąć ostatniej operacji. Flaga cofania jest ustawiana za każdym razem, gdy można cofnąć operację w formancie edycji.

Flaga cofania jest automatycznie czyszczona za każdym razem, gdy wywoływane są funkcje członkowskie [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) lub [SetHandle.](#sethandle) `CWnd`

Aby uzyskać więcej informacji, zobacz [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines

Wywołanie tej funkcji, aby ustawić włączenie lub wyłączenie znaków miękkich podziałów wiersza w ramach wielowierszowej kontrolki edycji.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Określa, czy mają być wstawiane miękkie znaki podziału wiersza. Wartość TRUE wstawia znaki; wartość FALSE usuwa je.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wystąpi formatowanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podział wiersza miękkiego składa się z dwóch zwrotów karetki i kanału wiersza wstawionego na końcu wiersza, który jest przerywany z powodu zawijania wyrazów. Podział linii twardej składa się z jednego powrotu karetki i posuwu wiersza. Linie, które kończą się podziałem linii `FmtLines`twardej, nie mają wpływu na linie .

System Windows będzie `CEdit` reagować tylko wtedy, gdy obiekt jest wielowierszowym formantem edycji.

`FmtLines`wpływa tylko na bufor zwrócony przez [GetHandle](#gethandle) i tekst zwrócony przez [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Nie ma to wpływu na wyświetlanie tekstu w formancie edycji.

Aby uzyskać więcej informacji, zobacz [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner

Pobiera tekst, który jest wyświetlany jako sygnał tekstowy lub wskazówka, w formancie edycji, gdy formant jest pusty.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[na zewnątrz] Wskaźnik do ciągu zawierającego tekst sygnalizacji.

*cchTekst*<br/>
[w] Liczba znaków, które mogą być odbierane. Numer ten zawiera kończący się znak NULL.

### <a name="return-value"></a>Wartość zwracana

Dla pierwszego przeciążenia, PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

Dla drugiego przeciążenia [CString,](../../atl-mfc-shared/using-cstring.md) który zawiera tekst sygnalizacji, jeśli metoda zakończy się pomyślnie; w przeciwnym razie pusty ciąg ("").

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_GETCUEBANNER,](/windows/win32/Controls/em-getcuebanner) który jest opisany w windows SDK. Aby uzyskać więcej informacji, zobacz [makro Edit_GetCueBannerText.](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Wywołanie tej funkcji, aby określić najwyższej widocznej linii w formancie edycji.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera najwyższej widocznej linii. W przypadku formantów edycji jednowierszowej zwracana wartość zwracana wynosi 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle

Wywołanie tej funkcji, aby pobrać dojście do pamięci aktualnie przydzielonej dla kontrolki edycji wielowierszowej.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście pamięci lokalnej, który identyfikuje buforu zawierającego zawartość formantu edycji. Jeśli wystąpi błąd, na przykład wysłanie wiadomości do kontrolki edycji jednowierszowej, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Dojście jest dojściem pamięci lokalnej i może być używane przez dowolną z funkcji pamięci **systemu Windows,** które przyjmują dojście pamięci lokalnej jako parametr.

`GetHandle`jest przetwarzany tylko za pomocą wielowierszowych formantów edycji.

Wywołanie `GetHandle` wielowierszowego formantu edycji w oknie dialogowym tylko wtedy, gdy zostało utworzone okno dialogowe z ustawioną flagą stylu DS_LOCALEDIT. Jeśli styl DS_LOCALEDIT nie jest ustawiony, nadal otrzymasz wartość zwracaną typu nonzero, ale nie będzie można użyć zwracanej wartości.

> [!NOTE]
> `GetHandle`nie będzie działać z systemem Windows 95/98. Jeśli zadzwonisz `GetHandle` w systemie Windows 95/98, zwróci null. `GetHandle`będzie działać zgodnie z dokumentami w systemie Windows NT, wersjach 3.51 i nowszych.

Aby uzyskać więcej informacji, zobacz [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight

Pobiera indeksy pierwszego i ostatniego znaków w zakresie tekstu, który jest wyróżniony w bieżącym formancie edycji.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pichStart*|[na zewnątrz] Indeks oparty na wartości zerowej pierwszego znaku w zakresie tekstu, który jest wyróżniony.|
|*pichEnd (pichEnd)*|[na zewnątrz] Indeks od zera ostatniego znaku w zakresie tekstu, który jest wyróżniony.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [komunikat EM_GETHILITE,](/windows/win32/Controls/em-gethilite) który jest opisany w windows SDK. Oba `SetHighlight` `GetHighlight` i są obecnie włączone tylko dla kompilacji UNICODE.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText

Wywołanie tej funkcji elementu członkowskiego, `CEdit` aby uzyskać limit tekstu dla tego obiektu.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący limit tekstu w CZAJach `CEdit` dla tego obiektu.

### <a name="remarks"></a>Uwagi

Limit tekstu to maksymalna ilość tekstu w CZAR, którą formant edycji może zaakceptować.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest dostępna począwszy od systemów Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit::GetLine

Wywołanie tej funkcji, aby pobrać wiersz tekstu z kontrolki edycji i umieszcza go w *lpszBuffer*.

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

*Nindex*<br/>
Określa numer wiersza do pobrania z wielowierszowego formantu edycji. Numery wierszy są oparte na wartościach zerowych; wartość 0 określa pierwszy wiersz. Ten parametr jest ignorowany przez kontrolkę edycji jednowierszowej.

*lpszBuffer (lpszBuffer)*<br/>
Wskazuje bufor, który odbiera kopię wiersza. Pierwsze słowo buforu musi określać maksymalną liczbę CHTAR, które mogą być kopiowane do buforu.

*nMaxLength*<br/>
Określa maksymalną liczbę znaków TCHAR, które mogą być kopiowane do buforu. `GetLine`umieszcza tę wartość w pierwszym słowie *lpszBuffer* przed wykonaniem połączenia do systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie skopiowanych. Zwracana wartość wynosi 0, jeśli numer wiersza określony przez *nIndex* jest większy niż liczba wierszy w formancie edycji.

### <a name="remarks"></a>Uwagi

Skopiowany wiersz nie zawiera znaku zakończenia zerowego.

Aby uzyskać więcej informacji, zobacz [EM_GETLINE](/windows/win32/Controls/em-getline) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount

Wywołanie tej funkcji, aby pobrać liczbę wierszy w wielowierszowym formancie edycji.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita zawierająca liczbę wierszy w formancie edycji wielowierszowej. Jeśli do formantu edycji nie wprowadzono żadnego tekstu, zwracana wartość wynosi 1.

### <a name="remarks"></a>Uwagi

`GetLineCount`jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins

Wywołanie tej funkcji elementu członkowskiego, aby pobrać lewy i prawy margines tego formantu edycji.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość lewego marginesu w programie WORD niskiego rzędu i szerokość prawego marginesu w programie WORD wysokiego rzędu.

### <a name="remarks"></a>Uwagi

Marginesy są mierzone w pikselach.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest dostępna począwszy od systemów Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify

Wywołanie tej funkcji, aby ustalić, czy zawartość formantu edycji zostały zmodyfikowane.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli zawartość kontroli edycji zostały zmodyfikowane; 0, jeśli pozostały niezmienione.

### <a name="remarks"></a>Uwagi

System Windows utrzymuje wewnętrzną flagę wskazującą, czy zawartość formantu edycji została zmieniona. Ta flaga jest wyczyszczona, gdy formant edycji jest tworzony po raz pierwszy i może być również wyczyszczone przez wywołanie [SetModify](#setmodify) funkcji elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar

Wywołanie tej funkcji, aby pobrać znak hasła, który jest wyświetlany w formancie edycji, gdy użytkownik wprowadza tekst.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa znak, który ma być wyświetlany zamiast znaku wpisanego przez użytkownika. Zwracana wartość jest NULL, jeśli nie istnieje znak hasła.

### <a name="remarks"></a>Uwagi

Jeśli formant edycji zostanie utworzony przy stylie ES_PASSWORD, biblioteka DLL obsługująca formant określa domyślny znak hasła. Manifest lub [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) metoda określa, które biblioteki DLL obsługuje formant edycji. Jeśli user32.dll obsługuje formant edycji, domyślnym znakiem hasła jest ASTERISK ('*', U+002A). Jeśli comctl32.dll w wersji 6 obsługuje kontrolkę edycji, domyślnym znakiem jest BLACK CIRCLE ('●', U+25CF). Aby uzyskać więcej informacji o tym, która biblioteka DLL i wersja obsługuje typowe formanty, zobacz [Wersje powłoki i typowe formanty](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Ta metoda wysyła [komunikat EM_GETPASSWORDCHAR,](/windows/win32/Controls/em-getpasswordchar) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect

Wywołanie tej funkcji, aby uzyskać prostokąt formatowania formantu edycji.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę, `RECT` która odbiera prostokąt formatowania.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna kontrolki edycji.

Prostokąt formatowania wielowierszowego formantu edycji może być modyfikowany przez funkcje członkowskie [SetRect](#setrect) i [SetRectNP.](#setrectnp)

Aby uzyskać więcej informacji, zobacz [EM_GETRECT](/windows/win32/Controls/em-getrect) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel

Wywołanie tej funkcji, aby uzyskać początkowe i końcowe pozycje znaków bieżącego zaznaczenia (jeśli istnieje) w formancie edycji, używając wartości zwracanej lub parametrów.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odwołanie do liczby całkowitej, która otrzyma pozycję pierwszego znaku w bieżącym zaznaczeniu.

*nEndChar (wychocie)*<br/>
Odwołanie do liczby całkowitej, która otrzyma pozycję pierwszego nieselekty wybranego znaku poza końcem bieżącego zaznaczenia.

### <a name="return-value"></a>Wartość zwracana

Wersja zwracana wartość DWORD, która zawiera pozycję początkową w słowie niskiego rzędu i położenie pierwszego nieselektyowanego znaku po zakończeniu zaznaczenia w słowie wysokiego rzędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETSEL](/windows/win32/Controls/em-getsel) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip

Ukrywa każdą końcówkę dymka skojarzoną z bieżącą kontrolą edycji.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła komunikat [EM_HIDEBALLOONTIP,](/windows/win32/Controls/em-hideballoontip) który jest opisany w windows SDK.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit::Tekst limit

Wywołanie tej funkcji, aby ograniczyć długość tekstu, który użytkownik może wprowadzić do formantu edycji.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*NChary*<br/>
Określa długość (w CZAry) tekstu, który użytkownik może wprowadzić. Jeśli ten parametr wynosi 0, długość tekstu jest ustawiona na UINT_MAX bajtów. Jest to zachowanie domyślne.

### <a name="remarks"></a>Uwagi

Zmiana limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma wpływu na żaden tekst już w formancie edycji, ani nie wpływa na długość tekstu skopiowanego do formantu edycji przez funkcję elementu członkowskiego [SetWindowText](cwnd-class.md#setwindowtext) w `CWnd`programie . Jeśli aplikacja używa `SetWindowText` tej funkcji do umieszczania większej ilości tekstu w `LimitText`formancie edycji niż określono w wywołaniu do , użytkownik może usunąć dowolny tekst w formancie edycji. Jednak limit tekstu uniemożliwi użytkownikowi zastąpienie istniejącego tekstu nowym tekstem, chyba że usunięcie bieżącego zaznaczenia spowoduje, że tekst spadnie poniżej limitu tekstu.

> [!NOTE]
> W systemach Win32 (Windows NT i Windows 95/98) [Funkcja SetLimitText](#setlimittext) zastępuje tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromChar

Wywołanie tej funkcji, aby pobrać numer wiersza, który zawiera określony indeks znaków.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Zawiera wartość indeksu od zera dla żądanego znaku w tekście formantu edycji lub zawiera -1. Jeśli *nIndex* jest -1, określa bieżący wiersz, czyli wiersz, który zawiera cieszę.

### <a name="return-value"></a>Wartość zwracana

Numer wiersza od zera wiersza zawierającego indeks znaków określony przez *nIndex*. Jeśli *nIndex* wynosi -1, zwracana jest liczba wiersza zawierającego pierwszy znak zaznaczenia. Jeśli nie ma wyboru, zwracany jest bieżący numer wiersza.

### <a name="remarks"></a>Uwagi

Indeks znaków to liczba znaków od początku kontrolki edycji.

Ta funkcja elementu członkowskiego jest używana tylko przez kontrolki edycji wielowierszowej.

Aby uzyskać więcej informacji, zobacz [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex

Wywołanie tej funkcji, aby pobrać indeks znaków wiersza w ramach wielowierszowego formantu edycji.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLina*<br/>
Zawiera wartość indeksu dla żądanego wiersza w tekście formantu edycji lub zawiera -1. Jeśli *nLine* jest -1, określa bieżący wiersz, czyli wiersz, który zawiera cieszę.

### <a name="return-value"></a>Wartość zwracana

Indeks znaków wiersza określonego w *nLine* lub -1, jeśli określona liczba wierszy jest większa niż liczba wierszy w formancie edycji.

### <a name="remarks"></a>Uwagi

Indeks znaków to liczba znaków od początku kontrolki edycji do określonego wiersza.

Ta funkcja elementu członkowskiego jest przetwarzana tylko przez kontrolki edycji wielowierszowej.

Aby uzyskać więcej informacji, zobacz [EM_LINEINDEX](/windows/win32/controls/em-lineindex) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit::Długość linii

Pobiera długość wiersza w formancie edycji.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLina*<br/>
Indeks od zera znaku w wierszu, którego długość ma zostać pobrana. Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

W przypadku formantów edycji jednowierszowej zwracana jest długość tekstu w formancie edycji w CZAR.

W przypadku kontrolek edycji wielowierszowej zwracana jest długość w TCHARs wiersza określonego przez parametr *nLine.* W przypadku tekstu ANSI długość jest liczbą bajtów w wierszu; w przypadku tekstu Unicode długość jest liczbą znaków w wierszu. Długość nie obejmuje znaku powrotu karetki na końcu wiersza.

Jeśli parametr *nLine* jest większa niż liczba znaków w formancie, zwracana wartość wynosi zero.

Jeśli parametr *nLine* wynosi -1, zwracana jest liczba niezaznaczonych znaków w wierszach zawierających zaznaczone znaki. Na przykład jeśli zaznaczenie rozciąga się od czwartego znaku jednego wiersza do ósmego znaku od końca następnego wiersza, zwracana wartość wynosi 10. Oznacza to, że trzy znaki w pierwszym wierszu i siedem w następnym.

Aby uzyskać więcej informacji na temat typu TCHAR, zobacz wiersz TCHAR w tabeli w [typach danych systemu Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Uwagi

Ta metoda jest obsługiwana przez komunikat [EM_LINELENGTH,](/windows/win32/Controls/em-linelength) który jest opisany w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll

Wywołanie tej funkcji, aby przewinąć tekst wielowierszowego formantu edycji.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*n Linie*<br/>
Określa liczbę linii do przewijania w pionie.

*NChary*<br/>
Określa liczbę pozycji znaków do przewijania w poziomie. Ta wartość jest ignorowana, jeśli formant edycji ma styl ES_RIGHT lub ES_CENTER.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

Formant edycji nie przewija się w pionie obok ostatniego wiersza tekstu w formancie edycji. Jeśli bieżący wiersz wraz z liczbą wierszy określonych przez *nLines* przekracza całkowitą liczbę wierszy w formancie edycji, wartość jest korygowana tak, aby ostatni wiersz formantu edycji był przewijany do góry okna sterowania edycją.

`LineScroll`można przewijać w poziomie obok ostatniego znaku dowolnej linii.

Aby uzyskać więcej informacji, zobacz [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::Paste

Wywołanie tej funkcji, aby wstawić `CEdit` dane ze Schowka do punktu wstawiania.

```
void Paste();
```

### <a name="remarks"></a>Uwagi

Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.

Aby uzyskać więcej informacji, zobacz [WM_PASTE](/windows/win32/dataxchg/wm-paste) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosFromChar

Wywołanie tej funkcji, aby uzyskać położenie (w lewym `CEdit` górnym rogu) danego znaku w tym obiekcie.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
Indeks od zera określonego znaku.

### <a name="return-value"></a>Wartość zwracana

Współrzędne lewego górnego rogu znaku określonego przez *nChar*.

### <a name="remarks"></a>Uwagi

Znak jest określony przez podanie jego wartość indeksu od zera. Jeśli *nChar* jest większy niż indeks ostatniego znaku w tym `CEdit` obiekcie, zwracana wartość określa współrzędne pozycji znaku tuż obok ostatniego znaku w tym `CEdit` obiekcie.

> [!NOTE]
> Ta funkcja elementu członkowskiego jest dostępna począwszy od systemów Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel

Wywołanie tej funkcji, aby zastąpić bieżące zaznaczenie w formancie edycji tekstem określonym przez *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText (Tekst lpszNewText)*<br/>
Wskazuje ciąg zakończony wartością null zawierający tekst zastępczy.

*bCanUndo*<br/>
Aby określić, że tę funkcję można cofnąć, należy ustawić wartość tego parametru na WARTOŚĆ PRAWDA . Wartością domyślną jest FAŁSZ.

### <a name="remarks"></a>Uwagi

Zastępuje tylko część tekstu w formancie edycji. Aby zastąpić cały tekst, należy użyć funkcji elementu członkowskiego [CWnd::SetWindowText.](cwnd-class.md#setwindowtext)

Jeśli nie ma bieżącego zaznaczenia, tekst zastępczy jest wstawiany w bieżącym miejscu kursora.

Aby uzyskać więcej informacji, zobacz [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner

Ustawia tekst wyświetlany jako sygnał tekstowy lub wskazówka w formancie edycji, gdy formant jest pusty.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[w] Wskaźnik do ciągu, który zawiera sygnał do wyświetlenia w formancie edycji.

*fDrawWhenFocused*<br/>
[w] Jeśli FALSE, baner sygnalizacji nie jest rysowany, gdy użytkownik kliknie w formancie edycji i nadaje kontroli fokus.

Jeśli true, baner sygnalizacji jest rysowany nawet wtedy, gdy formant ma fokus. Baner sygnalizacji znika, gdy użytkownik zaczyna wpisywać formant.

Wartością domyślną jest FAŁSZ.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_SETCUEBANNER,](/windows/win32/Controls/em-setcuebanner) który jest opisany w windows SDK. Aby uzyskać więcej informacji, zobacz [makro Edit_SetCueBannerTextFocused.](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)

### <a name="example"></a>Przykład

Poniższy przykład pokazuje [CEdit::SetCueBanner](#setcuebanner) metody.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle

Wywołanie tej funkcji, aby ustawić dojście do pamięci lokalnej, która będzie używana przez kontrolkę edycji wielowierszowej.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hBuffer (właśc.*<br/>
Zawiera dojście do pamięci lokalnej. Ten dojście musi zostać utworzony przez poprzednie wywołanie funkcji [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows przy użyciu flagi LMEM_MOVEABLE. Zakłada się, że pamięć zawiera ciąg zakończony z wartością null. Jeśli tak nie jest, pierwszy bajt przydzielonej pamięci powinien być ustawiony na 0.

### <a name="remarks"></a>Uwagi

Formant edycji użyje tego buforu do przechowywania aktualnie wyświetlanego tekstu zamiast przydzielania własnego buforu.

Ta funkcja elementu członkowskiego jest przetwarzana tylko przez wielowierszowe kontrolki edycji.

Zanim aplikacja ustawi nowy dojście pamięci, należy użyć [gethandle](#gethandle) funkcji elementu członkowskiego, aby `LocalFree` uzyskać uchwyt do bieżącego buforu pamięci i zwolnić tę pamięć za pomocą funkcji systemu Windows.

`SetHandle`czyści bufor cofania (funkcja elementu członkowskiego [CanUndo](#canundo) zwraca następnie 0) i flagę modyfikacji wewnętrznej (funkcja elementu członkowskiego [GetModify](#getmodify) zwraca następnie wartość 0). Okno kontroli edycji zostanie ponownie narysowane.

Tej funkcji elementu członkowskiego można używać w wielowierszowym formancie edycji w oknie dialogowym tylko po utworzeniu okna dialogowego z ustawioną flagą stylu DS_LOCALEDIT.

> [!NOTE]
> `GetHandle`nie będzie działać z systemem Windows 95/98. Jeśli zadzwonisz `GetHandle` w systemie Windows 95/98, zwróci null. `GetHandle`będzie działać zgodnie z dokumentami w systemie Windows NT, wersjach 3.51 i nowszych.

Aby uzyskać więcej informacji, zobacz [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)i [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight

Wyróżnia zakres tekstu wyświetlany w bieżącym formancie edycji.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ichStart*|[w] Indeks od zera pierwszego znaku w zakresie tekstu do podświetlenia.|
|*ichEnd (niem.*|[w] Indeks od zera ostatniego znaku w zakresie tekstu do podświetlenia.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [EM_SETHILITE,](/windows/win32/Controls/em-sethilite) który jest opisany w windows SDK.  Ta metoda wysyła komunikat [EM_SETHILITE,](/windows/win32/Controls/em-sethilite) który jest opisany w windows SDK. Oba `SetHighlight` `GetHighlight` i są włączone tylko dla kompilacji UNICODE.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText

Wywołanie tej funkcji elementu członkowskiego, `CEdit` aby ustawić limit tekstu dla tego obiektu.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*Nmax*<br/>
Nowy limit tekstu w znakach.

### <a name="remarks"></a>Uwagi

Limit tekstu to maksymalna ilość tekstu w znakach, którą formant edycji może zaakceptować.

Zmiana limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma wpływu na żaden tekst już w formancie edycji, ani nie wpływa na długość tekstu skopiowanego do formantu edycji przez funkcję elementu członkowskiego [SetWindowText](cwnd-class.md#setwindowtext) w `CWnd`programie . Jeśli aplikacja używa `SetWindowText` tej funkcji do umieszczania większej ilości tekstu w `LimitText`formancie edycji niż określono w wywołaniu do , użytkownik może usunąć dowolny tekst w formancie edycji. Jednak limit tekstu uniemożliwi użytkownikowi zastąpienie istniejącego tekstu nowym tekstem, chyba że usunięcie bieżącego zaznaczenia spowoduje, że tekst spadnie poniżej limitu tekstu.

Ta funkcja zastępuje [LimitText](#limittext) w win32.

Aby uzyskać więcej informacji, zobacz [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins

Wywołanie tej metody, aby ustawić lewy i prawy margines tego formantu edycji.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nNaft*<br/>
Szerokość nowego lewego marginesu w pikselach.

*nWej*<br/>
Szerokość nowego prawego marginesu w pikselach.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja elementu członkowskiego jest dostępna począwszy od systemów Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify

Wywołanie tej funkcji, aby ustawić lub wyczyścić zmodyfikowaną flagę dla formantu edycji.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZmodyfikowany*<br/>
Wartość TRUE wskazuje, że tekst został zmodyfikowany, a wartość FALSE wskazuje, że jest niezmodyfikowany. Domyślnie ustawiona jest zmodyfikowana flaga.

### <a name="remarks"></a>Uwagi

Zmodyfikowana flaga wskazuje, czy tekst w formancie edycji został zmodyfikowany. Jest on ustawiany automatycznie za każdym razem, gdy użytkownik zmieni tekst. Jego wartość może być pobierana za pomocą funkcji elementu członkowskiego [GetModify.](#getmodify)

Aby uzyskać więcej informacji, zobacz [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar

Wywołanie tej funkcji, aby ustawić lub usunąć znak hasła wyświetlany w formancie edycji, gdy użytkownik wpisuje tekst.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*Ch*<br/>
Określa znak, który ma być wyświetlany zamiast znaku wpisanego przez użytkownika. Jeśli *ch* wynosi 0, wyświetlane są rzeczywiste znaki wpisane przez użytkownika.

### <a name="remarks"></a>Uwagi

Po ustawieniu znaku hasła znak ten jest wyświetlany dla każdego znaku wpisywał użytkownika.

Ta funkcja elementu członkowskiego nie ma wpływu na kontrolkę edycji wielowierszowej.

Gdy `SetPasswordChar` wywoływana jest `CEdit` funkcja elementu członkowskiego, przerysuje wszystkie widoczne znaki przy użyciu znaku określonego przez *ch*.

Jeśli formant edycji jest tworzony przy ES_PASSWORD [stylu,](styles-used-by-mfc.md#edit-styles) domyślny znak hasła <strong>\*</strong>jest ustawiony na gwiazdkę ( ). Ten styl jest `SetPasswordChar` usuwany, jeśli jest wywoływana z *ch* ustawiona na 0.

Aby uzyskać więcej informacji, zobacz [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly

Wywołuje tę funkcję, aby ustawić stan tylko do odczytu kontrolki edycji.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bCzytyNie*<br/>
Określa, czy ustawić lub usunąć stan tylko do odczytu formantu edycji. Wartość TRUE ustawia stan tylko do odczytu; wartość FALSE ustawia stan do odczytu/zapisu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja zakończy się pomyślnie lub 0, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Bieżące ustawienie można znaleźć, testując flagę [ES_READONLY](styles-used-by-mfc.md#edit-styles) w wartości zwracanej [CWnd::GetStyle](cwnd-class.md#getstyle).

Aby uzyskać więcej informacji, zobacz [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect

Wywołanie tej funkcji, aby ustawić wymiary prostokąta przy użyciu określonych współrzędnych.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje strukturę `RECT` `CRect` lub obiekt, który określa nowe wymiary prostokąta formatowania.

### <a name="remarks"></a>Uwagi

Ten element członkowski jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Służy `SetRect` do ustawiania prostokąta formatowania wielowierszowego formantu edycji. Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna kontrolki edycji. Po utworzeniu formantu edycji prostokąt formatowania jest taki sam jak obszar klienta okna kontroli edycji. Za pomocą `SetRect` funkcji elementu członkowskiego aplikacja może sprawić, że prostokąt formatowania będzie większy lub mniejszy niż okno sterowania edycją.

Jeśli formant edycji nie ma paska przewijania, tekst zostanie przycięty, a nie zawinięty, jeśli prostokąt formatowania jest większy niż okno. Jeśli formant edycji zawiera obramowanie, prostokąt formatowania jest zmniejszany o rozmiar obramowania. Jeśli prostokąt zostanie dostosowany przez `GetRect` funkcję elementu członkowskiego, należy usunąć rozmiar obramowania przed `SetRect`przekazaniem prostokąta do .

Po `SetRect` wywołaniu tekst formantu edycji jest również sformatowany i ponownie wyeksponowany.

Aby uzyskać więcej informacji, zobacz [EM_SETRECT](/windows/win32/Controls/em-setrect) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP

Wywołanie tej funkcji w celu ustawienia prostokąta formatowania wielowierszowego formantu edycji.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje na `RECT` strukturę lub `CRect` obiekt, który określa nowe wymiary prostokąta.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest prostokątem ograniczającym tekst, który jest niezależny od rozmiaru okna kontrolki edycji.

`SetRectNP`jest identyczny `SetRect` z funkcją elementu członkowskiego, z tą różnicą, że okno kontroli edycji nie jest ponownie rysowane.

Po utworzeniu formantu edycji prostokąt formatowania jest taki sam jak obszar klienta okna kontroli edycji. Wywołując funkcję `SetRectNP` elementu członkowskiego, aplikacja może sprawić, że prostokąt formatowania będzie większy lub mniejszy niż okno kontroli edycji.

Jeśli formant edycji nie ma paska przewijania, tekst zostanie przycięty, a nie zawinięty, jeśli prostokąt formatowania jest większy niż okno.

Ten element członkowski jest przetwarzany tylko przez wielowierszowe kontrolki edycji.

Aby uzyskać więcej informacji, zobacz [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel

Wywołanie tej funkcji, aby wybrać zakres znaków w formancie edycji.

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parametry

*dwWybory*<br/>
Określa pozycję początkową w słowie niskiego rzędu i pozycję końcową w słowie wysokiego rzędu. Jeśli wyraz niskiego rzędu ma rozmiar 0, a wyraz wysokiego rzędu to -1, zaznaczony jest cały tekst w formancie edycji. Jeśli wyraz niskiego rzędu wynosi -1, wszelkie bieżące zaznaczenie jest usuwane.

*bNoScroll*<br/>
Wskazuje, czy ciesza powinna być przewijana do widoku. Jeśli FALSE, opiekuna jest przewijana do widoku. Jeśli true, ciesza nie jest przewijana do widoku.

*nStartChar*<br/>
Określa pozycję początkową. Jeśli *nStartChar* jest 0 i *nEndChar* jest -1, cały tekst w formancie edycji jest zaznaczona. Jeśli *nStartChar* jest -1, wszelkie bieżące zaznaczenie jest usuwany.

*nEndChar (wychocie)*<br/>
Określa pozycję końcową.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_SETSEL](/windows/win32/Controls/em-setsel) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops

Wywołanie tej funkcji, aby ustawić tabulatory w wielowierszowym formancie edycji.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Określa, że tabulatory mają być ustawiane w każdym oknie dialogowym *cxEachStop.*

*nTabStops (Niem.*<br/>
Określa liczbę tabulatorów zawartych w *rgTabStops*. Liczba ta musi być większa niż 1.

*rgTabStops (100)*<br/>
Wskazuje tablicę niepodpisanych liczby całkowite określające tabulatory w jednostkach dialogowych. Jednostka dialogowa jest odległością poziomą lub pionową. Jedna pozioma jednostka okna dialogowego jest równa jednej czwartej bieżącej jednostki szerokości podstawy okna dialogowego, a 1 pionowa jednostka okna dialogowa jest równa jednej ósmej bieżącej jednostki wysokości podstawy okna dialogowego. Jednostki podstawowe okna dialogowego są obliczane na podstawie wysokości i szerokości bieżącej czcionki systemowej. Funkcja `GetDialogBaseUnits` Systemu Windows zwraca bieżące jednostki bazowe okna dialogowego w pikselach.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli karty zostały ustawione; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Gdy tekst jest kopiowany do wielowierszowego formantu edycji, dowolny znak karty w tekście spowoduje wygenerowanie miejsca do następnego tabulatora.

Aby ustawić tabulatory na domyślny rozmiar 32 jednostek dialogowych, należy wywołać wersję bez parametrów tej funkcji elementu członkowskiego. Aby ustawić tabulatory na rozmiar inny niż 32, wywołaj wersję z parametrem *cxEachStop.* Aby ustawić tabulatory na tablicę rozmiarów, użyj wersji z dwoma parametrami.

Ta funkcja elementu członkowskiego jest przetwarzana tylko przez kontrolki edycji wielowierszowej.

`SetTabStops`nie powoduje automatycznego ponownego rysowania okna edycji. Jeśli zmienisz tabulatory dla tekstu znajdującego się już w formancie edycji, zadzwoń do [CWnd::InvalidateRect,](cwnd-class.md#invalidaterect) aby ponownie wyrywać okno edycji.

Aby uzyskać więcej informacji, zobacz [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) i [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [dla CEditView::SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip

Wyświetla końcówkę odnośnika skojarzoną z bieżącą kontrolką edycji.

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
|*pEditBalloonTip (Porady dotyczące gry w gry w gry)*|[w] Wskaźnik do [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) struktury, która opisuje końcówkę dymka.|
|*lpszTitle (lpszTitle)*|[w] Wskaźnik do ciągu Unicode, który zawiera tytuł końcówki dymka.|
|*lpszText (tekst)*|[w] Wskaźnik do ciągu Unicode zawierającego tekst końcówki dymka.|
|*ttiicon ( ttiIcon )*|[w] **Int,** który określa typ ikony do skojarzenia z końcówką dymka. Wartość domyślna to TTI_NONE. Aby uzyskać więcej `ttiIcon` informacji, zobacz element członkowski [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) struktury.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła komunikat [EM_SHOWBALLOONTIP,](/windows/win32/Controls/em-showballoontip) który jest opisany w windows SDK. Aby uzyskać więcej informacji, zobacz [makro Edit_ShowBalloonTip.](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje `m_cedit`zmienną , która jest używana do uzyskania dostępu do bieżącego formantu edycji. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Przykład

W poniższym przykładzie kodu jest wyświetlana wskazówka odnośnika dla formantu edycji. [Metoda CEdit::ShowBalloonTip](#showballoontip) określa tekst etykietki tytułu i dymka.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit::Cofnij

Wywołanie tej funkcji, aby cofnąć ostatnią operację kontroli edycji.

```
BOOL Undo();
```

### <a name="return-value"></a>Wartość zwracana

W przypadku kontrolki edycji jednowierszowej zwracana wartość zwracana jest zawsze niezerowa. W przypadku formantu edycji wielowierszowej wartość zwracana jest niezerowa, jeśli operacja cofania zakończy się pomyślnie, lub 0, jeśli operacja cofania nie powiedzie się.

### <a name="remarks"></a>Uwagi

Można również cofnąć operację cofania. Na przykład można przywrócić usunięty tekst przy `Undo`pierwszym wywołaniu do pliku . Tak długo, jak nie ma interwencji operacji edycji, można usunąć `Undo`tekst ponownie z drugiego połączenia do .

Aby uzyskać więcej informacji, zobacz [EM_UNDO](/windows/win32/Controls/em-undo) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](cwnd-class.md)<br/>
[Klasa CButton](cbutton-class.md)<br/>
[Klasa CComboBox](ccombobox-class.md)<br/>
[Klasa CListBox](clistbox-class.md)<br/>
[Klasa CScrollBar](cscrollbar-class.md)<br/>
[Klasa CStatic](cstatic-class.md)<br/>
[Klasa CDialog](cdialog-class.md)
