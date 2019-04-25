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
ms.openlocfilehash: 45c03d142c34186660aa2715081ffb0f45e85ccc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164075"
---
# <a name="cedit-class"></a>Klasa CEdit

Oferuje funkcje formantu edycji Windows.

## <a name="syntax"></a>Składnia

```
class CEdit : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|Konstruuje `CEdit` obiekt formantu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Określa, czy można cofnąć operacji kontrolki edycji.|
|[CEdit::CharFromPos](#charfrompos)|Pobiera wiersz i znak indeksów dla najbardziej zbliżony do określonej pozycji znaku.|
|[CEdit::Clear](#clear)|Usuwa (czyści) kontrolować aktualnie zaznaczonej edycji (jeśli istnieje).|
|[CEdit::Copy](#copy)|Kopiuje bieżącego zaznaczenia (jeśli istnieją) w kontrolce edycji do Schowka w formacie CF_TEXT.|
|[CEdit::Create](#create)|Tworzy formant edycji Windows i dołącza je do `CEdit` obiektu.|
|[CEdit::Cut](#cut)|Kontrolowanie bieżące zaznaczenie (jeśli istnieje) w trakcie edycji usuwa (kawałki) i sformatować usunięty tekst do Schowka w CF_TEXT kopii.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Resetuje kontroli (czyści) Flaga Cofnij edycję.|
|[CEdit::FmtLines](#fmtlines)|Ustawia włączenia nietrwałego podział wiersza znakami lub wyłączyć w kontrolce edycji wielu linii.|
|[CEdit::GetCueBanner](#getcuebanner)|Pobiera tekst, który jest wyświetlany jako podpowiedź tekstowa lub porady w formancie edycji, gdy kontrolka jest pusta i nie ma fokusu.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Określa znajdujące się najwyżej wiersza widocznego w formancie edycji.|
|[CEdit::GetHandle](#gethandle)|Pobiera uchwyt do pamięci, które jest aktualnie przydzielone dla formantu wielowierszowe edytowanie.|
|[CEdit::GetHighlight](#gethighlight)|Pobiera indeksy początkowe i końcowe znaki w zakresie tekst, który jest wyróżniony w bieżącym kontrolki edycji.|
|[CEdit::GetLimitText](#getlimittext)|Pobiera maksymalną ilość tekstu `CEdit` może zawierać.|
|[CEdit::GetLine](#getline)|Pobiera wiersz tekstu z kontrolki edycji.|
|[CEdit::GetLineCount](#getlinecount)|Pobiera liczbę wierszy w formancie edycji wielu linii.|
|[CEdit::GetMargins](#getmargins)|Pobiera lewego i prawego marginesu tego `CEdit`.|
|[CEdit::GetModify](#getmodify)|Określa, czy zawartość formantu edycji został zmieniony.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Pobiera znaku hasła, wyświetlana w formancie edycji, gdy użytkownik wprowadzi tekst.|
|[CEdit::GetRect](#getrect)|Pobiera formatowania prostokąt formant edycji.|
|[CEdit::GetSel](#getsel)|Pobiera położenie pierwszy i ostatni znak bieżące zaznaczenie w formancie edycji.|
|[CEdit::HideBalloonTip](#hideballoontip)|Ukrywa dowolnym dymku skojarzone z bieżącym kontrolki edycji.|
|[CEdit::LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić do kontrolki edycji.|
|[CEdit::LineFromChar](#linefromchar)|Pobiera numer wiersza w wierszu, który zawiera indeks określonego znaku.|
|[CEdit::LineIndex](#lineindex)|Pobiera indeks znaków wiersza w formancie edycji wielu linii.|
|[CEdit::LineLength](#linelength)|Pobiera długość wiersza w formancie edycji.|
|[CEdit::LineScroll](#linescroll)|Przewija tekst kontrolki edycji wielu linii.|
|[CEdit::Paste](#paste)|Wstawia dane ze Schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.|
|[CEdit::PosFromChar](#posfromchar)|Pobiera współrzędne lewego górnego rogu indeksu określonego znaku.|
|[CEdit::ReplaceSel](#replacesel)|Zamienia bieżące zaznaczenie w formancie edycji określony tekst.|
|[CEdit::SetCueBanner](#setcuebanner)|Ustawia tekst, który jest wyświetlany jako podpowiedź tekstowa lub porady w formancie edycji, gdy kontrolka jest pusta i nie ma fokusu.|
|[CEdit::SetHandle](#sethandle)|Ustawia dojście do pamięci lokalnej, używany przez kontrolkę edycji wielu linii.|
|[CEdit::SetHighlight](#sethighlight)|Najważniejsze funkcje zakres tekstu wyświetlanego w bieżącym formant edycji.|
|[CEdit::SetLimitText](#setlimittext)|Określa maksymalną ilość tekstu `CEdit` może zawierać.|
|[CEdit::SetMargins](#setmargins)|Ustawia lewego i prawego marginesu tego `CEdit`.|
|[CEdit::SetModify](#setmodify)|Ustawia lub czyści flagi modyfikacji kontrolki edycji.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Ustawia lub usuwa znaku hasła, wyświetlana w formancie edycji, gdy użytkownik wprowadzi tekst.|
|[CEdit::SetReadOnly](#setreadonly)|Ustawia stan tylko do odczytu formant edycji.|
|[CEdit::SetRect](#setrect)|Ustawia prostokąt formatowania kontroli wielowierszowe edytowanie i aktualizuje formantu.|
|[CEdit::SetRectNP](#setrectnp)|Ustawia prostokąt formatowania kontroli wielowierszowe edytowanie bez ponownego narysowania okno kontrolki.|
|[CEdit::SetSel](#setsel)|Wybiera zakres znaków w kontrolce edycji.|
|[CEdit::SetTabStops](#settabstops)|Formant edycji zestawy tabulatorów w wielu wierszach.|
|[CEdit::ShowBalloonTip](#showballoontip)|Wyświetla dymku, który jest skojarzony z bieżącym kontrolki edycji.|
|[CEdit::Undo](#undo)|Cofa ostatnią operację kontrolki edycji.|

## <a name="remarks"></a>Uwagi

Formant edycji jest oknem podrzędnym prostokątny, w którym użytkownik może wpisać tekst.

Można utworzyć formant edycji, z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CEdit` do konstruowania `CEdit` obiektu, a następnie wywołaj [Utwórz](#create) funkcji elementu członkowskiego, aby utworzyć Windows formantu edycyjnego i dołącz je do `CEdit` obiektu.

Konstrukcja może być jednoetapowy proces w klasę pochodną `CEdit`. Zapisywanie konstruktora dla klasy pochodnej i wywołanie `Create` z w konstruktorze.

`CEdit` Najważniejsze funkcje z dziedziczy `CWnd`. Do ustawiania i pobierania tekstu z `CEdit` obiektu, należy użyć `CWnd` elementów członkowskich [SetWindowText](cwnd-class.md#setwindowtext) i [getwindowtext —](cwnd-class.md#getwindowtext), które set lub get kontrolować całą zawartość edycji, nawet jeśli jego jest wieloliniowy formant. Wiersze tekstu w kontrolce wielowierszowy są oddzielone sekwencje znaków "\r\n". Ponadto w przypadku wielowierszowy formant edycji, pobieranie i ustawianie część tekstu formantu przez wywołanie metody `CEdit` elementów członkowskich [getline —](#getline), [SetSel](#setsel), [GetSel](#getsel)i [ ReplaceSel](#replacesel).

Jeśli chcesz obsługiwać Windows powiadomienia wysyłane przez formant edycji do elementu nadrzędnego (zazwyczaj klasą pochodną `CDialog`), dodanie funkcji składowej wejścia i program obsługi komunikatów mapy komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów ma następującą postać:

  **ON_**_POWIADOMIEŃ_**(** _identyfikator_**,** _memberFxn_ **)**

gdzie `id` Określa identyfikator okna elementu podrzędnego kontrolki edycji wysyłania powiadomienia, a `memberFxn` nazywa się nadrzędny element członkowski funkcji zostały napisane do obsługi powiadomień.

Prototyp funkcji elementu nadrzędnego jest następująca:

**afx_msg** void memberFxn **();**

Poniżej przedstawiono listę potencjalnych wpisy mapy komunikatów i opis przypadków, w których będą one wysyłane do elementu nadrzędnego:

- ON_EN_CHANGE użytkownik ma podjąć akcję, która może być zmieniony tekst w kontrolce edycji. W odróżnieniu od EN_UPDATE komunikat powiadomienia taki komunikat powiadomienia są wysyłane po Windows aktualizuje okno.

- ON_EN_ERRSPACE kontrolki edycji nie może przydzielić wystarczającej ilości pamięci, aby spełnić określonego żądania.

- ON_EN_HSCROLL użytkownik klika formant edycji poziomy pasek przewijania. Okno nadrzędne zostanie powiadomiony, zanim ekran zostanie zaktualizowany.

- ON_EN_KILLFOCUS kontrolki edycji traci fokus wprowadzania.

- ON_EN_MAXTEXT bieżącego włożenia przekroczył określoną liczbę znaków dla kontrolki edycji i dlatego została obcięta. Również wysyłane, gdy formant edycji nie ma stylu ES_AUTOHSCROLL liczbę znaków, które ma zostać wstawiony spowoduje przekroczenie szerokość kontrolki edycji. Również wysyłane, gdy formant edycji nie ma stylu ES_AUTOVSCROLL i łączna liczba wierszy, w wyniku Wstawianie tekstu spowoduje przekroczenie wysokość kontrolki edycji.

- ON_EN_SETFOCUS wysyłany, gdy formant edycji otrzymuje fokus wprowadzania.

- ON_EN_UPDATE kontrolki edycji wkrótce zmieniony tekst. Wysyłane po formant został sformatowany tekst, ale przed jego ekrany tekst tak, aby rozmiar okna może się zmienić, jeśli to konieczne.

- ON_EN_VSCROLL użytkownik klika formant edycji pionowy pasek przewijania. Okno nadrzędne zostanie powiadomiony, zanim ekran zostanie zaktualizowany.

Jeśli tworzysz `CEdit` obiektu w oknie dialogowym, `CEdit` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

Jeśli tworzysz `CEdit` obiekt z zasobem okna dialogowego za pomocą edytora okien dialogowych `CEdit` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

Jeśli tworzysz `CEdit` obiekt w tym oknie, konieczne może zniszczyć ją. Jeśli tworzysz `CEdit` obiektów na stosie, zostanie zniszczony automatycznie. Jeśli tworzysz `CEdit` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu zniszczyć ją, gdy użytkownik kończy Windows formantu edycyjnego. Jeśli przydzielisz wszystkie pamięci w `CEdit` obiektów, Zastąp `CEdit` destruktora w celu usunięcia alokacje.

Aby zmodyfikować określone style w formancie edycji (na przykład ES_READONLY) można wysyłać wiadomości określonych do kontrolki zamiast [ModifyStyle](cwnd-class.md#modifystyle). Zobacz [style kontrolki edycji](/windows/desktop/Controls/edit-control-styles) w Windows SDK.

Aby uzyskać więcej informacji na temat `CEdit`, zobacz [formantów](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

Wywołaj tę funkcję, aby określić, jeśli ostatnia operacja edycji można cofnąć.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ostatnia operacja Edytuj mogą zostać cofnięte przez wywołanie `Undo` funkcji członkowskiej; 0, jeśli nie można cofnąć.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_CANUNDO](/windows/desktop/Controls/em-canundo) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::Undo](#undo).

##  <a name="cedit"></a>  CEdit::CEdit

Konstruuje `CEdit` obiektu.

```
CEdit();
```

### <a name="remarks"></a>Uwagi

Użyj [Utwórz](#create) do konstruowania Windows formantu edycyjnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

Wywołaj tę funkcję, aby pobrać wiersz zaczynający się od zera i indeksów znak znaku najbliższym określonego punktu w tym `CEdit` kontroli

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
Współrzędne punktu w obszarze klienta, to `CEdit` obiektu.

### <a name="return-value"></a>Wartość zwracana

Indeks znaków w SŁOWIE niskiego rzędu, a indeks wiersza w programie WORD wyższego rzędu.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

Wywołaj tę funkcję można usunąć (Wyczyść) bieżącego zaznaczenia (jeśli istnieją) w kontrolce edycji.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Usuwanie wykonywane przez `Clear` mogą zostać cofnięte przez wywołanie metody [Cofnij](#undo) funkcja elementu członkowskiego.

Aby usunąć bieżące zaznaczenie i umieść usunięto zawartość w Schowku, należy wywołać [Wytnij](#cut) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [WM_CLEAR](/windows/desktop/dataxchg/wm-clear) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

Wywołaj tę funkcję, aby coy bieżące zaznaczenie (jeśli istnieją) w formancie edycji do Schowka w formacie CF_TEXT.

```
void Copy();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [WM_COPY](/windows/desktop/dataxchg/wm-copy) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

Tworzy formant edycji Windows i dołącza je do `CEdit` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki edycji. Zastosuj dowolną kombinację [style edycji](styles-used-by-mfc.md#edit-styles) do formantu.

*Rect*<br/>
Określa rozmiar i położenie kontrolki edycji. Może być `CRect` obiektu lub `RECT` struktury.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki edycji (zazwyczaj `CDialog`). Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki edycji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inicjowanie zakończy się; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CEdit` obiektu w dwóch krokach. Po pierwsze wywołanie `CEdit` Konstruktor i następnie wywołaniu `Create`, który tworzy Windows formantu edycyjnego i dołącza go do `CEdit` obiektu.

Gdy `Create` wykonuje Windows wysyła [WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize), [WM_CREATE](/windows/desktop/winmsg/wm-create), i [WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo) Komunikaty wyjściowe do kontrolki edycji.

Te komunikaty są obsługiwane domyślnie [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), i [ongetminmaxinfo —](cwnd-class.md#ongetminmaxinfo) funkcji elementów członkowskich w `CWnd` klasy bazowej. Aby rozszerzyć domyślnej obsługi komunikatów, należy wyprowadzić klasę z `CEdit`, dodać mapy komunikatów do nowej klasy, a zastąpienie powyżej funkcji elementów członkowskich programu obsługi komunikatów. Zastąp `OnCreate`, na przykład do przeprowadzenia wymaganych inicjowania dla nowej klasy.

Zastosuj następujące [Style okna ramowego](styles-used-by-mfc.md#window-styles) do kontrolki edycji.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_GROUP kontrolek grupy

- WS_TABSTOP, które mają zostać objęte kontrolki edycji kolejność tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>  CEdit::Cut

Wywołaj tę funkcję, aby usunąć (obcięty) bieżącego zaznaczenia (jeśli istnieją) w formancie edycji, a następnie skopiuj usunięty tekst do Schowka w formacie CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Uwagi

Usuwanie wykonywane przez `Cut` mogą zostać cofnięte przez wywołanie metody [Cofnij](#undo) funkcja elementu członkowskiego.

Aby usunąć bieżące zaznaczenie bez pogarszania usunięty tekst do Schowka, wywołaj [wyczyść](#clear) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [WM_CUT](/windows/desktop/dataxchg/wm-cut) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

Wywołaj tę funkcję, aby zresetować (Wyczyść) Flaga cofania formant edycji.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Uwagi

Kontrolka edycji będzie teraz nie można cofnąć ostatnią operację. Ustawiono flagę cofania, gdy operacja w kontrolce edycji można cofnąć.

Flaga cofania jest automatycznie czyszczona zawsze, gdy [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) lub [SetHandle](#sethandle) `CWnd` funkcji składowych są wywoływane.

Aby uzyskać więcej informacji, zobacz [EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

Wywołaj tę funkcję można ustawić lub wyłącz włączenia nietrwałego żadnych znaków w kontrolce edycji wielu linii.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Określa, czy mają zostać wstawione znaków nietrwałego podziału wiersza. Wartość TRUE wstawia znaków. wartość FALSE, usuwa je.

### <a name="return-value"></a>Wartość zwracana

Formatowanie występuje wartość różną od zera, jeśli istnieje; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podział wiersza nietrwałego składa się z dwóch znaki powrotu karetki i wysuwu wiersza na końcu wiersza, który został przerwany z powodu zawijania dodaje. Podział wiersza twardych składa się z jednego znaku powrotu karetki i wysuwu wiersza. Nie dotyczy linie kończyć się znakiem końca wiersza twardych `FmtLines`.

Windows będą odpowiadać tylko, jeśli `CEdit` obiekt jest formantem wielowierszowe edytowanie.

`FmtLines` dotyczy tylko buforu zwrócony przez [gethandle —](#gethandle) i tekstem zwróconym przez [WM_GETTEXT](/windows/desktop/winmsg/wm-gettext). Go nie ma wpływu na wyświetlanie tekstu w kontrolce edycji.

Aby uzyskać więcej informacji, zobacz [EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

Pobiera tekst, który jest wyświetlany jako podpowiedź tekstowa lub porady w formancie edycji, gdy kontrolka jest pusta.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[out] Wskaźnik do ciągu, który zawiera tekst wskaźnika.

*cchText*<br/>
[in] Liczba znaków, które mogą być odbierane. Liczba ta obejmuje kończącego znaku NULL.

### <a name="return-value"></a>Wartość zwracana

Pierwsze przeciążenie wartość TRUE jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

Dla drugie przeciążenie [CString](../../atl-mfc-shared/using-cstring.md) zawierające tekst wskaźnika, jeśli metoda jest pomyślnie; w przeciwnym razie pusty ciąg ("").

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner) komunikat, który jest opisany w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext) makra.

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

Wywołaj tę funkcję, aby określić najwyżej wiersza widocznego w formancie edycji.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks wiersza widocznego najwyższego poziomu. Dla formantów edycji jednowierszowego wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

Wywołaj tę funkcję można pobrać dojścia do pamięć, aktualnie przydzielonych dla kontrolki edycji wielu linii.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwytu pamięci lokalnej, który identyfikuje buforu zawierający zawartość kontrolki edycji. Jeśli wystąpi błąd, takie jak wysyłanie komunikatu do kontrolki edycji jednowierszowego, wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

Dojście jest uchwytem pamięci lokalnej i mogą być używane przez żaden z **lokalnego** funkcje pamięci Windows, w których pamięci lokalnej obsługi jako parametr.

`GetHandle` jest przetwarzany tylko przez formanty edycji wielu linii.

Wywołaj `GetHandle` wielowierszowe edytowanie kontrolki w oknie dialogowym tylko wtedy, gdy okno dialogowe zostało utworzone z ustawioną flagą DS_LOCALEDIT stylu. Jeśli nie ustawiono styl DS_LOCALEDIT, można mimo to uzyskać wartość zwracaną wartość różną od zera, ale nie można użyć wartości zwracane.

> [!NOTE]
> `GetHandle` nie będzie działać z Windows 95/98. Jeśli wywołasz `GetHandle` w Windows 95/98, to zostanie zwrócona wartość NULL. `GetHandle` będzie działać zgodnie z opisem w obszarze Windows NT w wersji 3.51 lub nowszej.

Aby uzyskać więcej informacji, zobacz [EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

Pobiera indeksy pierwszy i ostatni znak w zakresie tekst, który jest wyróżniony w bieżącym kontrolki edycji.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pichStart*|[out] Liczony od zera indeks pierwszego wystąpienia znaku w zakresie tekst, który zostanie wyróżniona.|
|*pichEnd*|[out] Liczony od zera indeks ostatniego znaku w zakresie tekst, który zostanie wyróżniona.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [EM_GETHILITE](/windows/desktop/Controls/em-gethilite) komunikat, który jest opisany w zestawie Windows SDK. Zarówno `SetHighlight` i `GetHighlight` są obecnie włączone UNICODE tylko do kompilacji.

##  <a name="getlimittext"></a>  CEdit::GetLimitText

Wywołaj tę funkcję elementu członkowskiego, aby pobrać limit tekstu, w tym `CEdit` obiektu.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący limit tekstu, w TCHARs, dla tego `CEdit` obiektu.

### <a name="remarks"></a>Uwagi

Limit tekstu jest maksymalną ilość tekstu w TCHARs, akceptujące kontrolki edycji.

> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

Wywołaj tę funkcję, aby pobrać wiersz tekstu z kontrolki edycji i umieszcza je w *lpszBuffer*.

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
Określa numer wiersza, który można pobrać z wielu linii do kontrolki edycji. Numery wierszy są oparte na zerze; wartość 0 określa pierwszy wiersz. Ten parametr jest ignorowany przez kontrolę edycji jeden wiersz.

*lpszBuffer*<br/>
Wskazuje buforu, który otrzymuje kopię wiersza. Pierwszy wyraz buforu, należy określić maksymalną liczbę TCHARs, które mogą być kopiowane do buforu.

*nMaxLength*<br/>
Określa maksymalną liczbę znaków TCHAR, które mogą być kopiowane do buforu. `GetLine` umieszcza tę wartość w pierwszy wyraz *lpszBuffer* przed wykonaniem wywołania do Windows.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście skopiowanych. Wartość zwracana to 0, jeśli numer wiersza określonego przez *nIndex* jest większa niż liczba wierszy w formancie edycji.

### <a name="remarks"></a>Uwagi

Skopiowanego wiersza nie zawiera znaku zakończenia o wartości null.

Aby uzyskać więcej informacji, zobacz [EM_GETLINE](/windows/desktop/Controls/em-getline) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetLineCount](#getlinecount).

##  <a name="getlinecount"></a>  CEdit::GetLineCount

Wywołaj tę funkcję można pobrać liczby wierszy w formancie edycji wielu linii.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Formant edycji całkowitą reprezentującą liczbę wierszy w wielu wierszach. Jeśli tekst nie został wprowadzony w formancie edycji, wartość zwracana to 1.

### <a name="remarks"></a>Uwagi

`GetLineCount` jest przetwarzany tylko przez formanty edycji wielu linii.

Aby uzyskać więcej informacji, zobacz [EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

Wywołaj tę funkcję elementu członkowskiego, aby pobrać lewego i prawego marginesu tej kontrolki edycji.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość lewy margines WORD niskiego rzędu i szerokość prawy margines w programie WORD wyższego rzędu.

### <a name="remarks"></a>Uwagi

Marginesy są mierzone w pikselach.

> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="getmodify"></a>  CEdit::GetModify

Wywołaj tę funkcję, aby ustalić, czy zawartość formantu edycji został zmieniony.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli zmodyfikowano zawartość kontrolki edycji; 0, jeśli one pozostać niezmieniona.

### <a name="remarks"></a>Uwagi

Windows przechowuje wewnętrzny flagę wskazującą, czy zawartość formantu edycji został zmieniony. Ta flaga jest czyszczona po kontrolki edycji tworzona jest najpierw, a także mogą zostać wyczyszczone, wywołując [SetModify](#setmodify) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

Wywołaj tę funkcję, aby pobrać znaku hasła, która jest wyświetlana w formancie edycji, gdy użytkownik wprowadzi tekst.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Wartość zwracana

Określa znak, który ma być wyświetlany zamiast znaku, który wpisany przez użytkownika. Wartość zwracana jest wartość NULL, jeśli istnieje Brak znaku hasła.

### <a name="remarks"></a>Uwagi

Jeśli utworzysz formant edycji stylu ES_PASSWORD biblioteki DLL, która obsługuje formant określa domyślny znak hasła. Manifest lub [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) Metoda określa, który obsługuje biblioteki DLL kontrolki edycji. Jeśli user32.dll obsługuje formant edycji, domyślny znak hasła jest GWIAZDKI ("*", U + 002A). Jeśli comctl32.dll w wersji 6 obsługuje formant edycji, domyślny znak jest czarne KÓŁKO ("●", U + 25CF). Aby uzyskać więcej informacji na temat obsługujący biblioteki DLL i wersji wspólnych formantów, zobacz [powłoki i wspólnej kontroli wersji](https://msdn.microsoft.com/library/windows/desktop/bb776779).

Ta metoda wysyła [EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

Wywołaj tę funkcję, aby pobrać formatowania prostokąt formant edycji.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` strukturę, która odbiera formatowania prostokąta.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest ograniczającą prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji.

Formatowania prostokąt kontrolkę edycji wielu linii, może być modyfikowana przez [setrect —](#setrect) i [SetRectNP](#setrectnp) funkcji elementów członkowskich.

Aby uzyskać więcej informacji, zobacz [EM_GETRECT](/windows/desktop/Controls/em-getrect) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LimitText](#limittext).

##  <a name="getsel"></a>  CEdit::GetSel

Wywołaj tę funkcję, aby uzyskać początkową i końcową pozycji znaku bieżącego zaznaczenia (jeśli istnieją) w kontrolce edycji, przy użyciu parametrów lub wartości zwracanej.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odwołanie do liczby całkowitej, który będzie otrzymywał położenie pierwszego wystąpienia znaku w bieżącym zaznaczeniu.

*nEndChar*<br/>
Odwołanie do liczby całkowitej, który będzie otrzymywał pozycja pierwszego znaku nonselected poza końcem bieżącego zaznaczenia.

### <a name="return-value"></a>Wartość zwracana

Wersja, która zwraca wartość typu DWORD zwraca wartość, która zawiera pozycja początkowa w programie word niskiego rzędu i położenie pierwszego wystąpienia znaku nonselected po zakończeniu wyboru w programie word wyższego rzędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_GETSEL](/windows/desktop/Controls/em-getsel) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

Ukrywa dowolnym dymku skojarzone z bieżącym kontrolki edycji.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła [EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="limittext"></a>  CEdit::LimitText

Wywołaj tę funkcję, aby ograniczyć długość tekstu, który użytkownik może wprowadzić do kontrolki edycji.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nChars*<br/>
Określa długość (w TCHARs) tekst, który użytkownik może wprowadzić. Jeśli ten parametr ma wartość 0, długość tekstu jest równa UINT_MAX bajtów. Jest to zachowanie domyślne.

### <a name="remarks"></a>Uwagi

Zmiana tego limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma ona wpływu na dowolny tekst już w formancie edycji ani nie ogranicza długość tekstu skopiowane do kontrolki edycji przez [SetWindowText](cwnd-class.md#setwindowtext) funkcji składowej we `CWnd`. Jeśli aplikacja używa `SetWindowText` funkcję, aby umieścić więcej tekstu w formancie edycji niż określona w wywołaniu `LimitText`, użytkownik może usunąć dowolny tekst w kontrolce edycji. Jednak limit tekstu uniemożliwi zastępując istniejący tekst nowym tekstem użytkownika, chyba że usuwanie bieżące zaznaczenie powoduje, że tekst nie przekraczają limit tekstu.

> [!NOTE]
>  W systemie Win32 (Windows 95/98 i Windows NT), [SetLimitText](#setlimittext) zastępuje tę funkcję.

Aby uzyskać więcej informacji, zobacz [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

Wywołaj tę funkcję, aby pobrać numer wiersza w wierszu, który zawiera indeks określonego znaku.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera wartość indeksu zaczynającego się od zera dla żądany znak w tekście kontrolki edycji lub zawiera wartość -1. Jeśli *nIndex* wynosi -1, określa bieżący wiersz, oznacza to, że wiersz, który zawiera karetki.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera numer wiersza, zawierający określone przez indeks znaków *nIndex*. Jeśli *nIndex* wynosi -1, numer wiersza, która zawiera pierwszy znak zaznaczenia jest zwracana. Jeśli nie zaznaczono żadnego fragmentu, zwracany jest bieżący numer wiersza.

### <a name="remarks"></a>Uwagi

Indeks znaków jest liczbę znaków od początku kontrolki edycji.

Ta funkcja elementu członkowskiego tylko jest używany przez formanty edycji wielu linii.

Aby uzyskać więcej informacji, zobacz [EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

Wywołaj tę funkcję, aby pobrać indeks znaków wiersza w formancie edycji wielu linii.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Zawiera wartość indeksu żądanego wiersza w tekście kontrolki edycji lub zawiera wartość -1. Jeśli *nLine* wynosi -1, określa bieżący wiersz, oznacza to, że wiersz, który zawiera karetki.

### <a name="return-value"></a>Wartość zwracana

Indeks znaków wiersza określonego w *nLine* lub wartość -1, jeśli określony numer wiersza jest większa niż liczba wierszy w formancie edycji.

### <a name="remarks"></a>Uwagi

Indeks znaków jest liczbę znaków od początku kontrolki edycji do określonego wiersza.

Ta funkcja członkowska jest przetwarzany tylko przez formanty edycji wielu linii.

Aby uzyskać więcej informacji, zobacz [EM_LINEINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761611) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

Pobiera długość wiersza w formancie edycji.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Liczony od zera indeks znaku w wierszu, którego długość ma być pobrana. Wartość domyślna to -1.

### <a name="return-value"></a>Wartość zwracana

Dla formantów edycji jednowierszowego wartość zwracana jest długość tekstu w formancie edycji TCHARs.

W przypadku kontrolek edycji wielowierszowy wartość zwracana jest długość wiersza określonego przez parametr TCHARs, *nLine* parametru. Tekst ANSI długość jest liczbą bajtów w linii; tekst Unicode długość jest liczba znaków w wierszu. Długość nie zawiera znaku powrotu karetki na końcu wiersza.

Jeśli *nLine* parametru jest większa niż liczba znaków w kontrolce, wartość zwracana wynosi zero.

Jeśli *nLine* parametru wynosi -1, wartość zwracana jest liczba znaków niezaznaczone w wierszach, które zawierają znaki wybrane. Na przykład jeśli zaznaczenie rozciąga się od znaku czwartego jednowierszowy za pośrednictwem osiem znaków od końca następnego wiersza, wartość zwracana wynosi 10. Oznacza to trzech znaków w pierwszym wierszu i siedem na następnej.

Aby uzyskać więcej informacji o typie danych TCHAR, zobacz wiersz TCHAR w tabeli w [typy danych Windows](/windows/desktop/WinProg/windows-data-types).

### <a name="remarks"></a>Uwagi

Ta metoda jest obsługiwana przez [EM_LINELENGTH](/windows/desktop/Controls/em-linelength) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineIndex](#lineindex).

##  <a name="linescroll"></a>  CEdit::LineScroll

Wywołaj tę funkcję, aby przewijać tekstu wielowierszowego edycji.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nLines*<br/>
Określa liczbę wierszy, aby przewijać w pionie.

*nChars*<br/>
Określa numer pozycji znaku do być przewijane w poziomie. Ta wartość jest ignorowana, jeśli kontrolka edycji zawiera ES_RIGHT albo ES_CENTER stylu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest przetwarzany tylko przez formantów edycji wielu linii.

Kontrolka edycji nie w pionie przewiń ekran za ostatni wiersz tekstu w kontrolce edycji. Jeśli bieżący wiersz oraz liczbę wierszy, określony przez *nLines* przekracza łączna liczba wierszy w formancie edycji, wartość jest korygowana, więc, że ostatni wiersz kontrolki edycji jest przewijane do góry okna kontrolki edycji.

`LineScroll` można przewijać w poziomie poza ostatnim znakiem każdego wiersza.

Aby uzyskać więcej informacji, zobacz [EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

##  <a name="paste"></a>  CEdit::Paste

Wywołaj tę funkcję, aby wstawić dane ze Schowka do `CEdit` w punkcie wstawiania.

```
void Paste();
```

### <a name="remarks"></a>Uwagi

Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.

Aby uzyskać więcej informacji, zobacz [WM_PASTE](/windows/desktop/dataxchg/wm-paste) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

Wywołaj tę funkcję, aby uzyskać pozycji (w lewym górnym rogu) danego znaku w ramach tej `CEdit` obiektu.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Liczony od zera indeks określonego znaku.

### <a name="return-value"></a>Wartość zwracana

Współrzędne w lewym górnym rogu znak określony przez *nChar*.

### <a name="remarks"></a>Uwagi

Znak jest określona, zapewniając jej wartość indeksu zaczynającego się od zera. Jeśli *nChar* jest większa niż indeks ostatniego znaku w tym `CEdit` obiekt, wartość zwracana określa współrzędne pozycji znaku tylko poza ostatnim znakiem w tym `CEdit` obiektu.

> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineFromChar](#linefromchar).

##  <a name="replacesel"></a>  CEdit::ReplaceSel

Wywołaj tę funkcję, aby zastąpić bieżące zaznaczenie w formancie edycji tekstu określonego przez *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText*<br/>
Wskazuje ciąg zakończony wartością null zawierający tekst zastępujący.

*bCanUndo*<br/>
Aby określić, że ta funkcja może być cofnięte, należy ustawić wartość tego parametru na wartość TRUE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

Zastępuje tylko część tekstu w kontrolce edycji. Jeśli chcesz zamienić cały tekst, użyj [CWnd::SetWindowText](cwnd-class.md#setwindowtext) funkcja elementu członkowskiego.

Jeśli nie ma bieżącego zaznaczenia, tekst zastępczy jest wstawiany w bieżącej lokalizacji kursora.

Aby uzyskać więcej informacji, zobacz [EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::LineIndex](#lineindex).

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

Ustawia tekst, który jest wyświetlany jako podpowiedź tekstowa lub Porada, w trakcie edycji kontroli, gdy kontrolka jest pusty.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[in] Wskaźnik na ciąg, który zawiera wskaźnik do wyświetlenia w kontrolce edycji.

*fDrawWhenFocused*<br/>
[in] W przypadku wartości FAŁSZ transparent wskaźnika nie jest narysowany, gdy użytkownik kliknie w formancie edycji i przenosi fokus na formant.

W przypadku opcji TRUE transparent wskaźnika jest rysowana nawet wtedy, gdy kontrolka jest ustawiony fokus. Transparent sygnalizacji znika, gdy użytkownik rozpoczyna się do typu w kontrolce.

Wartość domyślna to FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner) komunikat, który jest opisany w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) makra.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano [CEdit::SetCueBanner](#setcuebanner) metody.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

Wywołaj tę funkcję, aby ustawić dojście do pamięci lokalnej, używany przez kontrolkę edycji wielu linii.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hBuffer*<br/>
Zawiera dojście do pamięci lokalnej. Tego dojścia musi być utworzony przez poprzednie wywołanie [Funkcja LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) funkcji Windows przy użyciu flagi LMEM_MOVEABLE. Pamięć zakłada się, że zawierają ciąg zakończony znakiem null. Jeśli nie jest to możliwe, pierwszy bajt ilość przydzielonej pamięci powinna być równa 0.

### <a name="remarks"></a>Uwagi

Kontrolki edycji następnie użyje tego buforu do przechowywania tekstu w aktualnie wyświetlany, zamiast przydzielać swój własny buforu.

Ta funkcja członkowska jest przetwarzany tylko przez formantów edycji wielu linii.

Zanim aplikacja ustawia nowy uchwyt pamięci, należy używać [gethandle —](#gethandle) funkcja elementu członkowskiego, aby uzyskać dojście do bieżącego bufora pamięci i wolnego, przy użyciu pamięci `LocalFree` funkcji Windows.

`SetHandle` Czyści bufor cofania ( [CanUndo](#canundo) następnie funkcja elementu członkowskiego zwraca 0) oraz flagę modyfikacji wewnętrznego ( [GetModify](#getmodify) następnie funkcja elementu członkowskiego zwraca 0). Jest ponownie rysowany okna kontrolki edycji.

W oknie dialogowym można użyć tej funkcji elementu członkowskiego w formancie edycji wielu linii, tylko wtedy, gdy okno dialogowe zostały utworzone z ustawioną flagą styl DS_LOCALEDIT.

> [!NOTE]
> `GetHandle` nie będzie działać z Windows 95/98. Jeśli wywołasz `GetHandle` w Windows 95/98, to zostanie zwrócona wartość NULL. `GetHandle` będzie działać zgodnie z opisem w obszarze Windows NT w wersji 3.51 lub nowszej.

Aby uzyskać więcej informacji, zobacz [EM_SETHANDLE](/windows/desktop/Controls/em-sethandle), [Funkcja LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), i [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

Najważniejsze funkcje zakres tekstu wyświetlanego w bieżącym formant edycji.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ichStart*|[in] Liczony od zera indeks pierwszego wystąpienia znaku w zakresie tekstu, aby wyróżnić.|
|*ichEnd*|[in] Liczony od zera indeks ostatniego znaku w zakresie tekstu, aby wyróżnić.|

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) komunikat, który jest opisany w zestawie Windows SDK.  Ta metoda wysyła [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) komunikat, który jest opisany w zestawie Windows SDK. Zarówno `SetHighlight` i `GetHighlight` są włączone, UNICODE kompilacji tylko.

##  <a name="setlimittext"></a>  CEdit::SetLimitText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić limit tekstu, w tym `CEdit` obiektu.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*nMax*<br/>
Nowy limit tekstu, w znakach.

### <a name="remarks"></a>Uwagi

Limit tekstu jest maksymalną ilość tekstu w postaci, w jakie może akceptować kontrolki edycji.

Zmiana tego limitu tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma ona wpływu na dowolny tekst już w formancie edycji ani nie ogranicza długość tekstu skopiowane do kontrolki edycji przez [SetWindowText](cwnd-class.md#setwindowtext) funkcji składowej we `CWnd`. Jeśli aplikacja używa `SetWindowText` funkcję, aby umieścić więcej tekstu w formancie edycji niż określona w wywołaniu `LimitText`, użytkownik może usunąć dowolny tekst w kontrolce edycji. Jednak limit tekstu uniemożliwi zastępując istniejący tekst nowym tekstem użytkownika, chyba że usuwanie bieżące zaznaczenie powoduje, że tekst nie przekraczają limit tekstu.

Ta funkcja zastępuje [LimitText](#limittext) w systemie Win32.

Aby uzyskać więcej informacji, zobacz [EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmargins"></a>  CEdit::SetMargins

Wywołaj tę metodę, aby ustawić marginesy lewy i prawy tej kontrolki edycji.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nLeft*<br/>
Szerokość nowe lewy margines w pikselach.

*nRight*<br/>
Szerokość nowe prawy margines, w pikselach.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.

Aby uzyskać więcej informacji, zobacz [EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmodify"></a>  CEdit::SetModify

Wywołaj tę funkcję, aby ustawić lub wyczyścić flagę zmodyfikowanej kontrolki edycji.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Wartość TRUE wskazuje, że tekst został zmodyfikowany, a wartość FALSE wskazuje, że zostały zmodyfikowane. Domyślnie zmodyfikowane flaga jest ustawiona.

### <a name="remarks"></a>Uwagi

Zmodyfikowane flaga wskazuje, czy tekst w kontrolce edycji został zmodyfikowany. Ta opcja jest automatycznie ustawiana zawsze wtedy, gdy użytkownik zmieni tekst. Wartość może być pobierany za pomocą [GetModify](#getmodify) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetModify](#getmodify).

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

Wywołaj tę funkcję, aby ustawić lub usunąć znaku hasła, wyświetlana w formancie edycji, gdy użytkownik wpisze tekst.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Określa znak, które mają być wyświetlane zamiast znaku wpisana przez użytkownika. Jeśli *ch* wynosi 0, wyświetlane są rzeczywiste znaki wpisane przez użytkownika.

### <a name="remarks"></a>Uwagi

Gdy znaku hasła jest ustawiona, ten znak jest wyświetlany dla każdego znaku typy użytkownika.

Ta funkcja elementu członkowskiego nie ma wpływu na wielu linii formant edycji.

Gdy `SetPasswordChar` funkcja członkowska jest wywoływana, `CEdit` narysuje wszystkie znaki widoczne, korzystając ze znaku określonej przez *ch*.

Jeśli kontrolka edycji została utworzona za pomocą [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) styl domyślny znak hasła jest ustawiona na znak gwiazdki ( <strong>\*</strong>). Ten styl jest usuwany, jeśli `SetPasswordChar` jest wywoływana z *ch* ustawione na 0.

Aby uzyskać więcej informacji, zobacz [EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

Wywołuje tę funkcję, aby ustawić stan tylko do odczytu formant edycji.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bReadOnly*<br/>
Określa, czy należy ustawić lub usunąć tylko do odczytu stan kontrolki edycji. Wartość TRUE, ustawia stan tylko do odczytu; wartość FALSE, ustawia stan odczytu/zapisu.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli operacja się powiedzie, lub 0, jeśli błąd wystąpi.

### <a name="remarks"></a>Uwagi

Bieżące ustawienie można znaleźć, testując [ES_READONLY](styles-used-by-mfc.md#edit-styles) Flaga wartość zwracaną przez [CWnd::GetStyle](cwnd-class.md#getstyle).

Aby uzyskać więcej informacji, zobacz [EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

Wywołaj tę funkcję, aby ustawić wymiary prostokąta przy użyciu określonych współrzędnych.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który określa nowe wymiary prostokąta formatowania.

### <a name="remarks"></a>Uwagi

Ten element członkowski jest przetwarzany tylko przez formantów edycji wielu linii.

Użyj `SetRect` ustawienia formatowania formant edycji Prostokąt wielu linii. Prostokąt formatowania jest ograniczającą prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji. Podczas tworzenia kontrolki edycji Prostokąt formatowania jest taka sama jak obszaru klienckiego okna kontrolki edycji. Za pomocą `SetRect` funkcja elementu członkowskiego aplikacji ułatwia formatowania prostokąt większy lub mniejszy od okna kontrolki edycji.

Jeśli kontrolka edycji nie ma paska przewijania, tekst zostaną przycięte, nie zawinięty, jeśli prostokąt formatowania jest większe niż okno. Jeśli kontrolka edycji zawiera obramowanie, formatowania prostokąt została zmniejszona o rozmiar obramowania. Jeśli dostosowano prostokątowi zwróconemu przez `GetRect` funkcja elementu członkowskiego, należy usunąć rozmiar obramowania Zanim przekażesz prostokąt `SetRect`.

Gdy `SetRect` nosi kontrolki edycji tekstu jest również ponownie sformatowany i wyświetlane ponownie.

Aby uzyskać więcej informacji, zobacz [EM_SETRECT](/windows/desktop/Controls/em-setrect) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

Wywołaj tę funkcję, aby ustawić formatowania prostokąt kontrolkę edycji wielu linii.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje `RECT` struktury lub `CRect` obiekt, który określa nowe wymiary prostokąta.

### <a name="remarks"></a>Uwagi

Prostokąt formatowania jest ograniczającą prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji.

`SetRectNP` jest taka sama jak `SetRect` funkcję członkowską, z tą różnicą, że okna kontrolki edycji nie jest narysowany ponownie.

Podczas tworzenia kontrolki edycji Prostokąt formatowania jest taka sama jak obszaru klienckiego okna kontrolki edycji. Przez wywołanie metody `SetRectNP` funkcja elementu członkowskiego aplikacji ułatwia formatowania prostokąt większy lub mniejszy od okna kontrolki edycji.

Jeśli kontrolka edycji nie ma paska przewijania, tekst zostaną przycięte, nie zawinięty, jeśli prostokąt formatowania jest większe niż okno.

Ten element członkowski jest przetwarzany tylko przez formantów edycji wielu linii.

Aby uzyskać więcej informacji, zobacz [EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::SetRect](#setrect).

##  <a name="setsel"></a>  CEdit::SetSel

Wywołaj tę funkcję, aby wybrać zakres znaków w kontrolce edycji.

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

*dwSelection*<br/>
Określa pozycję początkową w programie word niskiego rzędu i pozycji końcowej w programie word wyższego rzędu. Jeśli wyraz niskiego rzędu wynosi 0 i word wyższego rzędu jest wartość -1, zostanie wybrany cały tekst w kontrolce edycji. Jeśli wyraz niskiego rzędu jest wartość -1, zostaną usunięte wszystkie bieżące zaznaczenie.

*bNoScroll*<br/>
Wskazuje, czy powinien być przewijane karetkę do widoku. W przypadku wartości FAŁSZ karetkę jest przewijane do widoku. W przypadku opcji TRUE karetkę nie jest przewijane do widoku.

*nStartChar*<br/>
Określa położenie początkowe. Jeśli *nStartChar* wynosi 0 i *nEndChar* wynosi -1, wszystkie zaznaczono tekstu w kontrolce edycji. Jeśli *nStartChar* wynosi -1, wszystkie bieżące zaznaczenie jest usunięte.

*nEndChar*<br/>
Określa pozycję końcową.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [EM_SETSEL](/windows/desktop/Controls/em-setsel) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEdit::GetSel](#getsel).

##  <a name="settabstops"></a>  CEdit::SetTabStops

Wywołaj tę funkcję, aby ustawienie pozycji tabulatorów w formancie edycji wielu linii.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Określa, czy można ustawić na pozycji tabulatorów co *cxEachStop* jednostki okna dialogowego.

*nTabStops*<br/>
Określa liczbę pozycji tabulatorów zawarte w *rgTabStops*. Ta liczba musi być większa niż 1.

*rgTabStops*<br/>
Wskazuje tablicy liczb całkowitych bez znaku, określając karcie zatrzymuje się w jednostkach okna dialogowego. Do okna dialogowego jest odległość pozioma lub pionowa. Jedna jednostka w poziomie okna dialogowego równą jednej czwartej bieżącej jednostki podstawowej szerokość okna dialogowego i 1 jednostka pionowy okno dialogowe jest równa jednej ósmej bieżącej jednostki podstawowej wysokość okna dialogowego. Okno dialogowe stanowiącej są obliczane na podstawie wysokość i szerokość bieżącej czcionki systemowej. `GetDialogBaseUnits` Windows funkcja zwraca bieżące okno dialogowe stanowiącej w pikselach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ustawiono kart; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli tekst jest kopiowany do kontrolki edycji wielu linii, wszelkie znak tabulacji w tekście spowoduje, że miejsce do wygenerowania do następnej pozycji tabulatora.

Aby ustawić domyślny rozmiar jednostki okna dialogowego 32 tabulatorów, wywołać bez parametrów wersja tej funkcji elementu członkowskiego. Aby ustawienie pozycji tabulatorów rozmiar niż 32, należy wywołać wersja, która *cxEachStop* parametru. Aby ustawienie pozycji tabulatorów do tablicy o rozmiarach, należy użyć wersji z dwoma parametrami.

Ta funkcja członkowska jest przetwarzany tylko przez formanty edycji wielu linii.

`SetTabStops` nie automatycznie ponownie narysować okno edycji. Jeśli zmienisz tabulatory tekst już w kontrolce edycji, wywołaj [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) ponowne okno edycji.

Aby uzyskać więcej informacji, zobacz [EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops) i [GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CEditView::SetTabStops](ceditview-class.md#settabstops).

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

Wyświetla dymku, który jest skojarzony z bieżącym kontrolki edycji.

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
|*pEditBalloonTip*|[in] Wskaźnik do [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) strukturę, która opisuje Porada dymek.|
|*lpszTitle*|[in] Wskaźnik na ciąg Unicode, który zawiera tytuł Porada dymek.|
|*lpszText*|[in] Wskaźnik do ciągu Unicode, który zawiera tekst porady dymek.|
|*ttiIcon*|[in] **INT** określająca typ ikonę, aby skojarzyć z końcówką dymek. Wartość domyślna to TTI_NONE. Aby uzyskać więcej informacji, zobacz `ttiIcon` członkiem [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) struktury.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja wysyła [EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip) komunikat, który jest opisany w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip) makra.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną `m_cedit`, to znaczy umożliwiają dostęp do bieżącego kontrolki edycji. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wyświetla dymku dla kontrolki edycji. [CEdit::ShowBalloonTip](#showballoontip) metody Określa tekst porady tytuł i dymek.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

Wywołaj tę funkcję, aby cofnąć ostatnią operację kontrolki edycji.

```
BOOL Undo();
```

### <a name="return-value"></a>Wartość zwracana

Kontrolki edycji jednowierszowego wartość zwracana jest zawsze wartość różną od zera. Kontrolki edycji wielu linii, wartość zwracana jest wartość różną od zera, jeśli operacja cofania zakończy się pomyślnie, lub 0, jeśli operacja cofania nie powiedzie się.

### <a name="remarks"></a>Uwagi

Można także cofnąć operację cofnięcia. Na przykład, można przywrócić usunięty tekst z pierwszym wywołaniu `Undo`. Tak długo, jak długo ma nie pośredniczące operacji edycji, możesz usunąć tekst między znakami dwóch ponownie drugie wywołanie `Undo`.

Aby uzyskać więcej informacji, zobacz [EM_UNDO](/windows/desktop/Controls/em-undo) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CMNCTRL2 próbki MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](cwnd-class.md)<br/>
[Klasa CButton](cbutton-class.md)<br/>
[Klasa CComboBox](ccombobox-class.md)<br/>
[Klasa CListBox](clistbox-class.md)<br/>
[Klasa CScrollBar](cscrollbar-class.md)<br/>
[Klasa CStatic](cstatic-class.md)<br/>
[Klasa CDialog](cdialog-class.md)
