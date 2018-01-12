---
title: Klasa CEdit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4418f20b267218b761dd6637762df1b420e9ac6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|[CEdit::CEdit](#cedit)|Konstruuje `CEdit` obiektu formantu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEdit::CanUndo](#canundo)|Określa, czy operacja formancie edycyjnym można cofnąć.|  
|[CEdit::CharFromPos](#charfrompos)|Pobiera indeksów wiersza i znaku najbardziej zbliżony do określonej pozycji znaku.|  
|[CEdit::Clear](#clear)|Usuwa (czyści) kontrolować bieżące zaznaczenie (jeśli istnieje) w edycji.|  
|[CEdit::Copy](#copy)|Kopiuje bieżące zaznaczenie (jeśli istnieją) w formancie edycyjnym do Schowka w **CF_TEXT** format.|  
|[CEdit::Create](#create)|Tworzy kontrolkę edycji systemu Windows i dołącza go do `CEdit` obiektu.|  
|[CEdit::Cut](#cut)|Kontrolowanie bieżące zaznaczenie (jeśli istnieje) w edycji usuwa (części) i kopiuje usunięty tekst do Schowka w **CF_TEXT** format.|  
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Resetuje formantu (czyści) Flaga Cofnij edycję.|  
|[CEdit::FmtLines](#fmtlines)|Ustawia lub wyłącz włączenia znaków nietrwałego podział wiersza w formancie edycji wielu linii.|  
|[CEdit::GetCueBanner](#getcuebanner)|Pobiera tekst, który jest wyświetlana jako tekst wskaźnika lub porada w kontrolce edycji, gdy formant jest pusty i nie ma fokusa.|  
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Określa znajdujące się najwyżej wiersza widocznego w kontrolce edycji.|  
|[CEdit::GetHandle](#gethandle)|Pobiera dojścia do pamięci przydzielonej aktualnie do wielu linii edycji.|  
|[CEdit::GetHighlight](#gethighlight)|Pobiera indeksów początkowe i końcowe znaki w zakresie tekstu, który zostanie wyróżniona w bieżącym kontrolki edycji.|  
|[CEdit::GetLimitText](#getlimittext)|Pobiera maksymalną ilość tekstu, to `CEdit` może zawierać.|  
|[CEdit::GetLine](#getline)|Pobiera wiersza tekstu z formantu edycyjnego.|  
|[CEdit::GetLineCount](#getlinecount)|Pobiera liczbę wierszy w formancie edycji wielu linii.|  
|[CEdit::GetMargins](#getmargins)|Pobiera lewego i prawego marginesu dla `CEdit`.|  
|[CEdit::GetModify](#getmodify)|Określa, czy zawartość formantu edycyjnego zostały zmodyfikowane.|  
|[CEdit::GetPasswordChar](#getpasswordchar)|Pobiera znak hasła wyświetlany w formancie edycji, gdy użytkownik wprowadzi tekst.|  
|[CEdit::GetRect](#getrect)|Pobiera prostokąt formatowania formantu edycyjnego.|  
|[CEdit::GetSel](#getsel)|Pobiera pierwszy i ostatni znak położenia bieżące zaznaczenie w formancie edycyjnym.|  
|[CEdit::HideBalloonTip](#hideballoontip)|Ukrywa dowolnym dymku skojarzone z bieżącym kontrolki edycji.|  
|[CEdit::LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić do formantu edycyjnego.|  
|[CEdit::LineFromChar](#linefromchar)|Pobiera numer wiersza, który zawiera indeks określony znak.|  
|[CEdit::LineIndex](#lineindex)|Pobiera indeks znaków wiersza w formancie edycji wielu linii.|  
|[CEdit::LineLength](#linelength)|Pobiera długość wiersza w kontrolce edycji.|  
|[CEdit::LineScroll](#linescroll)|Przewija tekst formantu edycji wielu linii.|  
|[CEdit::Paste](#paste)|Wstawia danych ze Schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w **CF_TEXT** format.|  
|[CEdit::PosFromChar](#posfromchar)|Pobiera współrzędne górnego lewego rogu indeksu określony znak.|  
|[CEdit::ReplaceSel](#replacesel)|Zamienia bieżące zaznaczenie w formancie edycji określony tekst.|  
|[CEdit::SetCueBanner](#setcuebanner)|Ustawia tekst, który jest wyświetlany jako tekst wskaźnika lub porada w kontrolce edycji, gdy formant jest pusty i nie ma fokusa.|  
|[CEdit::SetHandle](#sethandle)|Ustawia dojście do pamięci lokalnej, który będzie używany przez formant edycji wielu linii.|  
|[CEdit::SetHighlight](#sethighlight)|Najważniejsze funkcje zakres tekstu, który jest wyświetlany w bieżącej edycji.|  
|[CEdit::SetLimitText](#setlimittext)|Ustawia maksymalną ilość tekstu, to `CEdit` może zawierać.|  
|[CEdit::SetMargins](#setmargins)|Ustawia lewego i prawego marginesu dla tego `CEdit`.|  
|[CEdit::SetModify](#setmodify)|Ustawia lub usuwa flagę modyfikacji kontrolki edycji.|  
|[CEdit::SetPasswordChar](#setpasswordchar)|Ustawia lub usuwa hasło znak wyświetlany w formancie edycji, gdy użytkownik wprowadzi tekst.|  
|[CEdit::SetReadOnly](#setreadonly)|Ustawia stan tylko do odczytu kontrolki edycji.|  
|[CEdit::SetRect](#setrect)|Ustawia prostokąt formatowania formantu edycji wielu linii i aktualizuje formantu.|  
|[CEdit::SetRectNP](#setrectnp)|Ustawia prostokąt formatowania formantu edycji Wielowierszowe bez ponownego narysowania okna formantu.|  
|[CEdit::SetSel](#setsel)|Wybiera zakres znaków w formancie edycyjnym.|  
|[CEdit::SetTabStops](#settabstops)|Formant edycji zestawów tabulatorów w wielu wierszach.|  
|[CEdit::ShowBalloonTip](#showballoontip)|Wyświetla etykieta dymka skojarzony z bieżącym kontrolki edycji.|  
|[CEdit::Undo](#undo)|Cofa ostatnią operację kontrolki edycji.|  
  
## <a name="remarks"></a>Uwagi  
 Formant edycji jest oknem podrzędnym prostokątne, w którym użytkownik może wprowadzić tekst.  
  
 Formant edycji można utworzyć szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CEdit` do skonstruowania `CEdit` obiekt, a następnie wywołaj [Utwórz](#create) funkcji członkowskiej można utworzyć okna formantu edycyjnego i dołączenie go do `CEdit` obiektu.  
  
 Konstrukcja może być jednoetapowy proces w klasie pochodnej z `CEdit`. Zapisywanie konstruktora klasy pochodnej i wywołanie **Utwórz** z wewnątrz konstruktora.  
  
 `CEdit`Najważniejsze funkcje z dziedziczy `CWnd`. Do ustawiania i pobierania tekstu z `CEdit` obiektów, użyj `CWnd` funkcje Członkowskie [SetWindowText](cwnd-class.md#setwindowtext) i [GetWindowText](cwnd-class.md#getwindowtext), które set lub get kontrolować całą zawartość edycji, nawet jeśli jego jest wielowierszowe kontrolki. Wiersze tekstu w wielowierszowym formancie są rozdzielone przez sekwencje znaków "\r\n". Ponadto w przypadku wielowierszowe kontrolki edycji get i set część tekstu formantu przez wywołanie metody `CEdit` funkcje Członkowskie [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)i [ ReplaceSel](#replacesel).  
  
 Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows, wysyłany przez kontrolkę edycji do elementu nadrzędnego (zazwyczaj klasą pochodną `CDialog`), Dodaj funkcji członkowskiej wpisu i program obsługi komunikatów map wiadomości do klasy nadrzędnej dla każdego komunikatu.  
  
 Każdy wpis mapy komunikatów ma następującą postać:  
  
 **ON_**powiadomień **(** *identyfikator, memberFxn***)**  
  
 gdzie `id` Określa identyfikator okna podrzędnego kontrolki edycji wysyłania powiadomienia, oraz `memberFxn` jest nazwą funkcji członkowskiej nadrzędnego zostały zapisane do obsługi powiadomień.  
  
 Prototyp funkcji elementu nadrzędnego, jak wygląda następująco:  
  
 **afx_msg** void memberFxn **();**  
  
 Poniżej przedstawiono listę potencjalnych wpisów map wiadomości i opis przypadków, w których będą przesyłane do obiektu nadrzędnego:  
  
- **On_en_change —** użytkownik ma podjąć akcję, która może zmienić tekst w kontrolce edycji. W odróżnieniu od **EN_UPDATE** komunikat powiadomienia, to powiadomienie jest wysyłane po wyświetlanie aktualizacji systemu Windows.  
  
- **On_en_errspace —** formant edycyjny nie może przydzielić wystarczającej ilości pamięci do spełnienia określonego żądania.  
  
- **On_en_hscroll —** kliknięciu formantu edycyjnego poziomy pasek przewijania. Okno nadrzędne jest powiadamiany o przed zaktualizowaniem ekranu.  
  
- **On_en_killfocus —** formant edycyjny traci fokus wprowadzania.  
  
- **On_en_maxtext —** bieżącego wstawiania przekroczył określoną liczbę znaków dla kontrolki edycji i dlatego została obcięta. Również wysyłany, gdy formant edycyjny nie ma **es_autohscroll —** styl i liczbę znaków, które ma zostać wstawiony przekroczyłby szerokość kontrolki edycji. Również wysyłany, gdy formant edycyjny nie ma **es_autovscroll —** styl i całkowita liczba wierszy, wynikające z Wstawianie tekstu spowoduje przekroczenie wysokość formantu edycyjnego.  
  
- **On_en_setfocus —** wysyłany, gdy formant edycyjny zyska fokus wprowadzania.  
  
- **On_en_update —** ma wyświetli zmieniony tekst formantu edycyjnego. Wysyłane po formantu ma sformatowanego tekstu, ale przed jego ekrany tekst, dzięki czemu może się zmienić rozmiar okna, jeśli to konieczne.  
  
- **On_en_vscroll —** użytkownik klika formant edycyjny pionowy pasek przewijania. Okno nadrzędne jest powiadamiany o przed zaktualizowaniem ekranu.  
  
 W przypadku utworzenia `CEdit` obiektu w oknie dialogowym, `CEdit` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CEdit` obiektu z zasobu okna dialogowego za pomocą edytora okien dialogowych `CEdit` obiekt zostanie zniszczony automatycznie, gdy użytkownik zamyka okno dialogowe.  
  
 W przypadku utworzenia `CEdit` obiektów w ramach okna, może być również konieczne zniszczenia. W przypadku utworzenia `CEdit` obiektów na stosie, zostanie zniszczony automatycznie. W przypadku utworzenia `CEdit` obiektów na stercie przy użyciu **nowe** funkcji, należy wywołać **usunąć** formant edycji w obiekcie zniszczyć ją, gdy użytkownik kończy systemu Windows. Jeśli Przydziel wszystkie pamięci w `CEdit` obiektów, Zastąp `CEdit` destruktora zlikwidować alokacje.  
  
 Aby zmodyfikować niektórych style w formancie edycyjnym (takich jak **es_readonly —**), musisz wysłać określone komunikaty do formantu zamiast [ModifyStyle](cwnd-class.md#modifystyle). Zobacz [style formantu edycji](http://msdn.microsoft.com/library/windows/desktop/bb775464) w systemie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat funkcji `CEdit`, zobacz:  
  
- [Kontrolki](../../mfc/controls-mfc.md)  
  
-   Artykuł bazy wiedzy Q259949: informacje o: SetCaretPos() jest nieodpowiedni z CEdit lub kontrolki CRichEditCtrl  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](cobject-class.md)  
  
 [CCmdTarget —](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CEdit`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="canundo"></a>CEdit::CanUndo  
 Wywołanie tej funkcji w celu ustalenia, czy ostatniej operacji edycji można cofnąć.  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ostatnia operacja edycji można cofnąć przez wywołanie do **Cofnij** funkcja członkowska; 0, jeśli nie można cofnąć.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::Undo](#undo).  
  
##  <a name="cedit"></a>CEdit::CEdit  
 Konstruuje `CEdit` obiektu.  
  
```  
CEdit();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [Utwórz](#create) do skonstruowania formant edycji systemu Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]  
  
##  <a name="charfrompos"></a>CEdit::CharFromPos  
 Wywołanie tej funkcji można pobrać wiersz liczony od zera i indeksów znak znaku najbliższy punkt określonego w tym `CEdit` formantu  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Współrzędne punktu w obszarze klienckim tego `CEdit` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks znaków w znaczącymi bitami **WORD**, a indeks wierszy w kolejności wysokiej **WORD**.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]  
  
##  <a name="clear"></a>CEdit::Clear  
 Wywołanie tej funkcji do usunięcia (Usuń) bieżącym zaznaczeniu (jeśli istnieją) w formancie edycyjnym.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Usunięcie wykonywane przez **wyczyść** mogą zostać cofnięte przez wywołanie metody [Cofnij](#undo) funkcję elementu członkowskiego.  
  
 Aby usunąć bieżące zaznaczenie i umieść usunięto zawartość w Schowku, należy wywołać [Wytnij](#cut) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]  
  
##  <a name="copy"></a>CEdit::Copy  
 Wywołanie tej funkcji do coy bieżącym zaznaczeniu (jeśli istnieją) w formancie edycyjnym do Schowka w **CF_TEXT** format.  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]  
  
##  <a name="create"></a>CEdit::Create  
 Tworzy kontrolkę edycji systemu Windows i dołącza go do `CEdit` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu edycyjnego. Zastosuj dowolną kombinację [style edycji](edit-styles.md) do formantu.  
  
 `rect`  
 Określa rozmiar i położenie kontrolki edycji. Może być `CRect` obiektu lub `RECT` struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki edycji (zazwyczaj `CDialog`). Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator kontrolki edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CEdit` obiektu w dwóch krokach. Najpierw należy wywołać `CEdit` , a następnie wywołania konstruktora **Utwórz**, która tworzy kontrolkę edycji systemu Windows i dołącza go do `CEdit` obiektu.  
  
 Gdy **Utwórz** wykonuje system Windows wysyła [WM_NCCREATE](http://msdn.microsoft.com/library/windows/desktop/ms632635), [WM_NCCALCSIZE](http://msdn.microsoft.com/library/windows/desktop/ms632634), [WM_CREATE](http://msdn.microsoft.com/library/windows/desktop/ms632619), i [WM_ GETMINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632626) wiadomości do kontrolki edycji.  
  
 Komunikaty te są obsługiwane przez domyślnie [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), i [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) funkcje Członkowskie w `CWnd` klasy podstawowej. Aby rozszerzyć domyślnej obsługi wiadomości, klasa wyprowadzona z `CEdit`, Dodaj mapowanie komunikatów do nowej klasy i zastąpienie powyżej funkcje Członkowskie obsługi wiadomości. Zastąpienie `OnCreate`, na przykład, aby wykonać wymagane inicjowania dla nowej klasy.  
  
 Zastosuj następujące [Style okna](window-styles.md) do kontrolki edycji.  
  
- **Ws_child —** zawsze  
  
- **Ws_visible —** zwykle  
  
- **Ws_disabled —** rzadko  
  
- **Ws_group —** na grupowanie formantów  
  
- **Ws_tabstop —** do uwzględnienia kontrolki edycji w kolejności tabulacji  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]  
  
##  <a name="cut"></a>CEdit::Cut  
 Wywołanie tej funkcji do usunięcia (obcięty) w bieżącym zaznaczeniu (jeśli istnieją) w formancie edycyjnym i skopiuj usunięty tekst do Schowka w **CF_TEXT** format.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Uwagi  
 Usunięcie wykonywane przez **Wytnij** mogą zostać cofnięte przez wywołanie metody [Cofnij](#undo) funkcję elementu członkowskiego.  
  
 Aby usunąć bieżące zaznaczenie bez wprowadzania usunięty tekst do Schowka, wywołaj [wyczyść](#clear) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]  
  
##  <a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer  
 Wywołanie tej funkcji, aby zresetować (Wyczyść) Flaga cofania kontrolki edycji.  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>Uwagi  
 Kontrolka edycji będzie teraz nie można cofnąć ostatniej operacji. Zawsze, gdy operacja w formancie edycyjnym można cofnąć została ustawiona flaga cofania.  
  
 Flaga cofania jest automatycznie czyszczone po każdej zmianie [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) lub [SetHandle](#sethandle) `CWnd` są nazywane funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]  
  
##  <a name="fmtlines"></a>CEdit::FmtLines  
 Wywołanie tej funkcji można ustawić lub wyłącz włączenia znaków nietrwałego podział wiersza w formancie edycji wielu linii.  
  
```  
BOOL FmtLines(BOOL bAddEOL);
```  
  
### <a name="parameters"></a>Parametry  
 *bAddEOL*  
 Określa, czy znaki nietrwałego podziału wiersza są do wstawienia. Wartość **TRUE** wstawia znaków; wartość **FALSE** usuwa je.  
  
### <a name="return-value"></a>Wartość zwracana  
 Formatowanie występuje wartość niezerową, jeśli występuje; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Podział wiersza nietrwałego składa się z dwóch karetki i wysuwu wiersza wstawione na końcu wiersza, który został przerwany z powodu zawijania wyrazów. Podział wiersza składa się z jednego powrotu karetki i wysuwu wiersza. Nie dotyczy wierszy, które kończyć podział wiersza `FmtLines`.  
  
 System Windows będzie odpowiadać tylko, jeśli `CEdit` obiekt jest w formancie edycji wielu linii.  
  
 `FmtLines`dotyczy tylko buforu zwrócony przez [GetHandle](#gethandle) i tekst zwracany przez [WM_GETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632627). Nie ma to wpływu na wyświetlanie tekstu w formancie edycyjnym.  
  
 Aby uzyskać więcej informacji, zobacz [EM_FMTLINES](http://msdn.microsoft.com/library/windows/desktop/bb761570) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]  
  
##  <a name="getcuebanner"></a>CEdit::GetCueBanner  
 Pobiera tekst, który jest wyświetlana jako tekst wskaźnika lub porada w kontrolce edycji, gdy formant jest pusty.  
  
```  
BOOL GetCueBanner(
    LPWSTR lpszText,  
    int cchText) const;  
  
CString GetCueBanner() const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`lpszText`  
 Wskaźnik do ciąg, który zawiera tekst wskaźnika.  
  
 [in]`cchText`  
 Liczba znaków, które mogą być odbierane. Liczba ta obejmuje Kończenie `NULL` znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla pierwszego przeciążenia `true` przypadku powodzenia; w przeciwnym razie metody `false`.  
  
 Dla drugiego przeciążenia [cstring —](../../atl-mfc-shared/using-cstring.md) zawierający tekst wskaźnika, jeśli metoda przebiegło pomyślnie; w przeciwnym razie wartość pustego ciągu ("").  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [EM_GETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761572) komunikat, który jest opisany w zestawie SDK systemu Windows. Aby uzyskać więcej informacji, zobacz [Edit_GetCueBannerText](http://msdn.microsoft.com/library/windows/desktop/bb761695) makra.  
  
##  <a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine  
 Wywołanie tej funkcji, aby ustalić linię widoczne znajdujące się najwyżej w formancie edycji.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks wiersza widocznego najwyższego poziomu. Dla formantów edycyjnych jeden wiersz zwracana wartość to 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]  
  
##  <a name="gethandle"></a>CEdit::GetHandle  
 Wywołanie tej funkcji można pobrać dojścia do pamięci przydzielonego dla formantu edycji wielu linii.  
  
```  
HLOCAL GetHandle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście pamięci lokalnej identyfikujący buforu zawierający zawartość kontrolki edycji. Jeśli wystąpi błąd, takie jak wysyłanie komunikatu do formantu edycji jeden wiersz, zwracana wartość to 0.  
  
### <a name="remarks"></a>Uwagi  
 Dojście jest uchwytu pamięci lokalnej i mogą być używane przez jedną z **lokalnego** obsługi funkcji pamięci systemu Windows, które przyjmują pamięci lokalnej jako parametr.  
  
 **GetHandle** jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Wywołanie **GetHandle** kontrolki edycji wielu linii w oknie dialogowym tylko wtedy, gdy okno dialogowe utworzono za pomocą **DS_LOCALEDIT** styl ustawioną flagą. Jeśli **DS_LOCALEDIT** stylu nie jest ustawiona, będą nadal otrzymywać niezerowe wartości zwracanej, ale nie będzie mógł używać zwracanej wartości.  
  
> [!NOTE]
> **GetHandle** nie działa w systemie Windows 95/98. Jeśli należy wywołać **GetHandle** w systemie Windows 95/98 zwróci **NULL**. **GetHandle** będzie działać zgodnie z opisem w systemie Windows NT w wersji 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761576) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]  
  
##  <a name="gethighlight"></a>CEdit::GetHighlight  
 Pobiera indeksy pierwszy i ostatni znak w zakresie tekstu, który zostanie wyróżniona w bieżącym kontrolki edycji.  
  
```  
BOOL GetHighlight(
    int* pichStart,   
    int* pichEnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`pichStart`|Liczony od zera indeks pierwszego znaku w zakresie tekstu, który zostanie wyróżniona.|  
|[out]`pichEnd`|Liczony od zera indeks ostatni znak w zakres tekstu, które są wyróżnione.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [EM_GETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761578) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getlimittext"></a>CEdit::GetLimitText  
 Wywołanie tej funkcji Członkowskich uzyskanie limit tekstu dla tego `CEdit` obiektu.  
  
```  
UINT GetLimitText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący tekst limit, w bajtach, w tym `CEdit` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Limit tekstu jest maksymalny w bajtach, akceptujących kontrolki edycji.  
  
> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]  
  
##  <a name="getline"></a>CEdit::GetLine  
 Wywołanie tej funkcji można pobrać wiersza z formantu edycyjnego i umieszcza je w `lpszBuffer`.  
  
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
 `nIndex`  
 Określa numer wiersza, który można pobrać z wielu linii edycji kontrolki. Numerowanie wierszy jest liczony od zera; wartość 0 określa pierwszego wiersza. Ten parametr jest ignorowana przez kontrolkę edycji jeden wiersz.  
  
 `lpszBuffer`  
 Wskazuje buforu, który otrzyma kopię wiersza. Pierwsze słowo buforu, należy określić maksymalną liczbę znaków, które mogą zostać skopiowane do buforu.  
  
 `nMaxLength`  
 Określa maksymalną liczbę bajtów, które mogą zostać skopiowane do buforu. `GetLine`umieszcza tę wartość w pierwszej wyrazu `lpszBuffer` przed wykonaniem połączenia do systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów faktycznie skopiowane. Zwracana wartość wynosi 0, jeśli numer wiersza określony przez `nIndex` jest większa niż liczba wierszy w formancie edycyjnym.  
  
### <a name="remarks"></a>Uwagi  
 Skopiowanego wiersza nie zawiera znaku zakończenia wartości null.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>CEdit::GetLineCount  
 Wywołanie tej funkcji, aby pobrać liczbę wierszy w formancie edycji wielu linii.  
  
```  
int GetLineCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Formant edycji całkowitą reprezentującą liczbę wierszy w wielu wierszach. Jeśli tekst nie został wprowadzony w formancie edycji, zwracana wartość to 1.  
  
### <a name="remarks"></a>Uwagi  
 `GetLineCount`jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]  
  
##  <a name="getmargins"></a>CEdit::GetMargins  
 Wywołanie tej funkcji Członkowskich pobrać lewego i prawego marginesu tej kontrolki edycji.  
  
```  
DWORD GetMargins() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość lewy margines w znaczącymi bitami **WORD** i szerokość prawego marginesu w znaczącymi bitami **WORD**.  
  
### <a name="remarks"></a>Uwagi  
 Marginesy są mierzone w pikselach.  
  
> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761590) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="getmodify"></a>CEdit::GetModify  
 Wywołanie tej funkcji, aby określić, czy zawartość formantu edycyjnego zostały zmodyfikowane.  
  
```  
BOOL GetModify() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zostały zmodyfikowane zawartość kontrolki edycji; 0, jeśli ich pozostać bez zmian.  
  
### <a name="remarks"></a>Uwagi  
 System Windows zachowuje wewnętrzny flagę wskazującą, czy zawartość formantu edycyjnego zostały zmienione. Flaga ta zostanie wyczyszczona po kontrolki edycji utworzenia i mogą być również usunięte przez wywołanie metody [SetModify](#setmodify) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]  
  
##  <a name="getpasswordchar"></a>CEdit::GetPasswordChar  
 Wywołanie tej funkcji można pobrać znak hasła, która jest wyświetlana w formancie edycji, gdy użytkownik wprowadzi tekst.  
  
```  
TCHAR GetPasswordChar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa znaków, które mają być wyświetlane zamiast znaków, która zostanie wpisany. Wartość zwracana jest `NULL` Jeśli istnieje nie znaków hasła.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku utworzenia kontrolki edycji z **es_password —** styl, DLL, która obsługuje kontrolkę Określa domyślny znak hasła. Plik manifestu lub [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) Metoda określa, który obsługuje DLL kontrolki edycji. Jeśli user32.dll obsługuje kontrolki edycji, domyślny znak hasła jest znak GWIAZDKI ("*", U + 002A). Jeśli comctl32.dll w wersji 6 obsługuje kontrolki edycji, domyślny znak jest czarne KÓŁKO ("●", U + 25CF). Aby uzyskać więcej informacji o obsługujący biblioteki DLL i wersji wspólne kontrolki, zobacz [powłoki i wersji formantów wspólnych](http://msdn.microsoft.com/library/windows/desktop/bb776779).  
  
 Ta metoda wysyła [EM_GETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761594) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]  
  
##  <a name="getrect"></a>CEdit::GetRect  
 Wywołanie tej funkcji można pobrać prostokąt formatowania formantu edycyjnego.  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` strukturę, która odbiera formatowania prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt formatowania jest ograniczanie prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji.  
  
 Prostokąt formatowania formantu edycji wielu linii, może być modyfikowany przez [SetRect](#setrect) i [SetRectNP](#setrectnp) funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::LimitText](#limittext).  
  
##  <a name="getsel"></a>CEdit::GetSel  
 Wywołanie tej funkcji, aby uzyskać początkową i końcową pozycji znaku bieżącego zaznaczenia (jeśli istnieją) w formancie edycji, przy użyciu parametrów lub wartości zwracanej.  
  
```  
DWORD GetSel() const;  
  
void GetSel(
    int& nStartChar,  
    int& nEndChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartChar`  
 Odwołanie do wartości całkowitej, który będzie otrzymywał pozycja pierwszego znaku w bieżącym zaznaczeniu.  
  
 `nEndChar`  
 Odwołanie do wartości całkowitej, który będzie otrzymywał pozycja pierwszego znaku nonselected poza końcem bieżącego zaznaczenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wersja, która zwraca `DWORD` zwróci wartość, która zawiera pozycji początkowej w programie word znaczącymi bitami i pozycja pierwszego znaku nonselected po zakończeniu wyboru w programie word znaczących.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_GETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761598) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]  
  
##  <a name="hideballoontip"></a>CEdit::HideBalloonTip  
 Ukrywa dowolnym dymku skojarzone z bieżącym kontrolki edycji.  
  
```  
BOOL HideBalloonTip();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wysyła [EM_HIDEBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761604) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="limittext"></a>CEdit::LimitText  
 Wywołanie tej funkcji, aby ograniczyć długość tekstu, który użytkownik może wprowadzić w formancie edycyjnym.  
  
```  
void LimitText(int nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nChars`  
 Określa tekst, który użytkownik może wprowadzić długość (w bajtach). Jeśli ten parametr ma wartość 0, ma ustawioną wartość długość tekstu **uint_max —** bajtów. Jest to zachowanie domyślne.  
  
### <a name="remarks"></a>Uwagi  
 Zmiana limit tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Go nie ma wpływu na dowolny tekst już w formancie edycyjnym ani nie ogranicza długość tekstu skopiowane do edycji przez [SetWindowText](cwnd-class.md#setwindowtext) funkcji członkowskiej we `CWnd`. Jeśli aplikacja używa `SetWindowText` funkcji, aby umieścić tekst w formancie edycyjnym niż określona w wywołaniu `LimitText`, użytkownik może usunąć tekstu w formancie edycji. Jednak limit tekstu uniemożliwi zastępując istniejący tekst na nowy tekst użytkownika, chyba że usunięcie bieżącego zaznaczenia powoduje, że tekst, który spadną poniżej limit tekstu.  
  
> [!NOTE]
>  W systemie Win32 (z systemem Windows NT i system operacyjny Windows 95/98), [SetLimitText](#setlimittext) zastępuje tej funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]  
  
##  <a name="linefromchar"></a>CEdit::LineFromChar  
 Wywołanie tej funkcji można pobrać numer wiersza, który zawiera indeks określony znak.  
  
```  
int LineFromChar(int nIndex = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Zawiera wartość indeksu żądany znak w tekście kontrolki edycji lub zawiera wartość -1. Jeśli `nIndex` wynosi -1, określa bieżącego wiersza, oznacza to, że wiersz zawierający karetki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera numery wierszy zawierających określony przez indeks znaków `nIndex`. Jeśli `nIndex` wynosi -1, jest zwracany numer wiersza, który zawiera pierwszy znak zaznaczenia. Jeśli nie ma żadnego zaznaczenia, zwracany jest bieżący numer wiersza.  
  
### <a name="remarks"></a>Uwagi  
 Indeks znaków jest liczbę znaków od początku kontrolki edycji.  
  
 Ta funkcja członkowska jest używana tylko w formantach edycji wielu linii.  
  
 Aby uzyskać więcej informacji, zobacz [EM_LINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761609) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]  
  
##  <a name="lineindex"></a>CEdit::LineIndex  
 Wywołanie tej funkcji można pobrać indeks znaków wiersza w formancie edycji wielu linii.  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Zawiera wartość indeksu dla żądanego wiersza w tekście kontrolki edycji lub zawiera wartość -1. Jeśli `nLine` wynosi -1, określa bieżącego wiersza, oznacza to, że wiersz zawierający karetki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks znaków wiersza określony w `nLine` lub wartość -1 Jeśli liczba określonego wiersza jest większa niż liczba wierszy w formancie edycyjnym.  
  
### <a name="remarks"></a>Uwagi  
 Indeks znaków jest liczbę znaków od początku kontrolki edycji określony wiersz.  
  
 Funkcji członkowskiej jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Aby uzyskać więcej informacji, zobacz [EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]  
  
##  <a name="linelength"></a>CEdit::LineLength  
 Pobiera długość wiersza w kontrolce edycji.  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nLine`  
 Liczony od zera indeks znaków w wierszu, którego długość ma być pobrana. Wartość domyślna wynosi -1.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dla formantów edycyjnych jeden wiersz, wartość zwracana jest długość, w `TCHAR`s tekstu w formancie edycyjnym.  
  
 Dla wielowierszowych formantów edycyjnych, wartość zwracana jest długość, `TCHAR`s wiersza określony przez `nLine` parametru. Aby uzyskać [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] tekstu, długość jest to liczba bajtów w wierszu; tekst Unicode, długość jest liczba znaków w wierszu. Długość nie zawiera znak powrotu karetki na końcu linii.  
  
 Jeśli `nLine` parametru jest większa niż liczba znaków w formancie, zwracana wartość wynosi zero.  
  
 Jeśli `nLine` parametru wynosi -1, wartość zwracana jest liczba niezaznaczone znaków w wierszy, które zawierają znaki wybrane. Na przykład jeśli zaznaczenie rozciąga się od czwarty znaku o jeden wiersz za pośrednictwem osiem znaków od końca następnego wiersza, zwracana wartość wynosi 10. Oznacza to trzy znaki na pierwszy wiersz i siedem przy następnym.  
  
 Aby uzyskać więcej informacji na temat `TCHAR` typu, zobacz `TCHAR` wiersza w tabeli w [typów danych systemu Windows](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest obsługiwana przez [EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::LineIndex](#lineindex).  
  
##  <a name="linescroll"></a>CEdit::LineScroll  
 Wywołanie tej funkcji, aby przewijać tekst formantu edycji wielu linii.  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nLines`  
 Określa liczbę wierszy, aby przewijać w pionie.  
  
 `nChars`  
 Określa liczbę pozycji znaku można przewijać w poziomie. Ta wartość jest ignorowana, jeśli formant edycyjny ma albo **es_right —** lub **es_center —** stylu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Formant edycyjny nie jest przewijane w pionie poza ostatni wiersz tekstu w formancie edycyjnym. Jeśli bieżący wiersz i liczby wierszy określony przez `nLines` przekracza całkowitą liczbę wierszy w formancie edycyjnym, wartość jest ustawione tak, aby ostatni wiersz kontrolki edycji jest przewijane w górnej części okna kontrolki edycji.  
  
 `LineScroll`można przewijać w poziomie poza ostatni znak każdego wiersza.  
  
 Aby uzyskać więcej informacji, zobacz [EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::GetFirstVisibleLine](#getfirstvisibleline).  
  
##  <a name="paste"></a>CEdit::Paste  
 Wywołanie tej funkcji do wstawiania danych ze Schowka do `CEdit` punkt wstawiania.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Uwagi  
 Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w **CF_TEXT** format.  
  
 Aby uzyskać więcej informacji, zobacz [WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]  
  
##  <a name="posfromchar"></a>CEdit::PosFromChar  
 Wywołanie tej funkcji można pobrać pozycji (lewego górnego rogu) danego znaku w ramach tego `CEdit` obiektu.  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nChar`  
 Liczony od zera indeks określony znak.  
  
### <a name="return-value"></a>Wartość zwracana  
 Współrzędne górnego lewego rogu znak określony przez `nChar`.  
  
### <a name="remarks"></a>Uwagi  
 Znak jest określona przez podanie jego liczony od zera indeks wartości. Jeśli `nChar` jest większa niż indeks ostatni znak w tym `CEdit` obiektu, zwracana wartość określa współrzędne znaku na pozycji tylko po ostatnim znakiem w tym `CEdit` obiektu.  
  
> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::LineFromChar](#linefromchar).  
  
##  <a name="replacesel"></a>CEdit::ReplaceSel  
 Wywołanie tej funkcji, aby zastąpić bieżące zaznaczenie w formancie edycji tekstu określonego przez `lpszNewText`.  
  
```  
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewText`  
 Wskazuje zerem ciąg zawierający tekst zastępczy.  
  
 `bCanUndo`  
 Aby określić, że ta funkcja może być cofnięte, ustaw wartość tego parametru, aby **TRUE** . Wartość domyślna to **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tylko część tekstu w kontrolce edycji. Jeśli chcesz zamienić cały tekst, użyj [CWnd::SetWindowText](cwnd-class.md#setwindowtext) funkcję elementu członkowskiego.  
  
 Jeśli nie ma żadnego bieżącego zaznaczenia, tekst zastępczy jest wstawiany w bieżącej lokalizacji kursora.  
  
 Aby uzyskać więcej informacji, zobacz [EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::LineIndex](#lineindex).  
  
##  <a name="setcuebanner"></a>CEdit::SetCueBanner  
 Ustawia tekst, który jest wyświetlany jako wskaźnik tekstu lub Porada, w edycji sterować tym, gdy formant jest pusty.  
  
```  
BOOL SetCueBanner(LPCWSTR lpszText);

 
BOOL SetCueBanner(
    LPCWSTR lpszText,   
    BOOL fDrawWhenFocused = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszText`  
 Wskaźnik do ciąg, który zawiera wskaźnik do wyświetlenia w formancie edycyjnym.  
  
 [in]`fDrawWhenFocused`  
 Jeśli `false`, transparent wskaźnika nie jest rysowana, gdy użytkownik kliknie przycisk w formancie edycyjnym i przenosi fokus na formantu.  
  
 Jeśli `true`, transparent wskaźnika jest rysowany nawet wtedy, gdy formant ma fokus. Transparent sygnalizacji zniknie uruchomienia wpisz w formancie użytkownika.  
  
 Wartość domyślna to `false`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [EM_SETCUEBANNER](http://msdn.microsoft.com/library/windows/desktop/bb761639) komunikat, który jest opisany w zestawie SDK systemu Windows. Aby uzyskać więcej informacji, zobacz [Edit_SetCueBannerTextFocused](http://msdn.microsoft.com/library/windows/desktop/bb761703) makra.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano [CEdit::SetCueBanner](#setcuebanner) metody.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]  
  
##  <a name="sethandle"></a>CEdit::SetHandle  
 Wywołanie tej funkcji, aby ustawić dojście do pamięci lokalnej, który będzie używany przez formant edycji wielu linii.  
  
```  
void SetHandle(HLOCAL hBuffer);
```  
  
### <a name="parameters"></a>Parametry  
 *hBuffer*  
 Zawiera dojścia do pamięci lokalnej. Ta dojścia musi być utworzony przez poprzednie wywołanie [Funkcja LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723) za pomocą funkcji Windows **LMEM_MOVEABLE** flagi. Pamięć zakłada się, że zawierają ciąg znaków zakończony znakiem null. Jeśli nie jest to możliwe, pierwszy bajt alokacji pamięci powinna być równa 0.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolka edycji będzie używać tego buforu do przechowywania aktualnie wyświetlanego tekstu zamiast przydzielania własną buforu.  
  
 Ta funkcja członkowska jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Przed aplikacji Ustawia nowy uchwyt pamięci, należy używać [GetHandle](#gethandle) funkcji członkowskiej można uzyskać dojścia do bieżącego bufora pamięci i wolną przy użyciu tej pamięci **LocalFree** funkcji systemu Windows.  
  
 `SetHandle`czyści buforu cofania ( [CanUndo](#canundo) funkcji członkowskiej zwracana 0) i flagi modyfikacji wewnętrzny ( [GetModify](#getmodify) funkcji członkowskiej zwracana 0). Rysowane jest okno kontrolki edycji.  
  
 Możesz użyć tej funkcji elementu członkowskiego w formancie edycji wielu linii w oknie dialogowym tylko wtedy, gdy utworzono okna dialogowego z **DS_LOCALEDIT** styl ustawioną flagą.  
  
> [!NOTE]
> **GetHandle** nie działa w systemie Windows 95/98. Jeśli należy wywołać **GetHandle** w systemie Windows 95/98 zwróci **NULL**. **GetHandle** będzie działać zgodnie z opisem w systemie Windows NT w wersji 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETHANDLE](http://msdn.microsoft.com/library/windows/desktop/bb761641), [Funkcja LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), i [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]  
  
##  <a name="sethighlight"></a>CEdit::SetHighlight  
 Najważniejsze funkcje zakres tekstu, który jest wyświetlany w bieżącej edycji.  
  
```  
void SetHighlight(
    int ichStart,   
    int ichEnd);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`ichStart`|Liczony od zera indeks pierwszego znaku w zakres tekstu, aby wyróżnić.|  
|[in]`ichEnd`|Liczony od zera indeks ostatni znak w zakres tekstu, aby wyróżnić.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [EM_SETHILITE](http://msdn.microsoft.com/library/windows/desktop/bb761643) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="setlimittext"></a>CEdit::SetLimitText  
 Wywołanie tej funkcji członkowskich można ustawić limitu tekstu dla tego `CEdit` obiektu.  
  
```  
void SetLimitText(UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nMax`  
 Nowy limit tekstu, w znakach.  
  
### <a name="remarks"></a>Uwagi  
 Limit tekst to maksymalna ilość tekstu w znaków, która może zaakceptować kontrolki edycji.  
  
 Zmiana limit tekstu ogranicza tylko tekst, który użytkownik może wprowadzić. Go nie ma wpływu na dowolny tekst już w formancie edycyjnym ani nie ogranicza długość tekstu skopiowane do edycji przez [SetWindowText](cwnd-class.md#setwindowtext) funkcji członkowskiej we `CWnd`. Jeśli aplikacja używa `SetWindowText` funkcji, aby umieścić tekst w formancie edycyjnym niż określona w wywołaniu `LimitText`, użytkownik może usunąć tekstu w formancie edycji. Jednak limit tekstu uniemożliwi zastępując istniejący tekst na nowy tekst użytkownika, chyba że usunięcie bieżącego zaznaczenia powoduje, że tekst, który spadną poniżej limit tekstu.  
  
 Ta funkcja zastępuje [LimitText](#limittext) w Win32.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761647) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmargins"></a>CEdit::SetMargins  
 Wywołaj tę metodę, aby ustawić lewego i prawego marginesu tej kontrolki edycji.  
  
```  
void SetMargins(
    UINT nLeft,  
    UINT nRight);
```  
  
### <a name="parameters"></a>Parametry  
 *nLeft*  
 Szerokość nowego lewy margines, w pikselach.  
  
 *nRight*  
 Szerokość nowego prawy margines w pikselach.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja członkowska jest dostępnych w programie Windows 95 i Windows NT 4.0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb761649) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).  
  
##  <a name="setmodify"></a>CEdit::SetModify  
 Wywołanie tej funkcji do ustawiania i czyszczenia zmodyfikowane flagi dla kontrolki edycji.  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Wartość **TRUE** wskazuje, czy tekst został zmodyfikowany i wartość **FALSE** wskazuje on pozostaje niezmieniona. Domyślnie została ustawiona flaga zmodyfikowane.  
  
### <a name="remarks"></a>Uwagi  
 Zmodyfikowane flaga wskazuje, czy tekst w formancie edycyjnym został zmodyfikowany. Ta opcja jest automatycznie ustawiana zawsze, gdy użytkownik zmieni tekst. Jej wartość może być pobrany za pomocą [GetModify](#getmodify) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::GetModify](#getmodify).  
  
##  <a name="setpasswordchar"></a>CEdit::SetPasswordChar  
 Wywołanie tej funkcji, aby ustawić lub usunąć wyświetlany w formancie edycji, gdy użytkownik wpisze tekst znak hasła.  
  
```  
void SetPasswordChar(TCHAR ch);
```  
  
### <a name="parameters"></a>Parametry  
 *ch*  
 Określa znaków, które mają być wyświetlane zamiast znaków wpisana przez użytkownika. Jeśli *ch* ma wartość 0, wyświetlane są rzeczywiste znaki wpisywane przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Gdy znak hasła jest ustawiona, ten znak jest wyświetlana dla każdego znaku typy użytkownika.  
  
 Ta funkcja członkowska nie ma wpływu na wielu linii formantów edycji.  
  
 Gdy `SetPasswordChar` po wywołaniu funkcji członkowskiej `CEdit` ponownie utworzy wszystkie znaki widoczne przy użyciu znaku określonego przez *ch*.  
  
 Jeśli utworzono kontrolki edycji z [es_password —](edit-styles.md) styl domyślny znak hasła ustawiono gwiazdkę (  **\*** ). Ten styl jest usunięte, jeśli `SetPasswordChar` jest wywoływana z *ch* równa 0.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETPASSWORDCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761653) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]  
  
##  <a name="setreadonly"></a>CEdit::SetReadOnly  
 Wywołanie tej funkcji można ustawić stanu tylko do odczytu formantu edycji.  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bReadOnly`  
 Określa, czy do ustawiania lub usuwania stanie tylko do odczytu kontrolki edycji. Wartość **TRUE** ustawia stan tylko do odczytu; wartość **FALSE** ustawia stan odczytu/zapisu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, czy operacja się powiodła, 0 Jeśli błąd występuje.  
  
### <a name="remarks"></a>Uwagi  
 Bieżące ustawienia można znaleźć testując [es_readonly —](edit-styles.md) flagi w zwracanej wartości [CWnd::GetStyle](cwnd-class.md#getstyle).  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]  
  
##  <a name="setrect"></a>CEdit::SetRect  
 Wywołanie tej funkcji można ustawić wymiary prostokąt przy użyciu określonych współrzędnych.  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który określa nowe wymiary formatowania prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Użyj `SetRect` ustawienia formatowania formantu edycyjnego prostokąt wielu linii. Prostokąt formatowania jest ograniczanie prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji. Podczas tworzenia kontrolki edycji formatowania prostokąt jest taka sama jak obszaru klienckiego okna kontrolki edycji. Za pomocą `SetRect` funkcji członkowskiej aplikacji ułatwia formatowania prostokąt większy lub mniejszy niż okno kontrolki edycji.  
  
 Jeśli formant edycyjny nie ma paska przewijania, tekst zostaną przycięte, nie jest zawijany, jeśli formatowania prostokąt jest większy niż okno. Jeśli kontrolka edycji zawiera obramowanie, zostanie zmniejszona formatowania prostokąt rozmiar obramowania. Dostosowanie prostokąt zwrócony przez `GetRect` funkcji członkowskiej, musisz usunąć rozmiar obramowania przekazać prostokąt `SetRect`.  
  
 Gdy `SetRect` jest nazywany kontrolki edycji tekstu jest również ponownie sformatowany i wyświetlane ponownie.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]  
  
##  <a name="setrectnp"></a>CEdit::SetRectNP  
 Wywołanie tej funkcji, aby ustawić formatowania prostokąt kontrolkę edycji wielu linii.  
  
```  
void SetRectNP(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `RECT` struktury lub `CRect` obiekt, który określa nowe wymiary prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Prostokąt formatowania jest ograniczanie prostokąt tekst, który jest niezależny od rozmiaru okna kontrolki edycji.  
  
 `SetRectNP`jest taka sama jak `SetRect` funkcji członkowskiej, z wyjątkiem tego, że nie jest rysowane okna kontrolki edycji.  
  
 Podczas tworzenia kontrolki edycji formatowania prostokąt jest taka sama jak obszaru klienckiego okna kontrolki edycji. Wywołując `SetRectNP` funkcji członkowskiej aplikacji ułatwia formatowania prostokąt większy lub mniejszy niż okno kontrolki edycji.  
  
 Jeśli formant edycyjny nie ma paska przewijania, tekst zostaną przycięte, nie jest zawijany, jeśli formatowania prostokąt jest większy niż okno.  
  
 Ten element członkowski jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETRECTNP](http://msdn.microsoft.com/library/windows/desktop/bb761659) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::SetRect](#setrect).  
  
##  <a name="setsel"></a>CEdit::SetSel  
 Wywołanie tej funkcji, aby wybrać zakres znaków w formancie edycyjnym.  
  
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
 *dwSelection*  
 Określa położenie początkowe w programie word znaczącymi bitami i pozycji końcowej w programie word znaczących. Word znaczącymi bitami wynosi 0 i word znaczącymi to -1, cały tekst w formancie edycyjnym jest zaznaczone. Jeśli word znaczącymi to -1, wszystkie bieżące zaznaczenie zostanie usunięta.  
  
 *bNoScroll*  
 Wskazuje, czy karetkę powinien zostać wyświetlony w wyniku przewijania. Jeśli **FALSE**, karetkę jest wyświetlony w wyniku przewijania. Jeśli **TRUE**, karetkę nie jest przewijane w widoku.  
  
 `nStartChar`  
 Określa położenie początkowe. Jeśli `nStartChar` 0 i `nEndChar` wynosi -1, wszystkie tekst w formancie edycyjnym jest zaznaczone. Jeśli `nStartChar` wynosi -1, wszystkie bieżące zaznaczenie jest usunięte.  
  
 `nEndChar`  
 Określa pozycję końcową.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [EM_SETSEL](http://msdn.microsoft.com/library/windows/desktop/bb761661) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEdit::GetSel](#getsel).  
  
##  <a name="settabstops"></a>CEdit::SetTabStops  
 Wywołanie tej funkcji tabulatorów w formancie edycji wielu linii.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `cxEachStop`  
 Określa, że tabulatorów był co `cxEachStop` jednostki okna dialogowego.  
  
 `nTabStops`  
 Określa liczbę tabulatorów zawarte w `rgTabStops`. Ta liczba musi być większa niż 1.  
  
 `rgTabStops`  
 Punkty na tablicę liczb całkowitych bez znaku, określając karcie zatrzymuje się w jednostkach okna dialogowego. Jednostki okna dialogowego jest odległość pozioma lub pionowa. Jednostki okna dialogowego w poziomie jest taki sam, jak jedna czwarta bieżąca jednostka podstawowa szerokość okna dialogowego i 1 jednostka pionowy okna dialogowego jest równa 1 / 8 bieżąca jednostka podstawowa wysokość okna dialogowego. Jednostki podstawowy okna dialogowego są obliczane na podstawie wysokość i szerokość bieżącej czcionki systemowej. **GetDialogBaseUnits** systemu Windows funkcja zwraca bieżącego okna dialogowego podstawowej jednostki w pikselach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ustawiono kart; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli tekst jest kopiowany do formantu edycji wielu linii, wszelkie znak tabulacji w tekście spowoduje miejsca do wygenerowania do następnego tabulatora.  
  
 Ustawić tabulatorów domyślny rozmiar 32 jednostki okna dialogowego, należy wywołać wersji bez parametrów funkcji członkowskiej. Tabulatorów rozmiar niż 32, wywołaj wersji z `cxEachStop` parametru. Tabulatorów na tablicę rozmiary, użyj wersji z dwoma parametrami.  
  
 Funkcji członkowskiej jest przetwarzany tylko przez formantów edycyjnych wielu linii.  
  
 `SetTabStops`nie automatycznie są odświeżane okno edycji. Jeśli zmienisz tabulatorów dla tekstu w formancie edycyjnym wywołanie [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) ponowne okno edycji.  
  
 Aby uzyskać więcej informacji, zobacz [EM_SETTABSTOPS](http://msdn.microsoft.com/library/windows/desktop/bb761663) i [GetDialogBaseUnits](http://msdn.microsoft.com/library/windows/desktop/ms645475) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CEditView::SetTabStops](ceditview-class.md#settabstops).  
  
##  <a name="showballoontip"></a>CEdit::ShowBalloonTip  
 Wyświetla etykieta dymka skojarzony z bieżącym kontrolki edycji.  
  
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
|[in]`pEditBalloonTip`|Wskaźnik do [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) struktury, która opisuje etykieta dymka.|  
|[in]`lpszTitle`|Wskaźnik do ciągu Unicode, który zawiera tytuł etykieta dymka.|  
|[in]`lpszText`|Wskaźnik do ciągu Unicode, który zawiera tekst etykiety dymka.|  
|[in]`ttiIcon`|`INT` Określająca typ ikona do skojarzenia z etykieta dymka. Wartość domyślna to `TTI_NONE`. Aby uzyskać więcej informacji, zobacz `ttiIcon` członkiem [EDITBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb775466) struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wysyła [EM_SHOWBALLOONTIP](http://msdn.microsoft.com/library/windows/desktop/bb761668) komunikat, który jest opisany w zestawie SDK systemu Windows. Aby uzyskać więcej informacji, zobacz [Edit_ShowBalloonTip](http://msdn.microsoft.com/library/windows/desktop/bb761707) makra.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_cedit`, która jest umożliwiają dostęp do bieżącej kontrolki edycji. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia etykieta dymka dla kontrolki edycji. [CEdit::ShowBalloonTip](#showballoontip) metody Określa tekst porady tytuł i dymek.  
  
 [!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]  
  
##  <a name="undo"></a>CEdit::Undo  
 Wywołanie tej funkcji, aby cofnąć ostatnią operację kontrolki edycji.  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kontrolki edycji jeden wiersz zwracana wartość jest zawsze różną od zera. Kontrolki edycji wielu linii, zwracana wartość jest różna od zera, jeśli operacja cofania zakończy się pomyślnie, lub wartość 0 w przypadku niepowodzenia operacji cofania.  
  
### <a name="remarks"></a>Uwagi  
 Można także cofnąć operacji cofania. Na przykład można przywrócić usuniętego tekstu w pierwszym wywołaniu **Cofnij**. Tak długo, jak brak pośredniczące operacji edycji, należy usunąć go ponownie, używając drugie wywołanie **Cofnij**.  
  
 Aby uzyskać więcej informacji, zobacz [EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CALCDRIV](../../visual-cpp-samples.md)   
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](cwnd-class.md)   
 [Klasa CButton](cbutton-class.md)   
 [Ccombobox — klasa](ccombobox-class.md)   
 [Clistbox — klasa](clistbox-class.md)   
 [Klasa CScrollBar](cscrollbar-class.md)   
 [Klasa CStatic](cstatic-class.md)   
 [Klasa CDialog](cdialog-class.md)
