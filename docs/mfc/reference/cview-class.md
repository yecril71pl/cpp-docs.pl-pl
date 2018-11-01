---
title: Cview — klasa
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
ms.openlocfilehash: f325423c940df46940d7074c599eb8e502e90586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50669082"
---
# <a name="cview-class"></a>Cview — klasa

Oferuje podstawowe funkcje dla klas widoków zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView::CView](#cview)|Konstruuje `CView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Wyświetla okno dialogowe Drukuj i tworzy kontekst urządzenia drukarki; Wywołaj podczas zastępowania `OnPreparePrinting` funkcja elementu członkowskiego.|
|[CView::GetDocument](#getdocument)|Zwraca dokument skojarzony z widokiem.|
|[CView::IsSelected](#isselected)|Sprawdza, czy zaznaczono element dokumentu. Wymagane do obsługi.|
|[CView::OnDragEnter](#ondragenter)|Wywołuje się, gdy element jest najpierw przeciągnięte do regionu przeciągania i upuszczania w widoku.|
|[CView::OnDragLeave](#ondragleave)|Wywołuje się, gdy przeciąganego elementu powoduje, że region przeciągania i upuszczania w widoku.|
|[CView::OnDragOver](#ondragover)|Wywołuje się, gdy element zostanie przeciągnięty nad obszar przeciągania i upuszczania w widoku.|
|[CView::OnDragScroll](#ondragscroll)|Wywołuje się, by określić czy kursor jest przeciągany w regionie przewijania, okna.|
|[CView::OnDrop](#ondrop)|Wywołuje się, gdy element został porzucony w tym regionie przeciągania i upuszczania, widok domyślny program obsługi.|
|[CView::OnDropEx](#ondropex)|Wywołuje się, gdy element został porzucony, do obszaru przeciągania i upuszczania w widoku, podstawowy program obsługi.|
|[CView::OnInitialUpdate](#oninitialupdate)|Metoda wywoływana po widoku najpierw jest dołączony do dokumentu.|
|[CView::OnPrepareDC](#onpreparedc)|Wywołuje się przed `OnDraw` funkcja członkowska jest wywoływana do wyświetlania na ekranie lub `OnPrint` funkcja członkowska jest wywoływana dla podglądu wydruku lub drukowania.|
|[CView::OnScroll](#onscroll)|Metoda wywoływana podczas przeciągania elementów OLE poza granice tego widoku.|
|[CView::OnScrollBy](#onscrollby)|Wywołuje się, gdy jest przewijane widoku zawierającego aktywnych elementów OLE w miejscu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Wywołuje się, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.|
|[CView::OnActivateView](#onactivateview)|Wywołuje się, gdy widok jest aktywowany.|
|[CView::OnBeginPrinting](#onbeginprinting)|Wywołuje się, gdy rozpoczyna się zadanie drukowania; należy przesłonić ten element, aby przydzielić zasoby interface (GDI) urządzenia grafiki.|
|[CView::OnDraw](#ondraw)|Wywołuje się, by renderować obraz wyświetlanie na ekranie, drukowania i podglądu wydruku w dokumencie. Implementacja jest wymagana.|
|[CView::OnEndPrinting](#onendprinting)|Wywołuje się, gdy kończy się zadania drukowania; należy przesłonić, aby cofnąć alokacji zasobów GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Wywołuje się, gdy tryb podglądu jest został zakończony.|
|[CView::OnPreparePrinting](#onprepareprinting)|Metoda wywoływana przed dokumentu jest wydrukiem lub podglądem; należy przesłonić, aby zainicjować okno dialogowe drukowania.|
|[CView::OnPrint](#onprint)|Wywołuje się, by wydrukować lub podejrzeć stronę dokumentu.|
|[CView::OnUpdate](#onupdate)|Wywołuje się, by powiadomić widok, w którym jego dokument został zmodyfikowany.|

## <a name="remarks"></a>Uwagi

Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem i użytkownikiem: widok renderuje obraz dokumentu na ekranie lub drukarki i interpretuje dane wejściowe użytkownika jako operacje na dokumencie.

Widok jest elementem podrzędnym okna ramki. Więcej niż jeden widok można udostępniać okno ramowe, tak jak w przypadku okna rozdzielacza. Została ustanowiona relacja między klasa widoku, klasę okna ramowego i klasy dokumentu `CDocTemplate` obiektu. Gdy użytkownik otwiera nowe okno lub dzieli istniejące jedną platformę tworzy nowy widok i dołącza go do dokumentu.

Widok może zostać dołączony do tylko jeden dokument, ale dokumentu może mieć wiele widoków, które dołączono do niego tylko raz — na przykład, jeśli dokument jest wyświetlany w oknie podziału lub w wielu okien podrzędnych w wielu aplikacji interfejsu (MDI) dokumentu. Aplikacja może obsługiwać różnych typów widoków dla typu danego dokumentu; na przykład edytorze tekstów może dostarczyć, zarówno w widok całego tekstu dokumentu, jak i w widoku konspektu, który pokazuje tylko nagłówki sekcji. Te różne typy widoków można umieścić w osobnych okna ramowe lub oddzielne okienka jednej ramki okna, korzystając z okna rozdzielacza.

Widok może być odpowiedzialna za obsługę kilku różnych typów danych wejściowych, takich jak dane wejściowe z klawiatury, myszy dane wejściowe i dane wejściowe za pomocą przeciągania i upuszczania, a także polecenia menu i paski narzędzi, paski przewijania. Widok otrzyma poleceń przesyłany dalej przez jego ramki okna. Jeśli widok nie obsługuje danego polecenia, przekazuje polecenie, aby jego skojarzonego dokumentu. Podobnie jak wszystkie obiekty docelowe poleceń widok obsługuje komunikaty za pośrednictwem mapy komunikatów.

Odpowiada widok do wyświetlania i modyfikowania danych dokumentu, ale nie na zapisanie go. Dokument zawiera widok niezbędne szczegóły dotyczące jej danych. Można pozwolić, aby dostęp widok dokumentu elementy członkowskie danych bezpośrednio lub może zapewnić funkcji składowych w klasie dokumentów dla klasy widoku do wywołania.

Po zmianie danych dokumentu widoku odpowiedzialny za zmiany zwykle wywołuje [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkcji dla dokumentu, który powiadamia inne widoki, wywołując `OnUpdate` funkcję członkowską Każdy. Domyślna implementacja klasy `OnUpdate` unieważnia widok całego obszaru klienta. Można zastąpić go do unieważnienia tylko tych regionów obszaru klienckiego mapowane zmodyfikowane części dokumentu.

Aby użyć `CView`dziedziczyć po nim klasę i zaimplementować `OnDraw` funkcja elementu członkowskiego, aby wykonać wyświetlanie na ekranie. Można również użyć `OnDraw` przeprowadzić drukowania i podglądu wydruku. Struktura obsługuje drukowania pętli do drukowania i podglądu dokumentu.

Widok obsługi komunikatów paska przewijania za pomocą [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funkcji elementów członkowskich. Można zaimplementować komunikatów paska przewijania w tych funkcji, możesz też `CView` klasy pochodnej [CScrollView](../../mfc/reference/cscrollview-class.md) do obsługi przewijanie za Ciebie.

Oprócz `CScrollView`, biblioteki klas Microsoft Foundation udostępnia dziewięć innych klas pochodzących z `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), widoku, który umożliwia użycie dokumentu - widoku architektury za pomocą drzewa, listy i bogate edycji wzbogaconej.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), widok wyświetlający rekordy bazy danych w kontrolkach okno dialogowe.

- [CEditView](../../mfc/reference/ceditview-class.md), widok, który zapewnia edytorze zwykły tekst wielowierszowy. Możesz użyć `CEditView` obiektu jako formant w okno dialogowe, a także widoku do dokumentu.

- [CFormView](../../mfc/reference/cformview-class.md), przewijany widok, który zawiera formanty okno dialogowe i zależy od zasobu szablonu okna dialogowego.

- [CListView](../../mfc/reference/clistview-class.md), widok, który umożliwia użycie dokumentu - widoku architektury za pomocą kontrolki listy.

- [CRecordView](../../mfc/reference/crecordview-class.md), widok wyświetlający rekordy bazy danych w kontrolkach okno dialogowe.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), widok, który umożliwia użycie dokumentu - widoku architektura zaawansowanej edycji wzbogaconej.

- [CScrollView](../../mfc/reference/cscrollview-class.md), widok, który automatycznie zapewnia obsługę przewijania.

- [CTreeView](../../mfc/reference/ctreeview-class.md), widok, który umożliwia użycie dokumentu - widoku architektury za pomocą kontrolki drzewa.

`CView` Klasa ma również klasy pochodnej, o nazwie `CPreviewView`, używany przez platformę, do wykonania, wyświetlanie podglądu wydruku. Ta klasa obsługuje funkcje unikatowe dla okna podglądu wydruku, takich jak pasek narzędzi, jedną lub dwie strony w wersji zapoznawczej i powiększania, który jest powiększając wyświetlanego obrazu. Nie trzeba wywoływać lub przesłonić `CPreviewView`przez funkcje składowe, chyba że chcesz zaimplementować własny interfejs dla podglądu wydruku (na przykład, jeśli chcesz obsługi edycji w trybie podglądu wydruku). Aby uzyskać więcej informacji na temat korzystania z `CView`, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md) i [drukowanie](../../mfc/printing.md). Ponadto zobacz [techniczne 30 Uwaga](../../mfc/tn030-customizing-printing-and-print-preview.md) więcej informacji na temat dostosowywania podglądu wydruku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cview"></a>  CView::CView

Konstruuje `CView` obiektu.

```
CView();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora, gdy stworzono nowe okno ramowe lub okno zostanie podzielona. Zastąp [OnInitialUpdate](#oninitialupdate) funkcji elementu członkowskiego, aby zainicjować widoku, po dołączeniu dokumentu.

##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting

Wywołaj tę funkcję z zastąpienie metody [onprepareprinting —](#onprepareprinting) wywołuje okno dialogowe Drukuj i tworzenie kontekstu urządzenia drukarki.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli można rozpocząć drukowanie lub drukowania (wersja zapoznawcza); 0, jeśli operacja została anulowana.

### <a name="remarks"></a>Uwagi

Zachowanie tej funkcji zależy od tego, czy jest on wywoływana dla podglądu wydruku lub drukowania (określony przez `m_bPreview` członkiem *pInfo* parametru). Jeśli plik zostanie wydrukowany, funkcja wywoła okno dialogowe drukowania przy użyciu wartości w [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która *pInfo* wskazuje; po użytkownik zostało zamknięte okno dialogowe, funkcja tworzy kontekst urządzenia drukarki na podstawie ustawień użytkownika określonego w oknie dialogowym i zwraca ten kontekst urządzenia za pośrednictwem *pInfo* parametru. Używany jest ten kontekst urządzenia spowoduje wydrukowanie dokumentu.

Jeśli plik jest przeglądany, ta funkcja tworzy kontekst urządzenia drukarki przy użyciu bieżących ustawień drukarek; Ten kontekst urządzenia jest używana do symulowania drukarki w wersji zapoznawczej.

##  <a name="getdocument"></a>  CView::GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do dokumentu tego widoku.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CDocument](../../mfc/reference/cdocument-class.md) obiekt skojarzony z widokiem. Wartość NULL, jeśli widok nie jest dołączony do dokumentu.

### <a name="remarks"></a>Uwagi

Dzięki temu można wywoływać funkcje składowe dokumentu.

##  <a name="isselected"></a>  CView::IsSelected

Metoda wywoływana przez platformę, by sprawdzić, czy zaznaczono element określonego dokumentu.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskazuje element dokumentu poddawana testom.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element określony dokument jest wybrany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja zwraca wartość FALSE. Przesłonić tę funkcję, w przypadku wdrażania przy użyciu wybór [CDocItem](../../mfc/reference/cdocitem-class.md) obiektów. Musisz przesłonić tę funkcję, jeśli widok zawiera elementy OLE.

##  <a name="onactivateframe"></a>  CView::OnActivateFrame

Wywoływane przez platformę, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nInformacje*<br/>
Określa, czy okno ramowe jest aktywowane lub dezaktywowane. Może to być jedna z następujących wartości:

- Trwa dezaktywowanie WA_INACTIVE ramki okna.

- Kliknij WA_ACTIVE, które w oknie ramki jest aktywowane przez niektóre metody innej niż myszy (np. przy użyciu interfejsu klawiatury, aby wybrać okno).

- Trwa aktywowanie WA_CLICKACTIVE okno ramowe przez kliknięcie myszą

*pFrameWnd*<br/>
Wskaźnik do okna ramki, który ma być aktywowany.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego należy zastąpić, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe skojarzony widok jest aktywowane lub dezaktywowane. Na przykład [CFormView](../../mfc/reference/cformview-class.md) wykonuje to zastąpienie, zapisuje i przywraca formant, który jest ustawiony fokus.

##  <a name="onactivateview"></a>  CView::OnActivateView

Wywoływane przez platformę, gdy widok jest aktywowane lub dezaktywowane.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Wskazuje, czy widok jest aktywowane lub dezaktywowane.

*pActivateView*<br/>
Wskazuje obiekt widoku, który jest aktywowany.

*pDeactiveView*<br/>
Wskazuje obiekt widoku, który jest dezaktywowany.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, ustawia fokus do widoku aktywowany. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, jeśli widok jest aktywowane lub dezaktywowane. Na przykład, jeśli chcesz zapewnić specjalne podpowiedzi wizualne, które odróżnia widok aktywny od nieaktywne widoki możesz zbada *bActivate* parametru i odpowiednio zaktualizować wygląd tego widoku.

*PActivateView* i *pDeactiveView* parametrów polecenie tego samego widoku, jeśli aktywowaniu aplikacji głównej ramki okna bez zmian w bieżącym widokiem — na przykład, jeśli fokus jest. przeniesione z innej aplikacji do tego jednego, a nie z jeden widok do innej aplikacji lub podczas przełączania między oknami podrzędnymi MDI. Dzięki temu widok, który chcesz ponownie weź pod uwagę jego palety, w razie potrzeby.

Parametry te różnią się po [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) jest wywoływana z widoku, który różni się od co [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) zwróci. Najczęściej dzieje się za pomocą okna podziału.

##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting

Wywoływane przez platformę na początku zadanie podglądu wydruku lub drukowania po `OnPreparePrinting` została wywołana.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Należy przesłonić tę funkcję, aby przydzielić wszelkie GDI zasoby, takie jak pióra lub czcionek, wymagane specjalnie na potrzeby drukowania. Wybierz obiekty GDI w kontekście urządzenia z poziomu [OnPrint](#onprint) funkcja elementu członkowskiego dla każdej strony, który używa tych. Jeśli używasz tego samego obiektu widoku do wykonywania wyświetlanie na ekranie i drukowania, użyj oddzielnych zmiennych dla zasobów GDI wymaganych na każdym ekranie; Dzięki temu można zaktualizować ekran podczas drukowania.

Ta funkcja umożliwia również wykonać inicjowania, które są zależne od właściwości kontekstu urządzenia drukarki. Na przykład liczba stron potrzebne spowoduje wydrukowanie dokumentu może zależeć na temat ustawień, które użytkownik określił w oknie dialogowym drukowania (takie jak długość strony). W takiej sytuacji nie można określić długość dokumentu w [onprepareprinting —](#onprepareprinting) funkcja elementu członkowskiego, w którym będzie zwykle zrobisz; należy poczekać, aż kontekst urządzenia drukarki została utworzona na podstawie ustawień okno dialogowe. [Onbeginprinting —](#onbeginprinting) to pierwsza funkcja możliwym do zastąpienia, który zapewnia dostęp do [CDC](../../mfc/reference/cdc-class.md) obiekt reprezentujący kontekstu urządzenia drukarki, możesz więc ustawić długość dokumentu z tej funkcji. Należy pamiętać, że jeśli długość dokumentu nie jest określona przez ten czas, pasek przewijania nie jest wyświetlany podczas generowania podglądu wydruku.

##  <a name="ondragenter"></a>  CView::OnDragEnter

Wywoływane przez platformę, gdy wskaźnik myszy po raz pierwszy najedzie regionu bez przewijania, okna docelowego upuszczania.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciąganie obszar upuszczania widoku.

*dwKeyState*<br/>
Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Bieżącego położenia kursora myszy względem pola klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, która może wystąpić, jeśli użytkownik usunął obiekt, w tym miejscu. Typ listy zależy zwykle od bieżącego stanu klucza wskazywanym przez *dwKeyState*. Standardowa mapowanie Director DROPEFFECT wartości to:

- Nie można porzucić DROPEFFECT_NONE obiektu danych, w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem i jego serwera.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usunięcie oryginalnego obiektu. Zazwyczaj jest to domyślny efekt listy, jeśli widok może zaakceptować tego obiektu danych.

Aby uzyskać więcej informacji, zobacz próbce zaawansowanych koncepcji MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślna implementacja to nic nie rób i powrót DROPEFFECT_NONE.

Przesłonić tę funkcję, aby przygotować się do przyszłych wywołań [ondragover —](#ondragover) funkcja elementu członkowskiego. Wszystkie dane wymagane od obiektu danych powinny zostać pobrane w tej chwili do późniejszego użycia z `OnDragOver` funkcja elementu członkowskiego. Widok również powinien zostać zaktualizowany w tej chwili, aby przesłać opinię visual użytkownika. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragleave"></a>  CView::OnDragLeave

Wywoływane przez platformę podczas operacji przeciągania po przeniesieniu poza właściwy obszar upuszczania myszy dla tego okna.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Uwagi

Przesłonić tę funkcję, jeśli bieżący widok musi oczyścić wszelkich akcjach podjętych podczas [ondragenter —](#ondragenter) lub [ondragover —](#ondragover) wywołań, takich jak usuwanie wszelkie informacje i opinie użytkowników visual, gdy obiekt został przeciągnięty i porzucić .

##  <a name="ondragover"></a>  CView::OnDragOver

Wywoływane przez platformę podczas operacji przeciągania, gdy wskaźnik myszy zostanie przesunięty nad oknem docelowego upuszczania.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągany nad element docelowy upuszczania.

*dwKeyState*<br/>
Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Bieżące położenie myszy względem pola klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, która może wystąpić, jeśli użytkownik usunął obiekt, w tym miejscu. Typ listy często zależy od bieżącego stanu klucza wskazane przez *dwKeyState*. Standardowa mapowanie Director DROPEFFECT wartości to:

- Nie można porzucić DROPEFFECT_NONE obiektu danych, w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem i jego serwera.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usunięcie oryginalnego obiektu. Zazwyczaj jest to domyślny efekt listy, jeśli widok może zaakceptować obiekt danych.

Aby uzyskać więcej informacji, zobacz próbce zaawansowanych koncepcji MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślna implementacja to nic nie rób i powrót DROPEFFECT_NONE.

Należy przesłonić tę funkcję, aby dać wizualną opinię użytkownika podczas operacji przeciągania. Ponieważ ta funkcja jest wywoływana w sposób ciągły, każdy kod w nim zawarte optymalizacji możliwie. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragscroll"></a>  CView::OnDragScroll

Metoda wywoływana przez platformę przed wywołaniem [ondragenter —](#ondragenter) lub [ondragover —](#ondragover) do określenia, czy punkt znajduje się w regionie przewijania.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState*<br/>
Zawiera stan klawisze modyfikujące. Jest to kombinacja pojawiły się następujące: MK_CONTROL, MK_SHIFT, MK_ALT MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*Punkt*<br/>
Zawiera lokalizacji kursora, w pikselach, względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, która może wystąpić, jeśli użytkownik usunął obiekt, w tym miejscu. Typ listy zależy zwykle od bieżącego stanu klucza wskazywanym przez *dwKeyState*. Standardowa mapowanie Director DROPEFFECT wartości to:

- Nie można porzucić DROPEFFECT_NONE obiektu danych, w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem i jego serwera.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usunięcie oryginalnego obiektu.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągania może nastąpić lub odbywa się w widok elementu docelowego.

Aby uzyskać więcej informacji, zobacz próbce zaawansowanych koncepcji MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja automatycznie przewija systemu windows, gdy kursor jest przeciągany w domyślnym regionie przewijania wewnątrz obramowania każde okno. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondraw"></a>  CView::OnDraw

Metoda wywoływana przez platformę, by renderować obraz dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia, które ma być używany do renderowania obrazu dokumentu.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję, aby wykonać wyświetlanie na ekranie, drukowania i podglądu wydruku i przekazuje kontekst innego urządzenia w każdym przypadku. Brak implementacji domyślnej.

Musisz przesłonić tę funkcję, aby wyświetlić dokument. Wykonywać wywołania interface (GDI) urządzenia grafiki przy użyciu [CDC](../../mfc/reference/cdc-class.md) obiekt wskazywany przez *kontrolera pDC* parametru. Można wybrać zasoby interfejsu GDI, takie jak czcionki, lub pióra do kontekstu urządzenia przed rysowaniem i usuń zaznaczenie opcji je później. Często kod rysowania może być niezależny od urządzenia; oznacza to nie wymaga informacji o rodzaju urządzenia jest wyświetlany obraz.

Aby zoptymalizować rysowania, należy wywołać [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) funkcji składowej typu kontekstu urządzenia, aby dowiedzieć się, będą rysowane danego prostokąta. Jeśli potrzebujesz rozróżnienie między normalnym ekranu i drukowania, wywołaj [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) funkcji składowej typu kontekstu urządzenia.

##  <a name="ondrop"></a>  CView::OnDrop

Wywoływane przez platformę, gdy użytkownik zwolni obiektu danych za pośrednictwem prawidłowe miejsca docelowego.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

"pDataObject * wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) , są przenoszone do miejsca docelowego.

*dropEffect*<br/>
Efekt listy, który użytkownik zgłosił żądanie.

- DROPEFFECT_COPY tworzy kopię obiektu danych porzucana.

- DROPEFFECT_MOVE przenosi obiekt danych w bieżącym położeniu wskaźnika myszy.

- DROPEFFECT_LINK tworzy łącze między obiektu danych, a jego serwerem.

*Punkt*<br/>
Bieżące położenie myszy względem pola klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli spadek powiodła się. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi i zwraca wartość FALSE.

Należy przesłonić tę funkcję, aby zaimplementować efekt upuszczaniu OLE do obszaru klienckiego widoku. Obiekt danych może być badane za pośrednictwem *pDataObject* dla danych ze Schowka formatów i danych usunięte w określonym momencie.

> [!NOTE]
>  Struktura nie Wywołaj tę funkcję, jeśli zastąpienie [ondropex —](#ondropex) w tej klasie widoku.

##  <a name="ondropex"></a>  CView::OnDropEx

Wywoływane przez platformę, gdy użytkownik zwolni obiektu danych za pośrednictwem prawidłowe miejsca docelowego.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) , są przenoszone do miejsca docelowego.

*dropDefault*<br/>
Wpływ, jaki użytkownik wybrał dla operacji listy domyślne na podstawie bieżącego stanu klucza. Może to być DROPEFFECT_NONE. Efekty listy zostały omówione w sekcji uwag.

*listy rozwijanej*<br/>
Lista efekty listy, które obsługuje miejsca źródłowego. Wartości efekt listy można łączyć, używając bitowe OR ( **&#124;**) operacji. Efekty listy zostały omówione w sekcji uwag.

*Punkt*<br/>
Bieżące położenie myszy względem pola klienta widoku.

### <a name="return-value"></a>Wartość zwracana

Efekt listy, który jest wynikiem próby porzucenia w lokalizacji określonej przez *punktu*. Musi to być jedna z wartości wskazywane przez *dropEffectList*. Efekty listy zostały omówione w sekcji uwag.

### <a name="remarks"></a>Uwagi

Domyślna implementacja jest nic nie rób i zwracać wartości (-1) aby wskazać, że struktura powinny wywoływać [OnDrop](#ondrop) programu obsługi.

Należy przesłonić tę funkcję, aby zaimplementować efekt prawym przyciskiem myszy przeciągania i upuszczania. Prawym przyciskiem myszy, przeciągnij i upuść zwykle wyświetla menu opcji po zwolnieniu prawego przycisku myszy.

Zastąpienie metody `OnDropEx` należy szukać prawego przycisku myszy. Możesz wywołać [GetKeyState](https://msdn.microsoft.com/library/windows/desktop/ms646301) ani nie przechowują stanu prawym przyciskiem myszy z Twojej [ondragenter —](#ondragenter) programu obsługi.

- Jeśli prawy przycisk myszy jest wciśnięty, przesłonięcia powinien być wyświetlany w menu podręczne, która oferuje obsługę efekty listy według miejsca źródłowego.

   - Sprawdź *listy rozwijanej* na ustalenie efektów listy obsługiwanych przez źródło porzucenia. Włącz tylko te akcje w menu podręcznym.

   - Użyj [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) można ustawić domyślną akcję na podstawie *dropDefault*.

   - Na koniec podjąć działania oznaczane wybór użytkownika w menu podręcznym.

- Jeśli prawego przycisku myszy nie jest w dół, przesłonięcia powinien przetworzyć tę jako żądanie porzucenia standardowych. Za pomocą efektu docelowej, określone w *dropDefault*. Alternatywnie przesłonięcia może zwracać wartości (-1) z informacją, że `OnDrop` będzie obsługiwać tej operacji listy.

Użyj *pDataObject* zbadanie `COleDataObject` dla danych ze Schowka format i danych usunięte w określonym momencie.

Efekty listy opisują akcję skojarzoną z operacja przeciągania. Przejrzyj następującą listę upuszczania efektów:

- DROPEFFECT_NONE zrzutu będzie niedozwolone.

- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.

- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.

- Czy można nawiązać DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.

- DROPEFFECT_SCROLL wskazuje, że operacji przeciągania przewijania może nastąpić lub odbywa się w elemencie docelowym.

Aby uzyskać więcej informacji na temat ustawiania domyślnego polecenia menu, zobacz [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) w zestawie Windows SDK i [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) w tym woluminie.

##  <a name="onendprinting"></a>  CView::OnEndPrinting

Wywoływane przez platformę po wydrukowaniu lub podglądzie dokumentu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Przesłonić tę funkcję, aby zwolnić zasobów GDI przydzielonych w [onbeginprinting —](#onbeginprinting) funkcja elementu członkowskiego.

##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview

Wywoływane przez platformę, gdy użytkownik opuszcza tryb podglądu wydruku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania.

*Punkt*<br/>
Określa punkt na stronie, która została ostatnio wyświetlane w wersji zapoznawczej.

*pView*<br/>
Wskazuje obiekt widoku używany do podglądu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja wywołuje [onendprinting —](#onendprinting) funkcja elementu członkowskiego i przywraca rozpoczęcia ramką głównego okna do stanu sprzed podglądu wydruku. Należy przesłonić tę funkcję, aby wykonać specjalnego przetwarzania, jeśli tryb podglądu, zostanie zakończony. Na przykład, jeśli chcesz zachować pozycji użytkownika w dokumencie, podczas przełączania do trybu normalnego wyświetlania tryb podglądu, można przechodzić do pozycji opisanego przez *punktu* parametru i `m_nCurPage` członkiem `CPrintInfo` struktury, która *pInfo* parametr wskazuje.

Zawsze wywołuj klasy bazowej wersję `OnEndPrintPreview` z przesłonięcia, zwykle na końcu funkcji.

##  <a name="oninitialupdate"></a>  CView::OnInitialUpdate

Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja wywołuje [OnUpdate](#onupdate) funkcji składowej bez informacji o wskazówki (oznacza to, używanie domyślnych wartości 0 dla *lHint* parametr i wartość NULL w przypadku  *pHint* parametru). Należy przesłonić tę funkcję, by wykonać jednorazowe inicjowanie, która wymaga informacji o dokumencie. Na przykład jeśli aplikacja zawiera dokumenty o stałym rozmiarze, umożliwia tej funkcji inicjowania widoku limity przewijania w zależności od rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennym rozmiarze, użyj [OnUpdate](#onupdate) można zaktualizować przewijania ogranicza każdym razem, gdy zmiany w dokumencie.

##  <a name="onpreparedc"></a>  CView::OnPrepareDC

Metoda wywoływana przez platformę przed [OnDraw](#ondraw) funkcja członkowska jest wywoływana do wyświetlania na ekranie, a także przed [OnPrint](#onprint) funkcja członkowska jest wywoływana dla każdej strony w trakcie okresu zapoznawczego drukowania lub drukowania.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia, które ma być używany do renderowania obrazu dokumentu.

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania, jeśli `OnPrepareDC` jest wywoływana dla podglądu wydruku lub drukowania; `m_nCurPage` elementu członkowskiego Określa stronę o ma zostać wydrukowany. Ten parametr ma wartość NULL, jeśli `OnPrepareDC` jest wywoływana do wyświetlania na ekranie.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nie działają, jeśli funkcja jest wywoływana do wyświetlania na ekranie. Jednak ta funkcja zostanie zastąpiona w klasach pochodnych, takich jak [CScrollView](../../mfc/reference/cscrollview-class.md), by dostosować atrybuty kontekstu urządzenia; w związku z tym, zawsze powinna wywołać implementację klasy bazowej na początku przesłonięcia.

Jeśli funkcja jest wywoływana związane z drukowaniem, domyślna implementacja sprawdza, czy informacje o stronie przechowywane w *pInfo* parametru. Jeśli nie została określona długość dokumentu, `OnPrepareDC` zakłada dokumentu za długi po jednej stronie i zatrzymuje drukowania pętli, po jednej stronie został wydrukowany. Funkcja przestaje drukowania pętli, ustawiając `m_bContinuePrinting` element członkowski struktury na wartość FALSE.

Zastąp `OnPrepareDC` dla żadnego z następujących powodów:

- By dostosować atrybuty kontekstu urządzenia, zgodnie z potrzebami dla określonej strony. Na przykład jeśli zachodzi potrzeba Ustaw tryb mapowania lub innych właściwości kontekstu urządzenia, to zrobić w tej funkcji.

- Do wykonania wydruku w czasie dzielenia na strony. Zwykle określasz długość dokumentu po rozpoczęciu drukowanie przy użyciu [onprepareprinting —](#onprepareprinting) funkcja elementu członkowskiego. Jednak jeśli nie znasz wcześniej ile dokument (na przykład podczas drukowania nieokreślonej liczby rekordów z bazy danych), Zastąp `OnPrepareDC` do testowania do końca dokumentu, podczas drukowania jest niemożliwe. Gdy istnieje już dokumentu, które mają być drukowane, należy ustawić `m_bContinuePrinting` członkiem `CPrintInfo` struktury na wartość FALSE.

- Aby wysłać kodów wyjścia do drukarki na podstawie strony strona. Do wysyłania kodów wyjścia z `OnPrepareDC`, wywołaj `Escape` funkcji składowej typu *kontrolera pDC* parametru.

Wywołaj klasę bazową wersję `OnPrepareDC` na początku przesłonięcia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting

Wywoływane przez platformę przed dokumentu jest wydrukiem lub podglądem.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, opisująca bieżącego zadania drukowania.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, aby rozpocząć drukowanie; 0, jeśli zostało anulowane zadania drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi.

Należy przesłonić tę funkcję, aby włączyć drukowanie i Podgląd wydruku. Wywołaj [DoPreparePrinting](#doprepareprinting) funkcji członkowskiej, podając mu *pInfo* parametru, a następnie zwracają wartość zwracaną; `DoPreparePrinting` zostanie wyświetlone okno dialogowe drukowania i tworzy kontekst urządzenia drukarki. Jeśli chcesz zainicjować okno dialogowe Drukuj o wartości innej niż wartości domyślne, należy przypisać wartości do elementów członkowskich *pInfo*. Na przykład, jeśli znasz długość dokumentu, należy przekazać wartość do [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) funkcji składowej typu *pInfo* przed wywołaniem `DoPreparePrinting`. Ta wartość jest wyświetlana w polu do: pole w zakresie część okno dialogowe drukowania.

`DoPreparePrinting` Wyświetla okno dialogowe drukowania dla zadania (wersja zapoznawcza). Jeśli chcesz pominąć okno dialogowe drukowania dla zadania drukowania, sprawdź, czy `m_bPreview` członkiem *pInfo* ma wartość FAŁSZ, a następnie ustaw na TRUE przed przekazaniem go do `DoPreparePrinting`; później zresetowanie go na wartość FALSE.

Jeśli musisz wykonać inicjowania, które wymagają dostępu do `CDC` obiekt reprezentujący kontekstu urządzenia drukarki (na przykład, jeśli trzeba znać rozmiar strony przed określeniem długość dokumentu), Zastąp `OnBeginPrinting` elementu członkowskiego Funkcja.

Jeśli chcesz ustawić wartość `m_nNumPreviewPages` lub `m_strPageDesc` członkowie *pInfo* parametr, to zrobić po wywołaniu `DoPreparePrinting`. `DoPreparePrinting` Zestawy funkcji elementów członkowskich `m_nNumPreviewPages` wartość znajdującą się w aplikacji. Plik INI i ustawia `m_strPageDesc` do wartości domyślnej.

### <a name="example"></a>Przykład

  Zastąp `OnPreparePrinting` i wywołać `DoPreparePrinting` z zastąpienie tak, aby w ramach spowoduje wyświetlenie okna dialogowego drukowania i utworzenie drukarki kontrolera domeny dla Ciebie.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Jeśli znasz liczbę stron, dokument zawiera ustawienie maksymalnej strony `OnPreparePrinting` przed wywołaniem `DoPreparePrinting`. Struktura wyświetli numer strony maksymalna w polu "do" okno dialogowe drukowania.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>  CView::OnPrint

Metoda wywoływana przez platformę, by wydrukować lub podejrzeć stronę dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje `CPrintInfo` struktury, opisująca bieżącego zadania drukowania.

### <a name="remarks"></a>Uwagi

Dla każdej strony drukowanego, struktura wywołuje tę funkcję, natychmiast po wywołaniu [OnPrepareDC](#onpreparedc) funkcja elementu członkowskiego. Strona drukowanego jest określona przez `m_nCurPage` członkiem [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która *pInfo* wskazuje. Domyślna implementacja wywołuje [OnDraw](#ondraw) funkcja elementu członkowskiego i przekazuje je kontekstu urządzenia drukarki.

Należy przesłonić tę funkcję dla każdego z następujących powodów:

- Aby zezwolić na drukowanie dokumentów wielostronicowych. Renderowanie tylko części dokumentu, który odnosi się do strony właśnie drukowane. Jeśli używasz `OnDraw` przeprowadzić renderowania, można dostosować pochodzenia okienka ekranu, aby tylko odpowiednie części dokument został wydrukowany.

- Aby wydruk różnić się od obraz ekranu (to znaczy, jeśli aplikacja nie jest typu WYSIWYG). Zamiast przekazywać kontekst urządzenia do drukarki `OnDraw`, użyj kontekstu urządzenia, by renderować obraz przy użyciu atrybutów, które nie są wyświetlane na ekranie.

   Jeśli potrzebujesz zasobów GDI związane z drukowaniem, który nie jest używany do ekranu, zaznacz je w kontekście urządzenia przed rysowaniem i później usunąć ich zaznaczenie. Te zasoby GDI powinna zostać przydzielona w [onbeginprinting —](#onbeginprinting) i wydawane w [onendprinting —](#onendprinting).

- Aby zaimplementować w nagłówkach i stopkach strony. Można nadal używać `OnDraw` celu renderowania przez ograniczenie możliwości wykonywania obszar, który może drukować na.

Należy pamiętać, że `m_rectDraw` członkiem *pInfo* parametru w tym artykule opisano obszar drukowania strony w jednostkach logicznych.

Nie wywołuj `OnPrepareDC` w zastąpienie metody `OnPrint`; struktura wywołuje `OnPrepareDC` automatycznie przed wywołaniem `OnPrint`.

### <a name="example"></a>Przykład

Poniżej przedstawiono szkielet dla przesłoniętych `OnPrint` funkcji:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Inny przykład, zobacz [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>  CView::OnScroll

Wywoływane przez platformę, by określić czy przewijanie jest możliwe.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode*<br/>
Kod paska przewijania, który wskazuje użytkownika przewijanym żądania. Ten parametr składa się z dwóch części: mniej znaczący bajt, określający typ przewijania pojawiają się poziome i bajt wyższego rzędu, który określa typ przewijania występujących w pionie:

- Przewija SB_BOTTOM do dołu.

- Przewija SB_LINEDOWN jeden wiersz w dół.

- Przewija SB_LINEUP jeden wiersz w górę.

- Przewija SB_PAGEDOWN jedną stronę w dół.

- Przewija SB_PAGEUP jedną stronę w górę.

- SB_THUMBTRACK Drags przewiń okno na określonej pozycji. Bieżące położenie jest określona w *npos —*.

- Przewija SB_TOP do góry.

*npos —*<br/>
Zawiera bieżące położenie pola przewijania, jeśli kod pasek przewijania jest SB_THUMBTRACK; w przeciwnym razie nie jest używany. W zależności od zakresu początkowej przewijania *npos —* może być ujemny i powinny być rzutowane na **int** w razie potrzeby.

*bDoScroll*<br/>
Określa, czy rzeczywiście należy określoną akcję przewijania. W przypadku opcji TRUE przewijając powinny zostać wykonane; Jeśli wartość to FALSE, przewijając nie powinien wystąpić.

### <a name="return-value"></a>Wartość zwracana

Jeśli *bDoScroll* ma wartość TRUE i widoku zostało faktycznie przewijane, zwracany jest różna od zera; w przeciwnym razie 0. Jeśli *bDoScroll* jest wartość FALSE, a następnie zwraca wartość, która będzie wrócisz Jeśli *bDoScroll* zostały wartość TRUE, nawet jeśli użytkownik faktycznie nie przewijania.

### <a name="remarks"></a>Uwagi

W przypadku jednego ta funkcja jest wywoływana przez platformę, za pomocą *bDoScroll* ustawiona na wartość TRUE, gdy widok odbiera komunikat paska przewijania. W tym przypadku powinien rzeczywiście przewijać widok. W przeciwnym razie ta funkcja jest wywoływana z *bDoScroll* ustawić na wartość FALSE, gdy element OLE jest początkowo przeciągnięte do obszaru region automatyczne przewijanie miejsca docelowego przed faktycznie przewijanie ma miejsce. W takim przypadku należy nie faktycznie przewijania widoku.

##  <a name="onscrollby"></a>  CView::OnScrollBy

Wywoływane przez platformę, gdy użytkownik przegląda obszarze poza obecne widoku dokumentu, przeciągając element OLE na granicach bieżącego widoku lub przez operacje pionowych lub poziomych pasków przewijania.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Liczba pikseli przewijane w poziomie i w pionie.

*bDoScroll*<br/>
Określa, czy występuje przewijania widoku. W przypadku opcji TRUE przewijając odbywa się; Jeśli wartość to FALSE, przewijając nie występuje.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli widok mógł być przewijane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W klasach pochodnych ta metoda sprawdza, czy widok jest przewijany w kierunku użytkownik zażądał, a następnie aktualizuje nowego regionu, jeśli to konieczne. Ta funkcja automatycznie jest wywoływana [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) do wykonania rzeczywistego żądania przewijania.

Domyślna implementacja tej metody nie powoduje zmiany widoku, ale jeśli nie zostanie wywołany, widoku nie będzie przewijanie w `CScrollView`-klasy pochodnej.

Jeśli dokument szerokość lub wysokość przekracza 32767 pikseli, przewijając w przeszłości 32767 będzie działać, ponieważ `OnScrollBy` jest wywoływana z nieprawidłowym *sizeScroll* argumentu.

##  <a name="onupdate"></a>  CView::OnUpdate

Wywoływane przez platformę po zmodyfikowaniu tego widoku dokumentu; Ta funkcja jest wywoływana [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) i umożliwia widok, aby zaktualizować jego ekranu, aby uwzględnić te zmiany.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskazuje na widok, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie widoki, które mają zostać uaktualnione.

*lHint*<br/>
Zawiera informacje o modyfikacji.

*pHint*<br/>
Wskazuje do przechowywania informacji na temat zmian obiektu.

### <a name="remarks"></a>Uwagi

Jest również nazywany przez domyślną implementację elementu [OnInitialUpdate](#oninitialupdate). Domyślna implementacja unieważnia całego obszaru klienta, oznaczając je do malowania, po odebraniu następny komunikat WM_PAINT. Należy przesłonić tę funkcję, jeśli chcesz zaktualizować tylko do regionów mapowane zmodyfikowane części dokumentu. W tym celu należy przekazać informacji na temat zmian przy użyciu parametrów wskazówki.

Aby użyć *lHint*, zdefiniuj wskazówka specjalnych wartości, zazwyczaj maską bitów lub typu wyliczeniowego i dokumentu, przekazać jedną z następujących wartości. Do użycia *pHint*, wyprowadzić klasę z wskazówka [CObject](../../mfc/reference/cobject-class.md) i dokumentu, przekazać wskaźnik do obiektu wskazówka; podczas zastępowania `OnUpdate`, użyj [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) Funkcja elementu członkowskiego w celu określenia typu run-time obiektu wskazówki.

Zazwyczaj nie należy wykonywać dowolne rysowanie bezpośrednio z poziomu `OnUpdate`. Zamiast tego należy określić prostokąt opisujący we współrzędnych urządzenia obszar, który wymaga zaktualizowania; Przekaż ten prostokąt [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Powoduje to, że malowania przy następnym [WM_PAINT](/windows/desktop/gdi/wm-paint) wiadomość zostaje odebrana.

Jeśli *lHint* wynosi 0 i *pHint* ma wartość NULL, dokumentu zostało wysłane powiadomienie ogólną aktualizację. Jeśli widok otrzyma powiadomienie o ogólną aktualizację lub nie można go zdekodować wskazówek, należy go unieważnienie jego całego obszaru klienta.

## <a name="see-also"></a>Zobacz też

[Próbki MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)
