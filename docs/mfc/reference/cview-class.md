---
title: Klasa CView
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373200"
---
# <a name="cview-class"></a>Klasa CView

Zapewnia podstawowe funkcje dla klas widoku zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView::CView](#cview)|Konstruuje `CView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CView::DoPrzypoprawydanie](#doprepareprinting)|Wyświetla okno dialogowe Drukowanie i tworzy kontekst urządzenia drukarki; podczas zastępowania funkcji `OnPreparePrinting` elementu członkowskiego.|
|[CView::GetDocument](#getdocument)|Zwraca dokument skojarzony z widokiem.|
|[CView::IsSelected](#isselected)|Sprawdza, czy element dokumentu jest zaznaczony. Wymagane do obsługi OLE.|
|[CView::OnDragEnter](#ondragenter)|Wywoływana, gdy element jest przeciągany po raz pierwszy do regionu przeciągania i upuszczania widoku.|
|[CView::OnDragLeave](#ondragleave)|Wywoływana, gdy przeciągany element opuszcza obszar przeciągania i upuszczania widoku.|
|[CView::OnDragOver](#ondragover)|Wywoływana, gdy element jest przeciągany nad obszarem przeciągania i upuszczania widoku.|
|[CView::OnDragscroll](#ondragscroll)|Wywoływana w celu ustalenia, czy kursor jest przeciągany do regionu przewijania okna.|
|[CView::OnDrop](#ondrop)|Wywoływane, gdy element został upuszczony do przeciągnij i upuść region widoku, domyślny program obsługi.|
|[CView::OnDropEx](#ondropex)|Wywoływane, gdy element został upuszczony do przeciągnij i upuść region widoku, podstawowy program obsługi.|
|[CView::OnInitialUpdate](#oninitialupdate)|Wywoływana po dołączeniu widoku do dokumentu.|
|[CView::OnPrepareDC](#onpreparedc)|Wywoływana `OnDraw` przed wywołaniem funkcji elementu `OnPrint` członkowskiego do wyświetlania ekranu lub wywoływana jest funkcja elementu członkowskiego do drukowania lub podglądu wydruku.|
|[CView::OnScroll](#onscroll)|Wywoływane, gdy elementy OLE są przeciągane poza granice widoku.|
|[CView::OnScrollBy](#onscrollby)|Wywoływane, gdy widok zawierający aktywne elementy OLE w miejscu jest przewijany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Wywoływane, gdy okno ramki zawierające widok jest aktywowany lub dezaktywowany.|
|[CView::OnActivateView](#onactivateview)|Wywoływana, gdy widok jest aktywowany.|
|[CView::OnBeginPrinting](#onbeginprinting)|Wywoływana po rozpoczęciu zadania drukowania; zastępowanie alokacji zasobów interfejsu urządzenia graficznego (GDI).|
|[CView::OnDraw](#ondraw)|Wywoływana w celu renderowania obrazu dokumentu do wyświetlania ekranu, drukowania lub podglądu wydruku. Wymagana implementacja.|
|[CView::OnEndPrinting](#onendprinting)|Wywoływana po zakończeniu zadania drukowania; zastąpić, aby zdyskcesować zasoby GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Wywoływana po zakończeniu trybu podglądu.|
|[CView::OnPreparePrinting](#onprepareprinting)|Wywoływana przed wydrukowaniem lub podglądem dokumentu; aby zainicjować okno dialogowe Drukowanie.|
|[CView::OnPrint](#onprint)|Wywoływana w celu wydrukowania lub wyświetlenia podglądu strony dokumentu.|
|[CView::OnUpdate](#onupdate)|Wywoływany, aby powiadomić widok, że jego dokument został zmodyfikowany.|

## <a name="remarks"></a>Uwagi

Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem a użytkownikiem: widok renderuje obraz dokumentu na ekranie lub drukarce i interpretuje dane wejściowe użytkownika jako operacje na dokumencie.

Widok jest dziewką okna ramki. Więcej niż jeden widok może współużytkować okno ramki, jak w przypadku okna rozdzielacza. Relacja między klasą widoku, klasą okna ramki i klasą dokumentu jest ustanawiana przez `CDocTemplate` obiekt. Gdy użytkownik otworzy nowe okno lub podzieli istniejące, struktura tworzy nowy widok i dołącza go do dokumentu.

Widok może być dołączony tylko do jednego dokumentu, ale dokument może mieć wiele widoków dołączonych do niego naraz — na przykład, jeśli dokument jest wyświetlany w oknie rozdzielacza lub w wielu oknach podrzędnych w aplikacji interfejsu wielu dokumentów (MDI). Aplikacja może obsługiwać różne typy widoków dla danego typu dokumentu; na przykład edytor tekstu może zapewnić zarówno pełny widok tekstu dokumentu, jak i widok konspektu, który pokazuje tylko nagłówki sekcji. Te różne typy widoków można umieszczać w oddzielnych oknach ramek lub w oddzielnych okienkach okna pojedynczej ramki, jeśli używane jest okno rozdzielacza.

Widok może być odpowiedzialny za obsługę kilku różnych typów danych wejściowych, takich jak wprowadzanie klawiatury, wprowadzanie myszy lub wprowadzanie danych za pośrednictwem przeciągania i upuszczania, a także polecenia z menu, pasków narzędzi lub pasków przewijania. Widok odbiera polecenia przekazywane dalej przez okno ramki. Jeśli widok nie obsługuje danego polecenia, przekazuje polecenie do skojarzonego z nim dokumentu. Podobnie jak wszystkie obiekty docelowe polecenia, widok obsługuje wiadomości za pośrednictwem mapy wiadomości.

Widok jest odpowiedzialny za wyświetlanie i modyfikowanie danych dokumentu, ale nie za jego przechowywanie. Dokument zawiera widok z niezbędnymi szczegółami na temat jego danych. Można umożliwić widok dostęp do elementów członkowskich danych dokumentu bezpośrednio lub można zapewnić funkcje członkowskie w klasie dokumentu dla klasy widoku do wywołania.

Po zmianie danych dokumentu widok odpowiedzialny za zmiany zazwyczaj wywołuje [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkcji dla dokumentu, który powiadamia wszystkie `OnUpdate` inne widoki, wywołując funkcję elementu członkowskiego dla każdego. Domyślna implementacja `OnUpdate` unieważnia cały obszar klienta widoku. Można go zastąpić, aby unieważnić tylko te regiony obszaru klienta, które mapują zmodyfikowane części dokumentu.

Aby `CView`użyć , wywodź z `OnDraw` niej klasę i zaimplementuj funkcję elementu członkowskiego do wykonywania wyświetlania ekranu. Można również `OnDraw` użyć do drukowania i drukowania podglądu. Struktura obsługuje pętlę drukowania do drukowania i podglądu dokumentu.

Widok obsługuje komunikaty paska przewijania za pomocą funkcji elementów członkowskich [CWnd:::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll.](../../mfc/reference/cwnd-class.md#onvscroll) Można zaimplementować obsługę komunikatów na pasku `CView` przewijania w tych funkcjach lub można użyć klasy pochodnej [CScrollView](../../mfc/reference/cscrollview-class.md) do obsługi przewijania dla Ciebie.

Poza `CScrollView`tym biblioteka klas Microsoft Foundation zawiera `CView`dziewięć innych klas pochodzących z:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), widok, który umożliwia korzystanie z dokumentu — widok architektury z drzewa, listy i formantów edycji bogatej.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), widok, który wyświetla rekordy bazy danych w formantach okna dialogowego.

- [CEditView](../../mfc/reference/ceditview-class.md), widok, który zapewnia prosty edytor tekstu wielowierszowego. `CEditView` Obiekt można używać jako formantu w oknie dialogowym oraz widoku w dokumencie.

- [CFormView](../../mfc/reference/cformview-class.md), przewijany widok zawierający kontrolki okna dialogowego i oparty na zasobie szablonu okna dialogowego.

- [CListView](../../mfc/reference/clistview-class.md), widok, który umożliwia użycie dokumentu — architektura widoku z formantami listy.

- [CRecordView](../../mfc/reference/crecordview-class.md), widok, który wyświetla rekordy bazy danych w formantach okna dialogowego.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), widok, który umożliwia korzystanie z dokumentu — architektura widoku z bogatymi formantami edycji.

- [CScrollView](../../mfc/reference/cscrollview-class.md), widok, który automatycznie zapewnia obsługę przewijania.

- [CTreeView](../../mfc/reference/ctreeview-class.md), widok, który umożliwia użycie dokumentu — architektura widoku z formantami drzewa.

Klasa `CView` ma również pochodną klasę `CPreviewView`implementacji o nazwie , która jest używana przez platformę do wykonywania podglądu wydruku. Ta klasa zapewnia obsługę funkcji unikatowych dla okna podglądu wydruku, takich jak pasek narzędzi, podgląd jedno- lub dwustronicowy i powiększanie, czyli powiększanie podglądu obrazu. Nie musisz wywoływać ani zastępować żadnej `CPreviewView`z funkcji członkowskich, chyba że chcesz zaimplementować własny interfejs do podglądu wydruku (na przykład, jeśli chcesz obsługiwać edycję w trybie podglądu wydruku). Aby uzyskać więcej `CView`informacji na temat używania , zobacz [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md) i [drukowanie](../../mfc/printing.md). Ponadto więcej informacji na temat dostosowywania podglądu wydruku można znaleźć w [notatce technicznej 30.](../../mfc/tn030-customizing-printing-and-print-preview.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>CView::CView

Konstruuje `CView` obiekt.

```
CView();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora, gdy zostanie utworzone nowe okno ramki lub okno jest dzielone. Zastąpuj funkcję elementu członkowskiego [OnInitialUpdate,](#oninitialupdate) aby zainicjować widok po dołączeniu dokumentu.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPrzypoprawydanie

Wywołanie tej funkcji z zastąpienia [OnPreparePrinting](#onprepareprinting) wywołać okno dialogowe Drukowanie i utworzyć kontekst urządzenia drukarki.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) opisującą bieżące zadanie drukowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli można rozpocząć drukowanie lub podgląd wydruku; 0, jeśli operacja została anulowana.

### <a name="remarks"></a>Uwagi

Zachowanie tej funkcji zależy od tego, czy jest wywoływana do `m_bPreview` drukowania lub podglądu wydruku (określonego przez członka parametru *pInfo).* Jeśli plik jest drukowany, ta funkcja wywołuje okno dialogowe Drukuj, używając wartości w strukturze [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) na które wskazuje *pInfo;* po zamknięciu okna dialogowego użytkownik tworzy kontekst urządzenia drukarki na podstawie ustawień określonych przez użytkownika w oknie dialogowym i zwraca ten kontekst urządzenia za pomocą parametru *pInfo.* Ten kontekst urządzenia jest używany do drukowania dokumentu.

Jeśli podgląd pliku jest wyświetlany, ta funkcja tworzy kontekst urządzenia drukarki przy użyciu bieżących ustawień drukarki; ten kontekst urządzenia służy do symulowania drukarki podczas podglądu.

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument

Wywołanie tej funkcji, aby uzyskać wskaźnik do dokumentu widoku.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CDocument](../../mfc/reference/cdocument-class.md) skojarzonego z widokiem. NULL, jeśli widok nie jest dołączony do dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu można wywołać funkcje członkowskie dokumentu.

## <a name="cviewisselected"></a><a name="isselected"></a>CView::IsSelected

Wywoływane przez strukturę, aby sprawdzić, czy wybrany jest określony element dokumentu.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskazuje testowany element dokumentu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli zaznaczony jest określony element dokumentu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji zwraca WARTOŚĆ FAŁSZ. Zastąpuj tę funkcję, jeśli zaimplementujesz zaznaczenie przy użyciu obiektów [CDocItem.](../../mfc/reference/cdocitem-class.md) Należy zastąpić tę funkcję, jeśli widok zawiera elementy OLE.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView::OnActivateFrame

Wywoływana przez strukturę, gdy okno ramki zawierające widok jest aktywowany lub dezaktywowany.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nPaństwo*<br/>
Określa, czy okno ramki jest aktywowane czy dezaktywowane. Może to być jedna z następujących wartości:

- WA_INACTIVE Okno ramki jest dezaktywowane.

- WA_ACTIVE Okno ramki jest aktywowane za pomocą innej metody niż kliknięcie myszą (na przykład za pomocą interfejsu klawiatury, aby wybrać okno).

- WA_CLICKACTIVE Okno ramki jest aktywowane za pomocą kliknięcia myszą

*pFrameWnd (pFrameWnd)*<br/>
Wskaźnik do okna ramki, które ma być aktywowane.

### <a name="remarks"></a>Uwagi

Zastąpokaj tę funkcję elementu członkowskiego, jeśli chcesz wykonać specjalne przetwarzanie, gdy okno ramki skojarzone z widokiem jest aktywowane lub dezaktywowane. Na przykład [CFormView](../../mfc/reference/cformview-class.md) wykonuje to zastąpienie, gdy zapisuje i przywraca formant, który ma fokus.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>CView::OnActivateView

Wywoływane przez platformę, gdy widok jest aktywowany lub dezaktywowany.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bAktywowanie*<br/>
Wskazuje, czy widok jest aktywowany, czy dezaktywowany.

*pActivateView*<br/>
Wskazuje obiekt widoku, który jest aktywowany.

*pDeactiveView*<br/>
Wskazuje obiekt widoku, który jest dezaktywowany.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji ustawia fokus na widok jest aktywowany. Zastąpokaj tę funkcję, jeśli chcesz wykonać specjalne przetwarzanie, gdy widok jest aktywowany lub dezaktywowany. Na przykład, jeśli chcesz podać specjalne wskazówki wizualne, które odróżniają widok aktywny od widoków nieaktywnych, należy zbadać *bActivate* parametr i odpowiednio zaktualizować wygląd widoku.

Parametry *pActivateView* i *pDeactiveView* wskazują ten sam widok, jeśli okno ramki głównej aplikacji jest aktywowane bez zmian w widoku aktywnym — na przykład, jeśli fokus jest przenoszony z innej aplikacji do tej aplikacji, a nie z jednego widoku do drugiego w aplikacji lub podczas przełączania między oknami podrzędnymi MDI. Pozwala to na ponowne zrealizowanie jego palety, jeśli to konieczne.

Te parametry różnią się, gdy [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) jest wywoływana z widokiem, który różni się od [cFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) zwróci. Dzieje się tak najczęściej w przypadku okien rozdzielacza.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting

Wywoływana przez strukturę na początku zadania podglądu `OnPreparePrinting` wydruku lub drukowania, po wywołaniu.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia drukarki.

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) opisującą bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby przydzielić wszystkie zasoby GDI, takie jak pióra lub czcionki, potrzebne specjalnie do drukowania. Wybierz obiekty GDI w kontekście urządzenia z funkcji elementu członkowskiego [OnPrint](#onprint) dla każdej strony, która ich używa. Jeśli do wyświetlania ekranu i drukowania używany jest ten sam obiekt widoku, należy użyć oddzielnych zmiennych dla zasobów GDI potrzebnych do wyświetlania; pozwala to na aktualizację ekranu podczas drukowania.

Za pomocą tej funkcji można również wykonywać inicjalizowania, które zależą od właściwości kontekstu urządzenia drukarki. Na przykład liczba stron potrzebnych do wydrukowania dokumentu może zależeć od ustawień określonych przez użytkownika w oknie dialogowym Drukowanie (takich jak długość strony). W takiej sytuacji nie można określić długości dokumentu w funkcji elementu członkowskiego [OnPreparePrinting,](#onprepareprinting) w którym zwykle można to zrobić; należy poczekać, aż kontekst urządzenia drukarki zostanie utworzony na podstawie ustawień okna dialogowego. [OnBeginPrinting](#onbeginprinting) jest pierwszą nadpisywalną funkcją, która daje dostęp do obiektu [CDC](../../mfc/reference/cdc-class.md) reprezentującego kontekst urządzenia drukarki, dzięki czemu można ustawić długość dokumentu z tej funkcji. Należy zauważyć, że jeśli długość dokumentu nie zostanie określona przez ten czas, pasek przewijania nie jest wyświetlany podczas podglądu wydruku.

## <a name="cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter

Wywoływana przez strukturę, gdy mysz po raz pierwszy wchodzi do regionu bez przewijania okna docelowego upuszczania.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject (1000)*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągane do obszaru upuszczania widoku.

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Bieżąca pozycja myszy względem obszaru klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość z DROPEFFECT wyliczonego typu, który wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik upuścił obiekt w tej pozycji. Typ spadku zwykle zależy od bieżącego stanu klucza wskazanego przez *dwKeyState*. Standardowe mapowanie państw kluczy do wartości DROPEFFECT jest:

- DROPEFFECT_NONE Nie można upuścić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT Tworzy powiązanie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL Tworzy kopię upuszczonego obiektu.

- DROPEFFECT_MOVE dla MK_ALT Tworzy kopię upuszczonego obiektu i usuwa oryginalny obiekt. Jest to zazwyczaj domyślny efekt upuszczania, gdy widok może zaakceptować ten obiekt danych.

Aby uzyskać więcej informacji, zobacz przykładowe pojęcia zaawansowane MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślna implementacja jest nic nie robić i zwracać DROPEFFECT_NONE.

Zastąpokaj tę funkcję, aby przygotować się do przyszłych wywołań funkcji elementu członkowskiego [OnDragOver.](#ondragover) Wszelkie dane wymagane z obiektu danych powinny być pobierane w `OnDragOver` tej chwili do późniejszego użycia w funkcji elementu członkowskiego. Widok powinien być również aktualizowany w tej chwili, aby przekazać użytkownikowi wizualne opinie. Aby uzyskać więcej informacji, zobacz artykuł [OLE przeciąganie i upuszczanie: Implementowanie celu upuszczania](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave

Wywoływana przez strukturę podczas operacji przeciągania, gdy mysz jest przenoszona z prawidłowego obszaru upuszczania dla tego okna.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Uwagi

Zastąpość tę funkcję, jeśli bieżący widok musi oczyścić wszelkie akcje podjęte podczas [wywołań OnDragEnter](#ondragenter) lub [OnDragOver,](#ondragover) takie jak usuwanie wszelkich wizualnych opinii użytkowników, gdy obiekt został przeciągany i porzucony.

## <a name="cviewondragover"></a><a name="ondragover"></a>CView::OnDragOver

Wywoływana przez strukturę podczas operacji przeciągania, gdy mysz jest przenoszona nad oknem docelowym upuszczania.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject (1000)*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągane nad miejsce docelowe upuszczania.

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Bieżąca pozycja myszy względem obszaru klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość z DROPEFFECT wyliczonego typu, który wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik upuścił obiekt w tej pozycji. Typ upuszczenia często zależy od bieżącego stanu klucza wskazanego przez *dwKeyState*. Standardowe mapowanie państw kluczy do wartości DROPEFFECT jest:

- DROPEFFECT_NONE Nie można upuścić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT Tworzy powiązanie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL Tworzy kopię upuszczonego obiektu.

- DROPEFFECT_MOVE dla MK_ALT Tworzy kopię upuszczonego obiektu i usuwa oryginalny obiekt. Jest to zazwyczaj domyślny efekt upuszczania, gdy widok może zaakceptować obiekt danych.

Aby uzyskać więcej informacji, zobacz przykładowe pojęcia zaawansowane MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślną implementacją jest nic nie robić i zwracać DROPEFFECT_NONE.

Zastądnie tej funkcji, aby przekazać użytkownikowi wizualne informacje zwrotne podczas operacji przeciągania. Ponieważ ta funkcja jest wywoływana w sposób ciągły, każdy kod zawarty w niej powinien być zoptymalizowany w miarę możliwości. Aby uzyskać więcej informacji, zobacz artykuł [OLE przeciąganie i upuszczanie: Implementowanie celu upuszczania](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragscroll

Wywoływane przez platformę przed wywołaniem [OnDragEnter](#ondragenter) lub [OnDragOver,](#ondragover) aby ustalić, czy punkt znajduje się w regionie przewijania.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState (Stan klucza)*<br/>
Zawiera stan kluczy modyfikatora. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Zawiera położenie kursora w pikselach względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Wartość z DROPEFFECT wyliczonego typu, który wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik upuścił obiekt w tej pozycji. Typ spadku zwykle zależy od bieżącego stanu klucza wskazanego przez *dwKeyState*. Standardowe mapowanie państw kluczy do wartości DROPEFFECT jest:

- DROPEFFECT_NONE Nie można upuścić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT Tworzy powiązanie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL Tworzy kopię upuszczonego obiektu.

- DROPEFFECT_MOVE dla MK_ALT Tworzy kopię upuszczonego obiektu i usuwa oryginalny obiekt.

- DROPEFFECT_SCROLL Wskazuje, że operacja przewijania przeciągania ma wystąpić lub występuje w widoku docelowym.

Aby uzyskać więcej informacji, zobacz przykładowe pojęcia zaawansowane MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Zastądnie tej funkcji, jeśli chcesz zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja automatycznie przewija okna, gdy kursor jest przeciągany do domyślnego regionu przewijania wewnątrz obramowania każdego okna. Aby uzyskać więcej informacji, zobacz artykuł [OLE przeciąganie i upuszczanie: Implementowanie celu upuszczania](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondraw"></a><a name="ondraw"></a>CView::OnDraw

Wywoływane przez strukturę do renderowania obrazu dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obrazu dokumentu.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję do wykonywania wyświetlania ekranu, drukowania i podglądu wydruku i przekazuje inny kontekst urządzenia w każdym przypadku. Nie ma implementacji domyślnej.

Aby wyświetlić widok dokumentu, należy zastąpić tę funkcję. Można wykonywać wywołania interfejsu urządzenia graficznego (GDI) przy użyciu obiektu [CDC](../../mfc/reference/cdc-class.md) wskazanego przez parametr *pDC.* Przed rysowaniem można wybrać zasoby GDI, takie jak pióra lub czcionki, w kontekście urządzenia, a następnie usunąć ich usunięcie. Często kod rysunku może być niezależny od urządzenia; oznacza to, że nie wymaga informacji o tym, jaki typ urządzenia wyświetla obraz.

Aby zoptymalizować rysunek, należy wywołać funkcję elementu członkowskiego [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) kontekstu urządzenia, aby dowiedzieć się, czy dany prostokąt zostanie narysowany. Jeśli chcesz odróżnić zwykły ekran ekranowy od drukowania, należy wywołać funkcję elementu członkowskiego [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) w kontekście urządzenia.

## <a name="cviewondrop"></a><a name="ondrop"></a>CView::OnDrop

Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pomocą prawidłowego obiektu upuszczania.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

'pDataObject* Wskazuje na [COleDataObject,](../../mfc/reference/coledataobject-class.md) który jest upuszczony do punktu docelowego upuszczania.

*dropEffect (efekt upuszczania)*<br/>
Efekt upuszczania, o który poprosił użytkownik.

- DROPEFFECT_COPY Tworzy kopię obiektu danych, który jest usuwany.

- DROPEFFECT_MOVE Przenosi obiekt danych do bieżącej lokalizacji myszy.

- DROPEFFECT_LINK Tworzy łącze między obiektem danych a jego serwerem.

*Punkt*<br/>
Bieżąca pozycja myszy względem obszaru klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli spadek był udany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi i zwraca FALSE.

Zastąpość tę funkcję, aby zaimplementować efekt upuszczenia OLE do obszaru klienta widoku. Obiekt danych można zbadać za pomocą *pDataObject* dla formatów danych schowka i danych porzuconych w określonym punkcie.

> [!NOTE]
> Struktura nie wywołuje tej funkcji, jeśli istnieje zastąpienie [OnDropEx](#ondropex) w tej klasie widoku.

## <a name="cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx

Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pomocą prawidłowego obiektu upuszczania.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject (1000)*<br/>
Wskazuje [na COleDataObject,](../../mfc/reference/coledataobject-class.md) który jest upuszczony do docelowego upuszczania.

*dropDefault (niem.*<br/>
Efekt, który użytkownik wybrał dla domyślnej operacji upuszczania na podstawie bieżącego stanu klucza. Może to być DROPEFFECT_NONE. Efekty upuszczania są omówione w sekcji Uwagi.

*lista dropList*<br/>
Lista efektów upuszczania, które obsługuje źródło upuszczania. Wartości efektu upuszczania można łączyć za pomocą operacji bitowej OR **(&#124;). ** Efekty upuszczania są omówione w sekcji Uwagi.

*Punkt*<br/>
Bieżąca pozycja myszy względem obszaru klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania wynikający z próby upuszczania w lokalizacji określonej przez *punkt*. Musi to być jedna z wartości wskazanych przez *dropEffectList*. Efekty upuszczania są omówione w sekcji Uwagi.

### <a name="remarks"></a>Uwagi

Domyślna implementacja jest nic nie robić i zwracać wartość manekina ( -1 ), aby wskazać, że struktura powinna wywołać [OnDrop](#ondrop) obsługi.

Zastąp tę funkcję, aby zaimplementować efekt przeciągania i upuszczania prawego przycisku myszy. Naciśnięcie i upuszczenie prawego przycisku myszy zazwyczaj wyświetla menu opcji po zwolnieniu prawego przycisku myszy.

Zastąpienie `OnDropEx` powinno kwerendy dla prawego przycisku myszy. Można wywołać [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) lub przechowywać stan prawego przycisku myszy z obsługi [OnDragEnter.](#ondragenter)

- Jeśli prawy przycisk myszy jest w dół, zastąpienie powinno wyświetlać menu podręczne, które oferuje obsługę efektów upuszczania przez źródło upuszczania.

  - Sprawdź *dropList,* aby określić efekty upuszczania obsługiwane przez źródło upuszczania. Włącz tylko te akcje w menu podręcznym.

  - Użyj [SetMenuDefaultItem,](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) aby ustawić domyślną akcję opartą na *dropDefault*.

  - Na koniec należy podjąć akcję wskazaną przez wybór użytkownika z menu podręcznego.

- Jeśli prawy przycisk myszy nie jest w dół, zastąpienie należy przetworzyć to jako standardowe żądanie upuszczania. Użyj efektu upuszczania określonego w *upuszczaniuDefault*. Alternatywnie zastąpienie może zwrócić wartość manekina ( -1 ), `OnDrop` aby wskazać, że będzie obsługiwać tę operację upuszczania.

Użyj *pDataObject* do `COleDataObject` zbadania formatu danych schowka i danych porzuconych w określonym punkcie.

Efekty upuszczania opisują akcję skojarzoną z operacją upuszczania. Zobacz następującą listę efektów upuszczania:

- DROPEFFECT_NONE Kropla nie będzie dozwolona.

- DROPEFFECT_COPY zostanie wykonana operacja kopiowania.

- DROPEFFECT_MOVE zostanie wykonana operacja przenoszenia.

- DROPEFFECT_LINK zostanie ustanowione łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Wskazuje, że operacja przewijania przeciągania ma wystąpić lub występuje w miejscu docelowym.

Aby uzyskać więcej informacji na temat ustawiania domyślnego polecenia menu, zobacz [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) w zestawie Windows SDK i [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) w tym woluminie.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>CView::OnEndPrinting

Wywoływana przez strukturę po wydrukowaniu lub wyświetleniu podglądu dokumentu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia drukarki.

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) opisującą bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby zwolnić wszystkie zasoby GDI przydzielone w funkcji elementu członkowskiego [OnBeginPrinting.](#onbeginprinting)

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview

Wywoływana przez strukturę, gdy użytkownik kończy pracę w trybie podglądu wydruku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia drukarki.

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) opisującą bieżące zadanie drukowania.

*Punkt*<br/>
Określa punkt na stronie, który był ostatnio wyświetlany w trybie podglądu.

*pWidok*<br/>
Wskazuje obiekt widoku używany do wyświetlania podglądu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję elementu członkowskiego [OnEndPrinting](#onendprinting) i przywraca okno ramki głównej do stanu, w jaki był przed rozpoczęciem podglądu wydruku. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie po zakończeniu trybu podglądu. Na przykład, jeśli chcesz zachować pozycję użytkownika w dokumencie podczas przełączania z trybu podglądu do normalnego trybu wyświetlania, `CPrintInfo` można przewinąć do pozycji opisanej przez parametr *punktu* i `m_nCurPage` element członkowski struktury, na który wskazuje parametr *pInfo.*

Zawsze wywołać wersję `OnEndPrintPreview` klasy podstawowej z zastąpienia, zazwyczaj na końcu funkcji.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView::OnInitialUpdate

Wywoływane przez ramy po widoku jest najpierw dołączony do dokumentu, ale przed widok jest początkowo wyświetlany.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję elementu członkowskiego [OnUpdate](#onupdate) bez informacji o wskazówkach (czyli przy użyciu wartości domyślnych 0 dla parametru *lHint* i NULL dla parametru *pHint).* Zastąd w tej funkcji należy wykonać jednorazową inicjalizację, która wymaga informacji o dokumencie. Na przykład jeśli aplikacja ma dokumenty o stałym rozmiarze, można użyć tej funkcji, aby zainicjować limity przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennym rozmiarze, użyj [OnUpdate,](#onupdate) aby zaktualizować limity przewijania za każdym razem, gdy dokument się zmienia.

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC

Wywoływana przez strukturę przed [OnDraw](#ondraw) funkcji elementu członkowskiego jest wywoływana do wyświetlania na ekranie i przed [OnPrint](#onprint) funkcji elementu członkowskiego jest wywoływana dla każdej strony podczas drukowania lub podglądu wydruku.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obrazu dokumentu.

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) która opisuje `OnPrepareDC` bieżące zadanie drukowania, jeśli jest wywoływana do drukowania lub podglądu wydruku; element `m_nCurPage` członkowski określa stronę, która ma zostać wydrukowana. Ten parametr jest `OnPrepareDC` NULL, jeśli jest wywoływana do wyświetlania ekranu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi, jeśli funkcja jest wywoływana do wyświetlania ekranu. Jednak ta funkcja jest zastępowana w klasach pochodnych, takich jak [CScrollView](../../mfc/reference/cscrollview-class.md), aby dostosować atrybuty kontekstu urządzenia; w związku z tym należy zawsze wywołać implementacji klasy podstawowej na początku zastąpienia.

Jeśli funkcja jest wywoływana do drukowania, domyślna implementacja sprawdza informacje o stronie przechowywane w parametrze *pInfo.* Jeśli długość dokumentu nie została określona, przyjmuje założenie, `OnPrepareDC` że dokument ma długość jednej strony i zatrzymuje pętlę drukowania po wydrukowaniu jednej strony. Funkcja zatrzymuje pętlę drukowania, ustawiając `m_bContinuePrinting` element członkowski struktury na FAŁSZ.

Zastąp `OnPrepareDC` z następujących powodów:

- Aby dostosować atrybuty kontekstu urządzenia zgodnie z potrzebami dla określonej strony. Na przykład jeśli trzeba ustawić tryb mapowania lub inne cechy kontekstu urządzenia, wykonaj tę funkcję.

- Aby wykonać podział na strony w czasie drukowania. Zwykle można określić długość dokumentu podczas rozpoczynania drukowania, używając funkcji elementu członkowskiego [OnPreparePrinting.](#onprepareprinting) Jeśli jednak nie wiadomo z wyprzedzeniem, jak długo trwa dokument (na przykład podczas drukowania nieokreślonej liczby rekordów z bazy danych), należy zastąpić, `OnPrepareDC` aby przetestować koniec dokumentu podczas drukowania. Jeśli nie ma więcej dokumentu do wydrukowania, `m_bContinuePrinting` ustaw `CPrintInfo` element członkowski struktury na FAŁSZ.

- Aby wysłać kody uszkowe do drukarki na podstawie strony po stronie. Aby wysłać `OnPrepareDC`kody `Escape` ucieczki z , wywołać funkcję elementu członkowskiego parametru *pDC.*

Wywołanie wersji klasy `OnPrepareDC` podstawowej na początku zastąpienia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>CView::OnPreparePrinting

Wywoływane przez strukturę przed wydrukowaniem lub podglądem dokumentu.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pinfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) opisującą bieżące zadanie drukowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, aby rozpocząć drukowanie; 0, jeśli zadanie drukowania zostało anulowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi.

Aby włączyć drukowanie i podgląd, należy zastąpić tę funkcję. Wywołanie funkcji elementu członkowskiego [DoPreparePrinting,](#doprepareprinting) przekazując go parametr *pInfo,* a następnie zwraca jego wartość zwracaną; `DoPreparePrinting` wyświetla okno dialogowe Drukowanie i tworzy kontekst urządzenia drukarki. Jeśli chcesz zainicjować okno dialogowe Drukowanie z wartościami innymi niż wartości domyślne, przypisz wartości członkom *pInfo*. Na przykład, jeśli znasz długość dokumentu, przekaż tę wartość funkcji elementu członkowskiego [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) *pInfo* przed wywołaniem `DoPreparePrinting`. Ta wartość jest wyświetlana w polu Do: w części Zakres okna dialogowego Drukowanie.

`DoPreparePrinting`nie wyświetla okna dialogowego Drukowanie zadania podglądu. Jeśli chcesz pominąć okno dialogowe Drukowanie zadania `m_bPreview` drukowania, sprawdź, czy element członkowski *pInfo* jest FALSE, a następnie ustaw wartość TRUE przed przekazaniem go do `DoPreparePrinting`; zresetować go do FALSE.

Jeśli konieczne jest wykonanie inicjalizacji, które wymagają dostępu do obiektu reprezentującego `CDC` kontekst urządzenia drukarki (na przykład, jeśli musisz znać `OnBeginPrinting` rozmiar strony przed określeniem długości dokumentu), należy zastąpić funkcję elementu członkowskiego.

Jeśli chcesz ustawić wartość `m_nNumPreviewPages` lub `m_strPageDesc` członków parametru *pInfo,* zrób `DoPreparePrinting`to po wywołaniu . Funkcja `DoPreparePrinting` elementu `m_nNumPreviewPages` członkowskiego ustawia wartość znalezioną w aplikacji . INI i `m_strPageDesc` ustawia jego wartość domyślną.

### <a name="example"></a>Przykład

  Zastąd `OnPreparePrinting` `DoPreparePrinting` w stosunku do zastąpienia i wywołania, aby struktura wyświetlała okno dialogowe Drukowanie i tworzyła kontroler domeny drukarki.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Jeśli wiesz, ile stron zawiera dokument, ustaw `OnPreparePrinting` maksymalną stronę przed wywołaniem `DoPreparePrinting`. Struktura wyświetli maksymalny numer strony w polu "do" okna dialogowego Drukowanie.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>CView::OnPrint

Wywoływane przez strukturę do drukowania lub podglądu strony dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia drukarki.

*Pinfo*<br/>
Wskazuje strukturę opisującą `CPrintInfo` bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Dla każdej strony są drukowane, ramach wywołuje tę funkcję natychmiast po wywołaniu [OnPrepareDC](#onpreparedc) funkcji elementu członkowskiego. Strona drukowana jest określona `m_nCurPage` przez członka struktury [CPrintInfo,](../../mfc/reference/cprintinfo-structure.md) na którą wskazuje *pInfo.* Domyślna implementacja wywołuje [ondraw](#ondraw) funkcji elementu członkowskiego i przekazuje go kontekst urządzenia drukarki.

Zastąp tę funkcję z następujących powodów:

- Aby zezwolić na drukowanie dokumentów wielostronicowych. Renderuj tylko część dokumentu odpowiadającą aktualnie drukowanej stronie. Jeśli używasz `OnDraw` do renderowania, można dostosować początek rzutni tak, aby wydrukować tylko odpowiednią część dokumentu.

- Aby wydrukowany obraz wyglądał inaczej niż obraz na ekranie (to jest, jeśli aplikacja nie jest WYSIWYG). Zamiast przekazywania kontekstu urządzenia `OnDraw`drukarki do programu , użyj kontekstu urządzenia, aby renderować obraz przy użyciu atrybutów, które nie są wyświetlane na ekranie.

   Jeśli potrzebujesz zasobów GDI do drukowania, których nie używasz do wyświetlania ekranu, zaznacz je w kontekście urządzenia przed rysowaniem i usuń ich później. Te zasoby GDI powinny być przydzielane w [OnBeginPrinting](#onbeginprinting) i wydane w [OnEndPrinting](#onendprinting).

- Aby zaimplementować nagłówki lub stopki. Renderowania można `OnDraw` nadal używać, ograniczając obszar, na którym można drukować.

Należy zauważyć, że `m_rectDraw` element członkowski parametru *pInfo* opisuje obszar drukowania strony w jednostkach logicznych.

Nie należy `OnPrepareDC` dzwonić w `OnPrint`przesłonięcia ; framework wywołuje `OnPrepareDC` automatycznie przed `OnPrint`wywołaniem .

### <a name="example"></a>Przykład

Poniżej przedstawiono szkielet dla `OnPrint` funkcji zastąpione:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Inny przykład zobacz [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

## <a name="cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll

Wywoływane przez strukturę, aby ustalić, czy przewijanie jest możliwe.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode (Kod dostępu do NScrollCode)*<br/>
Kod kreskowy przewijania, który wskazuje żądanie przewijania użytkownika. Ten parametr składa się z dwóch części: bajtu niskiego rzędu, który określa typ przewijania występującego w poziomie oraz bajtu wysokiego rzędu, który określa typ przewijania występującego w pionie:

- SB_BOTTOM Przewiń do dołu.

- SB_LINEDOWN przewija jeden wiersz w dół.

- SB_LINEUP Przewija jedną linię w górę.

- SB_PAGEDOWN przewija jedną stronę w dół.

- SB_PAGEUP przewija jedną stronę w górę.

- SB_THUMBTRACK przeciąga pole przewijania do określonej pozycji. Bieżąca pozycja jest określona w *nPos*.

- SB_TOP Przewija się do góry.

*nPos (właso)*<br/>
Zawiera bieżącą pozycję pola przewijania, jeśli kod kreskowy przewijania jest SB_THUMBTRACK; w przeciwnym razie nie jest używany. W zależności od początkowego zakresu przewijania, *nPos* może być ujemny i powinien być rzutowanie **na int,** jeśli to konieczne.

*Bdoscroll*<br/>
Określa, czy faktycznie należy wykonać określoną akcję przewijania. Jeśli TRUE, następnie przewijanie powinno mieć miejsce; jeśli FALSE, przewijanie nie powinno wystąpić.

### <a name="return-value"></a>Wartość zwracana

Jeśli *bDoScroll* jest TRUE i widok został faktycznie przewinięty, a następnie powrócić nonzero; w przeciwnym razie 0. Jeśli *bDoScroll* jest FALSE, a następnie zwrócić wartość, która zostałaby zwrócona, jeśli *bDoScroll* były PRAWDZIWE, nawet jeśli w rzeczywistości nie wykonać przewijanie.

### <a name="remarks"></a>Uwagi

W jednym przypadku ta funkcja jest wywoływana przez platformę z *bDoScroll* ustawioną na TRUE, gdy widok odbiera komunikat paska przewijania. W takim przypadku należy przewinąć widok. W innym przypadku ta funkcja jest wywoływana z *bDoScroll* ustawiona na FALSE, gdy element OLE jest początkowo przeciągany do regionu automatycznego przewijania celu upuszczania przed przewijaniem faktycznie ma miejsce. W takim przypadku nie należy faktycznie przewijać widoku.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView::OnScrollBy

Wywoływane przez strukturę, gdy użytkownik wyświetla obszar poza bieżącym widokiem dokumentu, przeciągając element OLE względem bieżących obramowań widoku lub manipulując pionowymi lub poziomymi paskami przewijania.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*rozmiarScroll*<br/>
Liczba pikseli przewijanych w poziomie i w pionie.

*Bdoscroll*<br/>
Określa, czy występuje przewijanie widoku. Jeśli TRUE, następnie przewijanie odbywa się; jeśli FALSE, przewijanie nie występuje.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli widok był w stanie przewijać; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W klasach pochodnych ta metoda sprawdza, czy widok jest przewijany w kierunku żądanym przez użytkownika, a następnie aktualizuje nowy region, jeśli to konieczne. Ta funkcja jest automatycznie wywoływana przez [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) do wykonywania rzeczywistego żądania przewijania.

Domyślna implementacja tej metody nie zmienia widoku, ale jeśli nie jest wywoływana, widok nie będzie przewijany w klasie pochodnej. `CScrollView`

Jeśli szerokość lub wysokość dokumentu przekracza 32767 pikseli, przewijanie przeszłości `OnScrollBy` 32767 zakończy się niepowodzeniem, ponieważ jest wywoływana z nieprawidłowym *argumentem sizeScroll.*

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate

Wywoływane przez ramy po zmodyfikowaniu dokumentu widoku; ta funkcja jest wywoływana przez [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) i umożliwia widok, aby zaktualizować jego wyświetlania w celu odzwierciedlenia tych modyfikacji.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pSender (nadawca)*<br/>
Wskazuje widok, który zmodyfikował dokument, lub null, jeśli wszystkie widoki mają zostać zaktualizowane.

*Lhint*<br/>
Zawiera informacje o modyfikacjach.

*Phint*<br/>
Wskazuje obiekt przechowujący informacje o modyfikacjach.

### <a name="remarks"></a>Uwagi

Jest również wywoływana przez domyślną implementację [OnInitialUpdate](#oninitialupdate). Domyślna implementacja unieważnia cały obszar klienta, oznaczając go do malowania po odebraniu następnego WM_PAINT wiadomości. Zastądź tę funkcję, jeśli chcesz zaktualizować tylko te regiony, które mapują zmodyfikowane części dokumentu. Aby to zrobić, należy przekazać informacje o modyfikacjach przy użyciu parametrów wskazówki.

Aby użyć *lHint*, zdefiniuj specjalne wartości wskazówek, zazwyczaj maskę bitową lub typ wyliczony i niech dokument przekaże jedną z tych wartości. Aby użyć *pHint*, wyprowadzić klasę wskazówek z [CObject](../../mfc/reference/cobject-class.md) i dokument przekazać wskaźnik do obiektu podpowiedzi; podczas zastępowania `OnUpdate`, użyj [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) funkcji elementu członkowskiego, aby określić typ czasu wykonywania obiektu hint.

Zazwyczaj nie należy wykonywać żadnego `OnUpdate`rysunku bezpośrednio z pliku . Zamiast tego należy określić prostokąt opisujący we współrzędnych urządzenia obszar, który wymaga aktualizacji; przekazać ten prostokąt do [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Powoduje to, że obraz występuje przy następnym [odebraniu WM_PAINT](/windows/win32/gdi/wm-paint) wiadomości.

Jeśli *lHint* jest 0 i *pHint* jest NULL, dokument wysłał ogólne powiadomienie aktualizacji. Jeśli widok otrzyma ogólne powiadomienie o aktualizacji lub jeśli nie może zdekodować wskazówek, należy unieważnić cały obszar klienta.

## <a name="see-also"></a>Zobacz też

[Próbka MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)
