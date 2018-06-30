---
title: Cview — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7ff4e48bd7006c3706909d1791b82aa8cda2658
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123126"
---
# <a name="cview-class"></a>Cview — klasa
Zapewnia podstawowe funkcje dla klas widoku zdefiniowane przez użytkownika.  
  
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
|[CView::DoPreparePrinting](#doprepareprinting)|Wyświetla okno dialogowe Drukuj i tworzy kontekstu urządzenia drukarki; wywołania w przypadku przesłaniania `OnPreparePrinting` funkcję elementu członkowskiego.|  
|[CView::GetDocument](#getdocument)|Zwraca dokument skojarzony z widokiem.|  
|[CView::IsSelected](#isselected)|Sprawdza, czy zaznaczono element dokumentu. Wymagane do obsługi.|  
|[CView::OnDragEnter](#ondragenter)|Wywoływane, gdy element najpierw zostanie przeciągnięty do obszaru przeciągania i upuszczania w widoku.|  
|[CView::OnDragLeave](#ondragleave)|Wywoływane, gdy przeciąganego elementu opuszcza obszar przeciągania i upuszczania widoku.|  
|[CView::OnDragOver](#ondragover)|Wywoływane, gdy element zostanie przeciągnięty nad obszar przeciągania i upuszczania widoku.|  
|[CView::OnDragScroll](#ondragscroll)|Wywołuje się, by określić czy kursor jest przeciągany w regionie przewijania okna.|  
|[CView::OnDrop](#ondrop)|Wywoływane, gdy element został porzucony w regionie przeciągania i upuszczania widok domyślny program obsługi.|  
|[CView::OnDropEx](#ondropex)|Wywoływane, gdy element został porzucony w regionie przeciągania i upuszczania widokiem podstawowej obsługi.|  
|[CView::OnInitialUpdate](#oninitialupdate)|Metoda wywoływana po widoku najpierw jest dołączony do dokumentu.|  
|[CView::OnPrepareDC](#onpreparedc)|Wywoływana przed `OnDraw` funkcja członkowska jest wywoływana dla ekranu lub `OnPrint` funkcja członkowska jest wywoływana dla drukowania lub podglądu drukowania.|  
|[CView::OnScroll](#onscroll)|Wywoływane, gdy elementy OLE są przeciągnięty poza granice tego widoku.|  
|[CView::OnScrollBy](#onscrollby)|Wywoływane, gdy jest przewijane widok zawierający aktywnych elementów OLE w miejscu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|Wywoływane, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.|  
|[CView::OnActivateView](#onactivateview)|Wywoływane, gdy widok jest aktywowane.|  
|[CView::OnBeginPrinting](#onbeginprinting)|Wywołuje się po rozpoczęciu zadania drukowania; należy przesłonić, aby przydzielić zasoby urządzenia (GDI) interfejsu grafiki.|  
|[CView::OnDraw](#ondraw)|Wywołuje się, by renderować obraz dokumentu dla ekranu, drukowania lub podglądu wydruku. Implementacja wymagane.|  
|[CView::OnEndPrinting](#onendprinting)|Wywołuje się po zakończeniu zadania drukowania; zastąpienie można cofnąć alokacji zasobów GDI.|  
|[CView::OnEndPrintPreview](#onendprintpreview)|Wywoływane, gdy tryb podglądu zostanie zakończone.|  
|[CView::OnPreparePrinting](#onprepareprinting)|Metoda wywoływana przed dokumentu jest wydrukiem lub podglądem; należy przesłonić, aby zainicjować okno dialogowe drukowania.|  
|[CView::OnPrint](#onprint)|Wywołuje się, by wydrukować lub podejrzeć stronę dokumentu.|  
|[CView::OnUpdate](#onupdate)|Wywołuje się, by powiadomić widok, w którym jego dokument został zmodyfikowany.|  
  
## <a name="remarks"></a>Uwagi  
 Widok jest dołączony do dokumentu i działa jako pośrednik między dokumentu i użytkownika: widok renderuje obraz dokumentu na ekranie lub drukarki i interpretuje dane wejściowe użytkownika jako operacje na dokument.  
  
 Widok jest elementem podrzędnym ramki okna. Więcej niż jeden widok można udostępniać okno ramowe, tak jak w przypadku okna podziału. Relacja między klasę widoku, klasie okien ramowych i klasa dokumentu została ustanowiona `CDocTemplate` obiektu. Gdy użytkownik otwiera nowe okno lub dzieli istniejące jedną platformę tworzy nowy widok i dołącza go do dokumentu.  
  
 Widok może zostać dołączony do tylko jeden dokument, ale dokumentu może mieć wiele widoków jednocześnie dołączyć do niego — na przykład, jeśli dokument jest wyświetlany w oknie podziału lub w wielu okien podrzędnych w wiele aplikacji interfejsu (MDI) dokumentu. Aplikacja może obsługiwać różne typy widoków dla typu danego dokumentu; na przykład edytorze tekstów może zawierać zarówno widoku Pełny tekst dokumentu i widoku konspektu, który pokazuje tylko nagłówki sekcji. Te różne typy widoków można umieścić w oddzielnych ramka okna lub oddzielne okienka okna jedną ramkę korzystając z okna podziału.  
  
 Widok może być odpowiedzialny za obsługę kilku różnych typów danych wejściowych, takie jak klawiatury, myszy lub dane wejściowe za pośrednictwem przeciągania i upuszczania, a także polecenia menu, paski narzędzi i paski przewijania. Widok odbiera przekazywane przez jego ramkę okna poleceń. Jeśli widok nie obsługuje danego polecenia, przekazuje polecenia do jego skojarzonego dokumentu. Podobnie jak wszystkie obiekty docelowe poleceń widoku obsługuje komunikaty za pośrednictwem mapy komunikatów.  
  
 Widok jest odpowiedzialny wyświetlanie i modyfikowanie danych dokumentu, ale nie do przechowywania go. Dokument zawiera widok z niezbędne informacje o jego dane. Możesz pozwolić, aby dostęp widoku dokumentu elementy członkowskie danych bezpośrednio, lub zapewniają funkcje elementów członkowskich w klasie dokumentów w klasie widoku do wywołania.  
  
 Po zmianie danych dokumentu, widok odpowiedzialny za zmiany zwykle wywołuje [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) funkcja dla dokumentu, który powiadamia innych widoków wywołując `OnUpdate` funkcji członkowskiej dla Każdy. Domyślna implementacja `OnUpdate` unieważnia obszaru klienckiego całego widoku. Można je zastąpić, zanim unieważni tylko tych regionów obszaru klienta, które mapują zmodyfikowane części dokumentu.  
  
 Aby użyć `CView`, pochodną klasy i wykonywania `OnDraw` funkcji członkowskiej przeprowadzić ekranu. Można również użyć `OnDraw` przeprowadzić drukowania i podglądu wydruku. Struktury obsługi drukowania pętli do drukowania i podglądu dokumentu.  
  
 Widok obsługi komunikatów paska przewijania z [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funkcji elementów członkowskich. Można zaimplementować Obsługa tych funkcji komunikatów paska przewijania lub użyć `CView` klasy [CScrollView](../../mfc/reference/cscrollview-class.md) do obsługi przewijanie dla Ciebie.  
  
 Oprócz `CScrollView`, Microsoft Foundation Class Library udostępnia dziewięć klasy pochodzące od `CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md), widoku, który umożliwia użycie dokumentu — widok architektury z drzewa, listy i sformatowany formanty edycji.  
  
- [Cdaorecordview —](../../mfc/reference/cdaorecordview-class.md), widok, który wyświetla rekordów bazy danych w kontrolkach okno dialogowe.  
  
- [CEditView](../../mfc/reference/ceditview-class.md), widok zawiera edytor tekstu w wielu wierszach proste. Można użyć `CEditView` obiektu jako formant w okno dialogowe, a także widok w dokumencie.  
  
- [CFormView](../../mfc/reference/cformview-class.md), którą można przewijać w widoku, który zawiera formanty okno dialogowe i jest oparty na zasobu szablonu okna dialogowego.  
  
- [Clistview —](../../mfc/reference/clistview-class.md), widoku, który umożliwia użycie dokumentu — architektura widoku z kontrolki listy.  
  
- [CRecordView](../../mfc/reference/crecordview-class.md), widok, który wyświetla rekordów bazy danych w kontrolkach okno dialogowe.  
  
- [Cricheditview —](../../mfc/reference/cricheditview-class.md), widoku, który umożliwia użycie dokumentu — widok architektury oraz zaawansowanej edycji kontrolki.  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md), widoku, który automatycznie zapewnia obsługę przewijania.  
  
- [CTreeView —](../../mfc/reference/ctreeview-class.md), widoku, który umożliwia użycie dokumentu — architektura widoku z drzewa formantów.  
  
 `CView` Klasa ma również klasy pochodnej wdrożenia o nazwie `CPreviewView`, używany przez platformę do wykonania, wyświetlanie podglądu wydruku. Ta klasa obsługuje funkcje unikatowy w oknie Podgląd wydruku, takich jak pasek narzędzi podglądu stronę o podwójnej precyzji lub jednym i powiększanie, który jest powiększając wyświetlanego obrazu. Nie trzeba wywołać lub przesłonić `CPreviewView`przez funkcje Członkowskie, chyba że implementowania interfejsu podglądu wydruku (na przykład, jeśli mają być obsługiwane, edytowanie w trybie podglądu wydruku). Aby uzyskać więcej informacji na temat używania `CView`, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md) i [drukowanie](../../mfc/printing.md). Ponadto zobacz [30 Uwaga techniczna](../../mfc/tn030-customizing-printing-and-print-preview.md) Aby uzyskać więcej informacji o dostosowywaniu podglądu wydruku.  
  
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
 Struktura wywołuje konstruktor, gdy zostanie utworzone nowe okno ramowe lub okna jest podzielona. Zastąpienie [OnInitialUpdate](#oninitialupdate) funkcji członkowskiej zainicjować widoku po dołączeniu dokumentu.  
  
##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting  
 Wywołanie tej funkcji z zastąpienia z [OnPreparePrinting](#onprepareprinting) Wywołaj okno dialogowe Drukuj i tworzenie kontekstu urządzenia drukarki.  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która opisuje bieżącego zadania drukowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli można rozpocząć drukowania lub podglądu drukowania; 0, jeśli operacja została anulowana.  
  
### <a name="remarks"></a>Uwagi  
 Zachowanie tej funkcji zależy od tego, czy jest ona wywoływana dla drukowania lub podglądu drukowania (określonego przez `m_bPreview` członkiem *pInfo* parametru). Jeśli plik jest drukowanie, ta funkcja wywołuje okno dialogowe drukowania przy użyciu wartości w [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która *pInfo* wskazuje; po użytkownika zostało zamknięte okno dialogowe, funkcja ta umożliwia tworzenie kontekst urządzenia drukarki na podstawie ustawień użytkownika określonego w oknie dialogowym i zwraca ten kontekst urządzenia za pośrednictwem *pInfo* parametru. Ten kontekst urządzenia służy do drukowania dokumentu.  
  
 Jeśli plik jest przeglądany, ta funkcja tworzy kontekstu urządzenia drukarki przy użyciu bieżących ustawień drukarek; Ten kontekst urządzenia jest używana do symulowania drukarki w wersji zapoznawczej.  
  
##  <a name="getdocument"></a>  CView::GetDocument  
 Wywołanie tej funkcji, otrzymywać wskaźnik do dokumentu widoku.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CDocument](../../mfc/reference/cdocument-class.md) obiekt skojarzony z widokiem. Wartość NULL, jeśli widok nie jest dołączony do dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu można wywołać funkcji Członkowskich dokumentu.  
  
##  <a name="isselected"></a>  CView::IsSelected  
 Wywoływane przez platformę, by sprawdzić, czy zaznaczono element określonego dokumentu.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocItem*  
 Wskazuje element dokumentu testowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zaznaczono element określony dokument; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja zwraca wartość FALSE. Zastąpienie tej funkcji w przypadku wdrażania przy użyciu wybór [CDocItem](../../mfc/reference/cdocitem-class.md) obiektów. Należy przesłonić tę funkcję, jeśli widok zawiera elementy OLE.  
  
##  <a name="onactivateframe"></a>  CView::OnActivateFrame  
 Wywoływane przez platformę, gdy okno ramowe zawierające widok jest aktywowane lub dezaktywowane.  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *nInformacje*  
 Określa, czy okno ramowe jest aktywowane lub dezaktywowane. Może być jedną z następujących wartości:  
  
- Trwa dezaktywowanie WA_INACTIVE ramkę okna.  
  
- Kliknij WA_ACTIVE, który okno ramowe jest uaktywniany przez niektóre metody innej niż myszy (na przykład przy użyciu interfejsu klawiatury, aby wybrać okno).  
  
- Trwa aktywowanie WA_CLICKACTIVE okno ramowe przez kliknięcie myszą  
  
 *pFrameWnd*  
 Wskaźnik do okno ramowe, który ma być aktywowany.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję elementu członkowskiego, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe skojarzonego z widokiem jest aktywowane lub dezaktywowane. Na przykład [CFormView](../../mfc/reference/cformview-class.md) wykonuje to zastąpienie zapisuje i przywraca formantu, który ma fokus.  
  
##  <a name="onactivateview"></a>  CView::OnActivateView  
 Wywoływane przez platformę, gdy widok jest aktywowane lub dezaktywowane.  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>Parametry  
 *bActivate*  
 Wskazuje, czy widok jest aktywowane lub dezaktywowane.  
  
 *pActivateView*  
 Wskazuje obiekt widoku, który jest aktywowane.  
  
 *pDeactiveView*  
 Wskazuje obiekt widoku, który jest dezaktywowana.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja Ustawia fokus do widoku aktywowane. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy widok jest aktywowane lub dezaktywowane. Na przykład jeśli chcesz podać specjalne wizualnych, które odróżnienia widoku aktywnego nieaktywne widoki, czy sprawdzić *bActivate* parametru i odpowiednio zaktualizować wygląd widoku.  
  
 *PActivateView* i *pDeactiveView* parametry polecenie tego samego widoku, jeśli aktywowano aplikacji główne okno ramowe bez żadnych zmian w aktywnym widoku — na przykład, jeśli są fokus przeniesione z innej aplikacji z tym komputerem, a nie z jeden widok do innej aplikacji lub podczas przełączania między oknami podrzędnymi MDI. Widok do osiągnięcia ponownie swoją paletę dzięki temu w razie potrzeby.  
  
 Te parametry są różne podczas [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) jest wywoływana z widoku, który jest inny niż co [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) zwróci. Najczęściej dzieje się z okna podziału.  
  
##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting  
 Wywoływane przez platformę na początku zadania drukowania lub podglądu drukowania po `OnPreparePrinting` została wywołana.  
  
```  
virtual void OnBeginPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia drukarki.  
  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która opisuje bieżącego zadania drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja nie działa. Zastąpienie tej funkcji można przydzielić żadnych GDI zasoby, takie jak pióra lub czcionek, wymagane specjalnie na potrzeby drukowania. Wybierz obiekty GDI w kontekście urządzenia z poziomu [OnPrint](#onprint) funkcji członkowskiej dla każdej strony, która używa ich. Jeśli używasz tego samego obiektu widoku do wykonywania ekranu i drukowanie, użyj oddzielnych zmiennych dla zasobów GDI niezbędnych do wyświetlania każdego; Dzięki temu można zaktualizować ekran podczas drukowania.  
  
 Umożliwia także tej funkcji do wykonania operacji inicjowania, które są zależne od właściwości kontekstu urządzenia drukarki. Na przykład liczba stron potrzebne do drukowania dokumentu może zależeć od ustawienia określone przez użytkownika w oknie dialogowym drukowania (takie jak długość strony). W takiej sytuacji nie można określić długość dokumentu w [OnPreparePrinting](#onprepareprinting) funkcji członkowskiej, gdzie będzie zazwyczaj w takim; należy poczekać, aż kontekst urządzenia drukarki został utworzony na podstawie ustawień okno dialogowe. [OnBeginPrinting](#onbeginprinting) jest pierwszej funkcji możliwym do zastąpienia, który zapewnia dostęp do [CDC](../../mfc/reference/cdc-class.md) obiekt reprezentujący kontekstu urządzenia drukarki, tak aby długość dokumentu z tej funkcji. Należy pamiętać, że jeśli długość dokumentu nie jest określona przez ten czas, pasek przewijania nie jest wyświetlany podczas podglądu wydruku.  
  
##  <a name="ondragenter"></a>  CView::OnDragEnter  
 Wywoływane przez platformę, gdy mysz przejdzie najpierw region bez przewijania okna docelowy upuszczania.  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *Obiekt pDataObject*  
 Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciąganie obszar upuszczania widoku.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: MK_CONTROL, MK_SHIFT MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Bieżącego położenia kursora myszy względem obszaru klienckiego widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, który może mieć miejsce, jeśli użytkownik usunął obiektu, w tym miejscu. Typ listy zależy zwykle od bieżącego stanu klucza wskazywanym przez *dwKeyState*. Standardowe mapowanie Director DROPEFFECT wartości to:  
  
- Nie można porzucić DROPEFFECT_NONE obiekt danych w tym oknie.  
  
- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy powiązania między obiektem i jego serwera.  
  
- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.  
  
- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usuń oryginalny obiekt. Zazwyczaj jest to domyślny efekt upuść, gdy widok może zaakceptować tego obiektu danych.  
  
 Aby uzyskać więcej informacji, zobacz przykład pojęcia zaawansowane MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja jest nic nie rób i zwracać DROPEFFECT_NONE.  
  
 Przesłonić tę funkcję, aby przygotować się do przyszłych wywołaniach [OnDragOver](#ondragover) funkcję elementu członkowskiego. Wszystkie dane wymagane z obiektu danych powinny zostać pobrane w tej chwili do użycia w `OnDragOver` funkcję elementu członkowskiego. Widok należy również zaktualizować w tej chwili, aby przekazać opinię visual użytkownika. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragleave"></a>  CView::OnDragLeave  
 Wywoływane przez platformę podczas operacji przeciągania gdy wskaźnik myszy zostanie przesunięty poza właściwy obszar upuszczania dla tego okna.  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji, jeśli bieżący widok musi oczyścić wszelkich akcjach podjętych podczas [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) wywołań, taką jak usuwania wszelkich opinie użytkowników visual, dopóki obiekt został przeciągnięto i Upuszczono .  
  
##  <a name="ondragover"></a>  CView::OnDragOver  
 Wywoływane przez platformę podczas operacji przeciągania, gdy wskaźnik myszy jest przesuwany nad okno docelowe upuszczania.  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *Obiekt pDataObject*  
 Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) przeciągany nad element docelowy upuszczania.  
  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: MK_CONTROL, MK_SHIFT MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Bieżąca pozycja myszy względem obszaru klienckiego widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, który może mieć miejsce, jeśli użytkownik usunął obiektu, w tym miejscu. Typ listy często zależy od bieżącego stanu klucza wskazywany przez *dwKeyState*. Standardowe mapowanie Director DROPEFFECT wartości to:  
  
- Nie można porzucić DROPEFFECT_NONE obiekt danych w tym oknie.  
  
- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy powiązania między obiektem i jego serwera.  
  
- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.  
  
- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usuń oryginalny obiekt. Zazwyczaj jest to domyślny efekt upuść, gdy widok może zaakceptować obiekt danych.  
  
 Aby uzyskać więcej informacji, zobacz przykład pojęcia zaawansowane MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja jest nic nie rób i zwracać DROPEFFECT_NONE.  
  
 Należy przesłonić tę funkcję, aby przekazać opinię visual użytkownika podczas operacji przeciągania. Ponieważ ta funkcja jest wywoływana w sposób ciągły, dowolny kod zawarty w niej powinno być zoptymalizowane pod możliwie. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragscroll"></a>  CView::OnDragScroll  
 Metoda wywoływana przez platformę przed wywołaniem [OnDragEnter](#ondragenter) lub [OnDragOver](#ondragover) ustalenie, czy punkt znajduje się w regionie przewijania.  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *dwKeyState*  
 Zawiera stan klawisze modyfikujące. To jest kombinacją dowolną liczbę następujących: MK_CONTROL, MK_SHIFT MK_ALT, MK_LBUTTON, MK_MBUTTON i MK_RBUTTON.  
  
 *Punkt*  
 Zawiera lokalizację kursor w pikselach, względem ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od DROPEFFECT wyliczany typ, który wskazuje typ listy, który może mieć miejsce, jeśli użytkownik usunął obiektu, w tym miejscu. Typ listy zależy zwykle od bieżącego stanu klucza wskazywanym przez *dwKeyState*. Standardowe mapowanie Director DROPEFFECT wartości to:  
  
- Nie można porzucić DROPEFFECT_NONE obiekt danych w tym oknie.  
  
- DROPEFFECT_LINK dla MK_CONTROL &#124; MK_SHIFT tworzy powiązania między obiektem i jego serwera.  
  
- DROPEFFECT_COPY dla MK_CONTROL tworzy kopię upuszczony obiekt.  
  
- DROPEFFECT_MOVE dla MK_ALT tworzy kopię upuszczony obiekt i usuń oryginalny obiekt.  
  
- DROPEFFECT_SCROLL wskazuje, że operacja przewijania przeciągania może nastąpić lub występuje w widok elementu docelowego.  
  
 Aby uzyskać więcej informacji, zobacz przykład pojęcia zaawansowane MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, gdy chcesz zapewnić specjalnego zachowania dla tego zdarzenia. Domyślna implementacja automatycznie przewija systemu windows, gdy kursor jest przeciągany do domyślnego regionu przewijania wewnątrz obramowania każdego okna. Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie docelowego upuszczania](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondraw"></a>  CView::OnDraw  
 Wywoływane przez platformę, by renderować obraz dokumentu.  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia używanego do renderowania obrazu dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę funkcję, aby wykonać ekranu, drukowania i podglądu wydruku, a następnie przekazuje kontekst innego urządzenia w każdym przypadku. Brak implementacji domyślnej.  
  
 Należy przesłonić tę funkcję, aby wyświetlić dokument. Można tworzyć przy użyciu wywołania interfejsu (GDI) urządzenia graficznego [CDC](../../mfc/reference/cdc-class.md) obiekt wskazywany przez *kontrolera pDC* parametru. Możesz wybrać GDI zasoby, takie jak pióra lub czcionki, do kontekstu urządzenia przed rysowaniem i usuń zaznaczenie opcji je później. Często kod rysowania może być niezależny od urządzenia; oznacza to, że nie wymaga informacji o rodzaju urządzenia są wyświetlane obrazu.  
  
 Aby zoptymalizować rysunku, należy wywołać [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) funkcji członkowskiej klasy kontekstu urządzenia, aby dowiedzieć się, będzie rysowany danego prostokąta. Do rozróżniania normalne ekranu i drukowanie należy wywołać [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) funkcji członkowskiej klasy kontekstu urządzenia.  
  
##  <a name="ondrop"></a>  CView::OnDrop  
 Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pośrednictwem prawidłowy miejsca docelowego.  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 "obiekt pDataObject *  
 Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) który są przenoszone do miejsca docelowego.  
  
 *dropEffect*  
 Efekt upuszczania, który użytkownik zgłosił żądanie.  
  
- DROPEFFECT_COPY tworzy kopię obiektu danych usuwane.  
  
- DROPEFFECT_MOVE przenosi obiekt danych do bieżącej lokalizacji myszy.  
  
- DROPEFFECT_LINK tworzy łącze z obiektu danych i serwerem.  
  
 *Punkt*  
 Bieżąca pozycja myszy względem obszaru klienckiego widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli listy zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie robi nic i zwraca wartość FALSE.  
  
 Zastąpienie tej funkcji do zaimplementowania efekt upuszczanie OLE do obszaru klienckiego widoku. Obiekt danych można zbadać za pomocą *pDataObject* dla danych ze Schowka formaty i danych usunięte w określonym momencie.  
  
> [!NOTE]
>  Platformę nie wywołanie tej funkcji, jeśli zastąpienie [OnDropEx](#ondropex) w tej klasie widoku.  
  
##  <a name="ondropex"></a>  CView::OnDropEx  
 Wywoływane przez platformę, gdy użytkownik zwalnia obiekt danych za pośrednictwem prawidłowy miejsca docelowego.  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 *Obiekt pDataObject*  
 Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) który są przenoszone do miejsca docelowego.  
  
 *dropDefault*  
 Wpływ, jaki użytkownik wybrał dla operacji upuszczania domyślne na podstawie bieżącego stanu klucza. Może to być DROPEFFECT_NONE. Efekty upuszczania omówiono w sekcji uwag.  
  
 *listy rozwijanej*  
 Lista efekty upuszczania, które obsługuje miejsca źródłowego. Wartości efekt listy można łączyć, używając wartości bitowe lub ( **&#124;**) operacji. Efekty upuszczania omówiono w sekcji uwag.  
  
 *Punkt*  
 Bieżąca pozycja myszy względem obszaru klienckiego widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt upuszczania, który jest wynikiem próby porzucenia w lokalizacji określonej przez *punktu*. Musi to być jedna z wartości wskazywane przez *dropEffectList*. Efekty upuszczania omówiono w sekcji uwag.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja jest nic nie rób i zwracać wartość zastępczego (-1) aby wskazać, że platformę powinny wywoływać [OnDrop](#ondrop) programu obsługi.  
  
 Zastąpienie tej funkcji do zaimplementowania efekt prawego przycisku myszy przeciągania i upuszczania. Prawy przycisk myszy, przeciągnij i upuść są zwykle wyświetlane menu opcji po zwolnieniu prawego przycisku myszy.  
  
 Zastąpienia z `OnDropEx` należy wyszukać prawy przycisk myszy. Możesz wywołać [GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301) ani do przechowywania stanu prawego przycisku myszy z Twojej [OnDragEnter](#ondragenter) programu obsługi.  
  
-   Jeśli prawy przycisk myszy jest wyłączony, zastąpienia powinien być wyświetlany menu podręczne, które oferuje obsługę efekty upuszczania przez źródło upuszczania.  
  
    -   Sprawdź *listy rozwijanej* do określenia wpływu upuszczania obsługiwane przez źródło upuszczania. Włącz tylko te akcje w menu podręcznym.  
  
    -   Użyj [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) można ustawić domyślną akcję na podstawie *dropDefault*.  
  
    -   Na koniec wykonaj akcję wskazywanym przez określonego użytkownika, w menu podręcznym.  
  
-   Jeśli prawy przycisk myszy nie jest w dół, zastąpienia należy przetworzyć tę jako standardowa upuść żądanie. Za pomocą efektu upuszczania określone w *dropDefault*. Alternatywnie zastąpienia może zwrócić wartość zastępczego (-1) aby wskazać, że `OnDrop` obsłuży tej operacji usuwania.  
  
 Użyj *pDataObject* do sprawdzenia `COleDataObject` dla danych ze Schowka format i danych usunięte w określonym momencie.  
  
 Efekty upuszczania opisują akcję skojarzoną z operacji usuwania. Lista poniższych upuszczania efekty:  
  
- DROPEFFECT_NONE spadek nie będzie dozwolone.  
  
- DROPEFFECT_COPY, który będzie można wykonać operacji kopiowania.  
  
- DROPEFFECT_MOVE, który będzie można wykonać operacji przenoszenia.  
  
- Czy można ustanowić łącze A DROPEFFECT_LINK porzuconych danych do oryginalnych danych.  
  
- DROPEFFECT_SCROLL oznacza to, że operację przeciągania przewijania może nastąpić lub występuje w miejscu docelowym.  
  
 Aby uzyskać więcej informacji na temat ustawiania domyślne polecenie menu, zobacz [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) w zestawie Windows SDK i [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) w tym woluminie.  
  
##  <a name="onendprinting"></a>  CView::OnEndPrinting  
 Wywoływane przez platformę po wydrukowaniu lub podglądzie dokumentu.  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia drukarki.  
  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która opisuje bieżącego zadania drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja nie działa. Przesłonić tę funkcję, aby zwolnić wszystkie przydzielone w zasoby GDI [OnBeginPrinting](#onbeginprinting) funkcję elementu członkowskiego.  
  
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
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia drukarki.  
  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która opisuje bieżącego zadania drukowania.  
  
 *Punkt*  
 Określa punkt strony, który został ostatnio wyświetlane w wersji zapoznawczej.  
  
 *pView*  
 Wskazuje obiekt widok używany do podglądu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja wymaga [OnEndPrinting](#onendprinting) funkcji członkowskiej i przywraca rozpoczęcia głównego okna ramowego do stanu sprzed podglądu wydruku. Należy przesłonić tę funkcję, wykonywanie specjalnego przetwarzania, gdy tryb podglądu jest zakończony. Na przykład, jeśli chcesz zachować pozycji użytkownika w dokumencie podczas przełączania z trybu podglądu do trybu normalnego wyświetlania można przechodzić do pozycji opisanego przez *punktu* parametru i `m_nCurPage` członkiem `CPrintInfo` struktury, która *pInfo* wskazuje parametr.  
  
 Wywoływanie zawsze wersja klasy podstawowej `OnEndPrintPreview` z zastąpienia, zwykle na końcu funkcji.  
  
##  <a name="oninitialupdate"></a>  CView::OnInitialUpdate  
 Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja wymaga [OnUpdate](#onupdate) funkcji członkowskiej bez informacji o wskazówki (oznacza to, za pomocą domyślnej wartości 0 dla *lHint* parametr i wartość NULL w przypadku  *pHint* parametru). Należy przesłonić tę funkcję, by wykonać jednorazowe inicjowanie, która wymaga informacji na temat dokumentu. Na przykład jeśli aplikacja ma dokumentów o stałym rozmiarze, funkcja ta zainicjować limity przewijania widoku na podstawie rozmiaru dokumentu. Jeśli aplikacja obsługuje dokumenty o zmiennej długości, użyj [OnUpdate](#onupdate) zaktualizować przewijania ogranicza zawsze zmiany w dokumencie.  
  
##  <a name="onpreparedc"></a>  CView::OnPrepareDC  
 Metoda wywoływana przez platformę przed [OnDraw](#ondraw) funkcja członkowska jest wywoływana dla ekranu i przed [OnPrint](#onprint) funkcja członkowska jest wywoływana dla każdej strony podczas drukowania lub podglądu drukowania.  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia używanego do renderowania obrazu dokumentu.  
  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, który opisuje bieżącego zadania drukowania, jeśli `OnPrepareDC` jest wywoływana dla drukowania lub podglądu drukowania; `m_nCurPage` elementu członkowskiego Określa stronę o do drukowania. Ten parametr ma wartość NULL, jeśli `OnPrepareDC` jest wywoływana dla ekranu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji nie działają, jeśli funkcja jest wywoływana dla ekranu. Jednak ta funkcja jest przesłonięte w klasach pochodnych, takich jak [CScrollView](../../mfc/reference/cscrollview-class.md), by dostosować atrybuty kontekstu urządzenia; w związku z tym, zawsze powinny wywoływać implementację klasy podstawowej na początku zastąpienia.  
  
 Jeśli funkcja jest wywoływana do drukowania, domyślna implementacja sprawdza, czy strona informacji przechowywanych w *pInfo* parametru. Jeśli nie została określona długość dokumentu, `OnPrepareDC` przyjmuje dokumentu do jednej strony, które długie i zatrzymuje pętli drukowania po wydrukowaniu jedną stronę. Funkcja zatrzymuje pętli wydruku przez ustawienie `m_bContinuePrinting` elementu członkowskiego struktury na wartość FALSE.  
  
 Zastąpienie `OnPrepareDC` dla żadnego z następujących powodów:  
  
-   Aby dostosować atrybuty kontekstu urządzenia, zgodnie z potrzebami dla określonej strony. Na przykład ustawić tryb mapowania lub innych parametrów kontekstu urządzenia należy to zrobić w tej funkcji.  
  
-   Aby wykonać godzina drukowania podział na strony. Zwykle określ długość dokumentu po rozpoczęciu drukowanie za pomocą [OnPreparePrinting](#onprepareprinting) funkcję elementu członkowskiego. Jednak jeśli nie znasz z wyprzedzeniem, jak długo dokumentu jest (na przykład podczas drukowania nieokreślonej liczba rekordów z bazy danych), Zastąp `OnPrepareDC` próba na końcu dokumentu podczas drukowania jest niemożliwe. Jeśli istnieje już dokument do wydrukowania, należy skonfigurować `m_bContinuePrinting` członkiem `CPrintInfo` struktury na wartość FALSE.  
  
-   Aby wysłać kody ESC do drukarki na podstawie strony strona. Wysłać kody ucieczki z `OnPrepareDC`, wywołaj `Escape` funkcji członkowskiej klasy *kontrolera pDC* parametru.  
  
 Wywołanie klasy podstawowej wersji `OnPrepareDC` na początku zastąpienia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>  CView::OnPreparePrinting  
 Wywoływane przez platformę przed wydrukowaniu lub podglądzie dokumentu.  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pInfo*  
 Wskazuje [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która opisuje bieżącego zadania drukowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, aby rozpocząć drukowanie; 0, jeśli zadanie drukowania zostało anulowane.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa.  
  
 Należy przesłonić tę funkcję, aby włączyć drukowania i podglądu wydruku. Wywołanie [DoPreparePrinting](#doprepareprinting) funkcji członkowskiej, przekazanie jej *pInfo* parametr, a następnie wróć jego wartości zwracanej; `DoPreparePrinting` Wyświetla okno dialogowe Drukuj i tworzy kontekstu urządzenia drukarki. Jeśli chcesz zainicjować okno dialogowe drukowania z wartości innych niż domyślne, przypisanie wartości do elementów członkowskich *pInfo*. Na przykład, jeśli znasz długość dokumentu, wartość należy przekazać do [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) funkcji członkowskiej klasy *pInfo* przed wywołaniem `DoPreparePrinting`. Ta wartość jest wyświetlana w polu do: pole w części zakresu okno dialogowe drukowania.  
  
 `DoPreparePrinting` nie wyświetla okno dialogowe drukowania dla zadania w wersji zapoznawczej. Jeśli chcesz pominąć okno dialogowe drukowania w zadaniu drukowania, sprawdź, czy `m_bPreview` członkiem *pInfo* ma wartość FALSE, a następnie ustaw wartość true przed przekazaniem go do `DoPreparePrinting`; zresetować je później FAŁSZ.  
  
 Jeśli zachodzi potrzeba wykonania operacji inicjowania, które wymagają dostępu do `CDC` obiekt reprezentujący drukarki kontekstu urządzenia (na przykład należy wiedzieć przed określeniem długość dokumentu do rozmiaru strony), Zastąp `OnBeginPrinting` elementu członkowskiego Funkcja.  
  
 Jeśli chcesz ustawić wartość `m_nNumPreviewPages` lub `m_strPageDesc` członkami *pInfo* parametru zrobić po wywołaniu `DoPreparePrinting`. `DoPreparePrinting` Zestawy funkcji elementów członkowskich `m_nNumPreviewPages` wartość znalezioną w aplikacji. Plik INI i ustawia `m_strPageDesc` na wartość domyślną.  
  
### <a name="example"></a>Przykład  
  Zastąpienie `OnPreparePrinting` i Wywołaj `DoPreparePrinting` z zastąpienie tak, aby w ramach spowoduje wyświetlenie okna dialogowego drukowania i utworzenie drukarki kontrolera domeny do.  
  
 [!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 Jeśli znasz liczbę stron dokument zawiera ustawienie maksymalnej strony `OnPreparePrinting` przed wywołaniem `DoPreparePrinting`. Platformę wyświetli numer strony maksymalna w polu "do" okna dialogowego drukowania.  
  
 [!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>  CView::OnPrint  
 Wywoływane przez platformę, by wydrukować lub podejrzeć stronę dokumentu.  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *podstawowego kontrolera domeny*  
 Wskazuje kontekstu urządzenia drukarki.  
  
 *pInfo*  
 Wskazuje `CPrintInfo` struktury, która opisuje bieżącego zadania drukowania.  
  
### <a name="remarks"></a>Uwagi  
 Dla każdej strony drukowanej struktura wywołuje natychmiast po wywołaniu tej funkcji [OnPrepareDC](#onpreparedc) funkcję elementu członkowskiego. Drukowanej strony jest określona przez `m_nCurPage` członkiem [cprintinfo —](../../mfc/reference/cprintinfo-structure.md) struktury, która *pInfo* wskazuje. Domyślna implementacja wywołuje [OnDraw](#ondraw) funkcji członkowskiej i przekazuje je kontekstu urządzenia drukarki.  
  
 Zastąpienie tej funkcji dla żadnego z następujących powodów:  
  
-   Aby umożliwić drukowanie dokumenty wielostronicowe. Renderowanie tylko części dokumentu, który odpowiada obecnie drukowanej strony. Jeśli używasz `OnDraw` przeprowadzić renderowania, można dostosować pochodzenia okienka ekranu, aby drukowania odpowiedniej części dokumentu.  
  
-   Aby można było wydruk różnić się od obraz ekranu (Jeśli aplikacja nie jest w trybie WYSIWYG). Zamiast przekazywanie drukarki kontekst urządzenia do `OnDraw`, użyj kontekst urządzenia, by renderować obraz przy użyciu atrybutów nie są wyświetlane na ekranie.  
  
     Jeśli potrzebujesz zasobów GDI do drukowania, który nie jest używany do wyświetlania na ekranie, wybierz je w kontekście urządzenia przed rysowaniem i później wyłączyć. Te zasoby GDI powinna zostać przydzielona w [OnBeginPrinting](#onbeginprinting) i wydanej w [OnEndPrinting](#onendprinting).  
  
-   Aby zaimplementować nagłówków i stopek. Można nadal używać `OnDraw` celu renderowania przez ograniczenie obszaru można drukować na.  
  
 Należy pamiętać, że `m_rectDraw` członkiem *pInfo* parametru opisano obszar drukowania strony w jednostkach logicznych.  
  
 Nie wywołuj `OnPrepareDC` w zastąpienia z `OnPrint`; framework wywołania `OnPrepareDC` automatycznie przed wywołaniem `OnPrint`.  
  
### <a name="example"></a>Przykład  
 Poniżej przedstawiono szkielet dla przesłoniętych `OnPrint` funkcji:  
  
 [!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 Na przykład innego, zobacz [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).  
  
##  <a name="onscroll"></a>  CView::OnScroll  
 Wywoływane przez platformę, by określić czy przewijanie jest możliwe.  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *nScrollCode*  
 Kod paska przewijania, który wskazuje użytkownika do przewijania żądania. Ten parametr składa się z dwóch części: mniej znaczącego bajtu, który określa typ przewijania występujących w poziomie, a bajt znaczących, który określa typ przewijania występujących w pionie:  
  
- Przewija SB_BOTTOM do dołu.  
  
- Przewija SB_LINEDOWN jeden wiersz w dół.  
  
- Przewija SB_LINEUP jeden wiersz w górę.  
  
- Przewija SB_PAGEDOWN jedną stronę w dół.  
  
- Przewija SB_PAGEUP jedną stronę w górę.  
  
- SB_THUMBTRACK Drags przewiń okno na określonej pozycji. Bieżąca pozycja jest określona w *nPos*.  
  
- Przewija SB_TOP do góry.  
  
 *nPos*  
 Zawiera bieżącą pozycję pola przewijania, jeśli kod pasek przewijania jest SB_THUMBTRACK; w przeciwnym razie nie jest używany. W zależności od zakresu początkowej przewijania *nPos* może być ujemna ani powinny być rzutowane na **int** w razie potrzeby.  
  
 *bDoScroll*  
 Określa, czy rzeczywiście należy wykonać przewijania określonej akcji. Jeśli PRAWDA, następnie przewijanie powinno nastąpić; w przypadku wartości FAŁSZ następnie przewijanie nie powinien wystąpić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli *bDoScroll* ma wartość TRUE i widoku została faktycznie przewijane, zwracany jest różna od zera; w przeciwnym razie 0. Jeśli *bDoScroll* jest wartość FAŁSZ, a następnie zwraca wartość, która będzie zwrócono Jeśli *bDoScroll* zostały wartość TRUE, nawet jeśli użytkownik faktycznie nie przewijania.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku jednego ta funkcja jest wywoływana przez platformę z *bDoScroll* ustawiona na wartość TRUE, gdy widok otrzyma komunikat pasek przewijania. W takim przypadku należy faktycznie przewijania widoku. W przeciwnym razie ta funkcja jest wywoływana z *bDoScroll* ustawiona na wartość FALSE, gdy element OLE początkowo zostanie przeciągnięty w regionie przewijania automatycznego miejsca docelowego przed faktycznie przewijanie ma miejsce. W takim przypadku należy nie faktycznie przewijania widoku.  
  
##  <a name="onscrollby"></a>  CView::OnScrollBy  
 Wywoływane przez platformę, gdy użytkownik odwiedza obszarze poza obecny widoku dokumentu, przeciągając element OLE względem granic bieżącego widoku lub manipulowanie pionowych lub poziomych pasków przewijania.  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *sizeScroll*  
 Liczba pikseli przewijane w poziomie i w pionie.  
  
 *bDoScroll*  
 Określa, czy występuje przewijania widoku. Jeśli PRAWDA, następnie przewijanie ma miejsce; w przypadku wartości FAŁSZ następnie przewijanie nie występuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli widok mógł być przewijane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 W klasach pochodnych ta metoda sprawdza, czy widok jest przewijany w kierunku użytkownik zażądał, a następnie aktualizuje nowego regionu, w razie potrzeby. Ta funkcja jest automatycznie wywoływana [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) do wykonania rzeczywistego żądania przewijania.  
  
 Domyślna implementacja tej metody nie zmienia widoku, ale jeśli nie zostanie wywołany, widok nie będzie przewijany w `CScrollView`-klasy.  
  
 Jeśli dokument szerokości lub wysokości przekracza 32767 pikseli, przewijanie poza 32767 będzie działać, ponieważ `OnScrollBy` jest wywoływana z nieprawidłową *sizeScroll* argumentu.  
  
##  <a name="onupdate"></a>  CView::OnUpdate  
 Wywoływane przez platformę po zmodyfikowaniu widoku dokumentu; Ta funkcja jest wywoływana [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) i umożliwia widoku, aby zaktualizować jej wyświetlania w celu odzwierciedlenia tych zmian.  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>Parametry  
 *pSender*  
 Wskazuje widok, który zmodyfikował dokument, lub wartość NULL, jeśli mają być aktualizowane wszystkie widoki.  
  
 *lHint*  
 Zawiera informacje dotyczące zmiany.  
  
 *pHint*  
 Punkty do przechowywania informacji na temat zmian obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jest również wywoływany przez domyślną implementację elementu [OnInitialUpdate](#oninitialupdate). Domyślna implementacja unieważnia całego obszaru klienta, oznaczając je do malowania po odebraniu następny komunikat WM_PAINT. Należy przesłonić tę funkcję, jeśli chcesz zaktualizować tylko tych regionów, które mapują zmodyfikowane części dokumentu. W tym celu należy przekazać informacji na temat zmiany przy użyciu parametrów wskazówki.  
  
 Aby użyć *lHint*, zdefiniuj wartości wskazówka specjalne, zwykle maską bitów lub Typ wyliczany i dokument przekazać jedną z następujących wartości. Aby użyć *pHint*, klasa wyprowadzona z wskazówka [CObject](../../mfc/reference/cobject-class.md) i przekazać wskaźnik do obiektu wskazówkę; w przypadku przesłaniania dokumentu `OnUpdate`, użyj [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) Funkcja członkowska można ustalić typu czasu wykonywania obiektu wskazówki.  
  
 Zazwyczaj powinien nie wykonywania rysowanie bezpośrednio z `OnUpdate`. Zamiast tego należy określić prostokąt opisujący we współrzędnych urządzenia obszar, który wymaga zaktualizowania; Przekaż prostokąta do [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Powoduje to rysowania do przy następnym [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) odebrać wiadomości.  
  
 Jeśli *lHint* 0 i *pHint* ma wartość NULL, dokumentu zostało wysłane powiadomienie o aktualizacji ogólnych. Jeśli widok otrzyma powiadomienie o aktualizacji ogólnych lub nie można zdekodować wskazówek, należy go unieważnienie obszaru klienckiego cały.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Klasa CDocument](../../mfc/reference/cdocument-class.md)
