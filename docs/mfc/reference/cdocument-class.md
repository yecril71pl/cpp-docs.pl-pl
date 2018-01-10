---
title: "Cdocument — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dad4a2bb3da49b0163367761aeefe85384ecdfb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdocument-class"></a>Cdocument — klasa
Zapewnia podstawowe funkcje dla klas zdefiniowanych przez użytkownika dokumentu.  
  
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
|[CDocument::BeginReadChunks](#beginreadchunks)|Inicjuje bryłkach odczytu.|  
|[CDocument::CanCloseFrame](#cancloseframe)|Zaawansowane możliwym do zastąpienia; wywołuje się przed zamknięciem okno ramowe wyświetlania tego dokumentu.|  
|[CDocument::ClearChunkList](#clearchunklist)|Czyści listę fragmentu.|  
|[CDocument::ClearPathName](#clearpathname)|Czyści ścieżki obiektu dokumentu.|  
|[CDocument::DeleteContents](#deletecontents)|Wywołuje się, by wykonać czyszczenie dokumentu.|  
|[CDocument::FindChunk](#findchunk)|Wyszukuje napotkano fragment z określonym identyfikatorem GUID.|  
|[CDocument::GetAdapter](#getadapter)|Zwraca wskaźnik do obiektu implementacja `IDocument` interfejsu.|  
|[CDocument::GetDocTemplate](#getdoctemplate)|Zwraca wskaźnik do szablonu dokumentu, który opisuje typ dokumentu.|  
|[CDocument::GetFile](#getfile)|Zwraca wskaźnik do żądaną `CFile` obiektu.|  
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|Zwraca pozycję pierwszego na liście widoków; używany do rozpoczęcia iteracji.|  
|[CDocument::GetNextView](#getnextview)|Wykonuje iterację na liście widoków powiązany z dokumentem.|  
|[CDocument::GetPathName](#getpathname)|Zwraca ścieżkę pliku danych dokumentu.|  
|[CDocument::GetThumbnail](#getthumbnail)|Wywoływana w celu utworzenia mapy bitowej do użycia przez dostawcę miniatur do wyświetlania miniatury.|  
|[CDocument::GetTitle](#gettitle)|Zwraca tytuł dokumentu.|  
|[CDocument::InitializeSearchContent](#initializesearchcontent)|Wywołuje się, by zainicjować wyszukiwanie zawartości dla Obsługa wyszukiwania.|  
|[CDocument::IsModified](#ismodified)|Wskazuje, czy dokument został zmieniony od ostatniego zapisu.|  
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|Informuje, czy to wystąpienie `CDocument` obsługi wyszukiwania & Organizuj utworzenia obiektu.|  
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|Wywołuje się, by załadować ze strumienia danych dokumentu.|  
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|Metoda wywoływana przed czcionki podglądu rozbudowanego zostanie zmieniona.|  
|[CDocument::OnChangedViewList](#onchangedviewlist)|Metoda wywoływana po widoku jest dodane lub usunięte z dokumentu.|  
|[CDocument::OnCloseDocument](#onclosedocument)|Wywołuje się, by zamknąć dokument.|  
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|Wywoływane przez platformę, gdy trzeba utworzyć ramkę podglądu dla podglądu rozbudowanego.|  
|[CDocument::OnDocumentEvent](#ondocumentevent)|Wywoływane przez platformę w odpowiedzi na zdarzenia dokumentu.|  
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|Zastępuje tę metodę w klasie pochodnej do rysowania zawartości miniatur.|  
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|Wywoływane przez platformę, kiedy zachodzi potrzeba Załaduj ze strumienia danych dokumentu.|  
|[CDocument::OnNewDocument](#onnewdocument)|Wywołuje się, by utworzyć nowego dokumentu.|  
|[CDocument::OnOpenDocument](#onopendocument)|Wywołuje się, by otworzyć istniejący dokument.|  
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|Określa, że Obsługa podglądu, aby zwrócić HWND z wywołaniem funkcji przy uzyskaniu fokusu.|  
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|Określa, że Obsługa podglądu, aby obsłużyć naciśnięcia klawisza przekazywane z przekazywanie komunikatów procesu, w którym jest uruchomiony program obsługi podglądu.|  
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|Wywoływane, gdy zostanie zmieniony kolor tła podglądu rozbudowanego.|  
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|Wywoływane po zmianie czcionki podglądu rozbudowanego.|  
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|Wywoływane, gdy lokacja podglądu rozbudowanego została zmieniona.|  
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|Wywoływana, gdy zmieniono kolor tekstu sformatowanego w wersji zapoznawczej.|  
|[CDocument::OnSaveDocument](#onsavedocument)|Wywołuje się, by zapisać dokument na dysku.|  
|[CDocument::OnUnloadHandler](#onunloadhandler)|Wywoływane przez platformę, gdy Obsługa podglądu jest zwalniany.|  
|[CDocument::PreCloseFrame](#precloseframe)|Wywołuje się przed zamknięciem ramkę okna.|  
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|Odczytuje następny wartość fragmentu.|  
|[CDocument::ReleaseFile](#releasefile)|Wersje pliku, aby był dostępny do użytku przez inne aplikacje.|  
|[CDocument::RemoveChunk](#removechunk)|Usuwa napotkano fragment z określonym identyfikatorem GUID.|  
|[CDocument::RemoveView](#removeview)|Odłącza widoku z dokumentu.|  
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|Zaawansowane możliwym do zastąpienia; wywoływane, gdy Otwórz lub Zapisz operacji nie może zostać zakończona z powodu wyjątku.|  
|[CDocument::SaveModified](#savemodified)|Zaawansowane możliwym do zastąpienia; wywołuje się, by poprosić użytkownika, czy ma zostać zapisany dokument.|  
|[CDocument::SetChunkValue](#setchunkvalue)|Ustawia wartość fragmentu.|  
|[CDocument::SetModifiedFlag](#setmodifiedflag)|Ustawia flagę wskazującą, czy dokument ma zmodyfikowane od ostatniego zapisu.|  
|[CDocument::SetPathName](#setpathname)|Ustawia ścieżkę pliku danych używanego przez dokument.|  
|[CDocument::SetTitle](#settitle)|Ustawia tytuł dokumentu.|  
|[CDocument::UpdateAllViews](#updateallviews)|Powiadamia wszystkie widoki, które dokument został zmodyfikowany.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocument::OnFileSendMail](#onfilesendmail)|Wysyła wiadomość e-mail z dołączonym dokumentem.|  
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|Umożliwia polecenie Wyślij pocztę, jeśli występuje obsługi poczty.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|Określa, że `CDocument` obiekt został utworzony przez dllhost miniatur. Powinno zostać zaewidencjonowane `CView::OnDraw`.|  
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|Określa, że `CDocument` obiekt został utworzony przez prevhost dla `Rich Preview`. Powinno zostać zaewidencjonowane `CView::OnDraw`.|  
|[CDocument::m_bSearchMode](#m_bsearchmode)|Określa, że `CDocument` obiekt został utworzony przez indeksatora lub innych aplikacji wyszukiwania.|  
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|Określa kolor tła podglądu rozbudowanego okna. Tego koloru zostanie ustawiona przez hosta.|  
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|Określa kolor pierwszego planu podglądu rozbudowanego okna. Tego koloru zostanie ustawiona przez hosta.|  
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|Określa czcionkę dla okna podglądu rozbudowanego. Te informacje czcionki jest ustawiana przez hosta.|  
  
## <a name="remarks"></a>Uwagi  
 Dokument reprezentuje jednostkę dane, które zwykle użytkownik otwiera przy użyciu polecenia Otwórz plik i zapisuje za pomocą polecenia Zapisz plik.  
  
 **Cdocument —** obsługuje standardowe operacje, takie jak tworzenie dokumentów, załadowanie go i zapisać go. Platformę manipuluje dokumentów za pomocą interfejsu zdefiniowane przez **CDocument**.  
  
 Aplikacja może obsługiwać więcej niż jeden typ dokumentu. na przykład aplikacja może obsługiwać zarówno arkusze kalkulacyjne i dokumenty tekstowe. Każdy typ dokumentu ma skojarzone w szablonie; Szablon dokumentu określa, jakie zasoby (na przykład tabela menu, ikona lub akceleratora) są używane dla tego typu dokumentu. Każdy dokument zawiera wskaźnik do jego skojarzony `CDocTemplate` obiektu.  
  
 Użytkownicy korzystają z dokumentu za pomocą [CView](../../mfc/reference/cview-class.md) obiektów skojarzonych z nim. Widok renderuje obraz dokumentu w oknie ramowym i interpretuje dane wejściowe użytkownika jako operacje w dokumencie. Dokumentu może mieć wiele widoków skojarzonych z nim. Gdy użytkownik otwiera okno w dokumencie, platformę tworzy widok i dołącza go do dokumentu. Szablon dokumentu określa, jaki typ widoku i ramki okna są używane do wyświetlania każdego typu dokumentu.  
  
 Dokumenty są częścią standard w ramach polecenia routingu i w związku z tym odbierania poleceń od składników standardowy interfejs użytkownika (na przykład Zapisz plik element menu). Dokument odbiera polecenia przekazywane przez aktywnego widoku. Jeśli dokument nie obsługuje danego polecenia, przekazuje polecenia do szablonu dokumentu, który zarządza nim.  
  
 Modyfikacji danych dokumentu poszczególnych widokach musi odzwierciedlenia tych zmian. **Cdocument —** zapewnia [UpdateAllViews](#updateallviews) funkcji członkowskiej można powiadomić widoków o zmianach, więc widoków można odświeżyć się odpowiednio do potrzeb. Platformę również monituje użytkownika o Zapisz zmodyfikowany plik przed jego zamknięciem.  
  
 Aby zaimplementować dokumentów w typowej aplikacji, wykonaj następujące czynności:  
  
-   Klasa wyprowadzona z **CDocument** dla każdego typu dokumentu.  
  
-   Dodaj element członkowski zmienne do przechowywania danych każdy dokument.  
  
-   Implementowanie funkcji elementów członkowskich do odczytywania i modyfikowania danych dokumentu. Widoki dokumentu są najważniejsze użytkowników z tych funkcji Członkowskich.  
  
-   Zastąpienie [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) funkcji członkowskiej we własnej klasy dokumentu do zapisu i odczytu dokumentu danych do i z dysku.  
  
 **Cdocument —** obsługuje wysyłanie dokumentu pocztą, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).  
  
 Aby uzyskać więcej informacji na temat **CDocument**, zobacz [serializacji](../../mfc/serialization-in-mfc.md), [tematy architektury dokument/widok](../../mfc/document-view-architecture.md), i [tworzenia dokumentu/widoku](../../mfc/document-view-creation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocument`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="addview"></a>CDocument::AddView  
 Wywołanie tej funkcji, aby dołączyć widoku do dokumentu.  
  
```  
void AddView(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pView`  
 Wskazuje widoku dodawany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja dodaje określony widok do listy widoków skojarzonych z dokumentu. Funkcja ustawia również widoku wskaźnik dokumentu do tego dokumentu. Struktura wywołuje tej funkcji podczas podłączania obiektu nowo utworzony widok do dokumentu. Dzieje się tak w odpowiedzi do nowego pliku, otwórz plik lub nowe okno polecenia lub okno podziału dzieli się.  
  
 Wywołanie tej funkcji, tylko w przypadku ręcznego tworzenia i dołączania widoku. Zazwyczaj umożliwi framework łączenie dokumentów i widoków, definiując [cdoctemplate —](../../mfc/reference/cdoctemplate-class.md) powiązania klasy dokumentu, klasa widoku i ramki okna klasy obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]  
  
##  <a name="beginreadchunks"></a>CDocument::BeginReadChunks  
 Inicjuje bryłkach odczytu.  
  
```  
virtual void BeginReadChunks ();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="cancloseframe"></a>CDocument::CanCloseFrame  
 Wywoływane przez platformę przed zamknięciem okno ramowe zawierające dokumentu.  
  
```  
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrame`  
 Wskazuje okno ramowe widoku dołączonym do dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest bezpieczne zamknąć okno ramowe; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja sprawdza, czy istnieją inne okna ramowe wyświetlania dokumentu. Jeśli okno ramowe określony jest ostatnią, który wyświetla dokument, funkcji monit o zapisanie dokumentu, jeśli został on zmodyfikowany. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy okno ramowe jest zamknięty. Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="cdocument"></a>CDocument::CDocument  
 Konstruuje **CDocument** obiektu.  
  
```  
CDocument();
```  
  
### <a name="remarks"></a>Uwagi  
 Platformę obsługuje tworzenie dokumentów dla Ciebie. Zastąpienie [OnNewDocument](#onnewdocument) funkcji członkowskiej, aby wykonać inicjowania na podstawie powiązany z dokumentem; jest to szczególnie ważne w przypadku pojedynczego dokumentu (SDI) interfejsu aplikacji.  
  
##  <a name="clearchunklist"></a>CDocument::ClearChunkList  
 Czyści listę fragmentu.  
  
```  
virtual void ClearChunkList ();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="clearpathname"></a>CDocument::ClearPathName  
 Czyści ścieżki obiektu dokumentu.  
  
```  
virtual void ClearPathName();
```  
  
### <a name="remarks"></a>Uwagi  
 Wyczyszczenie ścieżki z `CDocument` obiektu powoduje aplikacji monit, gdy obok zapisaniu dokumentu. Dzięki temu **zapisać** polecenia przypominają **Zapisz jako** polecenia.  
  
##  <a name="deletecontents"></a>CDocument::DeleteContents  
 Wywoływane przez platformę, aby usunąć dane dokumentu bez niszczenia **CDocument** samego obiektu.  
  
```  
virtual void DeleteContents();
```  
  
### <a name="remarks"></a>Uwagi  
 Jest ona wywoływana bezpośrednio przed zamknięciem dokumentu ma zostać zniszczone. Jest również nazywany, aby upewnić się, że dokument jest pusty, zanim zostanie on użyty ponownie. Jest to szczególnie ważne dla aplikacji SDI, który używa tylko jeden dokument; dokument zostanie ponownie użyty zawsze, gdy użytkownik tworzy lub otwiera innego dokumentu. Wywołanie tej funkcji do zaimplementowania "Edytuj Wyczyść wszystko" lub podobne polecenie, które powoduje usunięcie wszystkich danych dokumentu. Domyślna implementacja ta funkcja nie działa. Należy przesłonić tę funkcję, aby usunąć dane w dokumencie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]  
  
##  <a name="findchunk"></a>CDocument::FindChunk  
 Wyszukuje fragmentu o określonym identyfikatorze GUID.  
  
```  
virtual POSITION FindChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parametry  
 `guid`  
 Określa identyfikator GUID fragmentu, aby znaleźć.  
  
 `pid`  
 Określa identyfikator PID procesu fragmentu można znaleźć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja na liście wewnętrznych fragmentu w przypadku powodzenia. W przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getadapter"></a>CDocument::GetAdapter  
 Zwraca wskaźnik do obiektu implementacja `IDocument` interfejsu.  
  
```  
virtual ATL::IDocument* GetAdapter();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do obiektu implementacja `IDocument` interfejsu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getdoctemplate"></a>CDocument::GetDocTemplate  
 Wywołanie tej funkcji, otrzymywać wskaźnik do szablonu dokumentu dla tego typu dokumentu.  
  
```  
CDocTemplate* GetDocTemplate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do szablonu dokumentu dla tego typu dokumentu lub **NULL** Jeśli dokument nie jest zarządzany przez szablon dokumentu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]  
  
##  <a name="getfile"></a>CDocument::GetFile  
 Wywołanie tej funkcji Członkowskich otrzymywać wskaźnik do `CFile` obiektu.  
  
```  
virtual CFile* GetFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna.  
  
 `pError`  
 Wskaźnik do obiektu wyjątku plików, które wskazuje stan ukończenia operacji.  
  
 `nOpenFlags`  
 Tryb dostępu i udostępniania. Określa akcję wykonywaną podczas otwierania pliku. Opcje wymienione w Konstruktorze cfile — można łączyć [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) przy użyciu wartości bitowe lub (&#124;) — operator. Opcji jednego udziału i uprawnień dostępu co są wymagane; **modeCreate** i **modeNoInherit** tryby są opcjonalne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CFile` obiektu.  
  
##  <a name="getfirstviewposition"></a>CDocument::GetFirstViewPosition  
 Wywołanie tej funkcji, aby uzyskać położenie pierwszy widok na liście widoków powiązany z dokumentem.  
  
```  
virtual POSITION GetFirstViewPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iteracji z [GetNextView](#getnextview) funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getnextview"></a>CDocument::GetNextView  
 Wywołanie tej funkcji do iteracji wszystkie widoki dokumentu.  
  
```  
virtual CView* GetNextView(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `rPosition`  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie wywołanie `GetNextView` lub [GetFirstViewPosition](#getfirstviewposition) funkcji elementów członkowskich. Ta wartość nie może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do widoku identyfikowane przez `rPosition`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwraca widok identyfikowane przez `rPosition` , a następnie ustawia `rPosition` do **pozycji** wartość następnego widoku na liście. Jeśli wyświetlanie pobranych będzie ostatniego na liście `rPosition` ustawiono **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]  
  
##  <a name="getpathname"></a>CDocument::GetPathName  
 Wywołanie tej funkcji można uzyskać w pełni kwalifikowana ścieżka pliku dyskowego dokumentu.  
  
```  
const CString& GetPathName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dokument w pełni kwalifikowaną ścieżkę. Ten ciąg jest pusty, jeśli dokument nie został zapisany lub nie ma skojarzonych z nim pliku dyskowego.  
  
##  <a name="getthumbnail"></a>CDocument::GetThumbnail  
 Tworzy mapę bitową do użycia przez dostawcę miniatur do wyświetlania miniatury.  
  
```  
virtual BOOL GetThumbnail(
    UINT cx,  
    HBITMAP* phbmp,  
    DWORD* pdwAlpha);
```  
  
### <a name="parameters"></a>Parametry  
 `cx`  
 Określa szerokość i wysokość mapy bitowej.  
  
 `phbmp`  
 Zawiera dojścia do mapy bitowej, gdy funkcja zwraca pomyślnie.  
  
 `pdwAlpha`  
 Zawiera wartość typu DWORD określającą wartość kanału alfa, gdy funkcja zwraca pomyślnie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli mapy bitowej do miniatury został utworzony pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettitle"></a>CDocument::GetTitle  
 Wywołanie tej funkcji, aby uzyskać tytuł dokumentu, który zazwyczaj jest określana na podstawie nazwy pliku dokumentu.  
  
```  
const CString& GetTitle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tytuł dokumentu.  
  
##  <a name="initializesearchcontent"></a>CDocument::InitializeSearchContent  
 Wywołuje się, by zainicjować wyszukiwanie zawartości obsługi wyszukiwania.  
  
```  
virtual void InitializeSearchContent ();
```  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej można zainicjować wyszukiwania zawartości. Zawartość musi być ciągiem z części oddzielone ";". Na przykład "punktu; Prostokąt; Element OLE".  
  
##  <a name="ismodified"></a>CDocument::IsModified  
 Wywołanie tej funkcji w celu ustalenia, czy dokument został zmieniony od ostatniego zapisu.  
  
```  
virtual BOOL IsModified();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument został zmodyfikowany od czasu ostatniego zapisu; w przeciwnym razie 0.  
  
##  <a name="issearchandorganizehandler"></a>CDocument::IsSearchAndOrganizeHandler  
 Informuje, czy to wystąpienie `CDocument` został utworzony przez program obsługi wyszukiwania & Organizuj.  
  
```  
BOOL IsSearchAndOrganizeHandler() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli to wystąpienie `CDocument` został utworzony przez program obsługi wyszukiwania & Organizuj.  
  
### <a name="remarks"></a>Uwagi  
 Obecnie ta funkcja zwraca `TRUE` tylko dla obsługi podglądu rozbudowanego zaimplementowana w poza serwerem przetwarzania. Można ustawić flagi odpowiednie (m_bPreviewHandlerMode, m_bSearchMode, m_bGetThumbnailMode) poziomie aplikacji, aby ta funkcja zwracany `TRUE`.  
  
##  <a name="loaddocumentfromstream"></a>CDocument::LoadDocumentFromStream  
 Wywołuje się, by załadować ze strumienia danych dokumentu.  
  
```  
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,  
    DWORD dwGrfMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Wskaźnik do strumienia. Ten strumień jest dostarczany przez powłokę.  
  
 `dwGrfMode`  
 Tryb dostępu do strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli operacja ładowania zakończy się powodzeniem, w przeciwnym razie HRESULT z kodem błędu.  
  
### <a name="remarks"></a>Uwagi  
 Można przesłonić tę metodę w klasie pochodnej, aby dostosować sposób ładowania danych ze strumienia.  
  
##  <a name="m_bgetthumbnailmode"></a>CDocument::m_bGetThumbnailMode  
 Określa, że `CDocument` obiekt został utworzony przez dllhost miniatur. Powinno zostać zaewidencjonowane `CView::OnDraw`.  
  
```  
BOOL m_bGetThumbnailMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Wskazuje, że dokument został utworzony przez dllhost miniatur.  
  
##  <a name="m_bpreviewhandlermode"></a>CDocument::m_bPreviewHandlerMode  
 Określa, że `CDocument` obiekt został utworzony przez prevhost dla podglądu rozbudowanego. Powinno zostać zaewidencjonowane `CView::OnDraw`.  
  
```  
BOOL m_bPreviewHandlerMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Wskazuje, że dokument został utworzony przez prevhost dla podglądu rozbudowanego.  
  
##  <a name="m_bsearchmode"></a>CDocument::m_bSearchMode  
 Określa, że `CDocument` obiekt został utworzony przez indeksatora lub innej aplikacji wyszukiwania.  
  
```  
BOOL m_bSearchMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 `TRUE`Wskazuje, że dokument został utworzony przez indeksatora lub innej aplikacji wyszukiwania.  
  
##  <a name="m_clrrichpreviewbackcolor"></a>CDocument::m_clrRichPreviewBackColor  
 Określa kolor tła okna podglądu rozbudowanego. Tego koloru zostanie ustawiona przez hosta.  
  
```  
COLORREF m_clrRichPreviewBackColor;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_clrrichpreviewtextcolor"></a>CDocument::m_clrRichPreviewTextColor  
 Określa kolor pierwszego planu podglądu rozbudowanego okna. Tego koloru zostanie ustawiona przez hosta.  
  
```  
COLORREF m_clrRichPreviewTextColor;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_lfrichpreviewfont"></a>CDocument::m_lfRichPreviewFont  
 Określa czcionkę dla okna podglądu rozbudowanego. Te informacje czcionki jest ustawiana przez hosta.  
  
```  
CFont m_lfRichPreviewFont;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onbeforerichpreviewfontchanged"></a>CDocument::OnBeforeRichPreviewFontChanged  
 Metoda wywoływana przed czcionki podglądu rozbudowanego zostanie zmieniona.  
  
```  
virtual void OnBeforeRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onchangedviewlist"></a>CDocument::OnChangedViewList  
 Wywoływane przez platformę po widoku jest dodane lub usunięte z dokumentu.  
  
```  
virtual void OnChangedViewList();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja sprawdza, czy ostatni widok jest usuwany, a jeśli tak, powoduje usunięcie dokumentu. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy w ramach dodaje lub usuwa z widoku. Na przykład jeśli chcesz, aby dokument pozostają otwarte, nawet, jeśli nie ma do niego dołączony widoków, należy przesłonić tę funkcję.  
  
##  <a name="onclosedocument"></a>CDocument::OnCloseDocument  
 Wywoływane przez platformę, gdy dokument zostanie zamknięty, zazwyczaj jako część polecenia Zamknij plik.  
  
```  
virtual void OnCloseDocument();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji niszczy wszystkich ramek, używany do wyświetlania dokumentu, zamyka widoku, czyści zawartość dokumentu, a następnie wywołuje [DeleteContents](#deletecontents) funkcji członkowskiej można usunąć dokumentu dane.  
  
 Należy przesłonić tę funkcję, jeśli chcesz wykonać oczyszczania specjalnego przetwarzania platformę powoduje zamknięcie dokumentu. Na przykład jeśli dokument reprezentuje rekord w bazie danych, można przesłonić tę funkcję, aby zamknąć bazy danych. Klasa podstawowa wersja tej funkcji powinny wywoływać z zastąpienia.  
  
##  <a name="oncreatepreviewframe"></a>CDocument::OnCreatePreviewFrame  
 Wywoływane przez platformę, gdy trzeba utworzyć ramkę podglądu dla podglądu rozbudowanego.  
  
```  
virtual BOOL OnCreatePreviewFrame();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli ramka została utworzona pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondocumentevent"></a>CDocument::OnDocumentEvent  
 Wywoływane przez platformę w odpowiedzi na zdarzenia dokumentu.  
  
```  
virtual void OnDocumentEvent(DocumentEvent deEvent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`deEvent`  
 Typ wyliczeniowy danych, który opisuje typ zdarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Zdarzenia dokumentu może mieć wpływ na wiele klas. Ta metoda jest odpowiedzialna za obsługę zdarzeń dokumentów, które mają wpływ na klasy innej niż [cdocument — klasa](../../mfc/reference/cdocument-class.md). Jedyna klasa, która musi odpowiadanie na zdarzenia dokumentu jest obecnie [CDataRecoveryHandler klasy](../../mfc/reference/cdatarecoveryhandler-class.md). `CDocument` Klasa ma inne metody zastępowalnych odpowiedzialny za obsługę wpływu na `CDocument`.  
  
 W poniższej tabeli przedstawiono możliwe wartości `deEvent` i zdarzenia, które są zgodne.  
  
|Wartość|Odpowiednie zdarzenie|  
|-----------|-------------------------|  
|`onAfterNewDocument`|Utworzono nowy dokument.|  
|`onAfterOpenDocument`|Nowy dokument został otwarty.|  
|`onAfterSaveDocument`|Dokument został zapisany.|  
|`onAfterCloseDocument`|Dokument został zamknięty.|  
  
##  <a name="ondrawthumbnail"></a>CDocument::OnDrawThumbnail  
 Zastępuje tę metodę w klasie pochodnej, aby narysować miniatury.  
  
```  
virtual void OnDrawThumbnail(
    CDC& dc,  
    LPRECT lprcBounds);
```  
  
### <a name="parameters"></a>Parametry  
 `dc`  
 Odwołanie do kontekstu urządzenia.  
  
 `lprcBounds`  
 Określa prostokąt ograniczający obszaru, gdzie ma być rysowany miniatury.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onfilesendmail"></a>CDocument::OnFileSendMail  
 Wysyła komunikat za pośrednictwem hosta rezydentna poczty (jeśli istnieją) w dokumencie jako załącznik.  
  
```  
void OnFileSendMail();
```  
  
### <a name="remarks"></a>Uwagi  
 `OnFileSendMail`wywołania [OnSaveDocument](#onsavedocument) do serializacji (bez tytułu i zmodyfikowane dokumenty do pliku tymczasowego, który jest następnie wysyłana za pośrednictwem poczty elektronicznej Zapisz). Jeśli dokument nie został zmodyfikowany, plik tymczasowy nie jest wymagane; oryginalny są wysyłane. `OnFileSendMail`ładuje MAPI32. Biblioteki DLL, jeśli nie został już załadowany.  
  
 Specjalne implementacja `OnFileSendMail` dla [COleDocument](../../mfc/reference/coledocument-class.md) poprawnie złożone dojść do plików.  
  
 **Cdocument —** obsługuje wysyłanie dokumentu pocztą, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="onloaddocumentfromstream"></a>CDocument::OnLoadDocumentFromStream  
 Wywoływane przez platformę, kiedy zachodzi potrzeba Załaduj ze strumienia danych dokumentu.  
  
```  
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,  
    DWORD grfMode);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 Wskaźnik do strumienia przychodzącego.  
  
 `grfMode`  
 Tryb dostępu do strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, jeśli obciążenie zakończy się pomyślnie; w przeciwnym razie kod błędu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onnewdocument"></a>CDocument::OnNewDocument  
 Wywoływane przez platformę jako część polecenia nowy plik.  
  
```  
virtual BOOL OnNewDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument został pomyślnie zainicjowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja wymaga [DeleteContents](#deletecontents) funkcji członkowskiej, aby upewnić się, że dokument jest pusty i oznaczy wtedy nowy dokument jako czystych. Należy przesłonić tę funkcję, aby zainicjować struktury danych dla nowego dokumentu. Klasa podstawowa wersja tej funkcji powinny wywoływać z zastąpienia.  
  
 Jeśli użytkownik wybierze polecenie Nowy plik w aplikacji SDI, platforma korzysta z tej funkcji może ponownie zainicjować istniejącego dokumentu, zamiast tworzenia nowej. Jeśli użytkownik wybierze nowy plik w wiele aplikacji interfejsu (MDI) dokumentu, platformę tworzy nowy dokument, a następnie wywołuje tę funkcję, aby go zainicjować. W tej funkcji, a nie w Konstruktorze polecenia nowy plik do skuteczne w SDI — aplikacje, należy umieścić kodu inicjowania.  
  
 Należy pamiętać, że istnieją przypadków, gdy `OnNewDocument` jest wywoływana dwukrotnie. Dzieje się tak, jeśli dokument jest osadzony jako serwer dokumentów ActiveX. Funkcja najpierw jest wywoływana przez `CreateInstance` — metoda (udostępnianych przez `COleObjectFactory`-klasy) i drugi raz przez `InitNew` — metoda (udostępnianych przez `COleServerDoc`-pochodnej klasy).  
  
### <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają alternatywne metody inicjowania obiektu dokumentu.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
##  <a name="onopendocument"></a>CDocument::OnOpenDocument  
 Wywoływane przez platformę jako część polecenia Otwórz plik.  
  
```  
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Wskazuje ścieżkę dokumentu, aby go otworzyć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument został pomyślnie załadowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji otwiera określony plik, wywołania [DeleteContents](#deletecontents) wywołania funkcji członkowskiej, aby upewnić się, że dokument jest pusty, [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) do odczytu tego pliku zawartość, a następnie oznacza dokumentu jako czystych. Należy przesłonić tę funkcję, jeśli chcesz użyć czegoś innego niż mechanizmu archiwum lub mechanizm pliku. Na przykład może napisać aplikację, której dokumenty reprezentują rekordy w bazie danych, a nie oddzielnych plików.  
  
 Jeśli użytkownik wybierze polecenie Otwórz plik w aplikacji SDI, platforma korzysta z tej funkcji może ponownie zainicjować istniejące **CDocument** obiektu zamiast tworzenia nowej. Jeśli użytkownik wybierze Otwórz plik w aplikacji MDI, platformę tworzy nową **CDocument** obiektu każdorazowo, a następnie wywołuje tę funkcję, aby go zainicjować. W tej funkcji, a nie w Konstruktorze polecenia Otwórz plik zadziałało w SDI — aplikacje, należy umieścić kodu inicjowania.  
  
### <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają alternatywne metody inicjowania obiektu dokumentu.  
  
 [!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]  
  
##  <a name="onpreviewhandlerqueryfocus"></a>CDocument::OnPreviewHandlerQueryFocus  
 Określa, że Obsługa podglądu do zwrócenia HWND pobierane z wywołaniem `GetFocus` funkcji.  
  
```  
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```  
  
### <a name="parameters"></a>Parametry  
 `phwnd`  
 [out] Gdy metoda zwróci wartość, zawiera wskaźnik do HWND zwracana z wywołania `GetFocus` funkcji z wątku pierwszego planu obsługi podglądu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia; lub wartość błędu w inny sposób.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onpreviewhandlertranslateaccelerator"></a>CDocument::OnPreviewHandlerTranslateAccelerator  
 Określa, że Obsługa podglądu, aby obsłużyć naciśnięcia klawisza przekazywane z przekazywanie komunikatów procesu, w którym jest uruchomiony program obsługi podglądu.  
  
```  
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pmsg`  
 [in] Wskaźnik do komunikatów okien.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli komunikat Naciśnięcie klawisza mogą być przetwarzane przez program obsługi podglądu, program obsługi przetwarza je i zwraca wartość S_OK. Jeśli Obsługa podglądu nie może przetworzyć komunikatu naciśnięcie klawisza, jego oferuje dla hosta za pomocą `IPreviewHandlerFrame::TranslateAccelerator`. Jeśli host przetwarza wiadomości, ta metoda zwraca wartość S_OK. Jeśli host nie przetwarza wiadomości, ta metoda zwraca wartości S_FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onrichpreviewbackcolorchanged"></a>CDocument::OnRichPreviewBackColorChanged  
 Wywoływane, gdy zostanie zmieniony kolor tła podglądu rozbudowanego.  
  
```  
virtual void OnRichPreviewBackColorChanged();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onrichpreviewfontchanged"></a>CDocument::OnRichPreviewFontChanged  
 Wywoływane po zmianie czcionki podglądu rozbudowanego.  
  
```  
virtual void OnRichPreviewFontChanged();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onrichpreviewsitechanged"></a>CDocument::OnRichPreviewSiteChanged  
 Wywoływane, gdy lokacja podglądu rozbudowanego została zmieniona.  
  
```  
virtual void OnRichPreviewSiteChanged();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onrichpreviewtextcolorchanged"></a>CDocument::OnRichPreviewTextColorChanged  
 Wywoływana, gdy zmieniono kolor tekstu sformatowanego w wersji zapoznawczej.  
  
```  
virtual void OnRichPreviewTextColorChanged();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onsavedocument"></a>CDocument::OnSaveDocument  
 Wywoływane przez platformę jako część polecenia Zapisz plik i Zapisz plik jako.  
  
```  
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Wskazuje pełną ścieżkę, do której ma zostać zapisany plik.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument został pomyślnie zapisany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji otwiera określony plik, wywołania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) można zapisać danych dokumentu do pliku, a następnie znaczniki dokumentu czyszczenia. Należy przesłonić tę funkcję, jeśli chcesz wykonać specjalnego przetwarzania, gdy w ramach zapisuje dokument. Na przykład może napisać aplikację, której dokumenty reprezentują rekordy w bazie danych, a nie oddzielnych plików.  
  
##  <a name="onunloadhandler"></a>CDocument::OnUnloadHandler  
 Wywoływane przez platformę, gdy Obsługa podglądu zostanie zwolniona.  
  
```  
virtual void OnUnloadHandler();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onupdatefilesendmail"></a>CDocument::OnUpdateFileSendMail  
 Umożliwia **ID_FILE_SEND_MAIL** polecenia, jeśli występuje obsługi poczty (MAPI).  
  
```  
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Wskaźnik do [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt skojarzony z **ID_FILE_SEND_MAIL** polecenia.  
  
### <a name="remarks"></a>Uwagi  
 W przeciwnym razie funkcja usuwa **ID_FILE_SEND_MAIL** polecenia, z menu, łącznie z separatorami powyżej lub poniżej odpowiednio elementu menu. MAPI jest włączone, jeśli MAPI32. DLL znajduje się w ścieżce i w sekcji [poczty] systemu Windows. Plik INI, MAPI = 1. Większość aplikacji umieść tego polecenia w menu Plik.  
  
 **Cdocument —** obsługuje wysyłanie dokumentu pocztą, jeśli występuje obsługi poczty (MAPI). Zobacz artykuły [tematy MAPI](../../mfc/mapi.md) i [Obsługa MAPI w MFC](../../mfc/mapi-support-in-mfc.md).  
  
##  <a name="precloseframe"></a>CDocument::PreCloseFrame  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę przed okno ramowe zostanie zniszczony.  
  
```  
virtual void PreCloseFrame(CFrameWnd* pFrame);
```  
  
### <a name="parameters"></a>Parametry  
 `pFrame`  
 Wskaźnik do [cframewnd —](../../mfc/reference/cframewnd-class.md) przechowuje skojarzone **CDocument** obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Może być zastąpiona Podaj oczyszczania niestandardowe, ale pamiętaj wywołać klasy podstawowej.  
  
 Domyślne ustawienie `PreCloseFrame` nie działają **CDocument**. **CDocument**-klas pochodnych [COleDocument](../../mfc/reference/coledocument-class.md) i [cricheditdoc —](../../mfc/reference/cricheditdoc-class.md) funkcja elementu członkowskiego.  
  
##  <a name="readnextchunkvalue"></a>CDocument::ReadNextChunkValue  
 Odczytuje wartość następnego fragmentu.  
  
```  
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```  
  
### <a name="parameters"></a>Parametry  
 `ppValue`  
 [out] Po powrocie z funkcji `ppValue` zawiera wartość, która została odczytana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="releasefile"></a>CDocument::ReleaseFile  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by wersji plików, udostępniając ją do użytku przez inne aplikacje.  
  
```  
virtual void ReleaseFile(
    CFile* pFile,  
    BOOL bAbort);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Wskaźnik do obiektu cfile — do zwolnienia.  
  
 `bAbort`  
 Określa, czy plik można zwolnić za pomocą `CFile::Close` lub `CFile::Abort`. **FALSE** Jeśli plik znajduje się zostać zwolniony za pomocą [CFile::Close](../../mfc/reference/cfile-class.md#close); **TRUE** Jeśli plik znajduje się zostać zwolniony za pomocą [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bAbort` jest **TRUE**, `ReleaseFile` wywołania `CFile::Abort`, a plik zostanie zwolniony. `CFile::Abort`nie spowoduje zgłoszenie wyjątku.  
  
 Jeśli `bAbort` jest **FALSE**, `ReleaseFile` wywołania `CFile::Close` i plik zostanie zwolniony.  
  
 Przesłonić tę funkcję elementu członkowskiego, aby wymagać akcji przez użytkownika, zanim plik zostanie zwolniony.  
  
##  <a name="removechunk"></a>CDocument::RemoveChunk  
 Usuwa fragmentu o określonym identyfikatorze GUID.  
  
```  
virtual void RemoveChunk(
    REFCLSID guid,  
    DWORD pid);
```  
  
### <a name="parameters"></a>Parametry  
 `Guid`  
 Określa identyfikator GUID fragmentu, który ma zostać usunięty.  
  
 `Pid`  
 Określa identyfikator PID fragmentu, który ma zostać usunięty.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removeview"></a>CDocument::RemoveView  
 Wywołanie tej funkcji można odłączyć widoku z dokumentu.  
  
```  
void RemoveView(CView* pView);
```  
  
### <a name="parameters"></a>Parametry  
 `pView`  
 Wskazuje widoku zostaną usunięte.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja usuwa określony widok z listy widoków skojarzonych z dokumentu. również ustawia wskaźnik dokumentu widoku **NULL**. Ta funkcja jest wywoływana przez platformę, gdy okno ramowe został zamknięty lub okienku okna podziału jest zamknięty.  
  
 Wywołanie tej funkcji tylko wtedy, gdy są ręcznie odłączanie widoku. Zazwyczaj umożliwi ramach, odłączyć dokumentów i widoków, definiując [cdoctemplate —](../../mfc/reference/cdoctemplate-class.md) powiązania klasy dokumentu, klasa widoku i ramki okna klasy obiektu.  
  
 Zapoznaj się z przykładem w [AddView](#addview) dla implementacji próbki.  
  
##  <a name="reportsaveloadexception"></a>CDocument::ReportSaveLoadException  
 Wywołuje się, jeśli wyjątek (zazwyczaj [CFileException](../../mfc/reference/cfileexception-class.md) lub [CArchiveException](../../mfc/reference/carchiveexception-class.md)) podczas zapisywania lub wczytywania dokumentu.  
  
```  
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,  
    CException* e,  
    BOOL bSaving,  
    UINT nIDPDefault);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Wskazuje nazwę dokumentu, która była zapisana lub załadować.  
  
 *e*  
 Wskazuje wyjątek, który został zgłoszony. Może być **NULL**.  
  
 *bSaving*  
 Flaga oznaczająca, jakie operacja jest w toku; różna od zera, jeśli dokument był zapisywane, 0 Jeśli załadowano dokumentu.  
  
 `nIDPDefault`  
 Identyfikator komunikatu o błędzie będzie wyświetlana, jeśli funkcja nie określa bardziej szczegółowe jeden.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja sprawdza obiekt wyjątku i wyszukuje komunikat o błędzie opisujący przyczynę. Jeśli nie można odnaleźć określonego komunikatu lub *e* jest **NULL**, określony przez komunikat ogólne `nIDPDefault` parametr jest używany. Funkcja następnie wyświetla komunikat zawierający komunikat o błędzie. Należy przesłonić tę funkcję, jeśli chcesz podać komunikaty o błędach dodatkowe, niestandardowych. Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="savemodified"></a>CDocument::SaveModified  
 Wywoływane przez platformę przed zmodyfikowanego dokumentu zostanie zamknięty.  
  
```  
virtual BOOL SaveModified();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest bezpieczne kontynuować i zamknąć dokument; 0, jeśli dokument nie powinno zostać zamknięte.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja tej funkcji wyświetla komunikat z prośbą czy zapisać zmiany w dokumencie, jeśli dowolne wprowadzono. Jeśli program wymaga innej procedury sygnalizowania, należy przesłonić tę funkcję. Jest to zaawansowane możliwym do zastąpienia.  
  
##  <a name="setchunkvalue"></a>CDocument::SetChunkValue  
 Ustawia wartość fragmentu.  
  
```  
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parametry  
 `pValue`  
 Określa wartość fragmentu, aby ustawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setmodifiedflag"></a>CDocument::SetModifiedFlag  
 Wywołanie tej funkcji po wybraniu wszelkie modyfikacje dokumentu.  
  
```  
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Flaga wskazująca, czy dokument został zmodyfikowany.  
  
### <a name="remarks"></a>Uwagi  
 Stale wywołanie tej funkcji, sprawdź, platformę monit o zapisanie zmian przed zamknięciem dokumentu. Zwykle należy użyć wartości domyślnej z **TRUE** dla `bModified` parametru. Aby oznaczyć dokumentu czyszczenie (bez modyfikacji), wywołanie tej funkcji przy użyciu wartości **FALSE**.  
  
##  <a name="setpathname"></a>CDocument::SetPathName  
 Wywołanie tej funkcji, aby określić pełną ścieżkę pliku dyskowego dokumentu.  
  
```  
virtual void SetPathName(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPathName`  
 Wskazuje ciąg do użycia jako ścieżkę dokumentu.  
  
 `bAddToMRU`  
 Określa, czy nazwa pliku zostanie dodany do listy ostatnio używanych (MRU) pliku. Jeśli **ma wartość TRUE,** nazwa pliku jest dodawana; Jeśli **FALSE**, nie został dodany.  
  
### <a name="remarks"></a>Uwagi  
 W zależności od wartości `bAddToMRU` ścieżka jest dodany lub nie dodany do listy ostatnio używanych przez aplikację. Należy pamiętać, że niektóre dokumenty nie są skojarzone z plikiem dyskowym. Wywołanie tej funkcji tylko wtedy, gdy są zastępowanie otwieranie i zapisywanie plików używanych przez platformę w implementacji domyślnej.  
  
##  <a name="settitle"></a>CDocument::SetTitle  
 Wywołanie tej funkcji, aby określić tytuł dokumentu (ciąg wyświetlany w pasku tytułu okna ramki).  
  
```  
virtual void SetTitle(LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 Wskazuje ciąg, który ma być używany jako tytuł dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji aktualizacji tytuły wszystkich ramka okna wyświetlające dokument.  
  
##  <a name="updateallviews"></a>CDocument::UpdateAllViews  
 Wywołanie tej funkcji po zmodyfikowaniu dokumentu.  
  
```  
void UpdateAllViews(
    CView* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pSender`  
 Wskazuje widok, który zmodyfikował dokument, lub **NULL** w przypadku wszystkich widoków aktualizacji.  
  
 `lHint`  
 Zawiera informacje dotyczące zmiany.  
  
 `pHint`  
 Punkty do przechowywania informacji na temat modyfikacji obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji należy wywołać po wywołaniu metody [SetModifiedFlag](#setmodifiedflag) funkcję elementu członkowskiego. Ta funkcja informuje każdego widoku dołączony do dokumentu, z wyjątkiem widoku określonego za `pSender`, że dokument został zmodyfikowany. Możesz wywoływać zwykle z widoku klasy tej funkcji po zmianie dokumentu za pośrednictwem widoku użytkownik.  
  
 Ta funkcja wymaga [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) funkcji członkowskiej dla każdego z wyjątkiem dokumentu wysyłanie wyświetlić przekazywanie `pHint` i `lHint`. Użyj tych parametrów do przekazywania informacji do widoków dotyczących zmian wprowadzonych do dokumentu. Może zakodować informacje przy użyciu `lHint` i/lub można zdefiniować [CObject](../../mfc/reference/cobject-class.md)-klasy do przechowywania informacji na temat zmian i przekazać tej klasy przy użyciu obiektu `pHint`. Zastąpienie `CView::OnUpdate` funkcji Członkowskich w Twojej [CView](../../mfc/reference/cview-class.md)-klasy w celu zoptymalizowania aktualizowanie widoku są wyświetlane na podstawie informacji przekazany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Przykładowe MFC SNAPVW](../../visual-cpp-samples.md)   
 [Przykładowe MFC NPP](../../visual-cpp-samples.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
