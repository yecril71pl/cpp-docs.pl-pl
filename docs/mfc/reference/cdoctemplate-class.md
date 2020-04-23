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
ms.openlocfilehash: 69b94a4188804f47c950ca31fb5cba80d85176e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753298"
---
# <a name="cdoctemplate-class"></a>Klasa CDocTemplate

Abstrakcyjna klasa podstawowa definiująca podstawowe funkcje szablonów dokumentów.

## <a name="syntax"></a>Składnia

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[Płyta CDocTemplate::CDocTemplate](#cdoctemplate)|Konstruuje `CDocTemplate` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Płyta CDocTemplate::AddDocument](#adddocument)|Dodaje dokument do szablonu.|
|[Płyta CDocTemplate::CloseAllDocuments](#closealldocuments)|Zamyka wszystkie dokumenty skojarzone z tym szablonem.|
|[Płyta CDocTemplate::CreateNewDocument](#createnewdocument)|Tworzy nowy dokument.|
|[Płyta CDocTemplate::CreateNewFrame](#createnewframe)|Tworzy nowe okno ramki zawierające dokument i widok.|
|[Płyta CDocTemplate::CreateOleFrame](#createoleframe)|Tworzy okno ramki z obsługą OLE.|
|[Płyta CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Tworzy ramkę podrzędną używaną w rozszerzonym podglądzie.|
|[Płyta CDocTemplate::GetDocString](#getdocstring)|Pobiera ciąg skojarzony z typem dokumentu.|
|[Płyta CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Pobiera położenie pierwszego dokumentu skojarzonego z tym szablonem.|
|[Płyta CDocTemplate::GetNextDoc](#getnextdoc)|Pobiera dokument i położenie następnego.|
|[Płyta CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicjuje okno ramki i opcjonalnie sprawia, że jest widoczna.|
|[Płyta CDocTemplate::LoadTemplate](#loadtemplate)|Ładuje zasoby dla `CDocTemplate` danej lub pochodnej klasy.|
|[Płyta CDocTemplate::MatchDocType](#matchdoctype)|Określa stopień zaufania do dopasowania między typem dokumentu a tym szablonem.|
|[Płyta CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otwiera plik określony przez nazwę ścieżki.|
|[Płyta CDocTemplate::Usuńdokument](#removedocument)|Usuwa dokument z szablonu.|
|[Płyta CDocTemplate::SaveAllModified](#saveallmodified)|Zapisuje wszystkie dokumenty skojarzone z tym szablonem, które zostały zmodyfikowane.|
|[Płyta CDocTemplate::SetContainerInfo](#setcontainerinfo)|Określa zasoby dla kontenerów OLE podczas edytowania elementu OLE w miejscu.|
|[Płyta CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Wyświetla domyślny tytuł na pasku tytułu okna dokumentu.|
|[Płyta CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Instalatory poza programem obsługi podglądu procesu.|
|[Płyta CDocTemplate::SetServerInfo](#setserverinfo)|Określa zasoby i klasy, gdy dokument serwera jest osadzony lub edytowany w miejscu.|

## <a name="remarks"></a>Uwagi

Zwykle tworzysz jeden lub więcej szablonów dokumentów w `InitInstance` implementacji funkcji aplikacji. Szablon dokumentu definiuje relacje między trzema typami klas:

- Klasa dokumentu, z `CDocument`której pochodzisz .

- Klasa widoku, która wyświetla dane z klasy dokumentu wymienionej powyżej. Tę klasę można wyprowadzić `CScrollView` `CFormView`z `CView` `CEditView`, , , lub . (Można również `CEditView` użyć bezpośrednio.)

- Klasa okna ramki, która zawiera widok. Dla aplikacji interfejsu pojedynczego dokumentu (SDI) należy `CFrameWnd`wyprowadzić tę klasę z programu . Dla aplikacji interfejsu wielu dokumentów (MDI) należy `CMDIChildWnd`wyprowadzić tę klasę z programu . Jeśli nie trzeba dostosowywać zachowanie okna ramki, można `CFrameWnd` użyć `CMDIChildWnd` lub bezpośrednio bez wyprowadzania własnej klasy.

Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który obsługuje. Jeśli na przykład aplikacja obsługuje zarówno arkusze kalkulacyjne, jak i dokumenty tekstowe, aplikacja ma dwa obiekty szablonu dokumentu. Każdy szablon dokumentu jest odpowiedzialny za tworzenie i zarządzanie wszystkimi dokumentami tego typu.

Szablon dokumentu przechowuje wskaźniki `CRuntimeClass` do obiektów dla klas okien dokumentu, widoku i ramki. Obiekty `CRuntimeClass` te są określone podczas konstruowania szablonu dokumentu.

Szablon dokumentu zawiera identyfikator zasobów używanych z typem dokumentu (takich jak zasoby menu, ikony lub tabeli akceleratora). Szablon dokumentu zawiera również ciągi zawierające dodatkowe informacje o jego typie dokumentu. Należą do nich nazwa typu dokumentu (na przykład "Arkusz") i rozszerzenia pliku (na przykład "xls"). Opcjonalnie może zawierać inne ciągi używane przez interfejs użytkownika aplikacji, Menedżera plików systemu Windows oraz obsługę łączenia i osadzania obiektów (OLE).

Jeśli aplikacja jest kontenerem OLE i/lub serwerem, szablon dokumentu definiuje również identyfikator menu używanego podczas aktywacji w miejscu. Jeśli aplikacja jest serwerem OLE, szablon dokumentu definiuje identyfikator paska narzędzi i menu używane podczas aktywacji w miejscu. Te dodatkowe zasoby OLE `SetContainerInfo` można `SetServerInfo`określić, wywołując i .

Ponieważ `CDocTemplate` jest klasą abstrakcyjną, nie można użyć klasy bezpośrednio. Typowa aplikacja używa jednej `CDocTemplate`z dwóch klas pochodnych dostarczonych `CSingleDocTemplate`przez bibliotekę klas Microsoft `CMultiDocTemplate`Foundation: , która implementuje SDI i , która implementuje MDI. Zobacz te klasy, aby uzyskać więcej informacji na temat korzystania z szablonów dokumentów.

Jeśli aplikacja wymaga paradygmatu interfejsu użytkownika, który zasadniczo różni się od SDI `CDocTemplate`lub MDI, można wyprowadzić własną klasę z .

Aby uzyskać `CDocTemplate`więcej informacji na temat , zobacz [Szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a>Płyta CDocTemplate::AddDocument

Ta funkcja służy do dodawania dokumentu do szablonu.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskaźnik do dokumentu, który ma zostać dodany.

### <a name="remarks"></a>Uwagi

Klasy pochodne [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) i [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) zastępują tę funkcję. Jeśli pochodzisz z własnej klasy `CDocTemplate`szablonu dokumentu z , klasa pochodna musi zastąpić tę funkcję.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a>Płyta CDocTemplate::CDocTemplate

Konstruuje `CDocTemplate` obiekt.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDSerwród*<br/>
Określa identyfikator zasobów używanych z typem dokumentu. Może to obejmować menu, ikonę, tabelę akceleratora i zasoby ciągów.

Zasób ciągu składa się z maksymalnie siedmiu podciągów oddzielonych znakiem '\n' (znak '\n' jest potrzebny jako uchwyt miejsca, jeśli podciąg nie jest uwzględniony; jednak końcowe znaki "\n"; te podciągi opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [GetDocString](#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Należy zauważyć, że ciąg zaczyna się od znaku '\n'; jest to spowodowane pierwszym podciągiem nie jest używany dla aplikacji MDI i tak nie jest uwzględniony. Ten ciąg można edytować za pomocą edytora ciągów; cały ciąg pojawia się jako pojedynczy wpis w Edytorze ciągów, a nie jako siedem oddzielnych wpisów.

*pDocClass (klasa pDocClass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa `CDocument`jest klasą pochodną, którą definiujesz w celu reprezentowania dokumentów.

*pFrameClass (klasa pFrameclass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy okna ramki. Ta klasa może `CFrameWnd`być klasą pochodną `CFrameWnd` lub może być sama, jeśli chcesz domyślne zachowanie dla okna ramki głównej.

*pViewClass (Klasa widoków)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa `CView`jest klasą pochodną zdefiniowaną w celu wyświetlenia dokumentów.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego `CDocTemplate` służy do konstruowania obiektu. Dynamicznie przydzielić `CDocTemplate` obiekt i przekazać go do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z funkcji `InitInstance` elementu członkowskiego klasy aplikacji.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a>Płyta CDocTemplate::CloseAllDocuments

Wywołanie tej funkcji elementu członkowskiego, aby zamknąć wszystkie otwarte dokumenty.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parametry

*bEndSession (Niesienie)*<br/>
Nie używany.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest zwykle używana jako część polecenia Wyjście pliku. Domyślna implementacja tej funkcji wywołuje [CDocument::DeleteContents funkcji członkowskiej,](../../mfc/reference/cdocument-class.md#deletecontents) aby usunąć dane dokumentu, a następnie zamyka okna ramki dla wszystkich widoków dołączonych do dokumentu.

Zastąpuj tę funkcję, jeśli chcesz wymagać od użytkownika wykonania specjalnego przetwarzania oczyszczania przed zamknięciem dokumentu. Na przykład jeśli dokument reprezentuje rekord w bazie danych, można zastąpić tę funkcję, aby zamknąć bazę danych.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a>Płyta CDocTemplate::CreateNewDocument

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć nowy dokument typu skojarzonego z tym szablonem dokumentu.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego dokumentu lub NULL, jeśli wystąpi błąd.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a>Płyta CDocTemplate::CreateNewFrame

Tworzy nowe okno ramki zawierające dokument i widok.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Dokument, do którego powinno się odnosić nowe okno ramki. Może mieć wartość NULL.

*pOther*<br/>
Okno ramki, na którym ma być oparte nowe okno ramki. Może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo utworzonego okna ramki lub NULL, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

`CreateNewFrame`używa `CRuntimeClass` obiektów przekazanych do konstruktora, aby utworzyć nowe okno ramki z dołączonym widokiem i dokumentem. Jeśli parametr *pDoc* ma wartość NULL, struktura wysyła komunikat TRACE.

Parametr *pOther* jest używany do implementacji polecenia Okno Nowe. Zapewnia okno ramki, na którym można modelować nowe okno ramki. Nowe okno ramki jest zwykle tworzone jako niewidoczne. Wywołanie tej funkcji, aby utworzyć okna ramki poza standardową implementacją struktury File New i File Open.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a>Płyta CDocTemplate::CreateOleFrame

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
Wskaźnik do dokumentu, do którego powinno się odnosić nowe okno ramki OLE.

*bCreateView*<br/>
Określa, czy widok jest tworzony wraz z ramką.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Jeśli *bCreateView* wynosi zero, tworzona jest pusta ramka.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a>Płyta CDocTemplate::GetDocString

Pobiera ciąg skojarzony z typem dokumentu.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do `CString` obiektu, który będzie zawierał ciąg, gdy funkcja zwraca.

*Indeks*<br/>
Indeks podciągu pobieranego z ciągu opisującego typ dokumentu. Ten parametr może mieć jedną z następujących wartości:

- `CDocTemplate::windowTitle`Nazwa wyświetlana na pasku tytułu okna aplikacji (na przykład "Microsoft Excel"). Prezentowanie tylko w szablonie dokumentu dla aplikacji SDI.

- `CDocTemplate::docName`Korzeń domyślnej nazwy dokumentu (na przykład "Arkusz"). Ten katalog główny oraz liczba jest używana dla domyślnej nazwy nowego dokumentu tego typu za każdym razem, gdy użytkownik wybierze polecenie Nowy z menu Plik (na przykład "Arkusz1" lub "Arkusz2"). Jeśli nie zostanie określony, "Bez tytułu" jest używany jako wartość domyślna.

- `CDocTemplate::fileNewName`Nazwa tego typu dokumentu. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, ten ciąg jest wyświetlany w oknie dialogowym Plik nowy (na przykład "Arkusz"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny za pomocą polecenia Plik nowy.

- `CDocTemplate::filterName`Opis typu dokumentu i filtru wieloznacznego pasującego do dokumentów tego typu. Ten ciąg jest wyświetlany na liście rozwijanej Pliki listy typów w oknie dialogowym Otwieranie plików (na przykład "Arkusze (*.xls)"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny za pomocą polecenia Otwieranie pliku.

- `CDocTemplate::filterExt`Rozszerzenie dla dokumentów tego typu (na przykład "xls"). Jeśli nie zostanie określony, typ dokumentu jest niedostępny za pomocą polecenia Otwieranie pliku.

- `CDocTemplate::regFileTypeId`Identyfikator typu dokumentu, który ma być przechowywany w bazie danych rejestracji obsługiwanej przez system Windows. Ten ciąg jest przeznaczony tylko do użytku wewnętrznego (na przykład "ExcelWorksheet"). Jeśli nie zostanie określony, nie można zarejestrować typu dokumentu w Menedżerze plików systemu Windows.

- `CDocTemplate::regFileTypeName`Nazwa typu dokumentu, który ma być przechowywany w bazie danych rejestracji. Ten ciąg może być wyświetlany w oknach dialogowych aplikacji uzyskujących dostęp do bazy danych rejestracji (na przykład "Arkusz programu Microsoft Excel").

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli znaleziono określony podciąg; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby pobrać określony podciąg opisujący typ dokumentu. Ciąg zawierający te podciągi są przechowywane w szablonie dokumentu i pochodzi od ciągu w pliku zasobu dla aplikacji. Struktura wywołuje tę funkcję, aby uzyskać ciągi potrzebne dla interfejsu użytkownika aplikacji. Jeśli określono rozszerzenie nazwy pliku dla dokumentów aplikacji, struktura wywołuje również tę funkcję podczas dodawania wpisu do bazy danych rejestracji systemu Windows; umożliwia to otwarcie dokumentów z Menedżera plików systemu Windows.

Wywołanie tej funkcji tylko wtedy, gdy `CDocTemplate`wyprowadzasz własną klasę z .

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a>Płyta CDocTemplate::GetFirstDocPosition

Pobiera położenie pierwszego dokumentu skojarzonego z tym szablonem.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji za pośrednictwem listy dokumentów skojarzonych z tym szablonem dokumentu; lub NULL, jeśli lista jest pusta.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do uzyskania pozycji pierwszego dokumentu na liście dokumentów skojarzonych z tym szablonem. Użyj wartości POSITION jako argumentu [CDocTemplate::GetNextDoc,](#getnextdoc) aby iterować za pośrednictwem listy dokumentów skojarzonych z szablonem.

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) i [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) zastępują tę czystą wirtualną funkcję. Każda klasa, z `CDocTemplate` której pochodzisz, musi również zastąpić tę funkcję.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a>Płyta CDocTemplate::GetNextDoc

Pobiera element listy identyfikowany przez *rPos,* a następnie ustawia *rPos* na wartość POSITION następnego wpisu na liście.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego dokumentu na liście dokumentów skojarzonych z tym szablonem.

### <a name="parameters"></a>Parametry

*rPos*<br/>
Odwołanie do wartości POSITION zwróconej przez poprzednie wywołanie do `GetNextDoc` [GetFirstDocPosition](#getfirstdocposition) lub .

### <a name="remarks"></a>Uwagi

Jeśli pobrany element jest ostatnim na liście, nowa wartość *rPos* jest ustawiona na WARTOŚĆ NULL.

Można użyć `GetNextDoc` w pętli iteracji do przodu, jeśli ustanowisz pozycję początkową z wywołaniem [GetFirstDocPosition](#getfirstdocposition).

Należy upewnić się, że wartość POSITION reprezentuje prawidłową pozycję na liście. Jeśli jest nieprawidłowa, wersja debugowania biblioteki klas programu Microsoft Foundation potwierdza.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a>Płyta CDocTemplate::InitialUpdateFrame

Inicjuje okno ramki i opcjonalnie sprawia, że jest widoczna.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Parametry

*pFrame (klatka)*<br/>
Okno ramki, które wymaga początkowej aktualizacji.

*pDoc*<br/>
Dokument, z którym skojarzona jest ramka. Może mieć wartość NULL.

*bMakevisible (Widoczne)*<br/>
Wskazuje, czy ramka powinna stać się widoczna i aktywna.

### <a name="remarks"></a>Uwagi

Zadzwoń `IntitialUpdateFrame` po utworzeniu nowej `CreateNewFrame`ramki z . Wywołanie tej funkcji powoduje, że widoki `OnInitialUpdate` w tym oknie ramki do odbierania ich wywołań. Ponadto jeśli wcześniej nie było aktywnego widoku, widok podstawowy okna ramki jest aktywny; widok podstawowy jest widokiem o identyfikatorze podrzędnym AFX_IDW_PANE_FIRST. Na koniec okno ramki jest widoczne, jeśli *bMakeVisible* jest niezerowe. Jeśli *bMakeVisible* wynosi zero, bieżący fokus i widoczny stan okna ramki pozostaną niezmienione.

Nie jest konieczne wywołanie tej funkcji podczas korzystania z implementacji struktury File New i File Open.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a>Płyta CDocTemplate::LoadTemplate

Ładuje zasoby dla `CDocTemplate` danej lub pochodnej klasy.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez `CDocTemplate` platformę, aby załadować zasoby dla danej lub pochodnej klasy. Zwykle jest wywoływana podczas budowy, z wyjątkiem sytuacji, gdy szablon jest budowany globalnie. W takim przypadku wywołanie `LoadTemplate` jest opóźnione do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) jest wywoływana.

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a>Płyta CDocTemplate::MatchDocType

Określa stopień zaufania do dopasowania między typem dokumentu a tym szablonem.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Nazwa ścieżki pliku, którego typ ma zostać określony.

*rpDocMatch*<br/>
Wskaźnik do dokumentu, który jest przypisany do pasującego dokumentu, jeśli plik określony przez *lpszPathName* jest już otwarty.

### <a name="return-value"></a>Wartość zwracana

Wartość z wyliczenia **ufności,** która jest zdefiniowana w następujący sposób:

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

Ta funkcja służy do określania typu szablonu dokumentu używanego do otwierania pliku. Jeśli aplikacja obsługuje wiele typów plików, na przykład można użyć tej funkcji, aby określić, który `MatchDocType` z dostępnych szablonów dokumentów jest odpowiedni dla danego pliku, wywołując dla każdego szablonu z kolei i wybierając szablon zgodnie z zwróconą wartością zaufania.

Jeśli plik określony przez *lpszPathName* jest już `CDocTemplate::yesAlreadyOpen` otwarty, ta funkcja `CDocument` zwraca i kopiuje obiekt pliku do obiektu w *rpDocMatch*.

Jeśli plik nie jest otwarty, ale rozszerzenie w *lpszPathName* pasuje do rozszerzenia określonego przez `CDocTemplate::filterExt`, ta funkcja zwraca `CDocTemplate::yesAttemptNative` i ustawia *rpDocMatch* na NULL. Aby uzyskać `CDocTemplate::filterExt`więcej informacji na temat , zobacz [CDocTemplate::GetDocString](#getdocstring).

Jeśli żaden z tych przypadków `CDocTemplate::yesAttemptForeign`nie jest spełniony, funkcja zwraca wartość .

Domyślna implementacja `CDocTemplate::maybeAttemptForeign` nie `CDocTemplate::maybeAttemptNative`zwraca lub . Zastąpuj tę funkcję, aby zaimplementować logikę dopasowywania typów odpowiednią dla aplikacji, być może przy użyciu tych dwóch wartości z wyliczenia **zaufania.**

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a>Płyta CDocTemplate::OpenDocumentFile

Otwiera plik określony przez ścieżkę.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
[w] Wskaźnik do ścieżki pliku zawierającego dokument, który ma zostać otwarty.

*bAddToMRU*<br/>
[w] TRUE wskazuje, że dokument jest jednym z najnowszych plików; FALSE wskazuje, że dokument nie jest jednym z najnowszych plików.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do dokumentu, którego plik jest nazwany przez *lpszPathName*; NULL, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Otwiera plik, którego ścieżka jest określona przez *lpszPathName*. Jeśli *lpszPathName* ma wartość NULL, tworzony jest nowy plik zawierający dokument typu skojarzonego z tym szablonem.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a>Płyta CDocTemplate::Usuńdokument

Usuwa dokument wskazany przez *pDoc* z listy dokumentów skojarzonych z tym szablonem.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pDoc*<br/>
Wskaźnik do dokumentu do usunięcia.

### <a name="remarks"></a>Uwagi

Klasy `CMultiDocTemplate` pochodne `CSingleDocTemplate` i zastąpić tę funkcję. Jeśli pochodzisz z własnej klasy `CDocTemplate`szablonu dokumentu z , klasa pochodna musi zastąpić tę funkcję.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a>Płyta CDocTemplate::SaveAllModified

Zapisuje wszystkie dokumenty, które zostały zmodyfikowane.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a>Płyta CDocTemplate::SetContainerInfo

Określa zasoby dla kontenerów OLE podczas edytowania elementu OLE w miejscu.

```cpp
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Parametry

*NIDOleInPlaceContainer*<br/>
Identyfikator zasobów używanych podczas aktywowania obiektu osadzonego.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić zasoby, które mają być używane, gdy obiekt OLE jest w miejscu aktywowane. Zasoby te mogą obejmować menu i tabele akceleratora. Ta funkcja jest zwykle wywoływana w [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkcji aplikacji.

Menu skojarzone z *nIDOleInPlaceContainer* zawiera separatory, które umożliwiają scalanie menu aktywowanego elementu w miejscu z menu aplikacji kontenera. Aby uzyskać więcej informacji na temat scalania menu serwera i kontenerów, zobacz artykuł [Menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a>Płyta CDocTemplate::SetDefaultTitle

Wywołanie tej funkcji, aby załadować domyślny tytuł dokumentu i wyświetlić go na pasku tytułu dokumentu.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Parametry

*Pdocument*<br/>
Wskaźnik do dokumentu, którego tytuł ma być ustawiony.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat domyślnego tytułu, zobacz opis `CDocTemplate::docName` w [CDocTemplate::GetDocString](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a>Płyta CDocTemplate::SetServerInfo

Określa zasoby i klasy, gdy dokument serwera jest osadzony lub edytowany w miejscu.

```cpp
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDOleEmbedding*<br/>
Identyfikator zasobów używanych podczas otwartego obiektu osadzonego w osobnym oknie.

*Serwer nIDOleInPlaceServer*<br/>
Identyfikator zasobów używanych podczas aktywowania obiektu osadzonego w miejscu.

*pOleFrameClass (klasa pOleFrameClass)*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury zawierającej informacje o klasie dla obiektu okna ramki utworzonego podczas aktywacji w miejscu występuje.

*pOleViewClass (klasa)*<br/>
Wskaźnik do `CRuntimeClass` struktury zawierającej informacje o klasie dla obiektu widoku utworzonego podczas aktywacji w miejscu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego w celu zidentyfikowania zasobów, które będą używane przez aplikację serwera, gdy użytkownik żąda aktywacji obiektu osadzonego. Zasoby te składają się z menu i tabel akceleratora. Ta funkcja jest zwykle `InitInstance` wywoływana w aplikacji.

Menu skojarzone z *nIDOleInPlaceServer* zawiera separatory, które umożliwiają scalanie menu serwera z menu kontenera. Aby uzyskać więcej informacji na temat scalania menu serwera i kontenerów, zobacz artykuł [Menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a>Płyta CDocTemplate::CreatePreviewFrame

Tworzy ramkę podrzędną używaną w rozszerzonym podglądzie.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego (zwykle dostarczane przez Powłoki).

*pDoc*<br/>
Wskaźnik do obiektu dokumentu, którego zawartość zostanie wyświetlona w podglądzie.

### <a name="return-value"></a>Wartość zwracana

Prawidłowy wskaźnik `CFrameWnd` do obiektu lub NULL, jeśli tworzenie nie powiedzie się.

### <a name="remarks"></a>Uwagi

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a>Płyta CDocTemplate::SetPreviewInfo

Konfiguruje program obsługi podglądu poza procesem.

```cpp
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Parametry

*nIDPreviewFrame*<br/>
Określa identyfikator zasobu ramki podglądu.

*pPreviewFrameClass*<br/>
Określa wskaźnik do struktury informacji o klasie środowiska uruchomieniowego ramki podglądu.

*pPreviewViewClass*<br/>
Określa wskaźnik do struktury informacji o klasie środowiska uruchomieniowego w widoku podglądu.

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
