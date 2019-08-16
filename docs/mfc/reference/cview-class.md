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
ms.openlocfilehash: abc1373e1bca2afcce493eef5245fb73b56cce4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502160"
---
# <a name="cview-class"></a>Klasa CView

Oferuje podstawowe funkcje dla klas widoków zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView:: CView](#cview)|Konstruuje `CView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CView::D oPreparePrinting](#doprepareprinting)|Wyświetla okno dialogowe Drukowanie i tworzy kontekst urządzenia drukarki; wywołuje się, `OnPreparePrinting` gdy zastępują funkcję członkowską.|
|[CView:: GetDocument](#getdocument)|Zwraca dokument skojarzony z widokiem.|
|[CView:: IsSelected](#isselected)|Testuje, czy element dokumentu jest zaznaczony. Wymagane na potrzeby obsługi OLE.|
|[CView:: OnDragEnter](#ondragenter)|Wywołuje się, gdy element jest najpierw przeciągany do obszaru przeciągania i upuszczania w widoku.|
|[CView:: OnDragLeave](#ondragleave)|Wywołuje się, gdy przeciągany element opuszcza region przeciągnij i upuść widoku.|
|[CView:: OnDragOver](#ondragover)|Wywołuje się, gdy element zostanie przeciągnięty w regionie przeciągania i upuszczania widoku.|
|[CView:: OnDragScroll](#ondragscroll)|Wywołuje się, by określić, czy kursor jest przeciągany do regionu przewijania okna.|
|[CView:: OnDrop](#ondrop)|Wywołuje się, gdy element został porzucony w regionie przeciągania i upuszczania widoku, domyślna procedura obsługi.|
|[CView:: OnDropEx](#ondropex)|Wywołuje się, gdy element został porzucony w regionie przeciągania i upuszczania widoku, podstawowa procedura obsługi.|
|[CView:: OnInitialUpdate](#oninitialupdate)|Wywoływana po pierwszym dołączeniu widoku do dokumentu.|
|[CView:: OnPrepareDC](#onpreparedc)|Wywoływana przed `OnDraw` wywołaniem funkcji składowej na potrzeby wyświetlania ekranu `OnPrint` lub funkcja członkowska jest wywoływana do drukowania lub podglądu wydruku.|
|[CView:: OnScroll](#onscroll)|Wywoływana, gdy elementy OLE są przeciągane poza obramowaniem widoku.|
|[CView:: OnScrollBy](#onscrollby)|Wywołuje się, gdy widok zawierający aktywne elementy OLE w miejscu jest przewijany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CView:: OnActivateFrame](#onactivateframe)|Wywoływana, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.|
|[CView:: OnActivateView](#onactivateview)|Wywoływana, gdy widok jest aktywowany.|
|[CView:: OnBeginPrinting](#onbeginprinting)|Wywołuje się, gdy rozpocznie się zadanie drukowania; zastąpienie w celu przydzielenia zasobów interfejsu GDI (Graphics Device Interface).|
|[CView:: OnDraw](#ondraw)|Wywołuje się, by renderować obraz dokumentu na potrzeby wyświetlania ekranu, drukowania lub podglądu wydruku. Wymagana implementacja.|
|[CView:: OnEndPrinting](#onendprinting)|Wywołuje się, gdy zakończyło się zadanie drukowania; Przesłoń, aby cofnąć alokację zasobów GDI.|
|[CView:: OnEndPrintPreview](#onendprintpreview)|Wywoływana, gdy tryb podglądu jest zakończony.|
|[CView:: OnPreparePrinting](#onprepareprinting)|Wywołuje się przed wydrukowaniem lub podglądem dokumentu; Zastąp, aby zainicjować drukowanie okna dialogowego.|
|[CView:: OnPrint](#onprint)|Wywołuje się, by wydrukować lub wyświetlić podgląd strony dokumentu.|
|[CView:: OnUpdate](#onupdate)|Wywołuje się, by powiadomić widok o modyfikacji dokumentu.|

## <a name="remarks"></a>Uwagi

Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentem a użytkownikiem: widok renderuje obraz dokumentu na ekranie lub na drukarce i interpretuje dane wejściowe użytkownika jako operacje na dokumencie.

Widok jest elementem podrzędnym okna ramki. Więcej niż jeden widok może współdzielić okno ramki, tak jak w przypadku okna rozdzielacza. Relacja między klasą widoku, klasą okna ramowego a klasą dokumentu jest określana przez `CDocTemplate` obiekt. Gdy użytkownik otwiera nowe okno lub dzieli istniejące, struktura konstruuje nowy widok i dołącza go do dokumentu.

Widok może być dołączony tylko do jednego dokumentu, ale dokument może mieć jednocześnie do niego dołączonych wiele widoków — na przykład jeśli dokument jest wyświetlany w oknie rozdzielacza lub w wielu oknach podrzędnych w aplikacji interfejsu wielu dokumentów (MDI). Aplikacja może obsługiwać różne typy widoków dla danego typu dokumentu; na przykład program przetwarzania tekstów może dostarczyć pełny widok tekstowy dokumentu oraz widok konspektu, który pokazuje tylko nagłówki sekcji. Te różne typy widoków można umieścić w oddzielnych oknach ramowych lub w oddzielnych okienkach okna pojedynczej ramki, jeśli używasz okna rozdzielacza.

Widok może być odpowiedzialny za obsługę kilku różnych typów danych wejściowych, takich jak dane wejściowe z klawiatury, dane wejściowe myszy lub dane wejściowe za pomocą przeciągania i upuszczania oraz poleceń z menu, pasków narzędzi lub pasków przewijania. Widok odbiera polecenia przekazane przez okno ramki. Jeśli widok nie obsługuje danego polecenia, przekazuje polecenie do skojarzonego z nim dokumentu. Podobnie jak w przypadku wszystkich elementów docelowych poleceń widok obsługuje komunikaty za pośrednictwem mapy komunikatów.

Widok jest odpowiedzialny za wyświetlanie i modyfikowanie danych dokumentu, ale nie do ich przechowywania. Dokument zawiera widok z niezbędnymi informacjami o jego danych. Możesz zezwolić na dostęp do widoku bezpośrednio członkom danych dokumentu lub udostępnić funkcje członkowskie w klasie dokumentu dla klasy widoku do wywołania.

Gdy dane dokumentu zmienią się, widok odpowiedzialny za zmiany zwykle wywołuje funkcję [CDocument:: funkcji UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) dla dokumentu, która powiadamia wszystkie inne widoki, wywołując `OnUpdate` funkcję członkowską dla każdego z nich. Domyślna implementacja `OnUpdate` unieważnia cały obszar klienta widoku. Można zastąpić go, aby unieważnił tylko te regiony obszaru klienta, które są mapowane na zmodyfikowane fragmenty dokumentu.

Aby użyć `CView`, należy utworzyć z niej klasę i `OnDraw` zaimplementować funkcję członkowską w celu przeprowadzenia wyświetlania ekranu. Za pomocą `OnDraw` programu można również wykonywać drukowanie i Podgląd wydruku. Platforma obsługuje pętlę drukowania na potrzeby drukowania i wyświetlania podglądu dokumentu.

Widok obsługuje komunikaty paska przewijania z funkcjami składowymi [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) . W tych funkcjach można zaimplementować obsługę komunikatów na pasku przewijania lub można użyć `CView` klasy pochodnej [CScrollView](../../mfc/reference/cscrollview-class.md) do obsługi przewijania.

Oprócz `CScrollView`, biblioteka MFC dostarcza dziewięć innych klas pochodzących od `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), widok, który umożliwia użycie architektury widoku dokumentu z kontrolkami, listami i formantami edycji wzbogaconej.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), widok wyświetlający rekordy bazy danych w kontrolkach okna dialogowego.

- [Elementu CEditView](../../mfc/reference/ceditview-class.md), widok, który udostępnia prosty edytor tekstu wielowierszowego. Możesz użyć `CEditView` obiektu jako formantu w oknie dialogowym, a także widoku dokumentu.

- [CFormView](../../mfc/reference/cformview-class.md), przewijany widok, który zawiera kontrolki okna dialogowego i jest oparty na zasobie szablonu okna dialogowego.

- [CListView](../../mfc/reference/clistview-class.md), widok, który umożliwia użycie architektury widoku dokumentu z kontrolkami listy.

- [Formularzy CRecordView](../../mfc/reference/crecordview-class.md), widok wyświetlający rekordy bazy danych w kontrolkach okna dialogowego.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), widok, który umożliwia użycie architektury widoku dokumentu z kontrolkami edycji wzbogaconej.

- [CScrollView](../../mfc/reference/cscrollview-class.md)— widok, który automatycznie zapewnia obsługę przewijania.

- [CTreeView](../../mfc/reference/ctreeview-class.md), widok, który umożliwia użycie architektury widoku dokumentu z kontrolkami drzewa.

Klasa ma również pochodną klasę implementacji o nazwie `CPreviewView`, która jest używana przez platformę do wykonywania podglądu wydruku. `CView` Ta klasa zapewnia obsługę funkcji unikatowych dla okna drukowania w wersji zapoznawczej, takich jak pasek narzędzi, jednostronicowa wersja zapoznawcza i powiększanie, czyli powiększenie obrazu z podglądem. Nie musisz wywoływać ani przesłaniać żadnych `CPreviewView`funkcji Członkowskich, chyba że chcesz zaimplementować własny interfejs na potrzeby podglądu wydruku (na przykład jeśli chcesz obsługiwać edytowanie w trybie podglądu wydruku). Aby uzyskać więcej informacji na `CView`temat korzystania z programu, zobacz [dokument/wyświetlanie architektury](../../mfc/document-view-architecture.md) i [Drukowanie](../../mfc/printing.md). Ponadto zobacz [Uwaga techniczna 30](../../mfc/tn030-customizing-printing-and-print-preview.md) , aby uzyskać więcej informacji na temat dostosowywania podglądu wydruku.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cview"></a>CView:: CView

Konstruuje `CView` obiekt.

```
CView();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje konstruktora po utworzeniu nowego okna ramki lub poddzieleniu okna. Zastąp funkcję elementu członkowskiego [OnInitialUpdate](#oninitialupdate) , aby zainicjować widok po dołączeniu dokumentu.

##  <a name="doprepareprinting"></a>CView::D oPreparePrinting

Wywołaj tę funkcję z przesłonięcia [OnPreparePrinting](#onprepareprinting) , aby wywołać okno dialogowe drukowania i utworzyć kontekst urządzenia drukarki.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli można rozpocząć drukowanie lub Podgląd wydruku; 0, jeśli operacja została anulowana.

### <a name="remarks"></a>Uwagi

Zachowanie funkcji jest zależne od tego, czy jest wywoływana do drukowania czy podglądu wydruku (określony przez `m_bPreview` element członkowski parametru *pInfo* ). Jeśli plik jest drukowany, ta funkcja wywołuje okno dialogowe drukowania przy użyciu wartości ze struktury [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która wskazuje; gdy użytkownik zamknął okno dialogowe, funkcja tworzy kontekst urządzenia drukarki na podstawie ustawień określonych przez użytkownika w oknie dialogowym i zwraca ten kontekst urządzenia za pomocą parametru *pInfo* . Ten kontekst urządzenia służy do drukowania dokumentu.

Jeśli plik jest w wersji zapoznawczej, ta funkcja tworzy kontekst urządzenia drukarki przy użyciu bieżących ustawień drukarki. Ten kontekst urządzenia służy do symulowania drukarki w trakcie okresu zapoznawczego.

##  <a name="getdocument"></a>CView:: GetDocument

Wywołaj tę funkcję, aby uzyskać wskaźnik do dokumentu widoku.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [CDocument](../../mfc/reference/cdocument-class.md) skojarzonego z widokiem. Wartość NULL, jeśli widok nie jest dołączony do dokumentu.

### <a name="remarks"></a>Uwagi

Umożliwia to wywoływanie funkcji Członkowskich dokumentu.

##  <a name="isselected"></a>CView:: IsSelected

Wywoływane przez platformę, aby sprawdzić, czy określony element dokumentu jest zaznaczony.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parametry

*pDocItem*<br/>
Wskazuje na testowany element dokumentu.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wybrano określony element dokumentu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji zwraca wartość FALSE. Zastąp tę funkcję, jeśli implementujesz wybór za pomocą obiektów [CDocItem](../../mfc/reference/cdocitem-class.md) . Należy przesłonić tę funkcję, jeśli widok zawiera elementy OLE.

##  <a name="onactivateframe"></a>CView:: OnActivateFrame

Wywoływane przez platformę, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parametry

*nInformacje*<br/>
Określa, czy okno ramki jest uaktywniane czy dezaktywowane. Może to być jedna z następujących wartości:

- WA_INACTIVE okno ramki jest dezaktywowane.

- WA_ACTIVE okno ramki jest uaktywniane za pomocą jakiejś metody innej niż kliknięcie myszą (na przykład za pomocą interfejsu klawiatury do zaznaczenia okna).

- WA_CLICKACTIVE okno ramki jest uaktywniane przez kliknięcie myszą

*pFrameWnd*<br/>
Wskaźnik do okna ramki, które ma zostać aktywowane.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję elementu członkowskiego, jeśli chcesz przeprowadzić przetwarzanie specjalne, gdy okno ramki skojarzone z widokiem jest aktywowane lub dezaktywowane. Na przykład [CFormView](../../mfc/reference/cformview-class.md) wykonuje to zastąpienie, gdy zapisuje i przywraca formant, który ma fokus.

##  <a name="onactivateview"></a>CView:: OnActivateView

Wywoływane przez platformę, gdy widok jest aktywowany lub dezaktywowany.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parametry

*bActivate*<br/>
Wskazuje, czy widok jest aktywowany, czy dezaktywowany.

*pActivateView*<br/>
Wskazuje na uaktywniany obiekt.

*pDeactiveView*<br/>
Wskazuje na obiekt widoku, który jest dezaktywowany.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji ustawia fokus dla aktywowanego widoku. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne, gdy widok jest aktywowany lub dezaktywowany. Na przykład, jeśli chcesz podać specjalne podpowiedzi wizualizacji odróżniające aktywny widok z nieaktywnych widoków, należy sprawdzić parametr *bActivate* i odpowiednio zaktualizować wygląd widoku.

Parametry *pActivateView* i *pDeactiveView* wskazują ten sam widok, jeśli okno głównej ramki aplikacji jest aktywowane bez zmian w aktywnym widoku — na przykład jeśli fokus jest transferowany z innej aplikacji do tej, zamiast z jednego widoku do innego w aplikacji lub podczas przełączania między oknami podrzędnymi MDI. Dzięki temu widok może przetworzyć swoją paletę, w razie potrzeby.

Parametry te różnią się, gdy [obiektu CFrameWnd:: SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) jest wywoływana z widokiem, który różni się od typu [obiektu CFrameWnd:: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) . Zdarza się to najczęściej z oknami rozdzielacza.

##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting

Wywoływane przez platformę na początku zadania drukowania lub podglądu wydruku po `OnPreparePrinting` wywołaniu.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby przydzielić wszelkie zasoby GDI, takie jak pióra lub czcionki, które są potrzebne do drukowania. Wybierz obiekty GDI w kontekście urządzenia z poziomu wbudowanej funkcji [](#onprint) składowej dla każdej strony, która z nich korzysta. Jeśli używasz tego samego obiektu widoku do przeprowadzenia zarówno wyświetlania ekranu, jak i drukowania, użyj oddzielnych zmiennych dla zasobów GDI wymaganych dla każdego ekranu. pozwala to na aktualizowanie ekranu podczas drukowania.

Za pomocą tej funkcji można także wykonać inicjalizacje zależne od właściwości kontekstu urządzenia drukarki. Na przykład liczba stron wymaganych do drukowania dokumentu może zależeć od ustawień określonych przez użytkownika w oknie dialogowym Drukowanie (na przykład długość strony). W takiej sytuacji nie można określić długości dokumentu w funkcji składowej [OnPreparePrinting](#onprepareprinting) , gdzie zwykle to zrobisz; musisz poczekać, aż kontekst urządzenia drukarki zostanie utworzony na podstawie ustawień okna dialogowego. [OnBeginPrinting](#onbeginprinting) to pierwsza funkcja, która umożliwia dostęp do obiektu [przechwytywania](../../mfc/reference/cdc-class.md) , reprezentującego kontekst urządzenia drukarki, dzięki czemu można ustawić długość dokumentu z tej funkcji. Należy pamiętać, że jeśli długość dokumentu nie jest określona przez ten czas, pasek przewijania nie jest wyświetlany w podglądzie wydruku.

##  <a name="ondragenter"></a>CView:: OnDragEnter

Wywoływane przez platformę, gdy mysz po raz pierwszy przejdzie w region nieprzewijalny okna upuszczania Target.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągany do obszaru upuszczania w widoku.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Bieżąca pozycja myszy względem obszaru klienckiego widoku.

### <a name="return-value"></a>Wartość zwracana

Wartość z typu wyliczeniowego DROPEFFECT, która wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik porzucił obiekt na tej pozycji. Typ elementu Drop zazwyczaj zależy od bieżącego stanu klucza wskazywanego przez *dwKeyState*. Standardowe mapowanie wartości parametrów DROPEFFECT są następujące:

- DROPEFFECT_NONE nie można porzucić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię usuniętego obiektu.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię usuniętego obiektu i usuwa oryginalny obiekt. Jest to zazwyczaj domyślnym efektem upuszczenia, gdy widok może akceptować ten obiekt danych.

Aby uzyskać więcej informacji, zobacz przykład zaawansowanych pojęć MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślna implementacja to nic robić i zwracają DROPEFFECT_NONE.

Zastąp tę funkcję, aby przygotować się do przyszłych wywołań funkcji składowej [OnDragOver](#ondragover) . Wszystkie dane wymagane z obiektu danych powinny zostać pobrane w tym momencie do późniejszego użycia w `OnDragOver` funkcji członkowskiej. Widok powinien również zostać zaktualizowany w tym momencie, aby dać użytkownikowi opinię. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie elementu docelowego](../../mfc/drag-and-drop-implementing-a-drop-target.md)upuszczania.

##  <a name="ondragleave"></a>CView:: OnDragLeave

Wywoływane przez platformę w trakcie operacji przeciągania, gdy wskaźnik myszy zostanie przeniesiony z prawidłowego obszaru upuszczania dla tego okna.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, jeśli bieżący widok wymaga oczyszczenia wszystkich akcji podjętych podczas wywołań [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) , takich jak usuwanie dowolnych opinii użytkowników wizualnych, gdy obiekt został przeciągnięty i usunięty.

##  <a name="ondragover"></a>CView:: OnDragOver

Wywoływane przez platformę w trakcie operacji przeciągania, gdy wskaźnik myszy zostanie przesunięty nad oknem elementu docelowego upuszczania.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągany nad elementem docelowym upuszczania.

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Bieżąca pozycja myszy względem obszaru widoku klienta.

### <a name="return-value"></a>Wartość zwracana

Wartość z typu wyliczeniowego DROPEFFECT, która wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik porzucił obiekt na tej pozycji. Typ upuszczenia często zależy od bieżącego stanu klucza wskazanego przez *dwKeyState*. Standardowe mapowanie wartości parametrów DROPEFFECT są następujące:

- DROPEFFECT_NONE nie można porzucić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię usuniętego obiektu.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię usuniętego obiektu i usuwa oryginalny obiekt. Jest to zazwyczaj domyślny efekt upuszczania, gdy widok może akceptować obiekt danych.

Aby uzyskać więcej informacji, zobacz przykład zaawansowanych pojęć MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Domyślną implementacją jest wykonanie niczego i zwrócenie DROPEFFECT_NONE.

Zastąp tę funkcję, aby dać użytkownikowi opinię wizualną podczas operacji przeciągania. Ponieważ ta funkcja jest wywoływana w sposób ciągły, każdy znajdujący się w niej kod powinien być zoptymalizowany jak najwięcej. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie elementu docelowego](../../mfc/drag-and-drop-implementing-a-drop-target.md)upuszczania.

##  <a name="ondragscroll"></a>CView:: OnDragScroll

Wywoływane przez platformę przed wywołaniem metody [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) w celu ustalenia, czy punkt znajduje się w regionie przewijania.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*dwKeyState*<br/>
Zawiera stan klawiszy modyfikujących. Jest to kombinacja dowolnej liczby następujących elementów: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.

*moment*<br/>
Zawiera lokalizację kursora (w pikselach) względem ekranu.

### <a name="return-value"></a>Wartość zwracana

Wartość z typu wyliczeniowego DROPEFFECT, która wskazuje typ upuszczenia, który wystąpi, jeśli użytkownik porzucił obiekt na tej pozycji. Typ elementu Drop zazwyczaj zależy od bieżącego stanu klucza wskazywanego przez *dwKeyState*. Standardowe mapowanie wartości parametrów DROPEFFECT są następujące:

- DROPEFFECT_NONE nie można porzucić obiektu danych w tym oknie.

- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy połączenie między obiektem a jego serwerem.

- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię usuniętego obiektu.

- DROPEFFECT_MOVE dla MK_ALT tworzy kopię usuniętego obiektu i usuwa oryginalny obiekt.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągnij ma miejsce lub występuje w widoku docelowym.

Aby uzyskać więcej informacji, zobacz przykład zaawansowanych pojęć MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, jeśli chcesz zapewnić specjalne zachowanie dla tego zdarzenia. Domyślna implementacja automatycznie przewija okna, gdy kursor jest przeciągany do domyślnego regionu przewijania wewnątrz obramowania każdego okna. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie elementu docelowego](../../mfc/drag-and-drop-implementing-a-drop-target.md)upuszczania.

##  <a name="ondraw"></a>CView:: OnDraw

Wywoływane przez platformę, by renderować obraz dokumentu.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obrazu dokumentu.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję w celu przeprowadzenia wyświetlania ekranu, drukowania i podglądu wydruku, a w każdym przypadku przekazuje inny kontekst urządzenia. Nie istnieje domyślna implementacja.

Należy zastąpić tę funkcję, aby wyświetlić widok dokumentu. Wywołania interfejsu GDI (Graphics Device Interface) można wykonywać za pomocą [](../../mfc/reference/cdc-class.md) obiektu przerzutowania wskazywanego przez parametr *PDC* . Możesz wybrać zasoby GDI, takie jak pióra lub czcionki, w kontekście urządzenia przed rysowaniem, a następnie usunąć ich zaznaczenie później. Często kod rysowania może być niezależny od urządzenia; oznacza to, że nie wymaga informacji o rodzaju urządzenia wyświetlającego obraz.

Aby zoptymalizować rysowanie, wywołaj funkcję członkowską [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) kontekstu urządzenia, aby dowiedzieć się, czy dany prostokąt zostanie narysowany. Jeśli chcesz rozróżnić normalny ekran wyświetlania i drukowania, wywołaj funkcję elementu [](../../mfc/reference/cdc-class.md#isprinting) Członkowskiego isprint kontekstu urządzenia.

##  <a name="ondrop"></a>CView:: OnDrop

Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pośrednictwem prawidłowego elementu docelowego upuszczania.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parametry

"pDataObject * wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) , który został porzucony do elementu docelowego upuszczania.

*dropEffect*<br/>
Efekt upuszczania zażądanego przez użytkownika.

- DROPEFFECT_COPY tworzy kopię obiektu danych, który jest usuwany.

- DROPEFFECT_MOVE przenosi obiekt danych do bieżącej lokalizacji myszy.

- DROPEFFECT_LINK tworzy łącze między obiektem danych i jego serwerem.

*moment*<br/>
Bieżąca pozycja myszy względem obszaru widoku klienta.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, Jeśli upuszczanie zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie robi niczego i zwraca wartość FALSE.

Zastąp tę funkcję, aby zaimplementować efekt upuszczania OLE w obszarze klienta widoku. Obiekt danych można sprawdzić za pomocą *pDataObject* dla formatów danych schowka i danych porzuconych w określonym punkcie.

> [!NOTE]
>  Struktura nie wywołuje tej funkcji, jeśli w tej klasie widoku istnieje przesłonięcie do [OnDropEx](#ondropex) .

##  <a name="ondropex"></a>CView:: OnDropEx

Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pośrednictwem prawidłowego elementu docelowego upuszczania.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parametry

*pDataObject*<br/>
Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) , która zostanie porzucona do elementu docelowego upuszczania.

*dropDefault*<br/>
Efekt wybrany przez użytkownika dla domyślnej operacji upuszczania na podstawie bieżącego stanu klucza. Może być DROPEFFECT_NONE. Efekty upuszczania zostały omówione w sekcji uwagi.

*dropList*<br/>
Lista efektów upuszczania obsługiwanych przez źródło upuszczania. Wartości efektów upuszczania można łączyć za pomocą operacji bitowej lub ( **&#124;** ). Efekty upuszczania zostały omówione w sekcji uwagi.

*moment*<br/>
Bieżąca pozycja myszy względem obszaru widoku klienta.

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania spowodowany próbą porzucenia w lokalizacji określonej przez *punkt*. Musi to być jedna z wartości wskazywanych przez *dropEffectList*. Efekty upuszczania zostały omówione w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Domyślna implementacja to nic nie rób i zwraca wartość fikcyjną (-1), aby wskazać, że struktura powinna wywołać procedurę [OnDrop](#ondrop) .

Zastąp tę funkcję, aby zaimplementować efekt przeciągania i upuszczania przycisku myszy. Prawy przycisk myszy — przeciąganie i upuszczanie zazwyczaj wyświetla menu opcji po wydaniu prawego przycisku myszy.

Przesłonięcie `OnDropEx` powinno być zapytania dla prawego przycisku myszy. Możesz wywołać [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) lub zapisać prawy stan przycisku myszy z procedury obsługi [OnDragEnter](#ondragenter) .

- Jeśli prawy przycisk myszy nie działa, przesłonięcie powinno wyświetlić menu podręczne, które oferuje obsługę efektów upuszczania przez źródło upuszczania.

   - Sprawdź *droplist* , aby określić efekty upuszczania obsługiwane przez źródło upuszczania. Włącz tylko te akcje w menu podręcznym.

   - Użyj [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) , aby ustawić akcję domyślną w oparciu o *DropDefault*.

   - Na koniec wykonaj akcję wskazywaną przez wybór użytkownika z menu podręcznego.

- Jeśli prawy przycisk myszy nie jest wyłączony, przesłonięcie powinno przetworzyć to jako standardowe żądanie upuszczania. Użyj efektu upuszczania określonego w *DropDefault*. Alternatywnie przesłonięcie może zwrócić wartość fikcyjną (-1), aby wskazać, `OnDrop` że będzie obsługiwać tę operację upuszczania.

Użyj *pDataObject* do sprawdzenia `COleDataObject` formatu danych schowka i danych porzuconych w określonym punkcie.

Efekty upuszczania opisują akcję skojarzoną z operacją drop. Zobacz poniższą listę efektów upuszczania:

- DROPEFFECT_NONE nie jest dozwolone.

- DROPEFFECT_COPY operacji kopiowania.

- DROPEFFECT_MOVE operacji przenoszenia.

- DROPEFFECT_LINK połączenie z usuniętych danych na oryginalne dane.

- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągnij ma miejsce lub występuje w elemencie docelowym.

Aby uzyskać więcej informacji na temat ustawiania domyślnego polecenia menu, zobacz Windows SDK [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) i [CMenu:: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) w tym woluminie.

##  <a name="onendprinting"></a>CView:: OnEndPrinting

Wywoływane przez platformę po wydrukowaniu lub podglądzie dokumentu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Przesłoń tę funkcję, aby zwolnić wszystkie zasoby GDI przydzieloną w funkcji składowej [OnBeginPrinting](#onbeginprinting) .

##  <a name="onendprintpreview"></a>CView:: OnEndPrintPreview

Wywoływane przez platformę, gdy użytkownik opuszcza tryb podglądu wydruku.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania.

*moment*<br/>
Określa punkt na stronie, która była ostatnio wyświetlana w trybie podglądu.

*pView*<br/>
Wskazuje obiekt widoku używany do podglądu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję członkowską [OnEndPrinting](#onendprinting) i przywraca okno głównej ramki do stanu, w którym znajdował się przed rozpoczęciem podglądu wydruku. Przesłoń tę funkcję, aby przeprowadzić przetwarzanie specjalne w przypadku zakończenia trybu podglądu. Na przykład jeśli chcesz zachować położenie użytkownika w dokumencie podczas przełączania z trybu podglądu do normalnego trybu wyświetlania, możesz przewijać do pozycji opisanej przez parametr *Point* i `m_nCurPage` element członkowski `CPrintInfo` struktury. czy parametr *pInfo* wskazuje na.

Zawsze Wywołaj wersję `OnEndPrintPreview` klasy bazowej z przesłonięcia, zazwyczaj na końcu funkcji.

##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate

Wywoływane przez platformę po pierwszym dołączeniu widoku do dokumentu, ale zanim widok jest początkowo wyświetlany.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję elementu członkowskiego [OnUpdate](#onupdate) bez informacji o wskazówkach (to oznacza użycie wartości domyślnych 0 dla parametru *lHint* i wartości null dla parametru *pHint* ). Zastąp tę funkcję, aby wykonać jednorazowe inicjowanie, które wymaga informacji o dokumencie. Na przykład jeśli aplikacja ma dokumenty o stałym rozmiarze, można użyć tej funkcji do zainicjowania limitów przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennym rozmiarze, użyj [OnUpdate](#onupdate) , aby aktualizować limity przewijania za każdym razem, gdy dokument ulega zmianie.

##  <a name="onpreparedc"></a>CView:: OnPrepareDC

Wywoływane przez platformę przed wywołaniem funkcji składowej [OnDraw](#ondraw) na potrzeby wyświetlania ekranu oraz przed wywołaniem funkcji składowej OnPrint dla każdej strony podczas drukowania lub podglądu wydruku. [](#onprint)

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obrazu dokumentu.

*pInfo*<br/>
Wskazuje na strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania, jeśli `OnPrepareDC` jest wywoływana do drukowania lub podglądu `m_nCurPage` wydruku; element członkowski Określa stronę do wydrukowania. Ten parametr ma wartość null `OnPrepareDC` , jeśli jest wywoływany na potrzeby wyświetlania ekranu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wykonuje nic, jeśli funkcja jest wywoływana do wyświetlania ekranu. Jednak ta funkcja jest zastępowana w klasach pochodnych, takich jak [CScrollView](../../mfc/reference/cscrollview-class.md), w celu dostosowania atrybutów kontekstu urządzenia; w związku z tym zawsze należy wywołać implementację klasy bazowej na początku przesłonięcia.

Jeśli funkcja jest wywoływana do drukowania, domyślna implementacja bada informacje o stronie przechowywane w parametrze *pInfo* . Jeśli długość dokumentu nie została określona, przyjmuje się, `OnPrepareDC` że dokument ma jedną stronę długą i zatrzyma pętlę drukowania po wydrukowaniu jednej strony. Funkcja przerywa pętlę drukowania, ustawiając `m_bContinuePrinting` element członkowski struktury na wartość false.

Przesłoń `OnPrepareDC` z jednego z następujących powodów:

- Aby dostosować atrybuty kontekstu urządzenia zgodnie z wymaganiami dla określonej strony. Na przykład jeśli trzeba ustawić tryb mapowania lub inne cechy kontekstu urządzenia, zrób to w tej funkcji.

- Do przeprowadzenia stronicowania w czasie drukowania. Zwykle określasz długość dokumentu podczas rozpoczynania drukowania przy użyciu funkcji składowej [OnPreparePrinting](#onprepareprinting) . Jeśli jednak nie wiesz, jak długo dokument jest (na przykład podczas drukowania nieokreślonych liczb rekordów z bazy danych), Przesłoń `OnPrepareDC` , aby sprawdzić koniec dokumentu podczas jego drukowania. Gdy nie ma więcej dokumentu do wydrukowania, ustaw `m_bContinuePrinting` element członkowski `CPrintInfo` struktury na wartość false.

- W celu wysłania kodów ucieczki do drukarki na podstawie strony. Aby wysłać Kody ucieczki `OnPrepareDC`z, należy `Escape` wywołać funkcję członkowską parametru *PDC* .

Wywołaj wersję `OnPrepareDC` klasy bazowej na początku przesłonięcia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting

Wywoływane przez platformę przed wydrukowaniem lub podglądem dokumentu.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pInfo*<br/>
Wskazuje strukturę [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , która opisuje bieżące zadanie drukowania.

### <a name="return-value"></a>Wartość zwracana

Od zera do rozpoczęcia drukowania; 0, jeśli zadanie drukowania zostało anulowane.

### <a name="remarks"></a>Uwagi

Domyślna implementacja nie robi nic.

Należy zastąpić tę funkcję, aby umożliwić drukowanie i Podgląd wydruku. Wywołaj funkcję elementu członkowskiego [DoPreparePrinting by otworzyć](#doprepareprinting) , przekazując ją do parametru *pInfo* , a następnie Zwróć wartość zwracaną. `DoPreparePrinting` wyświetla okno dialogowe Drukowanie i tworzy kontekst urządzenia drukarki. Jeśli chcesz zainicjować okno dialogowe Drukowanie z wartościami innymi niż domyślne, przypisz wartości do elementów członkowskich *pInfo*. Na przykład jeśli znasz długość dokumentu, przekaż wartość do funkcji składowej [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) elementu *pInfo* przed wywołaniem `DoPreparePrinting`. Ta wartość jest wyświetlana w polu do: w części zakres okna dialogowego drukowanie.

`DoPreparePrinting`nie wyświetla okna dialogowego Drukuj dla zadania w wersji zapoznawczej. Jeśli chcesz ominąć okno dialogowe drukowania dla zadania drukowania, sprawdź, czy `m_bPreview` element członkowski *pInfo* ma wartość false, a następnie ustaw dla niego wartość true przed przekazaniem do `DoPreparePrinting`niego, a następnie zresetuj go do wartości false.

Jeśli musisz wykonać inicjalizacje, które wymagają dostępu do `CDC` obiektu reprezentującego kontekst urządzenia drukarki (na przykład jeśli potrzebujesz znać rozmiar strony przed określeniem długości dokumentu), `OnBeginPrinting` Zastąp element członkowski funkcyjn.

Jeśli chcesz ustawić `m_nNumPreviewPages` wartość lub `m_strPageDesc` elementów członkowskich parametru *pInfo* , zrób to po wywołaniu `DoPreparePrinting`. Funkcja członkowska jest `m_nNumPreviewPages` ustawiana na wartość znalezioną w aplikacji. `DoPreparePrinting` Plik ini i ustawia `m_strPageDesc` jego wartość domyślną.

### <a name="example"></a>Przykład

  Przesłoń `OnPreparePrinting` i `DoPreparePrinting` Wywołaj z przesłonięcia, aby platforma wyświetlała okno dialogowe drukowania i utworzyć dla Ciebie kontroler domeny.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Jeśli wiesz, ile stron zawiera dokument, ustaw maksymalną stronę w `OnPreparePrinting` polu przed wywołaniem. `DoPreparePrinting` W strukturze zostanie wyświetlony maksymalny numer strony w polu "do" okna dialogowego Drukuj.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView:: OnPrint

Wywoływane przez platformę do drukowania lub wyświetlania podglądu strony dokumentu.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia drukarki.

*pInfo*<br/>
`CPrintInfo` Wskazuje strukturę opisującą bieżące zadanie drukowania.

### <a name="remarks"></a>Uwagi

Dla każdej drukowanej strony, struktura wywołuje tę funkcję natychmiast po wywołaniu funkcji składowej [OnPrepareDC](#onpreparedc) . Drukowana strona jest określana przez `m_nCurPage` element członkowski struktury [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) , do której odwołuje się *pInfo* . Domyślna implementacja wywołuje funkcję członkowską [OnDraw](#ondraw) i przekazuje ją do kontekstu urządzenia drukarki.

Przesłoń tę funkcję z jednego z następujących powodów:

- Aby umożliwić drukowanie dokumentów wielostronicowych. Renderuje tylko część dokumentu, która odnosi się do aktualnie drukowanej strony. Jeśli używasz `OnDraw` do wykonania renderowania, możesz dostosować Źródło okienka ekranu, tak aby była drukowana tylko odpowiednia część dokumentu.

- Aby wydrukowany obraz wyglądał inaczej niż obraz ekranu (oznacza to, że aplikacja nie jest w trybie WYSIWYG). Zamiast przekazywania kontekstu urządzenia drukarki do `OnDraw`programu, należy użyć kontekstu urządzenia do renderowania obrazu przy użyciu atrybutów niewidocznych na ekranie.

   Jeśli potrzebujesz zasobów GDI do drukowania, którego nie używasz na potrzeby wyświetlania ekranu, zaznacz je w kontekście urządzenia przed rysowaniem i usuń zaznaczenie ich później. Te zasoby GDI powinny być przydzielona w [OnBeginPrinting](#onbeginprinting) i wydane w [OnEndPrinting](#onendprinting).

- Do implementowania nagłówków lub stopek. Można nadal użyć `OnDraw` do wykonania renderowania przez ograniczenie obszaru, w którym można drukować.

Należy zauważyć, `m_rectDraw` że element członkowski parametru *pInfo* opisuje obszar drukowalny strony w jednostkach logicznych.

Nie wywołuj `OnPrepareDC` w `OnPrint`przesłonięciu; przed wywołaniem `OnPrint`struktury `OnPrepareDC` jest wywoływana automatycznie.

### <a name="example"></a>Przykład

Poniżej przedstawiono szkielet dla zastąpionej `OnPrint` funkcji:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Aby uzyskać inny przykład, zobacz [CRichEditView::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>CView:: OnScroll

Wywoływane przez platformę, aby określić, czy przewijanie jest możliwe.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nScrollCode*<br/>
Kod paska przewijania wskazujący żądanie przewijania użytkownika. Ten parametr składa się z dwóch części: bajt o niskiej kolejności, który określa typ przewijania w poziomie i bajt o dużej kolejności, który określa typ przewijania w pionie:

- SB_BOTTOM przewija do dołu.

- SB_LINEDOWN przewija jeden wiersz w dół.

- SB_LINEUP przewija jeden wiersz w górę.

- SB_PAGEDOWN Przewija jedną stronę w dół.

- SB_PAGEUP Przewija jedną stronę w górę.

- Pole przewijania SB_THUMBTRACK przeciąga do określonego położenia. Bieżąca pozycja jest określona w *nPos*.

- SB_TOP przewija do góry.

*nPos*<br/>
Zawiera bieżące położenie pola przewijania, jeśli kod paska przewijania jest SB_THUMBTRACK; w przeciwnym razie nie jest używany. W zależności od początkowego zakresu przewijania *nPos* może być ujemna i powinny być rzutowane na **int** w razie potrzeby.

*bDoScroll*<br/>
Określa, czy należy w rzeczywistości wykonać określoną akcję przewijania. Jeśli wartość jest równa TRUE, przewijanie powinno odbywać się; w przypadku wartości FALSE, przewijanie nie powinno być wykonywane.

### <a name="return-value"></a>Wartość zwracana

Jeśli *bDoScroll* ma wartość true, a widok został rzeczywiście przewinięty, zwróć wartość różną od zera. w przeciwnym razie 0. Jeśli *bDoScroll* ma wartość false, zwraca wartość, która zostałaby zwrócona, jeśli *bDoScroll* były prawdziwe, nawet jeśli nie będziesz w rzeczywistości przewijać.

### <a name="remarks"></a>Uwagi

W jednym przypadku ta funkcja jest wywoływana przez platformę z *bDoScroll* ustawioną na wartość true, gdy widok odbierze komunikat ScrollBar. W takim przypadku należy w rzeczywistości przewinąć widok. W innym przypadku ta funkcja jest wywoływana z *bDoScroll* ustawiona na false, gdy element OLE jest początkowo przeciągany do regionu autoprzewijania elementu docelowego upuszczania przed faktycznym przewinięciem. W takim przypadku nie należy w rzeczywistości przewijać widoku.

##  <a name="onscrollby"></a>CView:: OnScrollBy

Wywoływane przez platformę, gdy użytkownik przegląda obszar poza widokiem bieżącym dokumentu, przeciągając element OLE względem bieżących obramowań widoku lub manipulując pionowo lub poziomą paski przewijania.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*sizeScroll*<br/>
Liczba pikseli przewijana w poziomie i w pionie.

*bDoScroll*<br/>
Określa, czy ma nastąpić przewijanie widoku. W przypadku wartości TRUE następuje przewijanie; w przypadku wartości FALSE, przewijanie nie następuje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli widok był w stanie przewinąć; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

W klasach pochodnych ta metoda sprawdza, czy widok jest przewijany w kierunku zażądanym przez użytkownika, a następnie aktualizuje nowy region w razie potrzeby. Ta funkcja jest automatycznie wywoływana przez [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) , aby wykonać rzeczywiste żądanie przewijania.

Domyślna implementacja tej metody nie zmienia widoku, ale jeśli nie jest wywoływana, widok nie zostanie przewinięty w `CScrollView`klasie pochodnej.

Jeśli szerokość lub wysokość dokumentu przekracza 32767 pikseli, przewijanie ostatnich 32767 zakończy się `OnScrollBy` niepowodzeniem, ponieważ jest wywoływana z nieprawidłowym argumentem *sizeScroll* .

##  <a name="onupdate"></a>CView:: OnUpdate

Wywoływane przez platformę po zmodyfikowaniu dokumentu widoku; Ta funkcja jest wywoływana przez [CDocument:: funkcji UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) i pozwala widokowi na zaktualizowanie jego wyświetlania w celu odzwierciedlenia tych zmian.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskazuje widok, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie widoki mają zostać zaktualizowane.

*lHint*<br/>
Zawiera informacje o zmianach.

*pHint*<br/>
Wskazuje obiekt przechowujący informacje o zmianach.

### <a name="remarks"></a>Uwagi

Jest on również wywoływany przez domyślną implementację [OnInitialUpdate](#oninitialupdate). Domyślna implementacja unieważnia cały obszar klienta, zaznaczając ją do malowania po odebraniu następnego komunikatu WM_PAINT. Przesłoń tę funkcję, jeśli chcesz zaktualizować tylko te regiony, które są mapowane na zmodyfikowane fragmenty dokumentu. Aby to zrobić, należy przekazać informacje na temat modyfikacji przy użyciu parametrów wskazówki.

Aby użyć *lHint*, zdefiniuj specjalne wartości podpowiedzi, zazwyczaj maskę bitów lub typ wyliczeniowy, a dokument Przekaż jedną z tych wartości. Aby użyć *pHint*, należy utworzyć klasę podpowiedzi z [CObject](../../mfc/reference/cobject-class.md) i mieć dokument, aby przekazać wskaźnik do obiektu podpowiedzi; Podczas zastępowania `OnUpdate`należy użyć funkcji składowej [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) , aby określić typ czasu wykonywania obiektu wskazówki.

Zazwyczaj nie należy wykonywać żadnego rysowania bezpośrednio z programu `OnUpdate`. Zamiast tego należy określić prostokąt opisujący, w obszarze współrzędne urządzenia, obszar, który wymaga aktualizacji; Przekaż ten prostokąt do [CWnd:: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Powoduje to, że malowanie zostanie przeprowadzone przy następnym odebraniu komunikatu [WM_PAINT](/windows/win32/gdi/wm-paint) .

Jeśli *lHint* jest równa 0, a *pHint* ma wartość null, dokument przesłał ogólne powiadomienie o aktualizacji. Jeśli widok otrzyma powiadomienie o aktualizacji ogólnej lub nie można zdekodować wskazówek, powinna unieważnić cały obszar klienta.

## <a name="see-also"></a>Zobacz także

[Przykład MDIDOCVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)<br/>
[Klasa CDC](../../mfc/reference/cdc-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)
