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
ms.openlocfilehash: d356ba6b6134221c2fc9595fc6d78f91961c5b7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753244"
---
# <a name="cdocument-class"></a>Klasa CDocument

Zapewnia podstawowe funkcje dla klas dokumentów zdefiniowanych przez użytkownika.

## <a name="syntax"></a>Składnia

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|Konstruuje `CDocument` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::AddView](#addview)|Dołącza widok do dokumentu.|
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicjuje odczyt fragmentu.|
|[CDocument::CanCloseFrame](#cancloseframe)|Zaawansowane zastępowanie; przed zamknięciem okna ramki wyświetlające ten dokument.|
|[CDocument::ClearChunkList](#clearchunklist)|Czyści listę fragmentów.|
|[CDocument::ClearPathName](#clearpathname)|Czyści ścieżkę obiektu dokumentu.|
|[CDocument::DeleteContents](#deletecontents)|Wywoływana do czyszczenia dokumentu.|
|[CDocument::FindChunk](#findchunk)|Wyszukuje fragment z określonym identyfikatorem GUID.|
|[CDocument::GetAdapter](#getadapter)|Zwraca wskaźnik do interfejsu `IDocument` implementującego obiekt.|
|[CDocument::GetDocTemplate](#getdoctemplate)|Zwraca wskaźnik do szablonu dokumentu opisującego typ dokumentu.|
|[CDocument::GetFile](#getfile)|Zwraca wskaźnik do `CFile` żądanego obiektu.|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Zwraca pozycję pierwszego na liście widoków; używane do rozpoczęcia iteracji.|
|[CDocument::GetNextView](#getnextview)|Iteruje za pośrednictwem listy widoków skojarzonych z dokumentem.|
|[CDocument::GetPathName](#getpathname)|Zwraca ścieżkę pliku danych dokumentu.|
|[CDocument::GetThumbnail](#getthumbnail)|Wywoływana w celu utworzenia mapy bitowej, która ma być używana przez dostawcę miniatur do wyświetlania miniatur.|
|[CDocument::GetTitle](#gettitle)|Zwraca tytuł dokumentu.|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Wywoływana w celu zainicjowania zawartości wyszukiwania dla programu Search Handler.|
|[CDocument::Jestmodified](#ismodified)|Wskazuje, czy dokument został zmodyfikowany od czasu jego ostatniego zapisania.|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Określa, czy `CDocument` to wystąpienie obiektu zostało utworzone dla programu obsługi & organizuj wyszukiwanie.|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Wywoływana do ładowania danych dokumentu ze strumienia.|
|[CDocument::OnBeforeRichPreviewFontZmieniony](#onbeforerichpreviewfontchanged)|Wywoływana przed zmianą czcionki Rich Preview.|
|[CDocument::OnChangedViewList](#onchangedviewlist)|Wywoływana po dodaniu lub usunięciu widoku z dokumentu.|
|[CDocument::OnCloseDocument](#onclosedocument)|Wywołany, aby zamknąć dokument.|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Wywoływana przez platformę, gdy musi utworzyć ramkę podglądu dla rich preview.|
|[CDocument::OnDocumentEvent](#ondocumentevent)|Wywoływane przez ramy w odpowiedzi na zdarzenie dokumentu.|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Zastąpi tę metodę w klasie pochodnej, aby narysować zawartość miniatury.|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Wywoływana przez platformę, gdy musi załadować dane dokumentu ze strumienia.|
|[CDocument::OnNewDocument](#onnewdocument)|Wywoływana w celu utworzenia nowego dokumentu.|
|[CDocument::OnOpenDocument](#onopendocument)|Wywoływana w celu otwarcia istniejącego dokumentu.|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Kieruje program obsługi podglądu do zwrócenia HWND z wywołania Funkcji GetFocus.|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Kieruje program obsługi podglądu do obsługi naciśnięcia klawisza przekazywane z pompy wiadomości procesu, w którym jest uruchomiony program obsługi podglądu.|
|[CDocument::OnRichPreviewBackColorPosztowany](#onrichpreviewbackcolorchanged)|Wywoływana po zmianie koloru tła Rich Preview.|
|[CDocument::OnRichPreviewFontZmieniony](#onrichpreviewfontchanged)|Wywoływana po zmianie czcionki Rich Preview.|
|[CDocument::OnRichPreviewSiteZmieniem](#onrichpreviewsitechanged)|Wywoływana po zmianie witryny Rich Preview.|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Wywoływana po zmianie koloru tekstu Podglądu rich.|
|[CDocument::OnSaveDocument](#onsavedocument)|Wywoływana w celu zapisania dokumentu na dysku.|
|[CDocument::OnUnloadHandler](#onunloadhandler)|Wywoływane przez platformę, gdy program obsługi w wersji zapoznawczej jest zwalniany.|
|[CDocument::PreCloseFrame](#precloseframe)|Wywoływane przed zamknięciem okna ramki.|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Odczytuje następną wartość fragmentu.|
|[CDocument::ReleaseFile](#releasefile)|Zwalnia plik, aby udostępnić go do użytku przez inne aplikacje.|
|[CDocument::Usuń](#removechunk)|Usuwa fragment z określonym identyfikatorem GUID.|
|[CDocument::Usuńview](#removeview)|Odłącza widok od dokumentu.|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Zaawansowane zastępowanie; wywoływana, gdy operacja otwierania lub zapisywania nie może zostać ukończona z powodu wyjątku.|
|[CDocument::SaveModified](#savemodified)|Zaawansowane zastępowanie; zapytać użytkownika, czy dokument powinien zostać zapisany.|
|[CDocument::SetChunkValue](#setchunkvalue)|Ustawia wartość fragmentu.|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, że dokument został zmodyfikowany od czasu jego ostatniego zapisania.|
|[CDocument::Nazwa programu SetPath](#setpathname)|Ustawia ścieżkę pliku danych używanego przez dokument.|
|[CDocument::SetTitle](#settitle)|Ustawia tytuł dokumentu.|
|[CDocument::UpdateAllViews](#updateallviews)|Powiadamia wszystkie widoki, że dokument został zmodyfikowany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Włącza polecenie Wyślij pocztę, jeśli obsługa poczty jest obecna.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Określa, `CDocument` że obiekt został utworzony przez dllhost dla miniatur. Należy sprawdzić w `CView::OnDraw`.|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Określa, `CDocument` że obiekt został utworzony przez `Rich Preview`prevhost dla . Należy sprawdzić w `CView::OnDraw`.|
|[CDocument::m_bSearchMode](#m_bsearchmode)|Określa, `CDocument` że obiekt został utworzony przez indeksatora lub inną aplikację wyszukiwania.|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Określa kolor tła okna Podglądu rich. Ten kolor jest ustawiany przez hosta.|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Określa kolor pierwszego planu okna Podglądu rich. Ten kolor jest ustawiany przez hosta.|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Określa czcionkę tekstową okna Podglądu rich. Ta informacja o czcionce jest ustawiana przez hosta.|

## <a name="remarks"></a>Uwagi

Dokument reprezentuje jednostkę danych, którą użytkownik zazwyczaj otwiera za pomocą polecenia Otwieranie pliku i zapisuje za pomocą polecenia Zapisz plik.

`CDocument`obsługuje standardowe operacje, takie jak tworzenie dokumentu, ładowanie go i zapisywanie go. Struktura manipuluje dokumentami `CDocument`przy użyciu interfejsu zdefiniowanego przez program .

Aplikacja może obsługiwać więcej niż jeden typ dokumentu; na przykład aplikacja może obsługiwać zarówno arkusze kalkulacyjne, jak i dokumenty tekstowe. Każdy typ dokumentu ma skojarzony szablon dokumentu; szablon dokumentu określa, jakie zasoby (na przykład menu, ikona lub tabela akceleratora) są używane dla tego typu dokumentu. Każdy dokument zawiera wskaźnik do `CDocTemplate` skojarzonego z nim obiektu.

Użytkownicy wchodzą w interakcję z dokumentem za pośrednictwem skojarzonych z nim obiektów [CView.](../../mfc/reference/cview-class.md) Widok renderuje obraz dokumentu w oknie ramki i interpretuje dane wejściowe użytkownika jako operacje w dokumencie. Dokument może mieć skojarzone z nim wiele widoków. Gdy użytkownik otworzy okno w dokumencie, struktura tworzy widok i dołącza go do dokumentu. Szablon dokumentu określa, jaki typ widoku i okna ramki są używane do wyświetlania każdego typu dokumentu.

Dokumenty są częścią standardowego routingu poleceń framework i w związku z tym otrzymują polecenia ze standardowych składników interfejsu użytkownika (takich jak pozycja menu Zapisywanie plików). Dokument odbiera polecenia przekazywane dalej przez widok aktywny. Jeśli dokument nie obsługuje danego polecenia, przekazuje polecenie do szablonu dokumentu, który nim zarządza.

Po zmodyfikowaniu danych dokumentu każdy z jego widoków musi odzwierciedlać te modyfikacje. `CDocument`udostępnia [UpdateAllViews](#updateallviews) funkcji elementu członkowskiego, aby powiadomić widoki o takich zmianach, więc widoki można przemalować się w razie potrzeby. Struktura monituje również użytkownika o zapisanie zmodyfikowanego pliku przed jego zamknięciem.

Aby zaimplementować dokumenty w typowej aplikacji, należy wykonać następujące czynności:

- Wywodź `CDocument` klasę z każdego typu dokumentu.

- Dodaj zmienne członkowskie do przechowywania danych każdego dokumentu.

- Implementuj funkcje członkowskie do odczytu i modyfikowania danych dokumentu. Widoki dokumentu są najważniejszymi użytkownikami tych funkcji członkowskich.

- Zastąp [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji elementu członkowskiego w klasie dokumentu do pisania i odczytywania danych dokumentu na dysku i z dysku.

`CDocument`obsługuje wysyłanie dokumentu pocztą, jeśli obsługa poczty (MAPI) jest obecna. Zobacz artykuły [MAPI](../../mfc/mapi.md) i [MAPI Support w MFC](../../mfc/mapi-support-in-mfc.md).

Aby uzyskać `CDocument`więcej informacji na temat , zobacz [Serializacja](../../mfc/serialization-in-mfc.md), [Tematy architektury dokumentu/widoku](../../mfc/document-view-architecture.md)oraz [Tworzenie dokumentu/widoku](../../mfc/document-view-creation.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cdocumentaddview"></a><a name="addview"></a>CDocument::AddView

Wywołanie tej funkcji, aby dołączyć widok do dokumentu.

```cpp
void AddView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pWidok*<br/>
Wskazuje dodawany widok.

### <a name="remarks"></a>Uwagi

Ta funkcja dodaje określony widok do listy widoków skojarzonych z dokumentem; funkcja ustawia również wskaźnik dokumentu widoku do tego dokumentu. Struktura wywołuje tę funkcję podczas dołączania nowo utworzonego obiektu widoku do dokumentu; dzieje się tak w odpowiedzi na polecenie File New, File Open lub New Window lub po podzieleniu okna rozdzielacza.

Wywołanie tej funkcji tylko wtedy, gdy ręcznie tworzysz i dołączasz widok. Zazwyczaj można pozwolić ramy połączyć dokumenty i widoki, definiując [obiekt CDocTemplate](../../mfc/reference/cdoctemplate-class.md) skojarzyć klasę dokumentu, klasę widoku i klasy okna ramki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

## <a name="cdocumentbeginreadchunks"></a><a name="beginreadchunks"></a>CDocument::BeginReadChunks

Inicjuje odczyt fragmentu.

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentcancloseframe"></a><a name="cancloseframe"></a>CDocument::CanCloseFrame

Wywoływana przez strukturę przed zamknięciem okna ramki wyświetlającego dokument.

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame (klatka)*<br/>
Wskazuje okno ramki widoku dołączonego do dokumentu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli jest to bezpieczne, aby zamknąć okno ramki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza, czy istnieją inne okna ramki wyświetlające dokument. Jeśli określone okno ramki jest ostatnim, które wyświetla dokument, funkcja monituje użytkownika, aby zapisać dokument, jeśli został zmodyfikowany. Zastąd w tej funkcji należy wykonać specjalne przetwarzanie, gdy okno ramki jest zamknięte. Jest to zaawansowane zastąpienie.

## <a name="cdocumentcdocument"></a><a name="cdocument"></a>CDocument::CDocument

Konstruuje `CDocument` obiekt.

```
CDocument();
```

### <a name="remarks"></a>Uwagi

Struktura obsługuje tworzenie dokumentów dla Ciebie. Zastąp [onnewDocument](#onnewdocument) funkcji elementu członkowskiego do wykonywania inicjowania na podstawie poszczególnych dokumentów; jest to szczególnie ważne w aplikacjach interfejsu pojedynczego dokumentu (SDI).

## <a name="cdocumentclearchunklist"></a><a name="clearchunklist"></a>CDocument::ClearChunkList

Czyści listę fragmentów.

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentclearpathname"></a><a name="clearpathname"></a>CDocument::ClearPathName

Czyści ścieżkę obiektu dokumentu.

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Uwagi

Wyczyszczenie `CDocument` ścieżki z obiektu powoduje, że aplikacja monituje użytkownika o następne zapisanie dokumentu. Powoduje to, że polecenie **Zapisz** zachowuje się jak polecenie **Zapisz jako.**

## <a name="cdocumentdeletecontents"></a><a name="deletecontents"></a>CDocument::DeleteContents

Wywoływane przez strukturę, aby usunąć dane `CDocument` dokumentu bez niszczenia samego obiektu.

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Uwagi

Nazywa się to tuż przed zniszczeniem dokumentu. Jest również wywoływana w celu zapewnienia, że dokument jest pusty przed ponownym użyciem. Jest to szczególnie ważne w przypadku aplikacji SDI, która używa tylko jednego dokumentu; dokument jest ponownie odtwarzany za każdym razem, gdy użytkownik utworzy lub otworzy inny dokument. Wywołanie tej funkcji, aby zaimplementować "Edytuj wyczyść wszystko" lub podobne polecenie, które usuwa wszystkie dane dokumentu. Domyślna implementacja tej funkcji nic nie robi. Zastąd w tej funkcji należy usunąć dane z dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

## <a name="cdocumentfindchunk"></a><a name="findchunk"></a>CDocument::FindChunk

Wyszukuje fragment z określonym identyfikatorem GUID.

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*guid*<br/>
Określa identyfikator GUID fragmentu do znalezienia.

*Pid*<br/>
Określa identyfikator PID fragmentu do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Umieść na wewnętrznej liście fragmentów, jeśli zakończy się pomyślnie. W przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentgetadapter"></a><a name="getadapter"></a>CDocument::GetAdapter

Zwraca wskaźnik do obiektu implementującego `IDocument` interfejs.

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu implementującego `IDocument` interfejs.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentgetdoctemplate"></a><a name="getdoctemplate"></a>CDocument::GetDocTemplate

Wywołanie tej funkcji, aby uzyskać wskaźnik do szablonu dokumentu dla tego typu dokumentu.

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do szablonu dokumentu dla tego typu dokumentu lub NULL, jeśli dokument nie jest zarządzany przez szablon dokumentu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

## <a name="cdocumentgetfile"></a><a name="getfile"></a>CDocument::GetFile

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do `CFile` obiektu.

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżką do żądanego pliku. Ścieżka może być względna lub bezwzględna.

*Perror*<br/>
Wskaźnik do istniejącego obiektu wyjątku pliku, który wskazuje stan zakończenia operacji.

*nOpenLags*<br/>
Tryb udostępniania i dostępu. Określa akcję, która należy podjąć podczas otwierania pliku. Opcje można łączyć wymienione w konstruktorze [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) przy użyciu bitowego operatora OR (&#124;). Wymagane jest jedno uprawnienie dostępu i jedna opcja udziału; `modeCreate` tryby `modeNoInherit` są opcjonalne.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFile` obiektu.

## <a name="cdocumentgetfirstviewposition"></a><a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition

Wywołanie tej funkcji, aby uzyskać pozycję pierwszego widoku na liście widoków skojarzonych z dokumentem.

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość POSITION, która może służyć do iteracji za pomocą funkcji elementu członkowskiego [GetNextView.](#getnextview)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetnextview"></a><a name="getnextview"></a>CDocument::GetNextView

Wywołanie tej funkcji, aby iterować za pośrednictwem wszystkich widoków dokumentu.

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parametry

*rPozycja*<br/>
Odwołanie do wartości POSITION zwrócone przez `GetNextView` poprzednie wywołanie funkcji członkowskich lub [GetFirstViewPosition.](#getfirstviewposition) Ta wartość nie może być null.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do widoku identyfikowany przez *rPosition*.

### <a name="remarks"></a>Uwagi

Funkcja zwraca widok identyfikowany przez *rPosition,* a następnie ustawia *rPosition* do wartości POSITION następnego widoku na liście. Jeśli pobrany widok jest ostatnim na liście, *rPosition* jest ustawiona na WARTOŚĆ NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

## <a name="cdocumentgetpathname"></a><a name="getpathname"></a>CDocument::GetPathName

Wywołanie tej funkcji, aby uzyskać w pełni kwalifikowaną ścieżkę pliku dysku dokumentu.

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>Wartość zwracana

Ścieżka w pełni kwalifikowana dokumentu. Ten ciąg jest pusty, jeśli dokument nie został zapisany lub nie ma skojarzonego z nim pliku dysku.

## <a name="cdocumentgetthumbnail"></a><a name="getthumbnail"></a>CDocument::GetThumbnail

Tworzy mapę bitową, która ma być używana przez dostawcę miniatur do wyświetlania miniatury.

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Określa szerokość i wysokość mapy bitowej.

*phbmp (phbmp)*<br/>
Zawiera dojście do mapy bitowej, gdy funkcja zwraca pomyślnie.

*pdwAlfa*<br/>
Zawiera DWORD określając wartość kanału alfa, gdy funkcja zwraca pomyślnie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli mapa bitowa miniatury została pomyślnie utworzona; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentgettitle"></a><a name="gettitle"></a>CDocument::GetTitle

Wywołanie tej funkcji, aby uzyskać tytuł dokumentu, który jest zwykle pochodną nazwy pliku dokumentu.

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł dokumentu.

## <a name="cdocumentinitializesearchcontent"></a><a name="initializesearchcontent"></a>CDocument::InitializeSearchContent

Wywoływana w celu zainicjowania zawartości wyszukiwania dla programu wyszukiwania.

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Uwagi

Zastąpi tę metodę w klasie pochodnej, aby zainicjować zawartość wyszukiwania. Zawartość powinna być ciągiem z częściami rozdzielanych przez ";". Na przykład "punkt; prostokąt; ole pozycji".

## <a name="cdocumentismodified"></a><a name="ismodified"></a>CDocument::Jestmodified

Wywołanie tej funkcji, aby ustalić, czy dokument został zmodyfikowany, ponieważ został ostatnio zapisany.

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument został zmodyfikowany od czasu ostatniego zapisania; w przeciwnym razie 0.

## <a name="cdocumentissearchandorganizehandler"></a><a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler

Określa, czy `CDocument` to wystąpienie zostało utworzone dla programu obsługi search & Organize.

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, `CDocument` jeśli to wystąpienie zostało utworzone dla programu obsługi search & Organize.

### <a name="remarks"></a>Uwagi

Obecnie ta funkcja zwraca wartość TRUE tylko dla programów obsługi rich preview zaimplementowanych na serwerze poza procesem. Można ustawić odpowiednie flagi (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) na poziomie aplikacji, aby ta funkcja zwróciła wartość TRUE.

## <a name="cdocumentloaddocumentfromstream"></a><a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream

Wywoływana do ładowania danych dokumentu ze strumienia.

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
Wskaźnik do strumienia. Ten strumień jest dostarczany przez powłoki.

*dwGrfMode (tryb dwGrfMode)*<br/>
Tryb dostępu do strumienia.

### <a name="return-value"></a>Wartość zwracana

S_OK jeśli operacja ładowania powiedzie się, w przeciwnym razie HRESULT z kodem błędu.

### <a name="remarks"></a>Uwagi

Tę metodę można zastąpić w klasie pochodnej, aby dostosować sposób ładowania danych ze strumienia.

## <a name="cdocumentm_bgetthumbnailmode"></a><a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode

Określa, że `CDocument` obiekt został utworzony przez dllhost dla miniatur. Należy sprawdzić w `CView::OnDraw`.

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Uwagi

`TRUE`wskazuje, że dokument został utworzony przez dllhost dla miniatur.

## <a name="cdocumentm_bpreviewhandlermode"></a><a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode

Określa, że `CDocument` obiekt został utworzony przez prevhost dla Rich Preview. Należy sprawdzić w `CView::OnDraw`.

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Uwagi

Wartość TRUE wskazuje, że dokument został utworzony przez prevhost dla rich preview.

## <a name="cdocumentm_bsearchmode"></a><a name="m_bsearchmode"></a>CDocument::m_bSearchMode

Określa, że `CDocument` obiekt został utworzony przez indeksatora lub przez inną aplikację wyszukiwania.

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Uwagi

`TRUE`wskazuje, że dokument został utworzony przez indeksatora lub przez inną aplikację wyszukiwania.

## <a name="cdocumentm_clrrichpreviewbackcolor"></a><a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor

Określa kolor tła okna Podgląd bogaty. Ten kolor jest ustawiany przez hosta.

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentm_clrrichpreviewtextcolor"></a><a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor

Określa kolor pierwszego planu okna Podglądu rozszerzonego. Ten kolor jest ustawiany przez hosta.

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentm_lfrichpreviewfont"></a><a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont

Określa czcionkę tekstową okna Podgląd bogaty. Ta informacja o czcionce jest ustawiana przez hosta.

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonbeforerichpreviewfontchanged"></a><a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontZmieniony

Wywoływana przed zmianą czcionki Rich Preview.

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonchangedviewlist"></a><a name="onchangedviewlist"></a>CDocument::OnChangedViewList

Wywoływane przez strukturę po dodaniu widoku lub usunięciu z dokumentu.

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji sprawdza, czy ostatni widok jest usuwany, a jeśli tak, usuwa dokument. Zastąpokaj tę funkcję, jeśli chcesz wykonać specjalne przetwarzanie, gdy struktura dodaje lub usuwa widok. Na przykład jeśli chcesz, aby dokument pozostał otwarty, nawet jeśli nie ma żadnych widoków dołączonych do niego, należy zastąpić tę funkcję.

## <a name="cdocumentonclosedocument"></a><a name="onclosedocument"></a>CDocument::OnCloseDocument

Wywoływane przez strukturę, gdy dokument jest zamknięty, zazwyczaj jako część polecenia Zamknij plik.

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji niszczy wszystkie ramki używane do wyświetlania dokumentu, zamyka widok, czyści zawartość dokumentu, a następnie wywołuje funkcję elementu członkowskiego [DeleteContents,](#deletecontents) aby usunąć dane dokumentu.

Zastąpuj tę funkcję, jeśli chcesz wykonać specjalne przetwarzanie oczyszczania, gdy struktura zamyka dokument. Na przykład jeśli dokument reprezentuje rekord w bazie danych, można zastąpić tę funkcję, aby zamknąć bazę danych. Należy wywołać wersję klasy podstawowej tej funkcji z zastąpienia.

## <a name="cdocumentoncreatepreviewframe"></a><a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame

Wywoływana przez platformę, gdy musi utworzyć ramkę podglądu dla rich preview.

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ramka została utworzona pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentondocumentevent"></a><a name="ondocumentevent"></a>CDocument::OnDocumentEvent

Wywoływane przez ramy w odpowiedzi na zdarzenie dokumentu.

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>Parametry

*deEvent ( deEvent )*<br/>
[w] Wyliczony typ danych opisujący typ zdarzenia.

### <a name="remarks"></a>Uwagi

Zdarzenia dokumentu mogą mieć wpływ na wiele klas. Ta metoda jest odpowiedzialna za obsługę zdarzeń dokumentu, które wpływają na klasy inne niż [CDocument Class](../../mfc/reference/cdocument-class.md). Obecnie jedyną klasą, która musi odpowiadać na zdarzenia dokumentu jest [CDataRecoveryHandler Klasa](../../mfc/reference/cdatarecoveryhandler-class.md). Klasa `CDocument` ma inne możliwe do zastąpienia metody odpowiedzialne `CDocument`za obsługę wpływu na .

W poniższej tabeli wymieniono możliwe wartości *dla deEvent* i zdarzenia, które odpowiadają.

|Wartość|Odpowiednie zdarzenie|
|-----------|-------------------------|
|`onAfterNewDocument`|Utworzono nowy dokument.|
|`onAfterOpenDocument`|Otwarto nowy dokument.|
|`onAfterSaveDocument`|Dokument został zapisany.|
|`onAfterCloseDocument`|Dokument został zamknięty.|

## <a name="cdocumentondrawthumbnail"></a><a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail

Zastąpi tę metodę w klasie pochodnej, aby narysować miniaturę.

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Odwołanie do kontekstu urządzenia.

*lprcBounds (Obfity)*<br/>
Określa prostokąt ograniczający obszaru, w którym ma zostać narysowana miniatura.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonfilesendmail"></a><a name="onfilesendmail"></a>CDocument::OnFileSendMail

Wysyła wiadomość za pośrednictwem hosta poczty rezydenta (jeśli istnieje) z dokumentem jako załącznikiem.

```cpp
void OnFileSendMail();
```

### <a name="remarks"></a>Uwagi

`OnFileSendMail`wzywa [OnSaveDocument](#onsavedocument) do serializacji (zapisywania) dokumentów bez tytułu i zmodyfikowanych do pliku tymczasowego, który jest następnie wysyłany pocztą elektroniczną. Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest potrzebny; oryginał zostanie wysłany. `OnFileSendMail`ładuje MAPI32. DLL, jeśli nie został jeszcze załadowany.

Specjalna implementacja `OnFileSendMail` dla [COleDocument](../../mfc/reference/coledocument-class.md) obsługuje pliki złożone poprawnie.

`CDocument`obsługuje wysyłanie dokumentu pocztą, jeśli obsługa poczty (MAPI) jest obecna. Zobacz artykuły [Tematy MAPI](../../mfc/mapi.md) i [OBSŁUGA MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentonloaddocumentfromstream"></a><a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream

Wywoływana przez platformę, gdy musi załadować dane dokumentu ze strumienia.

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
Wskaźnik do strumienia przychodzącego.

*grfMode (grfMode)*<br/>
Tryb dostępu do strumienia.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli obciążenie zakończy się pomyślnie; w przeciwnym razie kod błędu.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonnewdocument"></a><a name="onnewdocument"></a>CDocument::OnNewDocument

Wywoływana przez strukturę jako część polecenia Plik nowy.

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli dokument został pomyślnie zainicjowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wywołuje funkcję elementu członkowskiego [DeleteContents,](#deletecontents) aby upewnić się, że dokument jest pusty, a następnie oznacza nowy dokument jako czysty. Zastąd w tej funkcji należy zainicjować strukturę danych dla nowego dokumentu. Należy wywołać wersję klasy podstawowej tej funkcji z zastąpienia.

Jeśli użytkownik wybierze polecenie Plik nowy w aplikacji SDI, struktura używa tej funkcji do ponownego zainicjowania istniejącego dokumentu, a nie tworzenia nowego. Jeśli użytkownik wybierze plik nowy w aplikacji interfejsu wielu dokumentów (MDI), struktura tworzy nowy dokument za każdym razem, a następnie wywołuje tę funkcję, aby go zainicjować. Kod inicjowania należy umieścić w tej funkcji, a nie w konstruktorze, aby polecenie Plik nowy było skuteczne w aplikacjach SDI.

Należy zauważyć, że `OnNewDocument` istnieją przypadki, w których jest wywoływana dwa razy. Dzieje się tak, gdy dokument jest osadzony jako serwer dokumentów ActiveX. Funkcja jest najpierw wywoływana `CreateInstance` przez metodę `COleObjectFactory`(widoczna przez klasę pochodną), a drugi przez `InitNew` metodę (widoczna przez klasę pochodną). `COleServerDoc`

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywne metody inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

## <a name="cdocumentonopendocument"></a><a name="onopendocument"></a>CDocument::OnOpenDocument

Wywoływana przez strukturę jako część polecenia Otwieranie pliku.

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Wskazuje ścieżkę dokumentu, który ma zostać otwarty.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument został pomyślnie załadowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołuje funkcję elementu członkowskiego [DeleteContents,](#deletecontents) aby upewnić się, że dokument jest pusty, wywołuje [CObject::Serialize,](../../mfc/reference/cobject-class.md#serialize) aby odczytać zawartość pliku, a następnie oznacza dokument jako czysty. Zastąp tę funkcję, jeśli chcesz użyć czegoś innego niż mechanizm archiwum lub mechanizm plików. Na przykład można napisać aplikację, w której dokumenty reprezentują rekordy w bazie danych, a nie oddzielne pliki.

Jeśli użytkownik wybierze polecenie File Open w aplikacji SDI, framework używa tej funkcji `CDocument` do ponownego zainicjowania istniejącego obiektu, a nie do tworzenia nowego. Jeśli użytkownik wybierze plik otwórz w aplikacji MDI, `CDocument` struktura tworzy nowy obiekt za każdym razem, a następnie wywołuje tę funkcję, aby go zainicjować. Kod inicjowania należy umieścić w tej funkcji, a nie w konstruktorze, aby polecenie File Open było skuteczne w aplikacjach SDI.

### <a name="example"></a>Przykład

Poniższe przykłady ilustrują alternatywne metody inicjowania obiektu dokumentu.

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

## <a name="cdocumentonpreviewhandlerqueryfocus"></a><a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus

Kieruje program obsługi podglądu do zwrócenia HWND `GetFocus` pobrane z wywołania funkcji.

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>Parametry

*phwnd (phwnd)*<br/>
[na zewnątrz] Gdy ta metoda zwraca, zawiera wskaźnik do HWND zwrócony z wywołania `GetFocus` funkcji z wątku pierwszego planu programu obsługi podglądu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK, jeśli zakończy się pomyślnie; lub wartość błędu w inny sposób.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonpreviewhandlertranslateaccelerator"></a><a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator

Kieruje program obsługi podglądu do obsługi naciśnięcia klawisza przekazywane z pompy wiadomości procesu, w którym jest uruchomiony program obsługi podglądu.

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>Parametry

*pmsg*<br/>
[w] Wskaźnik do wiadomości okna.

### <a name="return-value"></a>Wartość zwracana

Jeśli komunikat naciśnięcia klawisza mogą być przetwarzane przez program obsługi podglądu, program obsługi przetwarza go i zwraca S_OK. Jeśli program obsługi podglądu nie może przetworzyć komunikatu `IPreviewHandlerFrame::TranslateAccelerator`naciśnięcia klawisza, oferuje go hostowi za pośrednictwem programu . Jeśli host przetwarza komunikat, ta metoda zwraca S_OK. Jeśli host nie przetwarza wiadomości, ta metoda zwraca S_FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonrichpreviewbackcolorchanged"></a><a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorPosztowany

Wywoływana po zmianie koloru tła Rich Preview.

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonrichpreviewfontchanged"></a><a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontZmieniony

Wywoływana po zmianie czcionki Podglądu rich.

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonrichpreviewsitechanged"></a><a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteZmieniem

Wywoływana po zmianie witryny Rich Preview.

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonrichpreviewtextcolorchanged"></a><a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged

Wywoływana po zmianie koloru tekstu Podglądu sformatowania.

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonsavedocument"></a><a name="onsavedocument"></a>CDocument::OnSaveDocument

Wywoływana przez strukturę jako część polecenia Zapisz plik lub Zapisz plik jako.

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Wskazuje w pełni kwalifikowaną ścieżkę, do której należy zapisać plik.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli dokument został pomyślnie zapisany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji otwiera określony plik, wywołuje [CObject::Serialize,](../../mfc/reference/cobject-class.md#serialize) aby zapisać dane dokumentu do pliku, a następnie oznacza dokument jako czysty. Zastądź tę funkcję, jeśli chcesz wykonać specjalne przetwarzanie, gdy struktura zapisuje dokument. Na przykład można napisać aplikację, w której dokumenty reprezentują rekordy w bazie danych, a nie oddzielne pliki.

## <a name="cdocumentonunloadhandler"></a><a name="onunloadhandler"></a>CDocument::OnUnloadHandler

Wywoływane przez platformę, gdy program obsługi w wersji zapoznawczej jest zwalniany.

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Uwagi

## <a name="cdocumentonupdatefilesendmail"></a><a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail

Włącza polecenie ID_FILE_SEND_MAIL, jeśli obsługa poczty (MAPI) jest obecna.

```cpp
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Wskaźnik do obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) skojarzonego z poleceniem ID_FILE_SEND_MAIL.

### <a name="remarks"></a>Uwagi

W przeciwnym razie funkcja usuwa polecenie ID_FILE_SEND_MAIL z menu, w tym separatory powyżej lub poniżej elementu menu, stosownie do przypadku. MAPI jest włączona, jeśli MAPI32. Biblioteka DLL jest obecna w ścieżce i w sekcji [Mail] win. INI, MAPI=1. Większość aplikacji umieszcza to polecenie w menu Plik.

`CDocument`obsługuje wysyłanie dokumentu pocztą, jeśli obsługa poczty (MAPI) jest obecna. Zobacz artykuły [Tematy MAPI](../../mfc/mapi.md) i [OBSŁUGA MAPI w MFC](../../mfc/mapi-support-in-mfc.md).

## <a name="cdocumentprecloseframe"></a><a name="precloseframe"></a>CDocument::PreCloseFrame

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę przed zniszczeniem okna ramki.

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>Parametry

*pFrame (klatka)*<br/>
Wskaźnik do [CFrameWnd,](../../mfc/reference/cframewnd-class.md) który `CDocument` przechowuje skojarzony obiekt.

### <a name="remarks"></a>Uwagi

Można go zastąpić, aby zapewnić niestandardowe oczyszczanie, ale należy również wywołać klasę podstawową.

Domyślnie `PreCloseFrame` nie robi `CDocument`nic w . Klasy `CDocument`pochodne [COleDocument](../../mfc/reference/coledocument-class.md) i [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) używają tej funkcji elementu członkowskiego.

## <a name="cdocumentreadnextchunkvalue"></a><a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue

Odczytuje następną wartość fragmentu.

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>Parametry

*wartość ppValue*<br/>
[na zewnątrz] Gdy funkcja zwraca, *ppValue* zawiera wartość, która została odczytana.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentreleasefile"></a><a name="releasefile"></a>CDocument::ReleaseFile

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do wydania pliku, dzięki czemu jest dostępny do użycia przez inne aplikacje.

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>Parametry

*p Plik*<br/>
Wskaźnik do CFile obiektu, który ma zostać zwolniony.

*bAbort*<br/>
Określa, czy plik ma zostać wydany `CFile::Close` przy `CFile::Abort`użyciu jednego z nich, czy . FAŁSZ, jeśli plik ma zostać wydany przy użyciu [pliku CFile::Close](../../mfc/reference/cfile-class.md#close); PRAWDA, jeśli plik ma zostać wydany przy użyciu [pliku CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="remarks"></a>Uwagi

Jeśli *bAbort* ma `ReleaseFile` `CFile::Abort`wartość PRAWDA, wywołuje i plik jest zwolniony. `CFile::Abort`nie zda wyjątek.

Jeśli *bAbort* jest `ReleaseFile` `CFile::Close` FALSE, wywołania i plik jest zwolniony.

Zastąp tę funkcję elementu członkowskiego, aby wymagać akcji użytkownika przed wydaniem pliku.

## <a name="cdocumentremovechunk"></a><a name="removechunk"></a>CDocument::Usuń

Usuwa fragment z określonym identyfikatorem GUID.

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>Parametry

*Identyfikator guid*<br/>
Określa identyfikator GUID fragmentu do usunięcia.

*Pid*<br/>
Określa identyfikator PID fragmentu do usunięcia.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentremoveview"></a><a name="removeview"></a>CDocument::Usuńview

Wywołanie tej funkcji, aby odłączyć widok od dokumentu.

```cpp
void RemoveView(CView* pView);
```

### <a name="parameters"></a>Parametry

*pWidok*<br/>
Wskazuje usuwany widok.

### <a name="remarks"></a>Uwagi

Ta funkcja usuwa określony widok z listy widoków skojarzonych z dokumentem; ustawia również wskaźnik dokumentu widoku na NULL. Ta funkcja jest wywoływana przez platformę, gdy okno ramki jest zamknięte lub okienko okna rozdzielacza jest zamknięty.

Wywołanie tej funkcji tylko wtedy, gdy są ręcznie odłączania widoku. Zazwyczaj można pozwolić ramy odłączyć dokumenty i widoki, definiując [obiekt CDocTemplate](../../mfc/reference/cdoctemplate-class.md) skojarzyć klasę dokumentu, klasę widoku i klasy okna ramki.

Zobacz przykład w [AddView](#addview) dla implementacji przykładu.

## <a name="cdocumentreportsaveloadexception"></a><a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException

Wywoływane, jeśli wyjątek (zazwyczaj [CFileException](../../mfc/reference/cfileexception-class.md) lub [CArchiveException)](../../mfc/reference/carchiveexception-class.md)podczas zapisywania lub ładowania dokumentu.

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Wskazuje nazwę dokumentu, który był zapisywany lub ładowany.

*E*<br/>
Wskazuje na wyjątek, który został zgłoszony. Może być null.

*bZłuszanie*<br/>
Flaga wskazująca, jaka operacja była w toku; nonzero, jeśli dokument był zapisywany, 0, jeśli dokument był ładowany.

*nIDPDefault*<br/>
Identyfikator komunikatu o błędzie, który ma być wyświetlany, jeśli funkcja nie określa bardziej szczegółowego.

### <a name="remarks"></a>Uwagi

Domyślna implementacja sprawdza obiekt wyjątku i wyszukuje komunikat o błędzie, który szczegółowo opisuje przyczynę. Jeśli określona wiadomość nie zostanie znaleziona lub *e* ma wartość NULL, używany jest ogólny komunikat określony przez parametr *nIDPDefault.* Następnie funkcja wyświetla okno komunikatu zawierające komunikat o błędzie. Zastąd w tej funkcji należy podać dodatkowe, dostosowane komunikaty o błędach. Jest to zaawansowane zastąpienie.

## <a name="cdocumentsavemodified"></a><a name="savemodified"></a>CDocument::SaveModified

Wywoływane przez ramy przed zmodyfikowany dokument ma zostać zamknięty.

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli jest to bezpieczne, aby kontynuować i zamknąć dokument; 0, jeśli dokument nie powinien być zamknięty.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji wyświetla okno komunikatu z pytaniem użytkownika, czy zapisać zmiany w dokumencie, jeśli zostały wprowadzone. Zastąpokaj tę funkcję, jeśli program wymaga innej procedury monitowania. Jest to zaawansowane zastąpienie.

## <a name="cdocumentsetchunkvalue"></a><a name="setchunkvalue"></a>CDocument::SetChunkValue

Ustawia wartość fragmentu.

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parametry

*wartość pValue*<br/>
Określa wartość fragmentu do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdocumentsetmodifiedflag"></a><a name="setmodifiedflag"></a>CDocument::SetModifiedFlag

Wywołanie tej funkcji po dokonaniu jakichkolwiek zmian w dokumencie.

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZmodyfikowany*<br/>
Flaga wskazująca, czy dokument został zmodyfikowany.

### <a name="remarks"></a>Uwagi

Wywołując tę funkcję konsekwentnie, upewnij się, że struktura monituje użytkownika, aby zapisać zmiany przed zamknięciem dokumentu. Zazwyczaj należy użyć domyślnej wartości TRUE dla parametru *bModified.* Aby oznaczyć dokument jako czysty (niezmodyfikowany), należy wywołać tę funkcję z wartością FAŁSZ.

## <a name="cdocumentsetpathname"></a><a name="setpathname"></a>CDocument::Nazwa programu SetPath

Wywołanie tej funkcji, aby określić w pełni kwalifikowaną ścieżkę pliku dysku dokumentu.

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszPathName (nazwa lpszPathName)*<br/>
Wskazuje ciąg, który ma być używany jako ścieżka dla dokumentu.

*bAddToMRU*<br/>
Określa, czy nazwa pliku jest dodawana do listy ostatnio używanych plików (MRU). Jeśli true, nazwa pliku jest dodawany; jeśli FALSE, nie jest dodawany.

### <a name="remarks"></a>Uwagi

W zależności od wartości *bAddToMRU* ścieżka jest dodawana lub nie dodawana do listy MRU obsługiwanej przez aplikację. Należy zauważyć, że niektóre dokumenty nie są skojarzone z plikiem dysku. Wywołanie tej funkcji tylko wtedy, gdy są zastępowanie domyślnej implementacji do otwierania i zapisywania plików używanych przez platformę.

## <a name="cdocumentsettitle"></a><a name="settitle"></a>CDocument::SetTitle

Wywołanie tej funkcji, aby określić tytuł dokumentu (ciąg wyświetlany na pasku tytułu okna ramki).

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>Parametry

*lpszTitle (lpszTitle)*<br/>
Wskazuje ciąg, który ma być używany jako tytuł dokumentu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji aktualizuje tytuły wszystkich okien ramek, które wyświetlają dokument.

## <a name="cdocumentupdateallviews"></a><a name="updateallviews"></a>CDocument::UpdateAllViews

Wywołanie tej funkcji po zmodyfikowaniu dokumentu.

```cpp
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>Parametry

*pSender (nadawca)*<br/>
Wskazuje widok, który zmodyfikował dokument, lub null, jeśli wszystkie widoki mają zostać zaktualizowane.

*Lhint*<br/>
Zawiera informacje o modyfikacji.

*Phint*<br/>
Wskazuje obiekt przechowujący informacje o modyfikacji.

### <a name="remarks"></a>Uwagi

Tę funkcję należy wywołać po wywołaniu funkcji elementu członkowskiego [SetModifiedFlag.](#setmodifiedflag) Ta funkcja informuje każdy widok dołączony do dokumentu, z wyjątkiem widoku określonego przez *pSender*, że dokument został zmodyfikowany. Zazwyczaj wywołanie tej funkcji z klasy widoku po użytkownik zmienił dokument za pośrednictwem widoku.

Ta funkcja wywołuje [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) funkcji elementu członkowskiego dla każdego z widoków dokumentu z wyjątkiem widoku wysyłania, przekazywanie *pHint* i *lHint*. Te parametry służą do przekazywania informacji do widoków o modyfikacjach wprowadzonych w dokumencie. Można zakodować informacje za pomocą *lHint* i/lub zdefiniować klasę [CObject](../../mfc/reference/cobject-class.md)-derived, aby przechowywać informacje o modyfikacjach i przekazać obiekt tej klasy za pomocą *pHint*. Zastąpić `CView::OnUpdate` funkcję elementu członkowskiego w klasie [CView](../../mfc/reference/cview-class.md)-pochodna, aby zoptymalizować aktualizowanie wyświetlania widoku na podstawie przekazanych informacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Przykładowa npp MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
