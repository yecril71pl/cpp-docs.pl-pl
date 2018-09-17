---
title: Klasa CDocTemplate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbdb880c7165f314c004a7cbcad44dd3b76fd36
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709842"
---
# <a name="cdoctemplate-class"></a>Cdoctemplate — klasa
Abstrakcyjna klasa podstawowa definiująca podstawowe funkcje dla szablonów dokumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDocTemplate : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocTemplate::CDocTemplate](#cdoctemplate)|Konstruuje `CDocTemplate` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocTemplate::AddDocument](#adddocument)|Dodanie dokumentu do szablonu.|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zamyka wszystkie dokumenty skojarzone z tym szablonem.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Tworzy nowy dokument.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Tworzy nowe okno ramowe zawierające dokument i widok.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Tworzy okno z obsługą OLE ramki.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Tworzy ramkę podrzędne używane podglądu sformatowanego.|  
|[CDocTemplate::GetDocString](#getdocstring)|Pobiera ciąg, który został skojarzony z typem dokumentu.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Pobiera położenie pierwszego dokumentu, które są skojarzone z tym szablonem.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Pobiera dokument i położenie kolejny.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicjuje okno ramowe i opcjonalnie sprawia, że widoczne.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Ładuje zasoby dla danego `CDocTemplate` lub klasy pochodnej.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Określa stopień zaufania pasuje do typu dokumentu oraz tego szablonu.|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Zostanie otwarty w pliku określonym przez nazwę ścieżki.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Usunięcie dokumentu z szablonu.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Zapisuje wszystkie skojarzone z tym szablonem dokumenty, które zostały zmodyfikowane.|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Określa zasoby dla kontenerów OLE, podczas edycji elementu OLE w miejscu.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Wyświetla tytuł domyślny na pasku tytułu okna dokumentu.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Konfiguracje poza procesem w wersji zapoznawczej programu obsługi.|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|Określa zasobów i klas, gdy dokument serwera jest osadzony lub edytowany w miejscu.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj Utwórz co najmniej jeden szablon dokumentu w implementacji aplikacji `InitInstance` funkcji. Szablon dokumentu zdefiniuje relacje między trzy typy klas:  
  
-   Klasy dokumentów, które pochodzą z `CDocument`.  
  
-   Klasy widoku, która wyświetla dane z klasy dokumentu wymienionych powyżej. Utworzeniu klasy pochodnej tej klasy z `CView`, `CScrollView`, `CFormView`, lub `CEditView`. (Możesz również użyć `CEditView` bezpośrednio.)  
  
-   Klasy okna ramki, który zawiera widok. W przypadku aplikacji interfejsu (SDI) pojedynczego dokumentu utworzeniu klasy pochodnej tej klasy z `CFrameWnd`. Dla wielu dokumentów (MDI) aplikację z interfejsem, utworzeniu klasy pochodnej tej klasy z `CMDIChildWnd`. Jeśli nie potrzebujesz dostosować zachowanie ramki okna, możesz użyć `CFrameWnd` lub `CMDIChildWnd` bezpośrednio, bez wyprowadzanie własne klasy.  
  
 Twoja aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który ją obsługuje. Na przykład jeśli aplikacja obsługuje arkuszy kalkulacyjnych i dokumenty tekstowe, aplikacja ma dwa obiekty szablonu dokumentu. Każdy szablon dokumentu jest odpowiedzialny za tworzenie i zarządzanie nimi wszystkie dokumenty dla jego typu.  
  
 Szablon dokumentu, który przechowuje wskaźniki do `CRuntimeClass` obiektów do dokumentu, widok i klasy okien ramowych. Te `CRuntimeClass` obiekty są określane podczas tworzenia szablonu dokumentu.  
  
 Szablon dokumentu, który zawiera identyfikator zasoby używane za pomocą typu dokumentu (takich jak menu, ikona lub zasobów tabeli akceleratora). Szablon dokumentu, który ma także ciągów zawierających dodatkowe informacje na temat jego typ dokumentu. Obejmują one nazwę typu dokumentu (na przykład "arkusza") i rozszerzenie pliku (na przykład "xls"). Opcjonalnie może zawierać innych ciągów używane przez interfejs użytkownika, Menedżera plików Windows i łączenia obiektów i obsługa osadzania (OLE).  
  
 Jeśli aplikacja jest kontener OLE i/lub serwerem, szablon dokumentu, który definiuje również identyfikator menu używane podczas aktywacji w miejscu. Jeśli aplikacja serwera OLE, szablon dokumentu, który definiuje identyfikator paska narzędzi i menu używane podczas aktywacji w miejscu. Określ dodatkowe zasoby OLE, wywołując `SetContainerInfo` i `SetServerInfo`.  
  
 Ponieważ `CDocTemplate` jest klasą abstrakcyjną nie można użyć klasy bezpośrednio. Typowa aplikacja korzysta z jednego z dwóch `CDocTemplate`-pochodnych klas dostarczonych przez bibliotekę Microsoft Foundation Class: `CSingleDocTemplate`, który implementuje SDI, i `CMultiDocTemplate`, który implementuje MDI. Zobacz tych klas, aby uzyskać więcej informacji na temat korzystania z szablonów dokumentów.  
  
 Jeśli aplikacja wymaga paradygmatu interfejsu użytkownika, który różni się zasadniczo od SDI lub MDI, utworzeniu klasy pochodnej klasy z `CDocTemplate`.  
  
 Aby uzyskać więcej informacji na temat `CDocTemplate`, zobacz [szablonów dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 Aby dodać dokument do szablonu, należy użyć tej funkcji.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskaźnik do dokumentu, który ma zostać dodana.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) i [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) przesłonić tę funkcję. Jeśli uzyskujesz własne klasy szablonów dokumentów z `CDocTemplate`, klasy pochodne muszą przesłaniać tę funkcję.  
  
##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate  
 Konstruuje `CDocTemplate` obiektu.  
  
```  
CDocTemplate (
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDResource*  
 Określa identyfikator zasoby używane za pomocą typu dokumentu. Może to obejmować menu, ikony, tabeli akceleratora i zasoby w postaci ciągów.  
  
 Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak '\n' jest wymagane jako symbolu zastępczego, jeśli podciąg nie jest uwzględniony jednak nie są konieczne znaki końcowe '\n'); te podciągów opisują typ dokumentu. Aby uzyskać informacji na temat podciągów, zobacz [GetDocString](#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Należy zauważyć, że ciąg rozpoczyna się od znaku '\n'; jest to spowodowane pierwszego podciągu nie jest używana dla aplikacji MDI, a zatem nie jest dołączony. Możesz edytować ten ciąg przy użyciu edytora ciągów; cały ciąg pojawi się jako pojedynczy wpis w edytorze ciągu nie jako siedmiu osobnych wpisów.  
  
 *pDocClass*  
 Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest `CDocument`— zdefiniuj do reprezentowania dokumentów klasy pochodnej.  
  
 *pFrameClass*  
 Wskazuje `CRuntimeClass` obiektu klasę okna ramowego. Ta klasa może być `CFrameWnd`-klasy pochodnej lub może być `CFrameWnd` sam chcącym domyślne zachowanie dla okna głównej ramki.  
  
 *pViewClass*  
 Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`— należy zdefiniować, aby wyświetlić swoje dokumenty klasy pochodnej.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji elementu członkowskiego do konstruowania `CDocTemplate` obiektu. Dynamiczne przydzielanie `CDocTemplate` obiektu i przekazać ją do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z `InitInstance` funkcji składowej klasy aplikacji.  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 Wywołaj tę funkcję elementu członkowskiego, aby zamknąć wszystkie otwarte dokumenty.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parametry  
 *bEndSession*  
 Nie używany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest zwykle używana jako część polecenia Wyjdź z pliku. Domyślna implementacja ta funkcja wywołuje [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) funkcja elementu członkowskiego do usuwania dokumentu danych, a następnie zamyka okien ramowych wszystkich widoków dołączony do dokumentu.  
  
 Należy przesłonić tę funkcję, jeśli chcesz wymagać od użytkowników do wykonywania specjalnej operacji czyszczenia przetwarzania przed zamknięciem dokumentu. Na przykład jeśli dokument reprezentuje rekord w bazie danych, możesz zastąpić tę funkcję, aby zamknąć bazy danych.  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nowy dokument typ skojarzony z tym szablonem dokumentu.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego dokumentu, lub wartość NULL, jeśli wystąpi błąd.  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 Tworzy nowe okno ramowe zawierające dokument i widok.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Dokument, do którego należy odwoływać się nowe okno ramek. Może mieć wartości NULL.  
  
 *pOther*  
 Okno ramowe, na którym ma być oparte nowe okno ramek. Może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego ramki okna, lub wartość NULL, jeśli wystąpi błąd.  
  
### <a name="remarks"></a>Uwagi  
 `CreateNewFrame` używa `CRuntimeClass` obiekty przekazywane do konstruktora, aby utworzyć nowe okno ramek widok i dołączony dokument. Jeśli *pDoc* parametr ma wartość NULL, w ramach generuje komunikat śledzenia.  
  
 *POther* parametr jest używany do wdrożenia nowego okna polecenia. Udostępnia okno ramek, na którym ma zostać modelu nowe okno ramek. Nowe okno ramek jest zazwyczaj tworzony niewidoczne. Wywołaj tę funkcję, aby utworzyć okien ramowych poza implementacji standardowego środowiska nowy plik i Otwórz plik.  
  
##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame  
 Tworzy okno ramowe OLE.  
  
```  
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc,  
    BOOL bCreateView);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do ramki okna nadrzędnego.  
  
 *pDoc*  
 Wskaźnik do dokumentu, do której należy odwoływać się nowe okno ramek OLE.  
  
 *bCreateView*  
 Określa, czy widok jest tworzony wraz z ramki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ramki okna, jeśli to się powiedzie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bCreateView* wynosi zero, jest tworzony pustą ramkę.  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 Pobiera ciąg, który został skojarzony z typem dokumentu.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 Odwołanie do `CString` obiektu, który będzie zawierać ciąg, gdy funkcja zwraca.  
  
 *index*  
 Indeks podciąg pobieranych z ciągu, który opisuje typ dokumentu. Ten parametr może mieć jedną z następujących wartości:  
  
- `CDocTemplate::windowTitle` Nazwa wyświetlana na pasku (na przykład "Microsoft Excel") przy użyciu tytułu okna aplikacji. Istnieje tylko w szablonie dokumentu dla aplikacji interfejsu SDI.  
  
- `CDocTemplate::docName` Główny domyślnej nazwy dokumentu (na przykład "Arkusza"). Ten katalog główny, a także numer jest używany do domyślną nazwę nowego dokumentu tego typu zawsze wtedy, gdy użytkownik wybierze polecenie Nowy w menu Plik (np. "Arkusz1" lub "Sheet2 —"). Jeśli nie zostanie określony, "Bez tytułu" jest używany jako domyślny.  
  
- `CDocTemplate::fileNewName` Nazwa tego typu dokumentu. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, ten ciąg jest wyświetlany w oknie dialogowym Nowy plik (na przykład "arkusza"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia nowy plik.  
  
- `CDocTemplate::filterName` Opis typu dokumentu i filtr z symbolami wieloznacznymi pasujących dokumentów tego typu. Ten ciąg jest wyświetlany na liście rozwijanej pliki typu listy w oknie dialogowym Otwieranie pliku (na przykład "arkusze (*.xls)"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia Otwórz plik.  
  
- `CDocTemplate::filterExt` Rozszerzenie dla dokumentów tego typu (na przykład "xls"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia Otwórz plik.  
  
- `CDocTemplate::regFileTypeId` Identyfikator typu dokumentu, które mają być przechowywane w bazie danych rejestracji obsługiwane przez Windows. Ten ciąg jest tylko do użytku wewnętrznego (na przykład "ExcelWorksheet"). Jeśli nie zostanie określony, typ dokumentu nie można zarejestrować za pomocą Menedżera plików Windows.  
  
- `CDocTemplate::regFileTypeName` Nazwa typu dokumentu, które mają być przechowywane w bazie danych rejestracji. Ten ciąg może być wyświetlana w oknach dialogowych aplikacji uzyskujących dostęp do bazy danych rejestracji (na przykład "arkusz programu Microsoft Excel").  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli określony podciąg został znaleziony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję można pobrać określonego podciąg, opisujący typ dokumentu. Ciąg zawierający te podciągi są przechowywane w szablonie dokumentu i jest tworzony na podstawie ciągu w pliku zasobów dla aplikacji. Struktura wywołuje tę funkcję, aby pobrać ciągów, których potrzebuje interfejsu użytkownika. Jeśli zostały określone z rozszerzeniem nazwy pliku dla dokumentów aplikacji, platformę również wywołuje tę funkcję, dodając wpis w bazie danych rejestracji Windows; Dzięki temu dokumenty, które ma zostać otwarty z Menedżera plików Windows.  
  
 Wywołaj tę funkcję tylko wtedy, gdy są wyprowadzanie klasy z `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 Pobiera położenie pierwszego dokumentu, które są skojarzone z tym szablonem.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość pozycji, który może służyć do iteracji przez listę dokumentów skojarzone z tym szablonem dokumentu; lub wartość NULL, jeśli lista jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby uzyskać położenie pierwszego dokumentu na liście dokumentów skojarzonych z tym szablonem. Użyj wartości pozycji jako argument do [CDocTemplate::GetNextDoc](#getnextdoc) do iteracji przez listę dokumentów skojarzone z szablonem.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) i [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) zarówno zastąpienie tego czystą funkcję wirtualną. Każda klasa pochodzi od `CDocTemplate` również musisz przesłonić tę funkcję.  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 Pobiera element listy identyfikowane przez *RPO*, następnie ustawia *RPO* wartość pozycji następnego wpisu na liście.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego dokumentu na liście dokumentów skojarzonych z tym szablonem.  
  
### <a name="parameters"></a>Parametry  
 *wartościom celu punktu odzyskiwania*  
 Odwołanie do wartości pozycji, zwrócony przez poprzednie wywołanie [GetFirstDocPosition](#getfirstdocposition) lub `GetNextDoc`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element pobrane ostatnio na liście jest następnie nowa wartość *RPO* ma wartość NULL.  
  
 Możesz użyć `GetNextDoc` w pętli do przodu iteracji, jeśli ustanowisz początkowe położenie w wyniku wywołania [GetFirstDocPosition](#getfirstdocposition).  
  
 Należy się upewnić, że wartość pozycji reprezentuje poprawnej pozycji na liście. Jeśli jest nieprawidłowy, deklaracji rozkazujących wersję debugowania biblioteki klas Microsoft Foundation.  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 Inicjuje okno ramowe i opcjonalnie sprawia, że widoczne.  
  
```  
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,  
    CDocument* pDoc,  
    BOOL bMakeVisible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pFrame*  
 Okno ramowe wymaga aktualizacji początkowej.  
  
 *pDoc*  
 Dokument, z którym jest skojarzony ramki. Może mieć wartości NULL.  
  
 *bMakeVisible*  
 Wskazuje, czy ramki powinien stają się widoczne i aktywne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj `IntitialUpdateFrame` po utworzeniu nowej ramki za pomocą `CreateNewFrame`. Wywołanie tej funkcji powoduje, że widoki w tym oknie ramki, aby otrzymać ich `OnInitialUpdate` wywołania. Ponadto jeśli istnieje nie był wcześniej aktywnego widoku, widok głównej ramki okna zostanie aktywowane; podstawowy widok jest widokiem, za pomocą elementu podrzędnego ID AFX_IDW_PANE_FIRST. Na koniec okno ramowe stają się widoczne dla Jeśli *bMakeVisible* jest różna od zera. Jeśli *bMakeVisible* wynosi zero, bieżący fokus i widoczności ramki okna pozostanie niezmieniona.  
  
 Nie jest to konieczne wywołać tę funkcję, korzystając z ramowych implementacji nowy plik i Otwórz plik.  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 Ładuje zasoby dla danego `CDocTemplate` lub klasy pochodnej.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez platformę, by załadować zasobów dla danego `CDocTemplate` lub klasy pochodnej. Zwykle jest nazywane podczas konstruowania, z wyjątkiem sytuacji, gdy szablon jest budowany globalnie. W takim przypadku wywołanie `LoadTemplate` jest opóźnione aż do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) jest wywoływana.  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 Określa stopień zaufania pasuje do typu dokumentu oraz tego szablonu.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPathName*  
 Nazwa ścieżki pliku, którego typ jest ustalany.  
  
 *rpDocMatch*  
 Wskaźnik do dokumentu, który jest przypisany pasującego dokumentu, jeżeli plik określony przez *lpszPathName* jest już otwarty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od **ufności** wyliczenia, która jest zdefiniowana w następujący sposób:  
  
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
 Aby określić typ używany do otwierania pliku szablon dokumentu, należy użyć tej funkcji. Jeśli aplikacja obsługuje wiele typów plików, na przykład umożliwia tej funkcji ustalić, które szablonów dokumentów dostępnych jest odpowiednia dla danego pliku, wywołując `MatchDocType` dla każdego szablonu Wyłącz, a następnie wybierając szablon na podstawie położenia zwracana wartość zaufania.  
  
 Jeśli plik określony przez *lpszPathName* jest jeszcze otwarty, funkcja zwraca `CDocTemplate::yesAlreadyOpen` i kopiuje plik `CDocument` obiektu do obiektu w *rpDocMatch*.  
  
 Jeśli plik nie jest otwarty, ale rozszerzenie w *lpszPathName* pasuje do rozszerzenia określone przez `CDocTemplate::filterExt`, ta funkcja zwraca `CDocTemplate::yesAttemptNative` i ustawia *rpDocMatch* na wartość NULL. Aby uzyskać więcej informacji na temat `CDocTemplate::filterExt`, zobacz [CDocTemplate::GetDocString](#getdocstring).  
  
 Jeśli żaden przypadek ma wartość PRAWDA, funkcja zwraca `CDocTemplate::yesAttemptForeign`.  
  
 Domyślna implementacja zwraca `CDocTemplate::maybeAttemptForeign` lub `CDocTemplate::maybeAttemptNative`. Przesłonić tę funkcję, aby zaimplementować logikę dopasowanie typu odpowiednie dla aplikacji, być może za pomocą tych dwóch wartości z **ufności** wyliczenia.  
  
##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile  
 Otwiera plik określony przez ścieżkę.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
*lpszPathName*<br/>
[in] Wskaźnik do ścieżki pliku który zawiera dokument, który ma zostać otwarty.  
  
*bAddToMRU*<br/>
[in] Wartość TRUE wskazuje, że dokument jest jeden z najnowszych plików; Wartość FALSE wskazuje, że dokument nie jest jednym z najbardziej aktualne pliki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, w których plik jest nazwany przez *lpszPathName*; Wartość NULL, jeśli nie powiedzie.  
  
### <a name="remarks"></a>Uwagi  
 Otwiera plik, w których ścieżka jest określana przez *lpszPathName*. Jeśli *lpszPathName* ma wartość NULL, jest tworzony nowy plik, który zawiera dokument typu skojarzonego z tym szablonem.  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 Usuwa dokumentu wskazywany przez *pDoc* z listy dokumentów skojarzonych z tym szablonem.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskaźnik do dokumentu, który ma zostać usunięty.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne `CMultiDocTemplate` i `CSingleDocTemplate` przesłonić tę funkcję. Jeśli uzyskujesz własne klasy szablonów dokumentów z `CDocTemplate`, klasy pochodne muszą przesłaniać tę funkcję.  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 Zapisuje wszystkie dokumenty, które zostały zmodyfikowane.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Niezerowa Koniunkcja w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo  
 Określa zasoby dla kontenerów OLE, podczas edycji elementu OLE w miejscu.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDOleInPlaceContainer*  
 Identyfikator zasoby używane, gdy obiekt osadzony jest aktywny.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby ustawić zasoby, które ma być używany, gdy obiekt OLE jest aktywowany w miejscu. Te zasoby mogą obejmować menu i tabel akceleratora. Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkcji aplikacji.  
  
 Menu skojarzone z *nIDOleInPlaceContainer* zawiera separatory, które umożliwiają menu aktywowanego elementu w miejscu do scalenia z menu aplikacji kontenera. Aby uzyskać więcej informacji dotyczących scalania menu serwer i kontener, zobacz artykuł [menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 Wywołaj tę funkcję, aby załadować dokument domyślny tytuł i wyświetl ją na pasku tytułu dokumentu.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocument*  
 Wskaźnik do dokumentu, których tytuł jest do ustawienia.  
  
### <a name="remarks"></a>Uwagi  
 Instrukcje dotyczące tytuł domyślny, zobacz opis `CDocTemplate::docName` w [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo  
 Określa zasobów i klas, gdy dokument serwera jest osadzony lub edytowany w miejscu.  
  
```  
void SetServerInfo(
    UINT nIDOleEmbedding,  
    UINT nIDOleInPlaceServer = 0,  
    CRuntimeClass* pOleFrameClass = NULL,  
    CRuntimeClass* pOleViewClass = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDOleEmbedding*  
 Identyfikator zasoby używane podczas osadzonego obiektu jest otwarty w osobnym oknie.  
  
 *nIDOleInPlaceServer*  
 Identyfikator zasobów używana, gdy obiekt osadzony jest aktywowany w miejscu.  
  
 *pOleFrameClass*  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury zawierającej informacje o klasie dla obiektu okna ramki, które są tworzone podczas aktywacji w miejscu występuje.  
  
 *pOleViewClass*  
 Wskaźnik do `CRuntimeClass` struktury zawierającej informacje o klasie dla obiektu widoku tworzone podczas aktywacji w miejscu występuje.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję elementu członkowskiego w celu identyfikacji zasobów, które będą używane przez aplikację serwera, gdy użytkownik zażąda aktywacji osadzonego obiektu. Zasoby te składają się z menu i tabel akceleratora. Ta funkcja jest zazwyczaj wywoływana `InitInstance` aplikacji.  
  
 Menu skojarzone z *nIDOleInPlaceServer* zawiera separatory, zezwalających na menu serwera do scalenia z menu kontenera. Aby uzyskać więcej informacji dotyczących scalania menu serwer i kontener, zobacz artykuł [menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 Tworzy ramkę podrzędne używane podglądu sformatowanego.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do nadrzędnego okna (zazwyczaj zapewnionym przez powłokę).  
  
 *pDoc*  
 Wskaźnik do obiektu dokumentu, którego zawartość zostanie wyświetlona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do `CFrameWnd` obiekt lub wartość NULL, jeśli tworzenie zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 Konfiguruje poza procedury obsługi podglądu procesu.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDPreviewFrame*  
 Określa identyfikator zasobu ramki (wersja zapoznawcza).  
  
 *pPreviewFrameClass*  
 Określa wskaźnik do struktury informacji klasy środowiska uruchomieniowego ramki (wersja zapoznawcza).  
  
 *pPreviewViewClass*  
 Określa wskaźnik do struktury środowiska uruchomieniowego klasy informacji o widoku (wersja zapoznawcza).  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [Klasa CDocument](../../mfc/reference/cdocument-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CScrollView](../../mfc/reference/cscrollview-class.md)   
 [Klasa CEditView](../../mfc/reference/ceditview-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
