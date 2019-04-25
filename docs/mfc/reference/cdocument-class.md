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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164123"
---
# <a name="cdocument-class"></a>Klasa CDocument

Oferuje podstawowe funkcje dla klas dokumentów zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Konstruuje `CDocument` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::AddView](#addview)|Dołącza widoku do dokumentu.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicjuje Podziel odczytu.|
|[CDocument::CanCloseFrame](#cancloseframe)|Zaawansowane możliwym do zastąpienia; wywołuje się przed zamknięciem ramki okna wyświetlania tego dokumentu.|
|[CDocument::ClearChunkList](#clearchunklist)|Czyści listę fragmentów.|
|[CDocument::ClearPathName](#clearpathname)|Czyści ścieżkę obiektu dokumentu.|
|[CDocument::DeleteContents](#deletecontents)|Wywołana w celu przeprowadzenia czyszczenia dokumentu.|
|[CDocument::FindChunk](#findchunk)|Wyszukuje fragment z określonym identyfikatorem GUID.|
|[CDocument::GetAdapter](#getadapter)|Zwraca wskaźnik do implementacji obiektu `IDocument` interfejsu.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Zwraca wskaźnik do szablonu dokumentu, który opisuje typ dokumentu.|
|[CDocument::GetFile](#getfile)|Zwraca wskaźnik do żądanego `CFile` obiektu.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Zwraca pozycję pierwszego na liście widoków; Umożliwia rozpoczęcie iteracji.|
|[CDocument::GetNextView](#getnextview)|Wykonuje iterację na liście widoków skojarzonych z dokumentem.|
|[CDocument::GetPathName](#getpathname)|Zwraca ścieżkę do pliku danych dokumentu.|
|[CDocument::GetThumbnail](#getthumbnail)|Wywoływana, aby utworzyć mapę bitową do użycia przez dostawcę miniatur do wyświetlania miniatury.|
|[CDocument::GetTitle](#gettitle)|Zwraca element title dokumentu.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Wywołuje się, by zainicjować zawartość wyszukiwania dla procedury obsługi wyszukiwania.|
|[CDocument::IsModified](#ismodified)|Wskazuje, czy dokument został zmieniony od ostatniego zapisu.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Informuje, czy to wystąpienie `CDocument` obsługi wyszukiwania i Organizuj został utworzony obiekt.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Wywoływany w celu załadowania danych dokumentów ze strumienia.|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Metoda wywoływana przed zmianie czcionki podglądu sformatowanego.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Metoda wywoływana po widok jest dodane lub usunięte z dokumentu.|
|[CDocument::OnCloseDocument](#onclosedocument)|Wywołuje się, by zamknąć dokument.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Wywoływane przez platformę, kiedy zachodzi potrzeba Utwórz ramkę, która wersja zapoznawcza podglądu sformatowanego.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Metoda wywoływana przez platformę w odpowiedzi na zdarzenie dokumentu.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Zastępuje tę metodę w klasie pochodnej do rysowania zawartości miniaturę.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Wywoływane przez platformę, kiedy zachodzi potrzeba ładowanie danych dokumentów ze strumienia.|
|[CDocument::OnNewDocument](#onnewdocument)|Wywoływana, aby utworzyć nowy dokument.|
|[CDocument::OnOpenDocument](#onopendocument)|Wywołuje się, aby otworzyć istniejący dokument.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Określa, że procedury obsługi podglądu, aby zwrócić HWND z wywołaniem funkcji przy uzyskaniu fokusu.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Określa, że procedury obsługi podglądu, aby obsłużyć naciśnięcia klawisza przekazywane z pompy komunikatów procesu, w którym jest uruchomiony program obsługi (wersja zapoznawcza).|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Wywołuje się, gdy zmieniono kolor tła podglądu sformatowanego.|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Wywoływane po zmianie czcionki podglądu sformatowanego.|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Wywołuje się, gdy zmianie witryny podglądu sformatowanego.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Wywołuje się, gdy zmieniono kolor tekstu sformatowanego w wersji zapoznawczej.|
|[CDocument::OnSaveDocument](#onsavedocument)|Wywoływana, aby zapisać plik na dysku.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Wywoływane przez platformę, gdy Trwa zwalnianie procedury obsługi podglądu.|
|[CDocument::PreCloseFrame](#precloseframe)|Wywołuje się przed zamknięciem okna ramki.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Odczytuje wartość następnego fragmentów.|
|[CDocument::ReleaseFile](#releasefile)|Wersje plików, aby stał się dostępny do użytku przez inne aplikacje.|
|[CDocument::RemoveChunk](#removechunk)|Usuwa fragment z określonym identyfikatorem GUID.|
|[CDocument::RemoveView](#removeview)|Odłącza widoku z dokumentu.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Zaawansowane możliwym do zastąpienia; wywołuje się, gdy otwarty lub operacja zapisywania nie może zostać zakończona z powodu wyjątku.|
|[CDocument::SaveModified](#savemodified)|Zaawansowane możliwym do zastąpienia; wywołuje się, by poprosić użytkownika, czy można zapisać dokumentu.|
|[CDocument::SetChunkValue](#setchunkvalue)|Ustawia wartość fragmentów.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy dokument zostały zmodyfikowane od ostatniego zapisu.|
|[CDocument::SetPathName](#setpathname)|Ustawia ścieżkę pliku danych używanego przez dokument.|
|[CDocument::SetTitle](#settitle)|Ustawia tytuł dokumentu.|
|[CDocument::UpdateAllViews](#updateallviews)|Powiadamia o wszystkich widoków, które dokumentują został zmodyfikowany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączony dokument.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Włącza polecenia Wyślij pocztę, jeśli występuje obsługi poczty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Określa, że `CDocument` obiekt został utworzony przez dllhost miniatur. Powinny być sprawdzane `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Określa, że `CDocument` obiekt został utworzony przez prevhost dla `Rich Preview`. Powinny być sprawdzane `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Określa, że `CDocument` obiekt został utworzony przez indeksatora lub innych aplikacji wyszukiwania.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Określa kolor tła okna podglądu sformatowanego. Tego koloru zostanie ustawiona przez hosta.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Określa kolor pierwszego planu okna podglądu sformatowanego. Tego koloru zostanie ustawiona przez hosta.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Określa czcionkę dla okna podglądu sformatowanego. Te informacje czcionka jest ustawiany przez hosta.|

## <a name="remarks"></a>Uwagi

Dokument reprezentuje jednostkę danych użytkownik zwykle zostanie otwarty przy użyciu polecenia Otwórz plik i zapisuje za pomocą polecenia Zapisz plik.

`CDocument` obsługuje standardowe operacje, takie jak tworzenie dokumentów, załadowanie go i zapisanie go. Struktura manipuluje dokumentów za pomocą interfejsu zdefiniowane przez `CDocument`.

Aplikacja może obsługiwać więcej niż jeden typ dokumentu. na przykład aplikacja może obsługiwać, arkusze kalkulacyjne i dokumenty tekstowe. Każdy typ dokumentu ma szablonem powiązany dokument; Szablon dokumentu, który określa, jakie zasoby (na przykład tabela menu, ikona lub klawiszy skrótów) są używane dla tego typu dokumentu. Każdy dokument zawiera wskaźnik do związanych z nią `CDocTemplate` obiektu.

Użytkownicy korzystać z dokumentu za pośrednictwem [CView](../../mfc/reference/cview-class.md) obiektów skojarzonych z nim. Widok renderuje obraz dokumentu w oknie ramowym i interpretuje dane wejściowe użytkownika jako operacji na dokumencie. Dokumentu może mieć wiele widoków skojarzonych z nim. Gdy użytkownik otworzy okno w dokumencie, struktura tworzy widok i dołącza go do dokumentu. Szablon dokumentu, który określa, jakiego typu widoku i ramki okna są używane do wyświetlania każdego typu dokumentu.

Dokumenty są częścią standardu struktury polecenia routingu i w związku z tym odbierania poleceń od składników standardowy interfejs użytkownika (na przykład Zapisz plik element menu). Dokument otrzyma poleceń przekazywany przy bieżącym widokiem. Jeśli dokument nie obsługuje danego polecenia, przekazuje polecenia do szablonu dokumentu, który zarządza nim.

Po modyfikacji danych dokumentu we wszystkich widokach powinny odzwierciedlać te zmiany. `CDocument` udostępnia [funkcji UpdateAllViews](#updateallviews) funkcję członkowską powiadomienie widoków takie zmiany, więc widoki mogą sami repaint zgodnie z potrzebami. Struktura również monituje użytkownika o Zapisz zmodyfikowany plik przed jego zamknięciem.

Aby zaimplementować dokumentów w typowej aplikacji, wykonaj następujące czynności:

- Wyprowadzić klasę z `CDocument` dla każdego typu dokumentu.

- Dodaj zmienne Członkowskie do przechowywania danych poszczególnych dokumentów.

- Implementowanie funkcji elementów członkowskich do odczytywania i modyfikowania danych dokumentu. Widoki dokumentu są użytkownicy najważniejszych te funkcje elementów członkowskich.

- Zastąp [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcja elementu członkowskiego w klasie dokumentów do zapisywania i odczytywania danych dokumentu do i z dysku.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

Aby uzyskać więcej informacji na temat `CDocument`, zobacz [serializacji](../../mfc/serialization-in-mfc.md), [tematy architektury dokument/widok](../../mfc/document-view-architecture.md), i [tworzenia dokumentu/widoku](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="addview"></a>  CDocument::AddView

Wywołaj tę funkcję, aby dołączyć widoku do dokumentu.

```
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskazuje widoku dodawany.

### <a name="remarks"></a>Uwagi

Ta funkcja dodaje określony widok listy widoków skojarzonych z dokumentu. Funkcja spowoduje także ustawienie widoku wskaźnikiem dokumentu do tego dokumentu. Struktura wywołuje tę funkcję, podczas dołączania obiekt nowo utworzony widok do dokumentu. Dzieje się w odpowiedzi na polecenie Nowy plik, otwórz plik lub nowe okno lub okno rozdzielacza zostanie podzielona.

Wywołaj tę funkcję tylko wtedy, gdy są ręcznie tworzenie i dołączanie widoku. Zazwyczaj umożliwi framework łączenie dokumentów i widoków, definiując [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) obiektu do skojarzenia z klasą dokumentu, widoku klasy i klasę okna ramowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks

Inicjuje Podziel odczytu.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Uwagi

##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame

Wywoływane przez platformę przed zamknięciem okna ramki wyświetlania dokumentu.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Wskazuje okno ramowe widoku dołączony do dokumentu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli jest to bezpieczne zamknąć okno ramowe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza, czy istnieją inne okna ramowe wyświetlania dokumentu. Jeśli okno ramki o określonym jest ostatni, który wyświetla dokument, funkcja monit o zapisanie dokumentu, jeśli został zmodyfikowany. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe jest zamknięty. Jest to zaawansowany możliwym do zastąpienia.

##  <a name="cdocument"></a>  CDocument::CDocument

Konstruuje `CDocument` obiektu.

```
CDocument();
```

### <a name="remarks"></a>Uwagi

Struktura obsługuje tworzenie dokumentów dla Ciebie. Zastąp [OnNewDocument](#onnewdocument) funkcja elementu członkowskiego, aby wykonać inicjowania na podstawie powiązany z dokumentem; jest to szczególnie ważne w aplikacjach interfejsu (SDI) pojedynczego dokumentu.

##  <a name="clearchunklist"></a>  CDocument::ClearChunkList

Czyści listę fragmentów.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Uwagi

##  <a name="clearpathname"></a>  CDocument::ClearPathName

Czyści ścieżkę obiektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Uwagi

Czyszczenie ścieżki z `CDocument` obiektu powoduje, że aplikacja wyświetla monit o użytkownika, gdy dokument zostanie następnie zapisany. To sprawia, że **Zapisz** polecenia zachowują się jak **Zapisz jako** polecenia.

##  <a name="deletecontents"></a>  CDocument::DeleteContents

Wywoływane przez platformę, aby usunąć dane dokumentu bez niszczenia samego `CDocument` sam obiekt.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Uwagi

Jest ona wywoływana przed dokumencie mają zostać zniszczone. Jest również nazywany, aby upewnić się, że dokument jest pusty, zanim zostanie on użyty ponownie. Jest to szczególnie ważne w przypadku aplikacji interfejsu SDI, który używa tylko jeden dokument; dokument jest ponownie zawsze wtedy, gdy użytkownik tworzy lub zostanie otwarty w innym dokumencie. Wywołaj tę funkcję, aby zaimplementować "Edytuj wyczyść wszystkie" lub podobne polecenie usuwa wszystkie dane dokumentu. Domyślna implementacja tej funkcji, nic nie robi. Należy przesłonić tę funkcję, aby usunąć dane w dokumencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>  CDocument::FindChunk

Wyszukuje fragment o określonym identyfikatorze GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Identyfikator GUID*<br/>
Określa identyfikator GUID fragmentu, aby znaleźć.

*Identyfikator PID*<br/>
Określa identyfikator PID fragment można znaleźć.

### <a name="return-value"></a>Wartość zwracana

Pozycja na liście wewnętrznych fragmentów, w przypadku powodzenia. W przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="getadapter"></a>  CDocument::GetAdapter

Zwraca wskaźnik do implementacji obiektu `IDocument` interfejsu.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do implementacji obiektu `IDocument` interfejsu.

### <a name="remarks"></a>Uwagi

##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate

Wywołaj tę funkcję, aby uzyskać wskaźnik do szablonu dokumentu dla tego typu dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do szablonu dokumentu dla tego typu dokumentu lub wartość NULL, jeśli dokument nie jest zarządzany przez szablon dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>  CDocument::GetFile

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do `CFile` obiektu.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku plików, który wskazuje stan ukończenia operacji.

*nOpenFlags*<br/>
Tryb udostępnianiem i dostępem. Określa akcję wykonywaną podczas otwierania pliku. Można łączyć opcji wymienionych w Konstruktorze CFile [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) przy użyciu bitowe OR (&#124;) — operator. Uprawnienie dostępu jednego i jeden udział opcji są wymagane; `modeCreate` i `modeNoInherit` tryby są opcjonalne.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFile` obiektu.

##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

Wywołaj tę funkcję, aby uzyskać położenie pierwszy widok na liście widoków skojarzonych z dokumentem.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość pozycji, która może służyć do iteracji za pomocą [GetNextView](#getnextview) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>  CDocument::GetNextView

Wywołaj tę funkcję, aby wykonać iterację przez wszystkie widoki dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*elemencie rPosition*<br/>
Odwołanie do wartości pozycji zwrócony przez poprzednie wywołanie `GetNextView` lub [GetFirstViewPosition](#getfirstviewposition) funkcji elementów członkowskich. Ta wartość nie może być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do widoku identyfikowane przez *elemencie rPosition*.

### <a name="remarks"></a>Uwagi

Funkcja zwraca widok identyfikowane przez *elemencie rPosition* , a następnie ustawia *elemencie rPosition* wartość pozycji następnego widoku, na liście. Jeśli pobrano widoku jest ostatnim na liście, następnie *elemencie rPosition* ma wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>  CDocument::GetPathName

Wywołaj tę funkcję, aby uzyskać pełną ścieżkę pliku dyskowego dokumentu.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Wartość zwracana

W pełni kwalifikowana ścieżka dokumentu. Ten ciąg jest pusty, jeśli dokument nie został zapisany lub nie ma pliku dysku skojarzonego z nim.

##  <a name="getthumbnail"></a>  CDocument::GetThumbnail

Tworzy mapę bitową do użycia przez dostawcę miniatur do wyświetlania miniatury.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parametry

*cx*<br/>
Określa szerokość i wysokość mapy bitowej.

*phbmp*<br/>
Zawiera dojście do mapy bitowej, gdy funkcja zwraca pomyślnie.

*pdwAlpha*<br/>
Zawiera wartość DWORD, określając wartość kanał alfa, gdy funkcja zwraca pomyślnie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli mapę bitową do miniatury został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="gettitle"></a>  CDocument::GetTitle

Wywołaj tę funkcję, aby uzyskać tytuł dokumentu, który jest zazwyczaj tworzony na podstawie dokumentu, nazwa_pliku.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł dokumentu.

##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

Wywołuje się, by zainicjować zawartość wyszukiwania dla procedury obsługi wyszukiwania.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby zainicjować wyszukiwanie zawartości. Zawartość musi być ciągiem z części oddzielonych ";". Na przykład "punkt; Prostokąt; Element OLE".

##  <a name="ismodified"></a>  CDocument::IsModified

Wywołaj tę funkcję, aby ustalić, czy dokument został zmieniony od ostatniego zapisu.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został zmieniony od ostatniego zachowywania; w przeciwnym razie 0.

##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

Informuje, czy to wystąpienie `CDocument` została utworzona dla obsługi Organizuj & wyszukiwania.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli wystąpienie `CDocument` została utworzona dla obsługi Organizuj & wyszukiwania.

### <a name="remarks"></a>Uwagi

Obecnie ta funkcja zwraca wartość PRAWDA, tylko w przypadku obsługi podglądu sformatowanego zaimplementowane w poza serwerem przetwarzania. Odpowiednie flagi (m_bPreviewHandlerMode m_bSearchMode, m_bGetThumbnailMode) można ustawić na poziomu aplikacji, aby ta funkcja zwraca wartość TRUE.

##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

Wywoływany w celu załadowania danych dokumentów ze strumienia.

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

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja ładowania zakończy się powodzeniem, w przeciwnym razie wartość HRESULT z kodem błędu.

### <a name="remarks"></a>Uwagi

Można zastąpić tę metodę w klasie pochodnej, aby dostosować sposób ładowania danych ze strumienia.

##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

Określa, że `CDocument` obiekt został utworzony przez dllhost miniatur. Powinny być sprawdzane `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Uwagi

`TRUE` Wskazuje, czy dokument został utworzony przez dllhost miniatur.

##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

Określa, że `CDocument` obiekt został utworzony przez prevhost podglądu sformatowanego. Powinny być sprawdzane `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE wskazuje, że dokument został utworzony przez prevhost podglądu sformatowanego.

##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

Określa, że `CDocument` obiekt został utworzony przez indeksator lub innej aplikacji wyszukiwania.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Uwagi

`TRUE` Wskazuje, czy dokument został utworzony przez indeksator lub innej aplikacji wyszukiwania.

##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

Określa kolor tła okna podglądu sformatowanego. Tego koloru zostanie ustawiona przez hosta.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

Określa kolor pierwszego planu okna podglądu sformatowanego. Tego koloru zostanie ustawiona przez hosta.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

Określa czcionkę dla okna podglądu sformatowanego. Te informacje czcionka jest ustawiany przez hosta.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Uwagi

##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

Metoda wywoływana przed zmianie czcionki podglądu sformatowanego.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

Wywoływane przez platformę po widok jest dodane lub usunięte z dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja sprawdza, czy ostatni widok jest usuwana, a jeśli tak, powoduje usunięcie dokumentu. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, jeśli w ramach dodaje lub usuwa widoku. Na przykład jeśli chcesz, aby dokument pozostają otwarte, nawet wtedy, gdy Brak widoków podłączone do niego, należy przesłonić tę funkcję.

##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument

Wywoływane przez platformę, gdy dokument zostanie zamknięty, zwykle jako część polecenia Zamknij plik.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji niszczy wszystkich ramek, używany do wyświetlania dokumentu, zamyka widoku, czyści zawartość dokumentu, a następnie wywołuje [DeleteContents](#deletecontents) funkcja elementu członkowskiego, można usunąć dokumentu dane.

Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnej operacji czyszczenia przetwarzania w ramach powoduje zamknięcie dokumentu. Na przykład jeśli dokument reprezentuje rekord w bazie danych, możesz zastąpić tę funkcję, aby zamknąć bazy danych. Z przesłonięcia, należy wywołać tę funkcję w wersji klasy bazowej.

##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

Wywoływane przez platformę, kiedy zachodzi potrzeba Utwórz ramkę, która wersja zapoznawcza podglądu sformatowanego.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ramka został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

Metoda wywoływana przez platformę w odpowiedzi na zdarzenie dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*deEvent*<br/>
[in] Typ wyliczany danych, który opisuje typ zdarzenia.

### <a name="remarks"></a>Uwagi

Zdarzenia dokumentu może mieć wpływ na wiele klas. Ta metoda jest odpowiedzialna za obsługę zdarzeń dokumentów, które wpływają na klasy innej niż [klasa CDocument](../../mfc/reference/cdocument-class.md). Obecnie to jedyna klasa, która musi odpowiadać na zdarzenia dokumentu [klasa CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). `CDocument` Klasa ma inne zastąpienie metody odpowiedzialny za obsługę wpływu na `CDocument`.

Poniższa tabela zawiera listę możliwych wartości dla *deEvent* i zdarzenia, które są zgodne.

|Wartość|Odpowiednie zdarzenie|
|-----------|-------------------------|
|`onAfterNewDocument`|Utworzono nowy dokument.|
|`onAfterOpenDocument`|Nowy dokument został otwarty.|
|`onAfterSaveDocument`|Dokument został zapisany.|
|`onAfterCloseDocument`|Dokument został zamknięty.|

##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

Należy przesłonić tę metodę w klasie pochodnej, aby narysować miniatury.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*dc*<br/>
Odwołanie do kontekstu urządzenia.

*lprcBounds*<br/>
Określa prostokąt otaczający obszaru, gdzie ma być rysowany miniatury.

### <a name="remarks"></a>Uwagi

##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail

Wysyła komunikat za pośrednictwem hosta rezydentnego poczty (jeśli istnieją) w dokumencie jako załącznik.

```
void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail` wywołania [OnSaveDocument](#onsavedocument) do serializacji (Zapisz) bez tytułu i zmodyfikowane dokumenty do tymczasowego pliku, który jest następnie wysyłany za pośrednictwem poczty elektronicznej. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagana; oryginalne są wysyłane. `OnFileSendMail` ładuje MAPI32. Biblioteki DLL, jeśli nie została jeszcze załadowana.

Implementacja specjalny `OnFileSendMail` dla [COleDocument](../../mfc/reference/coledocument-class.md) obsługuje złożone pliki poprawnie.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

Wywoływane przez platformę, kiedy zachodzi potrzeba ładowanie danych dokumentów ze strumienia.

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

### <a name="return-value"></a>Wartość zwracana

S_OK, jeżeli obciążenie jest kończy się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

##  <a name="onnewdocument"></a>  CDocument::OnNewDocument

Metoda wywoływana przez framework jako część polecenia nowy plik.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został pomyślnie zainicjowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja wywołuje [DeleteContents](#deletecontents) funkcja elementu członkowskiego, aby upewnić się, że dokument jest pusty, a następnie oznacza nowy dokument jako czystych. Należy przesłonić tę funkcję, aby zainicjować struktury danych dla nowego dokumentu. Z przesłonięcia, należy wywołać tę funkcję w wersji klasy bazowej.

Jeśli użytkownik wybierze polecenie Nowy plik w aplikacji interfejsu SDI, środowisko wykorzystuje tę funkcję, aby ponownie zainicjować istniejący dokument, zamiast tworzenia nowej. Jeśli użytkownik wybierze nowy plik w wielu aplikacji interfejsu (MDI) dokumentu, struktura tworzy nowy dokument za każdym razem, a następnie wywołuje tę funkcję, aby go zainicjować. Kod inicjowania należy umieścić w tej funkcji, a nie w Konstruktorze polecenia nowy plik zaczęła obowiązywać w aplikacji SDI.

Należy zauważyć, że istnieją przypadków, gdy `OnNewDocument` jest wywoływana dwa razy. Dzieje się tak, gdy dokument zostanie osadzony jako serwer dokumentu ActiveX. Funkcja najpierw jest wywoływany przez `CreateInstance` — metoda (udostępnianych przez `COleObjectFactory`-klasy pochodnej) i drugi raz przez `InitNew` — metoda (udostępniany przez `COleServerDoc`-klasy pochodnej).

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywnych metod inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>  CDocument::OnOpenDocument

Metoda wywoływana przez framework jako część polecenia Otwórz plik.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje ścieżkę dokumentu, który ma zostać otwarty.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został pomyślnie załadowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołania [DeleteContents](#deletecontents) wywołuje funkcję elementu członkowskiego, aby upewnić się, że dokument jest pusty, [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do odczytu tego pliku zawartość, a następnie oznacza dokumentu jako czystych. Należy przesłonić tę funkcję, jeśli chcesz użyć innego niż mechanizmu archiwum lub mechanizm pliku. Na przykład napisać aplikację, w którym dokumenty reprezentują rekordy w bazie danych, a nie oddzielnych plików.

Jeśli użytkownik wybierze polecenia Otwórz plik w aplikacji interfejsu SDI, środowisko wykorzystuje tę funkcję, aby ponownie zainicjować istniejącego `CDocument` obiektu, zamiast tworzenia nowej. Jeśli użytkownik wybierze Otwórz plik w aplikacji MDI, struktura tworzy nowy `CDocument` obiektu każdorazowo, a następnie wywołuje tę funkcję, aby go zainicjować. Kod inicjowania należy umieścić w tej funkcji, a nie w Konstruktorze polecenia Otwórz plik zaczęła obowiązywać w aplikacji SDI.

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywnych metod inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

Określa, że procedury obsługi podglądu do zwrócenia HWND pobierane z wywołaniem `GetFocus` funkcji.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*phwnd*<br/>
[out] Po powrocie z tej metody zawiera wskaźnik do HWND zwrócony z wywołania `GetFocus` funkcji z wątku na pierwszym planie procedury obsługi podglądu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia; lub w przeciwnym razie wartość błędu.

### <a name="remarks"></a>Uwagi

##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

Określa, że procedury obsługi podglądu, aby obsłużyć naciśnięcia klawisza przekazywane z pompy komunikatów procesu, w którym jest uruchomiony program obsługi (wersja zapoznawcza).

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
[in] Wskaźnik do komunikatów okien.

### <a name="return-value"></a>Wartość zwracana

Jeśli komunikat o naciśnięcie klawisza mogą być przetwarzane przez program obsługi (wersja zapoznawcza), program obsługi przetwarza je i zwraca wartość S_OK. Jeśli program obsługi (wersja zapoznawcza) nie może przetworzyć komunikatu naciśnięcia klawisza, oferuje ją do hosta za pośrednictwem `IPreviewHandlerFrame::TranslateAccelerator`. Jeśli host przetworzy komunikat, ta metoda zwraca wartość S_OK. Ta metoda zwraca wartość S_FALSE, jeśli host nie przetwarza wiadomości.

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

Wywołuje się, gdy zmieniono kolor tła podglądu sformatowanego.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

Wywoływane po zmianie czcionki podglądu sformatowanego.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

Wywołuje się, gdy zmianie witryny podglądu sformatowanego.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

Wywołuje się, gdy zmieniono kolor tekstu sformatowanego w wersji zapoznawczej.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Uwagi

##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument

Metoda wywoływana przez framework jako część polecenia Zapisz plik i Zapisz plik jako.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje pełną ścieżkę, do której chcesz zapisać plik.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został pomyślnie zapisany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) można zapisać danych dokumentu do pliku, a następnie znaków dokumentu jako czyszczenia. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, jeśli w ramach zapisywania dokumentu. Na przykład napisać aplikację, w którym dokumenty reprezentują rekordy w bazie danych, a nie oddzielnych plików.

##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

Wywoływane przez platformę, gdy procedury obsługi podglądu jest zwalniana.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Uwagi

##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

Włącza polecenie ID_FILE_SEND_MAIL, jeśli obsługa poczty (MAPI) jest obecny.

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiektów powiązanych z poleceniem ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Uwagi

W przeciwnym razie funkcja usuwa polecenie ID_FILE_SEND_MAIL z menu, łącznie z separatorami powyżej lub poniżej elementu menu, zgodnie z potrzebami. MAPI jest włączona, jeśli MAPI32. Biblioteka DLL znajduje się w ścieżce i w sekcji [pocztą] ZWYCIĘSTWA. Plik INI, MAPI = 1. Większość aplikacji, umieść polecenie w menu Plik.

`CDocument` obsługuje wysyłanie dokumentu za pośrednictwem poczty, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

##  <a name="precloseframe"></a>  CDocument::PreCloseFrame

Ta funkcja członkowska jest wywoływana przez platformę, przed okno ramowe zostanie zniszczony.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame*<br/>
Wskaźnik do [CFrameWnd](../../mfc/reference/cframewnd-class.md) przechowuje skojarzone `CDocument` obiektu.

### <a name="remarks"></a>Uwagi

Może być zastąpiona zapewniają oczyszczania niestandardowe, ale pamiętaj wywołać klasy bazowej.

Domyślne ustawienie `PreCloseFrame` nic nie robi `CDocument`. `CDocument`-Klasy pochodne [COleDocument](../../mfc/reference/coledocument-class.md) i [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) użyć tej funkcji elementu członkowskiego.

##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

Odczytuje wartość następnego fragmentów.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*ppValue*<br/>
[out] Po powrocie z tej funkcji *ppValue* zawiera wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="releasefile"></a>  CDocument::ReleaseFile

Ta funkcja członkowska jest wywoływana przez platformę, by wersji pliku, udostępniając ją do użytku przez inne aplikacje.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do obiektu CFile do wydania.

*bAbort*<br/>
Określa, czy plik ma zostać zwolniona przy użyciu `CFile::Close` lub `CFile::Abort`. Wartość FALSE, jeśli plik ma zostać zwolniona, za pomocą [CFile::Close](../../mfc/reference/cfile-class.md#close); Wartość TRUE, jeśli plik ma zostać zwolniona, za pomocą [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Uwagi

Jeśli *bAbort* ma wartość PRAWDA, `ReleaseFile` wywołania `CFile::Abort`, i udostępnieniu pliku. `CFile::Abort` nie spowoduje zgłoszenie wyjątku.

Jeśli *bAbort* ma wartość FAŁSZ, `ReleaseFile` wywołania `CFile::Close` i udostępnieniu pliku.

Zastąpienie tej funkcji elementu członkowskiego, aby wymagać akcji przez użytkownika przed udostępnieniem pliku.

##  <a name="removechunk"></a>  CDocument::RemoveChunk

Usuwa fragment z określonym identyfikatorem GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Identyfikator GUID*<br/>
Określa identyfikator GUID fragment, który ma zostać usunięty.

*Identyfikator PID*<br/>
Określa identyfikator PID fragment, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

##  <a name="removeview"></a>  CDocument::RemoveView

Wywołaj tę funkcję, aby odłączyć widoku z dokumentu.

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pView*<br/>
Wskazuje widoku usuwany.

### <a name="remarks"></a>Uwagi

Ta funkcja usuwa określony widok z listy widoków skojarzonych z dokumentu. Ustawia również wskaźnikiem dokumentu tego widoku, wartość null. Ta funkcja jest wywoływana przez platformę, gdy okno ramowe został zamknięty lub okienku okna rozdzielacza jest zamknięty.

Wywołaj tę funkcję tylko wtedy, gdy są ręcznie odłączanie widoku. Zazwyczaj umożliwi framework odłączyć dokumentów i widoków, definiując [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) obiektu do skojarzenia z klasą dokumentu, widoku klasy i klasę okna ramowego.

Zobacz przykład w [AddView](#addview) przykładową implementację.

##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

Wywoływane, jeśli zostanie zgłoszony wyjątek (zazwyczaj [CFileException](../../mfc/reference/cfileexception-class.md) lub [CArchiveException](../../mfc/reference/carchiveexception-class.md)) podczas zapisywania lub wczytywania dokumentu.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje nazwę dokumentu, który został zapisany lub załadowane.

*e*<br/>
Wskazuje wyjątek, który został wygenerowany. Może mieć wartości NULL.

*bSaving*<br/>
Flaga oznaczająca, jakie operacja jest w toku; różna od zera, jeśli dokument był są zapisywane, 0 Jeśli załadowano dokumentu.

*nIDPDefault*<br/>
Identyfikator komunikatu o błędzie, mają być wyświetlane, jeśli funkcja nie określa bardziej konkretny akcelerator.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza obiekt wyjątku i szuka komunikat o błędzie opisujący przyczynę. Jeśli określony komunikat nie zostanie znaleziony, lub jeśli *e* ma wartość NULL, ogólny komunikat określony przez *nIDPDefault* parametr jest używany. Funkcja następnie wyświetla okno komunikatu, zawierającej komunikat o błędzie. Należy przesłonić tę funkcję, jeśli chcesz udostępnić komunikaty o błędach dodatkowe, dostosowane. Jest to zaawansowany możliwym do zastąpienia.

##  <a name="savemodified"></a>  CDocument::SaveModified

Wywoływane przez platformę przed zmodyfikowanego dokumentu zostanie zamknięty.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli jest bezpieczne kontynuować, a następnie zamknij dokument; 0, jeśli dokument nie powinien zostać zamknięty.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, wyświetla okno komunikatu pytania użytkownika czy zapisać zmiany w dokumencie, jeśli dowolny zostały wprowadzone. Należy przesłonić tę funkcję, jeśli program wymaga innej procedury monitem. Jest to zaawansowany możliwym do zastąpienia.

##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue

Ustawia wartość fragmentów.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Określa wartość fragmentu, aby ustawić.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

Wywołaj tę funkcję, po dokonaniu wszelkie modyfikacje dokumentu.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Flaga oznaczająca, czy dokument został zmieniony.

### <a name="remarks"></a>Uwagi

Stale wywołaniu tej funkcji, pewność, struktura monit o zapisanie zmian przed zamknięciem dokumentu. Zazwyczaj należy użyć wartość domyślną wartość TRUE dla *bModified* parametru. Aby oznaczyć dokumentu, ponieważ czyszczenie (niezmodyfikowanego), wywołaj tę funkcję, o wartości FALSE.

##  <a name="setpathname"></a>  CDocument::SetPathName

Wywołaj tę funkcję, aby określić pełną ścieżkę pliku dyskowego dokumentu.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Wskazuje ciąg, który ma być używany jako ścieżki dla dokumentu.

*bAddToMRU*<br/>
Określa, czy nazwa pliku zostanie dodany do listy ostatnio używanych (MRU) pliku. W przypadku opcji TRUE nazwa pliku jest dodawany; w przypadku wartości FAŁSZ nie został dodany.

### <a name="remarks"></a>Uwagi

W zależności od wartości *bAddToMRU* ścieżka jest dodane lub nie dodany do listy ostatnio używanych przez aplikację. Należy pamiętać, że niektóre dokumenty nie są skojarzone z plikiem dyskowym. Wywołaj tę funkcję tylko wtedy, gdy są zastępowanie Domyślna implementacja otwierania i zapisywania plików używanych przez platformę.

##  <a name="settitle"></a>  CDocument::SetTitle

Wywołaj tę funkcję, aby określić tytuł dokumentu (ciąg wyświetlany na pasku tytułu okna ramki).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle*<br/>
Wskazuje ciąg, który ma być używany jako tytuł dokumentu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji aktualizuje tytuły wszystkich okien ramowych wyświetlające dokument.

##  <a name="updateallviews"></a>  CDocument::UpdateAllViews

Wywołaj tę funkcję, po zmodyfikowaniu dokumentu.

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pSender*<br/>
Wskazuje na widok, który zmodyfikował dokument, lub wartość NULL, jeśli wszystkie widoki, które mają zostać uaktualnione.

*lHint*<br/>
Zawiera informacje o modyfikacji.

*pHint*<br/>
Wskazuje do przechowywania informacji o modyfikacji obiektu.

### <a name="remarks"></a>Uwagi

Należy wywołać tę funkcję, po wywołaniu metody [SetModifiedFlag](#setmodifiedflag) funkcja elementu członkowskiego. Ta funkcja informuje o poszczególnych widokach, dołączony do dokumentu, z wyjątkiem widoku określonego za *pSender*, który został zmodyfikowany dokumentu. Zazwyczaj wywołasz tę funkcję, od Twojej klasy widoku po użytkownik zmienił dokumentu za pośrednictwem widoku.

Ta funkcja wywołuje [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) funkcja elementu członkowskiego dla każdego z widoków dokumentu, z wyjątkiem wysyłanie wyświetlić przekazywanie *pHint* i *lHint*. Użyj tych parametrów do przekazania informacji do widoków dotyczących zmian wprowadzonych do dokumentu. Możesz zakodować informacje przy użyciu *lHint* i/lub można zdefiniować [CObject](../../mfc/reference/cobject-class.md)-klasy w celu przechowywania informacji na temat zmian, a następnie przekazuje obiekt tej klasy przy użyciu *pHint*. Zastąp `CView::OnUpdate` funkcja elementu członkowskiego w Twojej [CView](../../mfc/reference/cview-class.md)-klasy, aby zoptymalizować aktualizowanie widoku są wyświetlane w oparciu o informacje przekazywane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC NPP](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
