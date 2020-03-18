---
title: Klasa CDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420611"
---
# <a name="cdoctemplate-class"></a>Klasa CDocTemplate

Abstrakcyjna klasa bazowa, która definiuje podstawowe funkcje szablonów dokumentów.

## <a name="syntax"></a>Składnia

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Konstruuje obiekt `CDocTemplate`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocTemplate:: AddDocument](#adddocument)|Dodaje dokument do szablonu.|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zamyka wszystkie dokumenty skojarzone z tym szablonem.|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Tworzy nowy dokument.|
|[CDocTemplate::CreateNewFrame](#createnewframe)|Tworzy nowe okno ramek zawierające dokument i widok.|
|[CDocTemplate::CreateOleFrame](#createoleframe)|Tworzy okno ramki z obsługą OLE.|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Tworzy ramkę podrzędną używaną dla zaawansowanej wersji zapoznawczej.|
|[CDocTemplate::GetDocString](#getdocstring)|Pobiera ciąg skojarzony z typem dokumentu.|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Pobiera pozycję pierwszego dokumentu skojarzonego z tym szablonem.|
|[CDocTemplate::GetNextDoc](#getnextdoc)|Pobiera dokument i położenie następnego.|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicjuje okno ramki i opcjonalnie sprawia, że jest ono widoczne.|
|[CDocTemplate::LoadTemplate](#loadtemplate)|Ładuje zasoby dla danego `CDocTemplate` lub klasy pochodnej.|
|[CDocTemplate::MatchDocType](#matchdoctype)|Określa stopień zaufania w dopasowaniu między typem dokumentu a tym szablonem.|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otwiera plik określony przez nazwę ścieżki.|
|[CDocTemplate::RemoveDocument](#removedocument)|Usuwa dokument z szablonu.|
|[CDocTemplate::SaveAllModified](#saveallmodified)|Zapisuje wszystkie dokumenty skojarzone z tym szablonem, które zostały zmodyfikowane.|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Określa zasoby dla kontenerów OLE podczas edycji elementu OLE w miejscu.|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Wyświetla domyślny tytuł na pasku tytułu okna dokumentu.|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Instalator procedury obsługi podglądu procesu.|
|[CDocTemplate::SetServerInfo](#setserverinfo)|Określa zasoby i klasy, gdy dokument serwera jest osadzony lub edytowany w miejscu.|

## <a name="remarks"></a>Uwagi

Zwykle tworzony jest co najmniej jeden szablon dokumentu w implementacji funkcji `InitInstance` aplikacji. Szablon dokumentu definiuje relacje między trzema typami klas:

- Klasa dokumentu, która pochodzi od `CDocument`.

- Klasa widoku, która wyświetla dane z klasy dokumentu wymienionej powyżej. Tę klasę można utworzyć na podstawie `CView`, `CScrollView`, `CFormView`lub `CEditView`. (Można również użyć `CEditView` bezpośrednio).

- Klasa okna ramki, która zawiera widok. W przypadku aplikacji interfejsu pojedynczego dokumentu (SDI) Klasa ta pochodzi od `CFrameWnd`. W przypadku aplikacji interfejsu wielu dokumentów (MDI) Klasa pochodzi od `CMDIChildWnd`. Jeśli nie musisz dostosowywać zachowania okna ramki, możesz użyć `CFrameWnd` lub `CMDIChildWnd` bezpośrednio bez wyznaczania własnych klas.

Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który obsługuje. Na przykład jeśli aplikacja obsługuje arkusze kalkulacyjne i dokumenty tekstowe, aplikacja ma dwa obiekty szablonu dokumentu. Każdy szablon dokumentu jest odpowiedzialny za tworzenie wszystkich dokumentów tego typu i zarządzanie nimi.

Szablon dokumentu przechowuje wskaźniki do `CRuntimeClass` obiektów dla klas dokumentów, widoków i okien ramowych. Te `CRuntimeClass` obiekty są określane podczas konstruowania szablonu dokumentu.

Szablon dokumentu zawiera identyfikator zasobów używanych z typem dokumentu (takiego jak menu, ikona lub zasoby tabeli akceleratora). Szablon dokumentu zawiera również ciągi zawierające dodatkowe informacje o typie dokumentu. Obejmują one nazwę typu dokumentu (na przykład "arkusz") i rozszerzenie pliku (na przykład "xls"). Opcjonalnie może zawierać inne ciągi używane przez interfejs użytkownika aplikacji, Menedżera plików systemu Windows oraz obsługę łączenia i osadzania obiektów (OLE).

Jeśli aplikacja jest kontenerem OLE i/lub serwerem, szablon dokumentu definiuje również identyfikator menu używane podczas aktywacji w miejscu. Jeśli aplikacja jest serwerem OLE, szablon dokumentu definiuje identyfikator paska narzędzi i menu używanego podczas aktywacji w miejscu. Możesz określić te dodatkowe zasoby OLE, wywołując `SetContainerInfo` i `SetServerInfo`.

Ponieważ `CDocTemplate` jest klasą abstrakcyjną, nie można użyć klasy bezpośrednio. Typowa aplikacja korzysta z jednej z dwóch klas pochodnych `CDocTemplate`dostarczonych przez biblioteka MFC: `CSingleDocTemplate`, która implementuje interfejs SDI i `CMultiDocTemplate`, który implementuje MDI. Zobacz te klasy, aby uzyskać więcej informacji o korzystaniu z szablonów dokumentów.

Jeśli aplikacja wymaga modelu użytkownika, który różni się od interfejsu SDI lub MDI, można utworzyć własną klasę z `CDocTemplate`.

Aby uzyskać więcej informacji na temat `CDocTemplate`, zobacz [Szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="adddocument"></a>CDocTemplate:: AddDocument

Użyj tej funkcji, aby dodać dokument do szablonu.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskaźnik do dokumentu, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Klasy pochodne [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) i [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) przesłaniają tę funkcję. W przypadku wyprowadzania własnej klasy szablonu dokumentu od `CDocTemplate`, Klasa pochodna musi zastąpić tę funkcję.

##  <a name="cdoctemplate"></a>CDocTemplate::CDocTemplate

Konstruuje obiekt `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Określa identyfikator zasobów używanych z typem dokumentu. Może to obejmować menu, ikonę, tabelę akceleratorów i zasoby ciągu.

Zasób ciągu składa się z maksymalnie siedmiu podciągów oddzielonych znakiem "\n" (znak "\n" jest potrzebny jako symbol zastępczy, jeśli podciąg nie jest uwzględniony, ale kończy się znakiem "\n"); te podciągi opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [GetDocString](#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Należy zauważyć, że ciąg rozpoczyna się od znaku "\n"; jest to spowodowane tym, że pierwszy podciąg nie jest używany w aplikacjach MDI i dlatego nie jest uwzględniony. Można edytować ten ciąg za pomocą edytora ciągów; cały ciąg pojawia się jako pojedynczy wpis w edytorze ciągów, a nie jako siedem oddzielnych wpisów.

*pDocClass*<br/>
Wskazuje obiekt `CRuntimeClass` klasy dokumentu. Ta klasa jest klasą pochodną `CDocument`, która jest definiowana do reprezentowania dokumentów.

*pFrameClass*<br/>
Wskazuje obiekt `CRuntimeClass` klasy okna ramek. Ta klasa może być klasą pochodną `CFrameWnd`lub można ją `CFrameWnd`, jeśli chcesz, aby domyślne zachowanie głównego okna ramki.

*pViewClass*<br/>
Wskazuje obiekt `CRuntimeClass` klasy widoku. Ta klasa jest klasą pochodną `CView`, która jest definiowana do wyświetlania dokumentów.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska służy do konstruowania obiektu `CDocTemplate`. Dynamicznie Przydziel obiekt `CDocTemplate` i przekaż go do [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z funkcji składowej `InitInstance` klasy aplikacji.

##  <a name="closealldocuments"></a>CDocTemplate::CloseAllDocuments

Wywołaj tę funkcję elementu członkowskiego, aby zamknąć wszystkie otwarte dokumenty.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession*<br/>
Nie jest używany.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest zwykle używana jako część polecenia Zakończ plik. Domyślna implementacja tej funkcji wywołuje funkcję członkowską [CDocument::D eletecontents](../../mfc/reference/cdocument-class.md#deletecontents) , aby usunąć dane dokumentu, a następnie zamyka okna ramowe dla wszystkich widoków dołączonych do dokumentu.

Zastąp tę funkcję, jeśli chcesz, aby użytkownik musiał wykonać specjalne oczyszczanie przed zamknięciem dokumentu. Jeśli na przykład dokument reprezentuje rekord w bazie danych, można zastąpić tę funkcję, aby zamknąć bazę danych.

##  <a name="createnewdocument"></a>CDocTemplate::CreateNewDocument

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nowy dokument typu skojarzonego z tym szablonem dokumentu.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonego dokumentu lub wartość NULL w przypadku wystąpienia błędu.

##  <a name="createnewframe"></a>CDocTemplate::CreateNewFrame

Tworzy nowe okno ramek zawierające dokument i widok.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Dokument, do którego ma się odwoływać nowe okno ramki. Może mieć wartość NULL.

*pOther*<br/>
Okno ramek, na którym ma być oparta Nowa ramka. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo utworzonego okna ramki lub wartość NULL w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

`CreateNewFrame` używa obiektów `CRuntimeClass`, które przechodzą do konstruktora, aby utworzyć nowe okno ramki z dołączonym widokiem i dokumentem. Jeśli parametr *PDOC* ma wartość null, struktura GENERUJE komunikat śledzenia.

Parametr *pOther* jest używany do implementowania okna nowe polecenie. Zawiera okno ramowe, w którym należy modelować nowe okno ramek. Nowe okno ramki jest zwykle tworzone niewidoczne. Wywołaj tę funkcję, aby utworzyć okna ramowe poza standardową implementacją pliku nowy i Otwórz plik.

##  <a name="createoleframe"></a>CDocTemplate::CreateOleFrame

Tworzy okno ramki OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego ramki.

*pDoc*<br/>
Wskaźnik do dokumentu, do którego ma się odwoływać nowe okno ramki OLE.

*bCreateView*<br/>
Określa, czy widok jest tworzony wraz z ramką.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do okna ramki, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Jeśli *bCreateView* ma wartość zero, tworzona jest pusta ramka.

##  <a name="getdocstring"></a>CDocTemplate::GetDocString

Pobiera ciąg skojarzony z typem dokumentu.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do obiektu `CString`, który będzie zawierać ciąg, gdy funkcja zwraca wartość.

*indeks*<br/>
Indeks podciągu pobieranego z ciągu, który opisuje typ dokumentu. Ten parametr może mieć jedną z następujących wartości:

- Nazwa `CDocTemplate::windowTitle` wyświetlana na pasku tytułu okna aplikacji (na przykład "Microsoft Excel"). Występuje tylko w szablonie dokumentu dla aplikacji SDI.

- `CDocTemplate::docName` katalog główny dla nazwy dokumentu domyślnego (na przykład "arkusz"). Ten katalog główny i numer są używane jako domyślna nazwa nowego dokumentu tego typu za każdym razem, gdy użytkownik wybierze nowe polecenie z menu plik (na przykład "Arkusz1" lub "arkusz Arkusz2"). Jeśli nie zostanie określony, jako domyślny używany jest "bez tytułu".

- Nazwa `CDocTemplate::fileNewName` tego typu dokumentu. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, ten ciąg jest wyświetlany w oknie dialogowym Nowy plik (na przykład "arkusz"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny przy użyciu polecenia nowy plik.

- `CDocTemplate::filterName` opis typu dokumentu oraz filtr symboli wieloznacznych pasujących do dokumentów tego typu. Ten ciąg jest wyświetlany na liście rozwijanej listy plików typu w oknie dialogowym Otwieranie pliku (na przykład "arkusze (*. xls)"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny przy użyciu polecenia Otwórz plik.

- `CDocTemplate::filterExt` rozszerzenie dla dokumentów tego typu (na przykład "xls"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny przy użyciu polecenia Otwórz plik.

- Identyfikator `CDocTemplate::regFileTypeId` typu dokumentu, który ma być przechowywany w bazie danych rejestracji obsługiwanej przez system Windows. Ten ciąg służy tylko do użytku wewnętrznego (na przykład "ExcelWorksheet"). Jeśli nie zostanie określony, typ dokumentu nie może być zarejestrowany w Menedżerze plików systemu Windows.

- Nazwa `CDocTemplate::regFileTypeName` typu dokumentu, który ma być przechowywany w bazie danych rejestracji. Ten ciąg może być wyświetlany w oknach dialogowych aplikacji, które uzyskują dostęp do bazy danych rejestracji (na przykład "arkusz programu Microsoft Excel").

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli znaleziono określony podciąg; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać konkretny podciąg opisujący typ dokumentu. Ciąg zawierający te podciągi jest przechowywany w szablonie dokumentu i pochodzi od ciągu w pliku zasobów dla aplikacji. Struktura wywołuje tę funkcję, aby uzyskać ciągi potrzebne do interfejsu użytkownika aplikacji. Jeśli określono rozszerzenie nazwy pliku dla dokumentów aplikacji, struktura wywołuje również tę funkcję przy dodawaniu wpisu do bazy danych rejestracji systemu Windows; pozwala to otwierać dokumenty z Menedżera plików systemu Windows.

Wywołaj tę funkcję tylko w przypadku wyprowadzania własnej klasy z `CDocTemplate`.

##  <a name="getfirstdocposition"></a>CDocTemplate::GetFirstDocPosition

Pobiera pozycję pierwszego dokumentu skojarzonego z tym szablonem.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość pozycji, która może służyć do iteracji na liście dokumentów skojarzonych z tym szablonem dokumentu; lub wartość NULL, jeśli lista jest pusta.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby pobrać pozycję pierwszego dokumentu na liście dokumentów skojarzonych z tym szablonem. Użyj wartości POSITION jako argumentu do [CDocTemplate:: GetNextDoc](#getnextdoc) , aby wykonać iterację listy dokumentów skojarzonych z szablonem.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) i [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) zastępują te czyste funkcje wirtualne. Każda klasa pochodna `CDocTemplate` musi również przesłaniać tę funkcję.

##  <a name="getnextdoc"></a>CDocTemplate::GetNextDoc

Pobiera element list identyfikowany przez *RPO*, a następnie ustawia *RPO* na wartość pozycji następnego wpisu na liście.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do następnego dokumentu na liście dokumentów skojarzonych z tym szablonem.

### <a name="parameters"></a>Parametry

*RPO*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie wywołanie [GetFirstDocPosition](#getfirstdocposition) lub `GetNextDoc`.

### <a name="remarks"></a>Uwagi

Jeśli pobrany element jest ostatni na liście, Nowa wartość *RPO* jest ustawiona na wartość null.

Możesz użyć `GetNextDoc` w pętli iteracji do przodu, jeśli zostanie nadana początkowa pozycja z wywołaniem do [GetFirstDocPosition](#getfirstdocposition).

Musisz się upewnić, że wartość pozycji reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowana biblioteka MFC potwierdzenia.

##  <a name="initialupdateframe"></a>CDocTemplate::InitialUpdateFrame

Inicjuje okno ramki i opcjonalnie sprawia, że jest ono widoczne.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Okno ramki, które wymaga początkowej aktualizacji.

*pDoc*<br/>
Dokument, z którym jest skojarzona ramka. Może mieć wartość NULL.

*bMakeVisible*<br/>
Wskazuje, czy ramka powinna być widoczna i aktywna.

### <a name="remarks"></a>Uwagi

Wywołaj `IntitialUpdateFrame` po utworzeniu nowej ramki z `CreateNewFrame`. Wywołanie tej funkcji powoduje, że widoki w tym oknie ramki są odbierane `OnInitialUpdate` wywołania. Ponadto, jeśli nie był wcześniej aktywny widok, podstawowy widok okna ramki zostanie uaktywniony; Widok podstawowy to widok z IDENTYFIKATORem podrzędnym AFX_IDW_PANE_FIRST. Na koniec okno ramki jest widoczne, jeśli *bMakeVisible* jest różna od zera. Jeśli *bMakeVisible* ma wartość zero, bieżący fokus i stan widoczny okna ramki pozostaną bez zmian.

Nie jest konieczne Wywołaj tę funkcję w przypadku korzystania z implementacji pliku New i Open pliku przez platformę.

##  <a name="loadtemplate"></a>CDocTemplate::LoadTemplate

Ładuje zasoby dla danego `CDocTemplate` lub klasy pochodnej.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w celu załadowania zasobów dla danego `CDocTemplate` lub klasy pochodnej. Zwykle jest wywoływana podczas konstruowania, z wyjątkiem sytuacji, gdy szablon jest konstruowany globalnie. W takim przypadku wywołanie `LoadTemplate` jest opóźnione do momentu wywołania [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) .

##  <a name="matchdoctype"></a>CDocTemplate::MatchDocType

Określa stopień zaufania w dopasowaniu między typem dokumentu a tym szablonem.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Nazwa ścieżki pliku, którego typ ma zostać określony.

*rpDocMatch*<br/>
Wskaźnik do dokumentu, do którego przypisano pasujący dokument, jeśli plik określony przez *lpszPathName* jest już otwarty.

### <a name="return-value"></a>Wartość zwrócona

Wartość z wyliczenia **pewności** , która jest definiowana w następujący sposób:

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby określić typ szablonu dokumentu, który ma być używany do otwierania pliku. Jeśli aplikacja obsługuje wiele typów plików, na przykład za pomocą tej funkcji można określić, które z dostępnych szablonów dokumentów są odpowiednie dla danego pliku, wywołując `MatchDocType` dla każdego szablonu z kolei i wybierając szablon zgodnie z zwróconą wartością zaufania.

Jeśli plik określony przez *lpszPathName* jest już otwarty, ta funkcja zwraca `CDocTemplate::yesAlreadyOpen` i kopiuje obiekt `CDocument` pliku do obiektu w *rpDocMatch*.

Jeśli plik nie jest otwarty, ale rozszerzenie w *lpszPathName* dopasowuje rozszerzenie określone przez `CDocTemplate::filterExt`, ta funkcja zwraca `CDocTemplate::yesAttemptNative` i ustawia *rpDocMatch* na null. Aby uzyskać więcej informacji na temat `CDocTemplate::filterExt`, zobacz [CDocTemplate:: GetDocString](#getdocstring).

Jeśli żadna z przypadków ma wartość true, funkcja zwraca `CDocTemplate::yesAttemptForeign`.

Domyślna implementacja nie zwraca `CDocTemplate::maybeAttemptForeign` ani `CDocTemplate::maybeAttemptNative`. Przesłoń tę funkcję, aby zaimplementować logikę zgodną z typem odpowiednim dla aplikacji, na przykład korzystając z tych dwóch wartości z wyliczenia **zaufania** .

##  <a name="opendocumentfile"></a>CDocTemplate::OpenDocumentFile

Otwiera plik określony przez ścieżkę.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
podczas Wskaźnik do ścieżki pliku zawierającego dokument do otwarcia.

*bAddToMRU*<br/>
podczas Wartość TRUE wskazuje, że dokument jest jednym z najnowszych plików; Wartość FALSE wskazuje, że dokument nie jest jednym z najnowszych plików.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do dokumentu, którego plik jest nazwany przez *lpszPathName*; Wartość NULL, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Otwiera plik, którego ścieżka jest określona przez *lpszPathName*. Jeśli *lpszPathName* ma wartość null, tworzony jest nowy plik zawierający dokument typu skojarzonego z tym szablonem.

##  <a name="removedocument"></a>CDocTemplate::RemoveDocument

Usuwa dokument wskazany przez *PDOC* z listy dokumentów skojarzonych z tym szablonem.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskaźnik do dokumentu, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Klasy pochodne `CMultiDocTemplate` i `CSingleDocTemplate` przesłaniają tę funkcję. W przypadku wyprowadzania własnej klasy szablonu dokumentu od `CDocTemplate`, Klasa pochodna musi zastąpić tę funkcję.

##  <a name="saveallmodified"></a>CDocTemplate::SaveAllModified

Zapisuje wszystkie dokumenty, które zostały zmodyfikowane.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość niezerowa, jeśli powodzenie; w przeciwnym razie 0.

##  <a name="setcontainerinfo"></a>CDocTemplate::SetContainerInfo

Określa zasoby dla kontenerów OLE podczas edycji elementu OLE w miejscu.

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parametry

*nIDOleInPlaceContainer*<br/>
Identyfikator zasobów używany podczas aktywowania osadzonego obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić zasoby, które będą używane, gdy obiekt OLE jest aktywowany. Te zasoby mogą obejmować menu i tabele akceleratorów. Ta funkcja jest zazwyczaj wywoływana w funkcji [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) aplikacji.

Menu skojarzone z *nIDOleInPlaceContainer* zawiera separatory zezwalające menu aktywowanego elementu w miejscu do scalenia z menu aplikacji kontenera. Aby uzyskać więcej informacji na temat scalania menu serwera i kontenera, zobacz [menu artykułów i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="setdefaulttitle"></a>CDocTemplate::SetDefaultTitle

Wywołaj tę funkcję, aby załadować tytuł domyślny dokumentu i wyświetlić go na pasku tytułu dokumentu.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parametry

*pDocument*<br/>
Wskaźnik do dokumentu, którego tytuł ma być ustawiony.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat domyślnego tytułu, zobacz Opis `CDocTemplate::docName` w [CDocTemplate:: GetDocString](#getdocstring).

##  <a name="setserverinfo"></a>CDocTemplate::SetServerInfo

Określa zasoby i klasy, gdy dokument serwera jest osadzony lub edytowany w miejscu.

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDOleEmbedding*<br/>
Identyfikator zasobów używanych, gdy osadzony obiekt jest otwierany w osobnym oknie.

*nIDOleInPlaceServer*<br/>
Identyfikator zasobów używanych, gdy osadzony obiekt jest aktywowany w miejscu.

*pOleFrameClass*<br/>
Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) zawierającej informacje o klasie dla obiektu okna ramki tworzonego podczas aktywacji w miejscu.

*pOleViewClass*<br/>
Wskaźnik do struktury `CRuntimeClass` zawierającej informacje o klasie dla obiektu widoku utworzonego podczas aktywacji w miejscu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby identyfikować zasoby, które będą używane przez aplikację serwera, gdy użytkownik zażąda aktywacji obiektu osadzonego. Te zasoby składają się z menu i tabel akceleratorów. Ta funkcja jest zwykle wywoływana w `InitInstance` aplikacji.

Menu skojarzone z *nIDOleInPlaceServer* zawiera separatory, które umożliwiają scalanie menu serwera z menu kontenera. Aby uzyskać więcej informacji na temat scalania menu serwera i kontenera, zobacz [menu artykułów i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).

##  <a name="createpreviewframe"></a>CDocTemplate::CreatePreviewFrame

Tworzy ramkę podrzędną używaną dla zaawansowanej wersji zapoznawczej.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego (zwykle udostępnianego przez powłokę).

*pDoc*<br/>
Wskaźnik do obiektu dokumentu, którego zawartość będzie wyświetlana w podglądzie.

### <a name="return-value"></a>Wartość zwrócona

Prawidłowy wskaźnik do obiektu `CFrameWnd` lub wartość NULL, jeśli Tworzenie nie powiedzie się.

### <a name="remarks"></a>Uwagi

##  <a name="setpreviewinfo"></a>CDocTemplate::SetPreviewInfo

Konfiguruje procedurę obsługi podglądu poza procesem.

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDPreviewFrame*<br/>
Określa identyfikator zasobu ramki podglądu.

*pPreviewFrameClass*<br/>
Określa wskaźnik do struktury informacji klasy środowiska uruchomieniowego ramki podglądu.

*pPreviewViewClass*<br/>
Określa wskaźnik do struktury informacji o klasie środowiska uruchomieniowego widoku podglądu.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CScrollView](../../mfc/reference/cscrollview-class.md)<br/>
[Klasa CEditView](../../mfc/reference/ceditview-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
