---
title: Klasa CDocument
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418700"
---
# <a name="cdocument-class"></a>Klasa CDocument

Oferuje podstawowe funkcje dla klas dokumentów zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocument:: CDocument](#cdocument)|Konstruuje obiekt `CDocument`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocument:: AddView](#addview)|Dołącza widok do dokumentu.|
|[CDocument:: BeginReadChunks](#beginreadchunks)|Inicjuje odczytywanie fragmentu.|
|[CDocument:: CanCloseFrame](#cancloseframe)|Zaawansowany zaawansowanie; wywołuje się przed zamknięciem okna ramki wyświetlającego ten dokument.|
|[CDocument:: ClearChunkList](#clearchunklist)|Czyści listę fragmentów.|
|[CDocument:: ClearPathName](#clearpathname)|Czyści ścieżkę obiektu dokumentu.|
|[CDocument::D eleteContents](#deletecontents)|Wywołuje się, by wykonać czyszczenie dokumentu.|
|[CDocument:: FindChunk](#findchunk)|Szuka fragmentu o określonym identyfikatorze GUID.|
|[CDocument:: getadapter](#getadapter)|Zwraca wskaźnik do obiektu implementującego interfejs `IDocument`.|
|[CDocument:: GetDocTemplate](#getdoctemplate)|Zwraca wskaźnik do szablonu dokumentu, który opisuje typ dokumentu.|
|[CDocument:: GetFile](#getfile)|Zwraca wskaźnik do żądanego obiektu `CFile`.|
|[CDocument:: GetFirstViewPosition](#getfirstviewposition)|Zwraca pozycję pierwszego z listy widoków; używane do rozpoczęcia iteracji.|
|[CDocument:: GetNextView](#getnextview)|Wykonuje iterację na liście widoków skojarzonych z tym dokumentem.|
|[CDocument:: getPathname](#getpathname)|Zwraca ścieżkę pliku danych dokumentu.|
|[CDocument:: GetThumbnail](#getthumbnail)|Wywołuje się, by utworzyć mapę bitową, która będzie używana przez dostawcę miniatur do wyświetlania miniatury.|
|[CDocument:: getTitle](#gettitle)|Zwraca tytuł dokumentu.|
|[CDocument:: InitializeSearchContent](#initializesearchcontent)|Wywołuje się, by zainicjować zawartość wyszukiwania dla procedury obsługi wyszukiwania.|
|[CDocument:: IsModified](#ismodified)|Wskazuje, czy dokument został zmodyfikowany od czasu ostatniego zapisywania.|
|[CDocument:: IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Wskazuje, czy to wystąpienie `CDocument` obiektu zostało utworzone dla & wyszukiwania Organizuj program obsługi.|
|[CDocument:: LoadDocumentFromStream](#loaddocumentfromstream)|Wywołuje się, by załadować dane dokumentu ze strumienia.|
|[CDocument:: OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Wywoływana przed zmianą czcionki Rich Preview.|
|[CDocument:: OnChangedViewList](#onchangedviewlist)|Wywoływana po dodaniu lub usunięciu widoku do dokumentu.|
|[CDocument:: OnCloseDocument](#onclosedocument)|Wywołuje się, by zamknąć dokument.|
|[CDocument:: OnCreatePreviewFrame](#oncreatepreviewframe)|Wywoływane przez platformę, gdy musi utworzyć ramkę podglądu dla zaawansowanej wersji zapoznawczej.|
|[CDocument:: OnDocumentEvent](#ondocumentevent)|Wywoływane przez platformę w odpowiedzi na zdarzenie dokumentu.|
|[CDocument:: OnDrawThumbnail](#ondrawthumbnail)|Zastąp tę metodę w klasie pochodnej, aby narysować zawartość miniatury.|
|[CDocument:: OnLoadDocumentFromStream](#onloaddocumentfromstream)|Wywoływane przez platformę, gdy musi załadować dane dokumentu ze strumienia.|
|[CDocument:: OnNewDocument](#onnewdocument)|Wywołuje się, by utworzyć nowy dokument.|
|[CDocument:: OnOpenDocument](#onopendocument)|Wywołuje się, by otworzyć istniejący dokument.|
|[CDocument:: OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Kieruje procedurę obsługi podglądu, aby zwracała wartość HWND z wywołania funkcji GetFocus.|
|[CDocument:: OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Kieruje procedurę obsługi podglądu, aby obsłużyć naciśnięcie klawisza przesłane z pompy komunikatów procesu, w którym jest uruchomiony program obsługi podglądu.|
|[CDocument:: OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Wywoływana, gdy kolor tła sformatowanej wersji zapoznawczej został zmieniony.|
|[CDocument:: OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Wywołuje się, gdy zmieniono zaawansowaną czcionkę podglądu.|
|[CDocument:: OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Wywołuje się, gdy zmieniono zaawansowaną witrynę w wersji zapoznawczej.|
|[CDocument:: OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Wywoływana, gdy kolor tekstu sformatowanego podglądu został zmieniony.|
|[CDocument:: OnSaveDocument](#onsavedocument)|Wywołuje się, by zapisać dokument na dysku.|
|[CDocument:: OnUnloadHandler](#onunloadhandler)|Wywoływane przez platformę, gdy procedura obsługi podglądu jest zwalniana.|
|[CDocument::P reCloseFrame](#precloseframe)|Wywoływana przed zamknięciem okna ramki.|
|[CDocument:: ReadNextChunkValue](#readnextchunkvalue)|Odczytuje następną wartość fragmentu.|
|[CDocument:: ReleaseFile](#releasefile)|Zwalnia plik, aby udostępnić go do użytku przez inne aplikacje.|
|[CDocument:: RemoveChunk](#removechunk)|Usuwa fragment o określonym identyfikatorze GUID.|
|[CDocument:: RemoveView](#removeview)|Odłącza widok od dokumentu.|
|[CDocument:: ReportSaveLoadException](#reportsaveloadexception)|Zaawansowany zaawansowanie; wywołuje się, gdy nie można ukończyć operacji otwierania lub zapisywania z powodu wyjątku.|
|[CDocument:: SaveModified](#savemodified)|Zaawansowany zaawansowanie; wywołuje się, by poprosił użytkownika o to, czy dokument powinien być zapisany.|
|[CDocument:: SetChunkValue](#setchunkvalue)|Ustawia wartość fragmentu.|
|[CDocument:: SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, że dokument został zmodyfikowany od czasu ostatniego zapisywania.|
|[CDocument:: setpathname](#setpathname)|Ustawia ścieżkę pliku danych używanego przez dokument.|
|[CDocument:: settitle](#settitle)|Ustawia tytuł dokumentu.|
|[CDocument:: funkcji UpdateAllViews](#updateallviews)|Powiadamia wszystkie widoki, które dokument został zmodyfikowany.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocument:: OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|
|[CDocument:: OnUpdateFileSendMail](#onupdatefilesendmail)|Włącza polecenie Wyślij pocztę, jeśli jest dostępna obsługa poczty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDocument:: m_bGetThumbnailMode](#m_bgetthumbnailmode)|Określa, że obiekt `CDocument` został utworzony przez program dllhost dla miniatur. Należy zaewidencjonować `CView::OnDraw`.|
|[CDocument:: m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Określa, że obiekt `CDocument` został utworzony przez prevhost dla `Rich Preview`. Należy zaewidencjonować `CView::OnDraw`.|
|[CDocument:: m_bSearchMode](#m_bsearchmode)|Określa, że obiekt `CDocument` został utworzony za pomocą indeksatora lub innej aplikacji wyszukiwania.|
|[CDocument:: m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Określa kolor tła okna zaawansowanej wersji zapoznawczej. Ten kolor jest ustawiany przez hosta.|
|[CDocument:: m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Określa kolor pierwszego planu okna zaawansowanej wersji zapoznawczej. Ten kolor jest ustawiany przez hosta.|
|[CDocument:: m_lfRichPreviewFont](#m_lfrichpreviewfont)|Określa czcionkę tekstu dla zaawansowanego okna podglądu. Te informacje o czcionce są ustawiane przez hosta.|

## <a name="remarks"></a>Uwagi

Dokument reprezentuje jednostkę danych, które są zwykle otwierane za pomocą polecenia Otwórz plik i zapisuje przy użyciu polecenia Zapisz plik.

`CDocument` obsługuje standardowe operacje, takie jak tworzenie dokumentu, ładowanie go i zapisywanie. Struktura operuje na dokumentach przy użyciu interfejsu zdefiniowanego przez `CDocument`.

Aplikacja może obsługiwać więcej niż jeden typ dokumentu; na przykład aplikacja może obsługiwać zarówno arkusze kalkulacyjne, jak i dokumenty tekstowe. Każdy typ dokumentu ma skojarzony szablon dokumentu; szablon dokumentu określa, jakie zasoby (na przykład menu, ikonę lub tabela akceleratora) są używane dla tego typu dokumentu. Każdy dokument zawiera wskaźnik do skojarzonego obiektu `CDocTemplate`.

Użytkownicy pracują z dokumentem za pomocą skojarzonych z nim obiektów [CView](../../mfc/reference/cview-class.md) . Widok renderuje obraz dokumentu w oknie klatki i interpretuje dane wejściowe użytkownika jako operacje na dokumencie. Z dokumentem może być skojarzonych wiele widoków. Gdy użytkownik otwiera okno w dokumencie, struktura tworzy widok i dołącza go do dokumentu. Szablon dokumentu określa, jakiego typu widok i okno ramki są używane do wyświetlania każdego typu dokumentu.

Dokumenty są częścią standardowego routingu poleceń struktury i w związku z tym odbierają polecenia ze standardowych składników interfejsu użytkownika (takich jak element menu Zapisz plik). Dokument odbiera polecenia przekazane przez aktywny widok. Jeśli dokument nie obsługuje danego polecenia, przekazuje polecenie do szablonu dokumentu, który go zarządza.

Gdy dane dokumentu są modyfikowane, każdy z jego widoków musi odzwierciedlać te modyfikacje. `CDocument` udostępnia funkcję elementu członkowskiego [funkcji UpdateAllViews](#updateallviews) , aby powiadomić widoki takich zmian, dzięki czemu w razie potrzeby widoki mogą być odświeżane. W strukturze jest również wyświetlany komunikat z prośbą o zapisanie zmodyfikowanego pliku przed jego zamknięciem.

Aby zaimplementować dokumenty w typowej aplikacji, należy wykonać następujące czynności:

- Utwórz klasę z `CDocument` dla każdego typu dokumentu.

- Dodaj Zmienne Członkowskie do przechowywania danych poszczególnych dokumentów.

- Zaimplementuj funkcje członkowskie na potrzeby odczytywania i modyfikowania danych dokumentu. Widoki dokumentu są najważniejszymi użytkownikami tych funkcji elementów członkowskich.

- Zastąp funkcję członkowską [CObject:: Serializer](../../mfc/reference/cobject-class.md#serialize) w klasie Document, aby zapisać i odczytać dane dokumentu z i z dysku.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli istnieje obsługa poczty (MAPI). Zapoznaj się z artykułami obsługa [MAPI](../../mfc/mapi.md) i [MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

Aby uzyskać więcej informacji na temat `CDocument`, zobacz temat informacje o architekturze [serializacji](../../mfc/serialization-in-mfc.md), [dokumentu/widoku](../../mfc/document-view-architecture.md)oraz [Tworzenie dokumentów/widoków](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="addview"></a>CDocument:: AddView

Wywołaj tę funkcję, aby dołączyć widok do dokumentu.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskazuje dodawany widok.

### <a name="remarks"></a>Uwagi

Ta funkcja umożliwia dodanie określonego widoku do listy widoków skojarzonych z tym dokumentem. funkcja ustawia również wskaźnik dokumentu widoku do tego dokumentu. Struktura wywołuje tę funkcję podczas dołączania nowo utworzonego obiektu widoku do dokumentu; dzieje się tak w odpowiedzi na plik New, Open File lub New Window lub po poddzieleniu okna rozdzielacza.

Wywołaj tę funkcję tylko w przypadku ręcznego tworzenia i dołączania widoku. Zazwyczaj umożliwisz platformom łączenie dokumentów i widoków przez zdefiniowanie obiektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) w celu skojarzenia klasy dokumentu, klasy widoku i klasy okien ramek.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>CDocument:: BeginReadChunks

Inicjuje odczytywanie fragmentu.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Uwagi

##  <a name="cancloseframe"></a>CDocument:: CanCloseFrame

Wywoływane przez platformę przed zamknięciem okna ramki dokumentu.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Wskazuje okno ramki widoku dołączonego do dokumentu.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli można bezpiecznie zamknąć okno ramki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza, czy istnieją inne okna ramowe wyświetlające dokument. Jeśli określone okno ramy jest ostatnim, w którym jest wyświetlany dokument, funkcja wyświetli komunikat z prośbą o zapisanie dokumentu, jeśli został zmodyfikowany. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne po zamknięciu okna ramki. Jest to zaawansowany możliwy do zaawansowania.

##  <a name="cdocument"></a>CDocument:: CDocument

Konstruuje obiekt `CDocument`.

```
CDocument();
```

### <a name="remarks"></a>Uwagi

Platforma obsługuje tworzenie dokumentów. Przesłoń funkcję elementu członkowskiego [OnNewDocument](#onnewdocument) , aby przeprowadzić inicjalizację dla poszczególnych dokumentów. jest to szczególnie ważne w aplikacjach interfejsu pojedynczego dokumentu (SDI).

##  <a name="clearchunklist"></a>CDocument:: ClearChunkList

Czyści listę fragmentów.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Uwagi

##  <a name="clearpathname"></a>CDocument:: ClearPathName

Czyści ścieżkę obiektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Uwagi

Wyczyszczenie ścieżki z obiektu `CDocument` powoduje, że aplikacja monituje użytkownika o zapisanie dokumentu. Powoduje to, że polecenie **Save** zachowuje się jak polecenie **Zapisz jako** .

##  <a name="deletecontents"></a>CDocument::D eleteContents

Wywoływane przez platformę, aby usunąć dane dokumentu bez niszczenia samego obiektu `CDocument`.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Uwagi

Jest wywoływana tuż przed zniszczeniem dokumentu. Jest również wywoływana, aby upewnić się, że dokument jest pusty przed ponownym użyciem. Jest to szczególnie ważne w przypadku aplikacji SDI, która używa tylko jednego dokumentu; dokument jest używany ponownie za każdym razem, gdy użytkownik utworzy lub otworzy inny dokument. Wywołaj tę funkcję, aby zaimplementować polecenie "Edytuj Wyczyść wszystko" lub podobne, które usuwa wszystkie dane dokumentu. Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby usunąć dane w dokumencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>CDocument:: FindChunk

Szuka fragmentu o określonym identyfikatorze GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*ident*<br/>
Określa identyfikator GUID fragmentu do znalezienia.

*identyfikatora*<br/>
Określa identyfikator PID fragmentu do znalezienia.

### <a name="return-value"></a>Wartość zwrócona

W razie powodzenia Umieść na wewnętrznej liście fragmentów. W przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="getadapter"></a>CDocument:: getadapter

Zwraca wskaźnik do obiektu implementującego interfejs `IDocument`.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu implementującego interfejs `IDocument`.

### <a name="remarks"></a>Uwagi

##  <a name="getdoctemplate"></a>CDocument:: GetDocTemplate

Wywołaj tę funkcję, aby uzyskać wskaźnik do szablonu dokumentu dla tego typu dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do szablonu dokumentu dla tego typu dokumentu lub wartości NULL, jeśli dokument nie jest zarządzany przez szablon dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>CDocument:: GetFile

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do obiektu `CFile`.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który wskazuje stan ukończenia operacji.

*nOpenFlags*<br/>
Tryb udostępniania i dostępu. Określa akcję, która ma zostać podjęta podczas otwierania pliku. Można połączyć opcje wymienione w konstruktorze CFile [CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) za pomocą operatora bitowego or (&#124;). Wymagane są jedno uprawnienie dostępu i jedna opcja udostępniania; tryby `modeCreate` i `modeNoInherit` są opcjonalne.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `CFile`.

##  <a name="getfirstviewposition"></a>CDocument:: GetFirstViewPosition

Wywołaj tę funkcję, aby pobrać pozycję pierwszego widoku na liście widoków skojarzonych z tym dokumentem.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość pozycji, która może być używana dla iteracji z funkcją składową [GetNextView](#getnextview) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>CDocument:: GetNextView

Wywołaj tę funkcję, aby wykonać iterację wszystkich widoków dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*Elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwróconej przez poprzednie wywołanie do funkcji składowych `GetNextView` lub [GetFirstViewPosition](#getfirstviewposition) . Ta wartość nie może być RÓWNa NULL.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do widoku identyfikowanego przez *elemencie rPosition*.

### <a name="remarks"></a>Uwagi

Funkcja zwraca widok identyfikowany przez *elemencie rPosition* , a następnie ustawia *elemencie RPOSITION* na wartość pozycji następnego widoku na liście. Jeśli pobrany widok jest ostatni na liście, *elemencie rPosition* jest ustawiony na wartość null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>CDocument:: getPathname

Wywołaj tę funkcję, aby uzyskać w pełni kwalifikowaną ścieżkę pliku dysku dokumentu.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Wartość zwrócona

W pełni kwalifikowana ścieżka dokumentu. Ten ciąg jest pusty, jeśli dokument nie został zapisany lub nie ma skojarzonego z nim pliku dyskowego.

##  <a name="getthumbnail"></a>CDocument:: GetThumbnail

Tworzy mapę bitową, która będzie używana przez dostawcę miniatur do wyświetlania miniatury.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parametry

*CX*<br/>
Określa szerokość i wysokość mapy bitowej.

*phbmp*<br/>
Zawiera uchwyt do mapy bitowej, gdy funkcja zwraca się pomyślnie.

*pdwAlpha*<br/>
Zawiera element DWORD określający wartość kanału alfa, gdy funkcja zwraca się pomyślnie.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość PRAWDA, jeśli mapa bitowa dla miniatury została utworzona pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="gettitle"></a>CDocument:: getTitle

Wywołaj tę funkcję, aby uzyskać tytuł dokumentu, który zazwyczaj pochodzi od nazwy pliku dokumentu.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Wartość zwrócona

Tytuł dokumentu.

##  <a name="initializesearchcontent"></a>CDocument:: InitializeSearchContent

Wywołuje się, by zainicjować zawartość wyszukiwania dla procedury obsługi wyszukiwania.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Uwagi

Zastąp tę metodę w klasie pochodnej, aby zainicjować zawartość wyszukiwania. Zawartość powinna być ciągiem z częściami rozdzielonymi znakiem ";". Na przykład "punkt; prostokąt element OLE ".

##  <a name="ismodified"></a>CDocument:: IsModified

Wywołaj tę funkcję, aby określić, czy dokument został zmodyfikowany od czasu ostatniego zapisywania.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli dokument został zmodyfikowany od czasu ostatniego zapisania; w przeciwnym razie 0.

##  <a name="issearchandorganizehandler"></a>CDocument:: IsSearchAndOrganizeHandler

Wskazuje, czy to wystąpienie `CDocument` zostało utworzone dla programu obsługi wyszukiwania & organizowania.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE, jeśli to wystąpienie `CDocument` zostało utworzone dla & wyszukiwania Organizuj program obsługi.

### <a name="remarks"></a>Uwagi

Obecnie ta funkcja zwraca wartość TRUE tylko dla programów obsługi zaawansowanej wersji zapoznawczej wdrożonych na serwerze poza procesem. Aby ta funkcja zwracała wartość TRUE, można ustawić odpowiednie flagi (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) na poziomie aplikacji.

##  <a name="loaddocumentfromstream"></a>CDocument:: LoadDocumentFromStream

Wywołuje się, by załadować dane dokumentu ze strumienia.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Wskaźnik do strumienia. Ten strumień jest dostarczany przez powłokę.

*dwGrfMode*<br/>
Tryb dostępu do strumienia.

### <a name="return-value"></a>Wartość zwrócona

S_OK, jeśli operacja ładowania się powiedzie, w przeciwnym razie HRESULT z kodem błędu.

### <a name="remarks"></a>Uwagi

Można zastąpić tę metodę w klasie pochodnej, aby dostosować sposób ładowania danych ze strumienia.

##  <a name="m_bgetthumbnailmode"></a>CDocument:: m_bGetThumbnailMode

Określa, że obiekt `CDocument` został utworzony przez program dllhost dla miniatur. Należy zaewidencjonować `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Uwagi

`TRUE` wskazuje, że dokument został utworzony przez program dllhost dla miniatur.

##  <a name="m_bpreviewhandlermode"></a>CDocument:: m_bPreviewHandlerMode

Określa, że obiekt `CDocument` został utworzony przez prevhost dla zaawansowanej wersji zapoznawczej. Należy zaewidencjonować `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE wskazuje, że dokument został utworzony za pomocą prevhost dla zaawansowanej wersji zapoznawczej.

##  <a name="m_bsearchmode"></a>CDocument:: m_bSearchMode

Określa, że obiekt `CDocument` został utworzony przez indeksator lub przez inną aplikację wyszukiwania.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Uwagi

`TRUE` wskazuje, że dokument został utworzony przez indeksator lub przez inną aplikację wyszukiwania.

##  <a name="m_clrrichpreviewbackcolor"></a>CDocument:: m_clrRichPreviewBackColor

Określa kolor tła okna zaawansowanej wersji zapoznawczej. Ten kolor jest ustawiany przez hosta.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_clrrichpreviewtextcolor"></a>CDocument:: m_clrRichPreviewTextColor

Określa kolor pierwszego planu okna zaawansowanej wersji zapoznawczej. Ten kolor jest ustawiany przez hosta.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_lfrichpreviewfont"></a>CDocument:: m_lfRichPreviewFont

Określa czcionkę tekstową okna zaawansowanej wersji zapoznawczej. Te informacje o czcionce są ustawiane przez hosta.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Uwagi

##  <a name="onbeforerichpreviewfontchanged"></a>CDocument:: OnBeforeRichPreviewFontChanged

Wywoływana przed zmianą czcionki Rich Preview.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onchangedviewlist"></a>CDocument:: OnChangedViewList

Wywoływane przez platformę po dodaniu lub usunięciu widoku do dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji sprawdza, czy ostatni widok jest usuwany, a jeśli tak, usuwa dokument. Przesłoń tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne, gdy struktura doda lub usunie widok. Na przykład jeśli chcesz, aby dokument pozostał otwarty nawet wtedy, gdy nie ma dołączonych widoków, Zastąp tę funkcję.

##  <a name="onclosedocument"></a>CDocument:: OnCloseDocument

Wywoływane przez platformę, gdy dokument jest zamknięty, zazwyczaj jako część polecenia Zamknij plik.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji niszczy wszystkie ramki używane do wyświetlania dokumentu, zamyka widok, czyści zawartość dokumentu, a następnie wywołuje funkcję elementu członkowskiego [DeleteContents](#deletecontents) w celu usunięcia danych dokumentu.

Przesłoń tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne oczyszczania podczas zamykania dokumentu przez strukturę. Jeśli na przykład dokument reprezentuje rekord w bazie danych, można zastąpić tę funkcję, aby zamknąć bazę danych. Należy wywołać wersję klasy bazowej tej funkcji z przesłonięcia.

##  <a name="oncreatepreviewframe"></a>CDocument:: OnCreatePreviewFrame

Wywoływane przez platformę, gdy musi utworzyć ramkę podglądu dla zaawansowanej wersji zapoznawczej.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość TRUE, jeśli ramka została utworzona pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ondocumentevent"></a>CDocument:: OnDocumentEvent

Wywoływane przez platformę w odpowiedzi na zdarzenie dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*Równo*<br/>
podczas Wyliczany typ danych, który opisuje typ zdarzenia.

### <a name="remarks"></a>Uwagi

Zdarzenia dokumentu mogą mieć wpływ na wiele klas. Ta metoda jest odpowiedzialna za obsługę zdarzeń dokumentu, które mają wpływ na klasy inne niż [klasa CDocument](../../mfc/reference/cdocument-class.md). Obecnie jedyną klasą, która musi odpowiadać na zdarzenia dokumentu, jest [Klasa CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Klasa `CDocument` ma inne metody umożliwiające zmianę, które są odpowiedzialne za obsługę wpływu na `CDocument`.

Poniższa tabela zawiera listę możliwych wartości dla *nierównych* i zdarzeń, z którymi odpowiada.

|Wartość|Odpowiednie zdarzenie|
|-----------|-------------------------|
|`onAfterNewDocument`|Utworzono nowy dokument.|
|`onAfterOpenDocument`|Otwarto nowy dokument.|
|`onAfterSaveDocument`|Dokument został zapisany.|
|`onAfterCloseDocument`|Dokument został zamknięty.|

##  <a name="ondrawthumbnail"></a>CDocument:: OnDrawThumbnail

Przesłoń tę metodę w klasie pochodnej, aby narysować miniaturę.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Odwołanie do kontekstu urządzenia.

*lprcBounds*<br/>
Określa prostokąt ograniczenia obszaru, w którym ma zostać narysowana miniatura.

### <a name="remarks"></a>Uwagi

##  <a name="onfilesendmail"></a>CDocument:: OnFileSendMail

Wysyła komunikat za pośrednictwem zamieszkałego hosta poczty (jeśli istnieje) do dokumentu jako załącznik.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail` wywołuje [OnSaveDocument](#onsavedocument) do serializacji (Save) bez tytułu i modyfikacji dokumentów do pliku tymczasowego, który następnie jest wysyłany pocztą elektroniczną. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagany; zostanie wysłany oryginalny. `OnFileSendMail` ładuje MAPI32. DLL, jeśli nie został jeszcze załadowany.

Specjalna implementacja `OnFileSendMail` dla [COleDocument](../../mfc/reference/coledocument-class.md) obsługuje pliki złożone prawidłowo.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli istnieje obsługa poczty (MAPI). Zapoznaj się z artykułami [MAPI tematów](../../mfc/mapi.md) i [obsługą MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>CDocument:: OnLoadDocumentFromStream

Wywoływane przez platformę, gdy musi załadować dane dokumentu ze strumienia.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
Wskaźnik do strumienia przychodzącego.

*grfMode*<br/>
Tryb dostępu do strumienia.

### <a name="return-value"></a>Wartość zwrócona

S_OK, jeśli ładowanie zakończyło się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

##  <a name="onnewdocument"></a>CDocument:: OnNewDocument

Wywoływane przez platformę w ramach polecenia nowy plik.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli dokument został pomyślnie zainicjowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję elementu członkowskiego [DeleteContents](#deletecontents) , aby upewnić się, że dokument jest pusty, a następnie oznacza nowy dokument jako czysty. Zastąp tę funkcję, aby zainicjować strukturę danych dla nowego dokumentu. Należy wywołać wersję klasy bazowej tej funkcji z przesłonięcia.

Jeśli użytkownik wybierze polecenie plik nowe w aplikacji SDI, struktura użyje tej funkcji, aby ponownie zainicjować istniejący dokument zamiast tworzyć nowy. Jeśli użytkownik wybierze pozycję plik nowy w aplikacji interfejsu wielu dokumentów (MDI), struktura utworzy nowy dokument za każdym razem, a następnie wywoła tę funkcję, aby ją zainicjować. Kod inicjalizacji należy umieścić w tej funkcji zamiast w konstruktorze, aby polecenie File New działało w aplikacjach SDI.

Należy zauważyć, że istnieją przypadki, w których `OnNewDocument` jest wywoływana dwa razy. Dzieje się tak, gdy dokument jest osadzony jako serwer dokumentów ActiveX. Funkcja jest wywoływana najpierw przez metodę `CreateInstance` (uwidocznioną przez klasę pochodną `COleObjectFactory`) i drugi raz przez metodę `InitNew` (uwidocznioną przez klasę pochodną `COleServerDoc`).

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywne metody inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>CDocument:: OnOpenDocument

Wywoływane przez platformę w ramach polecenia Otwórz plik.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje ścieżkę do dokumentu do otwarcia.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli dokument został pomyślnie załadowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołuje funkcję elementu członkowskiego [DeleteContents](#deletecontents) , aby upewnić się, że dokument jest pusty, wywołuje [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize) , aby odczytać zawartość pliku, a następnie oznacza dokument jako czysty. Zastąp tę funkcję, jeśli chcesz użyć czegoś innego niż mechanizm archiwizowania lub mechanizm plików. Można na przykład napisać aplikację, w której dokumenty reprezentują rekordy w bazie danych, a nie osobne pliki.

Jeśli użytkownik wybierze polecenie Otwórz plik w aplikacji SDI, struktura użyje tej funkcji, aby ponownie zainicjować istniejący obiekt `CDocument`, zamiast tworzyć nowe. Jeśli użytkownik wybierze plik otwarty w aplikacji MDI, struktura konstruuje nowy obiekt `CDocument` za każdym razem, a następnie wywoła tę funkcję, aby ją zainicjować. Kod inicjalizacji należy umieścić w tej funkcji zamiast w konstruktorze, aby polecenie otwarcia pliku działało w aplikacjach SDI.

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywne metody inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>CDocument:: OnPreviewHandlerQueryFocus

Kieruje procedurę obsługi podglądu do zwrócenia parametru HWND pobranego z wywołania funkcji `GetFocus`.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*phwnd*<br/>
określoną Gdy ta metoda zwraca, zawiera wskaźnik do elementu HWND zwróconego przez wywołanie funkcji `GetFocus` z wątku pierwszego planu obsługi podglądu.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK, jeśli się powiedzie; lub w przeciwnym razie wartość błędu.

### <a name="remarks"></a>Uwagi

##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument:: OnPreviewHandlerTranslateAccelerator

Kieruje procedurę obsługi podglądu, aby obsłużyć naciśnięcie klawisza przesłane z pompy komunikatów procesu, w którym jest uruchomiony program obsługi podglądu.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
podczas Wskaźnik do komunikatu okna.

### <a name="return-value"></a>Wartość zwrócona

Jeśli komunikat o naciśnięciu klawisza może być przetwarzany przez procedurę obsługi podglądu, program obsługi przetwarza go i zwraca S_OK. Jeśli program obsługi podglądu nie może przetworzyć komunikatu o naciśnięciu klawisza, oferuje go hostowi za pośrednictwem `IPreviewHandlerFrame::TranslateAccelerator`. Jeśli host przetwarza komunikat, ta metoda zwraca S_OK. Jeśli host nie przetwarza komunikatu, Metoda ta zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewbackcolorchanged"></a>CDocument:: OnRichPreviewBackColorChanged

Wywoływana, gdy kolor tła Rich Preview został zmieniony.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewfontchanged"></a>CDocument:: OnRichPreviewFontChanged

Wywołuje się, gdy zmieniono czcionkę Rich Preview.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewsitechanged"></a>CDocument:: OnRichPreviewSiteChanged

Wywoływana, gdy zmieniono witrynę rozbudowanej wersji zapoznawczej.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewtextcolorchanged"></a>CDocument:: OnRichPreviewTextColorChanged

Wywoływana, gdy kolor tekstu sformatowanego podglądu został zmieniony.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onsavedocument"></a>CDocument:: OnSaveDocument

Wywoływane przez platformę w ramach polecenia Zapisz plik lub Zapisz jako.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje w pełni kwalifikowaną ścieżkę, w której plik powinien zostać zapisany.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli dokument został pomyślnie zapisany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołuje [CObject:: serializacji](../../mfc/reference/cobject-class.md#serialize) w celu zapisania danych dokumentu do pliku, a następnie oznacza dokument jako czysty. Zastąp tę funkcję, jeśli chcesz przeprowadzić przetwarzanie specjalne podczas zapisywania dokumentu przez strukturę. Można na przykład napisać aplikację, w której dokumenty reprezentują rekordy w bazie danych, a nie osobne pliki.

##  <a name="onunloadhandler"></a>CDocument:: OnUnloadHandler

Wywoływane przez platformę, gdy procedura obsługi podglądu została zwolniona.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Uwagi

##  <a name="onupdatefilesendmail"></a>CDocument:: OnUpdateFileSendMail

Włącza ID_FILE_SEND_MAIL polecenie, jeśli jest dostępna obsługa poczty (MAPI).

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) skojarzonego z poleceniem ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Uwagi

W przeciwnym razie funkcja usuwa ID_FILE_SEND_MAIL polecenie z menu, w tym separatory powyżej lub poniżej elementu menu. Interfejs MAPI jest włączony, jeśli MAPI32. Biblioteka DLL jest obecna w ścieżce i, w sekcji [mail] w artykule WIN. Plik INI, MAPI = 1. Większość aplikacji umieszcza to polecenie w menu plik.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli istnieje obsługa poczty (MAPI). Zapoznaj się z artykułami [MAPI tematów](../../mfc/mapi.md) i [obsługą MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>CDocument::P reCloseFrame

Ta funkcja członkowska jest wywoływana przez platformę przed zniszczeniem okna ramowego.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Wskaźnik do [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) , który zawiera skojarzony obiekt `CDocument`.

### <a name="remarks"></a>Uwagi

Można go zastąpić, aby zapewnić niestandardową oczyszczanie, ale również należy wywołać klasę bazową.

Wartość domyślna `PreCloseFrame` nie ma nic w `CDocument`. Klasy pochodne `CDocument`[COleDocument](../../mfc/reference/coledocument-class.md) i [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) używają tej funkcji elementu członkowskiego.

##  <a name="readnextchunkvalue"></a>CDocument:: ReadNextChunkValue

Odczytuje następną wartość fragmentu.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*ppValue*<br/>
określoną Gdy funkcja zwraca, *ppValue* zawiera wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="releasefile"></a>CDocument:: ReleaseFile

Ta funkcja członkowska jest wywoływana przez platformę w celu zwolnienia pliku, dzięki czemu będzie dostępna do użytku przez inne aplikacje.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do obiektu CFile, który ma zostać wypublikowany.

*bAbort*<br/>
Określa, czy plik ma zostać opublikowany przy użyciu `CFile::Close` lub `CFile::Abort`. FAŁSZ, jeśli plik ma zostać opublikowany przy użyciu [CFile:: Close](../../mfc/reference/cfile-class.md#close); Ma wartość TRUE, jeśli plik ma zostać opublikowany przy użyciu [CFile:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Uwagi

Jeśli *bAbort* ma wartość TRUE, `ReleaseFile` wywołuje `CFile::Abort`i plik zostanie wydane. `CFile::Abort` nie zgłosi wyjątku.

Jeśli *bAbort* ma wartość FALSE, `ReleaseFile` wywołania `CFile::Close` i plik zostanie wydane.

Przesłoń tę funkcję elementu członkowskiego, aby wymagać akcji przez użytkownika przed zwolnieniem pliku.

##  <a name="removechunk"></a>CDocument:: RemoveChunk

Usuwa fragment o określonym identyfikatorze GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Ident*<br/>
Określa identyfikator GUID fragmentu, który ma zostać usunięty.

*Identyfikatora*<br/>
Określa identyfikator PID fragmentu, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

##  <a name="removeview"></a>CDocument:: RemoveView

Wywołaj tę funkcję, aby odłączyć widok od dokumentu.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskazuje na usunięcie widoku.

### <a name="remarks"></a>Uwagi

Ta funkcja usuwa określony widok z listy widoków skojarzonych z tym dokumentem. ustawia również wskaźnik dokumentu widoku na wartość NULL. Ta funkcja jest wywoływana przez platformę, gdy okno ramki jest zamknięte lub zostało zamknięte okienko rozdzielacza.

Wywołaj tę funkcję tylko w przypadku ręcznego odłączania widoku. Zazwyczaj umożliwimy odłączenie dokumentów i widoków struktury przez zdefiniowanie obiektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) w celu skojarzenia klasy dokumentu, klasy widoku i klasy okna ramowego.

Zapoznaj się z przykładem w lokalizacji [AddView](#addview) w celu uzyskania przykładowej implementacji.

##  <a name="reportsaveloadexception"></a>CDocument:: ReportSaveLoadException

Wywołuje się, gdy wyjątek jest zgłaszany (zazwyczaj [CFileException](../../mfc/reference/cfileexception-class.md) lub [CArchiveException](../../mfc/reference/carchiveexception-class.md)) podczas zapisywania lub ładowania dokumentu.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje nazwę dokumentu, który został zapisywany lub załadowany.

*e*<br/>
Wskazuje wyjątek, który został zgłoszony. Może mieć wartość NULL.

*bSaving*<br/>
Flaga oznaczająca, jaka operacja była w toku; niezerowe, jeśli dokument był zapisywany, 0, jeśli dokument został załadowany.

*nIDPDefault*<br/>
Identyfikator komunikatu o błędzie, który ma być wyświetlany, jeśli funkcja nie określa bardziej szczegółowego.

### <a name="remarks"></a>Uwagi

Implementacja domyślna sprawdza obiekt wyjątku i wyszukuje komunikat o błędzie, który opisuje przyczynę. Jeśli określona wiadomość nie zostanie znaleziona lub jeśli *e* ma wartość null, zostanie użyty komunikat ogólny określony przez parametr *nIDPDefault* . Następnie funkcja wyświetli okno komunikatu zawierające komunikat o błędzie. Zastąp tę funkcję, jeśli chcesz zapewnić dodatkowe, niestandardowe komunikaty o niepowodzeniu. Jest to zaawansowany możliwy do zaawansowania.

##  <a name="savemodified"></a>CDocument:: SaveModified

Wywoływane przez platformę przed zamknięciem zmodyfikowanego dokumentu.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość różna od zera, jeśli jest bezpieczna do kontynuowania i zamknięcia dokumentu; 0, jeśli dokument nie powinien być zamknięty.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wyświetla okno komunikatu z pytaniem o to, czy zapisać zmiany w dokumencie, jeśli zostały wprowadzone. Przesłoń tę funkcję, jeśli program wymaga innej procedury monitowania. Jest to zaawansowany możliwy do zaawansowania.

##  <a name="setchunkvalue"></a>CDocument:: SetChunkValue

Ustawia wartość fragmentu.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Określa wartość fragmentu do ustawienia.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="setmodifiedflag"></a>CDocument:: SetModifiedFlag

Wywołaj tę funkcję po wprowadzeniu jakichkolwiek modyfikacji dokumentu.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Flaga oznaczająca, czy dokument został zmodyfikowany.

### <a name="remarks"></a>Uwagi

Przez wywołanie tej funkcji spójnej, należy się upewnić, że struktura będzie monitował użytkownika o zapisanie zmian przed zamknięciem dokumentu. Zazwyczaj należy używać domyślnej wartości TRUE dla parametru *bModified* . Aby oznaczyć dokument jako czysty (niemodyfikowany), Wywołaj tę funkcję z wartością FALSE.

##  <a name="setpathname"></a>CDocument:: setpathname

Wywołaj tę funkcję, aby określić w pełni kwalifikowaną ścieżkę pliku dysku dokumentu.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje ciąg, który ma być używany jako ścieżka do dokumentu.

*bAddToMRU*<br/>
Określa, czy nazwa pliku jest dodawana do listy ostatnio używanych plików (MRU). Jeśli wartość jest równa TRUE, nazwa pliku zostanie dodana; w przypadku wartości FALSE nie jest dodawany.

### <a name="remarks"></a>Uwagi

W zależności od wartości *bAddToMRU* ścieżka zostanie dodana lub nie została dodana do listy MRU obsługiwanej przez aplikację. Należy zauważyć, że niektóre dokumenty nie są skojarzone z plikiem dysku. Wywołaj tę funkcję tylko w przypadku zastąpienia domyślnej implementacji otwierania i zapisywania plików używanych przez platformę.

##  <a name="settitle"></a>CDocument:: settitle

Wywołaj tę funkcję, aby określić tytuł dokumentu (ciąg wyświetlany na pasku tytułu okna ramki).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Wskazuje ciąg, który ma być używany jako tytuł dokumentu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji aktualizuje tytuły wszystkich okien ramowych, które wyświetlają dokument.

##  <a name="updateallviews"></a>CDocument:: funkcji UpdateAllViews

Wywołaj tę funkcję po zmodyfikowaniu dokumentu.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskazuje widok, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie widoki mają zostać zaktualizowane.

*lHint*<br/>
Zawiera informacje na temat modyfikacji.

*pHint*<br/>
Wskazuje obiekt przechowujący informacje o modyfikacji.

### <a name="remarks"></a>Uwagi

Należy wywołać tę funkcję po wywołaniu funkcji składowej [SetModifiedFlag](#setmodifiedflag) . Ta funkcja informuje każdy widok dołączony do dokumentu, z wyjątkiem widoku określonego przez *pSender*, że dokument został zmodyfikowany. Ta funkcja jest zazwyczaj wywoływana z klasy widoku po zmianie dokumentu przez użytkownika za pośrednictwem widoku.

Ta funkcja wywołuje funkcję członkowską [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate) dla każdego z widoków dokumentu poza widokiem wysyłającym, przekazując *pHint* i *lHint*. Te parametry służą do przekazywania informacji do widoków o zmianach wprowadzonych do dokumentu. Informacje można kodować przy użyciu *lHint* i/lub można zdefiniować klasę pochodną [CObject](../../mfc/reference/cobject-class.md)do przechowywania informacji o zmianach i przekazać obiekt tej klasy przy użyciu *pHint*. Przesłoń `CView::OnUpdate` funkcję członkowską w klasie pochodnej [CView](../../mfc/reference/cview-class.md), aby zoptymalizować aktualizację wyświetlania widoku na podstawie przeprowadzonych informacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład MDIDOCVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład SNAPVW MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład NPP MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
