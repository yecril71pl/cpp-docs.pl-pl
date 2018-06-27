---
title: Cdoctemplate — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9a1ee27994a83206b576452d30b108f01c794353
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957566"
---
# <a name="cdoctemplate-class"></a>Cdoctemplate — klasa
Abstrakcyjna klasa podstawowa definiujący funkcje podstawowe dla szablonów dokumentów.  
  
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
|[CDocTemplate::AddDocument](#adddocument)|Dodaje dokumentu w szablonie.|  
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|Zamyka wszystkie dokumenty skojarzone z tym szablonem.|  
|[CDocTemplate::CreateNewDocument](#createnewdocument)|Tworzy nowy dokument.|  
|[CDocTemplate::CreateNewFrame](#createnewframe)|Tworzy okno ramowe zawierające widok i dokumentów.|  
|[CDocTemplate::CreateOleFrame](#createoleframe)|Tworzy okno ramowe włączone OLE.|  
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|Tworzy ramkę podrzędnego używany do podglądu rozbudowanego.|  
|[CDocTemplate::GetDocString](#getdocstring)|Pobiera ciąg skojarzone z typem dokumentu.|  
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|Pobiera położenie pierwszego skojarzone z tym szablonem dokumentu.|  
|[CDocTemplate::GetNextDoc](#getnextdoc)|Pobiera dokument i położenie kolejnego.|  
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|Inicjuje okno ramowe i opcjonalnie umożliwia widoczne.|  
|[CDocTemplate::LoadTemplate](#loadtemplate)|Ładuje zasobów dla danego `CDocTemplate` lub klasy.|  
|[CDocTemplate::MatchDocType](#matchdoctype)|Określa stopień zaufania pasuje do typu dokumentu i ten szablon.|  
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|Otwiera plik określony przez nazwę ścieżki.|  
|[CDocTemplate::RemoveDocument](#removedocument)|Usuwa dokumentu z szablonu.|  
|[CDocTemplate::SaveAllModified](#saveallmodified)|Zapisuje wszystkie skojarzone z tym szablonem dokumenty, które zostały zmodyfikowane.|  
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|Określa zasoby dla kontenerów OLE podczas edycji elementu OLE w miejscu.|  
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|Wyświetla domyślny tytuł w pasku tytułu okna dokumentu.|  
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|Konfiguracje poza Obsługa podglądu procesu.|  
|[CDocTemplate::SetServerInfo](#setserverinfo)|Określa klasy i zasobów, gdy dokument serwera jest osadzony lub edycji w miejscu.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj utworzyć co najmniej jeden szablon dokumentu w implementacji aplikacji `InitInstance` funkcji. Szablon dokumentu definiuje relacje trzy typy klas:  
  
-   Klasy dokumentów, który pochodzi od `CDocument`.  
  
-   Klasy widoku, która zawiera dane z klasy dokumentu wymienionych powyżej. Można pochodzi ta klasa z `CView`, `CScrollView`, `CFormView`, lub `CEditView`. (Można również użyć `CEditView` bezpośrednio.)  
  
-   Klasy okna ramki, który zawiera widok. Dla aplikacji sieci pojedynczego dokumentu (SDI) interfejsu pochodzi ta klasa z `CFrameWnd`. Dla wielu aplikacji interfejsu (MDI) dokumentu pochodzi ta klasa z `CMDIChildWnd`. Jeśli nie potrzebujesz dostosować zachowanie okno ramowe, możesz użyć `CFrameWnd` lub `CMDIChildWnd` bezpośrednio, bez wyprowadzanie własne klasy.  
  
 Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który go obsługuje. Na przykład jeśli aplikacja obsługuje arkusze kalkulacyjne i dokumenty tekstowe, aplikacja ma dwa obiekty szablonu dokumentu. Każdego szablonu dokumentu jest odpowiedzialny za tworzenie i zarządzanie nimi wszystkie dokumenty dla jego typu.  
  
 Szablon dokumentu przechowuje wskaźniki do `CRuntimeClass` obiektów dla dokumentu, widok i klasy okien ramowych. Te `CRuntimeClass` obiekty zostały określone podczas tworzenia szablonu dokumentu.  
  
 Szablon dokumentu zawiera identyfikator zasobów użyty z typem dokumentu (np. menu ikonę i zasoby tabeli akceleratora). Szablon dokumentu ma również ciągów, które zawierają dodatkowe informacje o jego typ dokumentu. Obejmują one Nazwa typu dokumentu (na przykład "Arkusz") i rozszerzenie pliku (na przykład "xls"). Opcjonalnie może zawierać inne parametry używane przez interfejs użytkownika aplikacji, Menedżera plików systemu Windows i łączenie i osadzanie (OLE) pomocy technicznej.  
  
 W przypadku kontener OLE i/lub serwera aplikacji szablonu dokumentu definiuje również identyfikator menu używane podczas aktywacji w miejscu. Jeśli aplikacja serwera OLE, szablon dokumentu definiuje identyfikator narzędzi i menu używane podczas aktywacji w miejscu. Określ te dodatkowe zasoby OLE wywołując `SetContainerInfo` i `SetServerInfo`.  
  
 Ponieważ `CDocTemplate` jest klasą abstrakcyjną, nie można użyć klasy bezpośrednio. Typowa aplikacja korzysta z jednego z dwóch `CDocTemplate`-udostępniane przez Microsoft Foundation Class Library klas pochodnych: `CSingleDocTemplate`, który implementuje SDI, i `CMultiDocTemplate`, który implementuje MDI. Zobacz tych klas, aby uzyskać więcej informacji na temat używania szablonów dokumentów.  
  
 Jeśli aplikacja wymaga modelu interfejsu użytkownika, który różni się od SDI lub MDI, mogą dziedziczyć klasy z `CDocTemplate`.  
  
 Aby uzyskać więcej informacji na temat `CDocTemplate`, zobacz [szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocTemplate`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="adddocument"></a>  CDocTemplate::AddDocument  
 Ta funkcja służy do dodawania dokumentu do szablonu.  
  
```  
virtual void AddDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskaźnik do dokumentu, który ma zostać dodana.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) i [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) przesłonić tę funkcję. Jeśli pochodzi własne klasy szablonów dokumentów z `CDocTemplate`, klasy pochodne muszą przesłaniać tej funkcji.  
  
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
 Określa identyfikator zasoby używane do typu dokumentu. Może to obejmować menu, ikona tabeli akceleratora i zasoby ciągów.  
  
 Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak "\n" jest potrzebny jako symbolu zastępczego, jeśli nie dołączono podciągu jednak znakami "\n" nie są konieczne); te podciągów opisu typu dokumentu. Aby uzyskać informacje na podciągów, zobacz [GetDocString](#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Należy pamiętać, że ciąg rozpoczyna się od znaku "\n"; jest to spowodowane pierwszego podciągu nie jest używany przez aplikacje MDI i dlatego nie jest dołączana. Można edytować tego ciągu za pomocą Edytora ciągu; cały ciąg jest wyświetlany jako pojedynczy wpis w edytorze ciągu nie jako siedmiu oddzielne wpisy.  
  
 *pDocClass*  
 Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest `CDocument`-klasy definiowane w celu odzwierciedlenia dokumentów.  
  
 *pFrameClass*  
 Wskazuje `CRuntimeClass` obiekt klasy ramki okna. Ta klasa może być `CFrameWnd`-klasy lub może być `CFrameWnd` sam Jeśli domyślne zachowanie dla użytkownika głównego okna ramowego.  
  
 *pViewClass*  
 Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`-klasy zdefiniuj do wyświetlania dokumentów.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji Członkowskich do skonstruowania `CDocTemplate` obiektu. Dynamiczne przydzielanie `CDocTemplate` obiektu i przekaż go do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) z `InitInstance` funkcji członkowskiej klasy aplikacji.  
  
##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments  
 Wywołanie tej funkcji Członkowskich, aby zamknąć wszystkie otwarte dokumenty.  
  
```  
virtual void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parametry  
 *bEndSession*  
 Nie używany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego zwykle jest używana jako część polecenia Exit pliku. Domyślna implementacja ta funkcja wymaga [CDocument::DeleteContents](../../mfc/reference/cdocument-class.md#deletecontents) funkcji członkowskiej można usunąć dokumentu danych, a następnie zamyka okna ramowe dla wszystkich widoków dołączonym do dokumentu.  
  
 Należy przesłonić tę funkcję, jeśli chcesz wymagać od użytkownika do wykonania oczyszczania specjalnego przetwarzania przed zamknięciem dokumentu. Na przykład jeśli dokument reprezentuje rekord w bazie danych, można przesłonić tę funkcję, aby zamknąć bazy danych.  
  
##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument  
 Wywołanie tej funkcji Członkowskich, aby utworzyć nowy dokument typu skojarzonego z tym szablonem dokumentu.  
  
```  
virtual CDocument* CreateNewDocument();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo utworzonego dokumentu lub **NULL** w przypadku wystąpienia błędu.  
  
##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame  
 Tworzy okno ramowe zawierające widok i dokumentów.  
  
```  
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,  
    CFrameWnd* pOther);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Dokument, do którego należy odwoływać się nowe okno ramowe. Może być **NULL**.  
  
 *pOther*  
 Okno ramowe nowe okno ramowe o podstawie. Może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okno ramowe nowo utworzony lub **NULL** w przypadku wystąpienia błędu.  
  
### <a name="remarks"></a>Uwagi  
 `CreateNewFrame` używa `CRuntimeClass` obiektów przekazany do konstruktora, aby utworzyć nowe okno ramowe widok i dołączony dokument. Jeśli *pDoc* parametr jest **NULL**, ramach danych wyjściowych śledzenia wiadomości.  
  
 *POther* parametr jest używany do wdrożenia nowego okna polecenia. Zapewnia on okno ramowe, na którym się nowe okno ramowe modelu. Nowe okno ramowe jest zazwyczaj tworzony niewidoczne. Wywołanie tej funkcji można utworzyć okna ramowe poza implementacja standardowych ramy nowy plik i Otwórz plik.  
  
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
 Wskaźnik do dokumentu, do którego należy odwoływać się nowe okno ramowe OLE.  
  
 *bCreateView*  
 Określa, czy widok jest tworzony wraz z ramki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do okno ramowe w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bCreateView* wynosi zero, zostanie utworzona pusta ramka.  
  
##  <a name="getdocstring"></a>  CDocTemplate::GetDocString  
 Pobiera ciąg skojarzone z typem dokumentu.  
  
```  
virtual BOOL GetDocString(
    CString& rString,  
    enum DocStringIndex index) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *rString*  
 Odwołanie do `CString` obiekt, który będzie zawierać ciąg, gdy funkcja zwraca wartość.  
  
 *index*  
 Indeks podciąg pobieranych z ciągu, który opisuje typ dokumentu. Ten parametr może mieć jedną z następujących wartości:  
  
- **CDocTemplate::windowTitle** nazwę wyświetlaną w tytule okna aplikacji paska (na przykład "Microsoft Excel"). Przedstawia tylko z szablonu dla SDI — aplikacje.  
  
- **CDocTemplate::docName** główny domyślnej nazwy dokumentu (na przykład "Arkusz"). Ten katalog główny, a także liczbę, służy do domyślną nazwę nowego dokumentu tego typu zawsze, gdy użytkownik wybierze nowego polecenia w menu Plik (na przykład "Sheet1 —" lub "Sheet2 —"). Jeśli nie zostanie określony, "Bez tytułu" jest używany jako domyślny.  
  
- **CDocTemplate::fileNewName** nazwę tego typu dokumentu. Jeśli aplikacja obsługuje więcej niż jednego typu dokumentu, ten ciąg jest wyświetlany w oknie dialogowym Nowy plik (na przykład "Arkusz"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia nowy plik.  
  
- **CDocTemplate::filterName** opis typu dokumentu i Filtr symbolu wieloznacznego pasujących dokumentów tego typu. Ten ciąg jest wyświetlana na liście rozwijanej pliki typu listy w oknie dialogowym Otwieranie pliku (na przykład "arkusze (*.xls)"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia Otwórz plik.  
  
- **CDocTemplate::filterExt** rozszerzenie dla tego typu (na przykład "xls"). Jeśli nie określono typu dokumentu jest niedostępny, za pomocą polecenia Otwórz plik.  
  
- **CDocTemplate::regFileTypeId** identyfikator typu dokumentu, które mają być przechowywane w bazie danych rejestracji obsługiwane przez system Windows. Ten ciąg jest tylko do użytku wewnętrznego (na przykład "ExcelWorksheet"). Jeśli nie zostanie określony, typ dokumentu nie można zarejestrować przy użyciu Menedżera plików systemu Windows.  
  
- **CDocTemplate::regFileTypeName** Nazwa typu dokumentu mają być przechowywane w bazie danych rejestracji. Ten ciąg może być wyświetlana w oknach dialogowych aplikacji, które uzyskują dostęp do bazy danych rejestracji (na przykład "arkusz programu Microsoft Excel").  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wskazany podciąg został znaleziony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji do pobrania określonego podciągu opisujące typ dokumentu. Ciąg zawierający podciągów te są przechowywane z szablonu i pochodzi z parametrów w pliku zasobów dla aplikacji. Struktura wywołuje tę funkcję, aby pobrać ciągi potrzebnych do interfejsu użytkownika. Jeśli zostały określone rozszerzenie nazwy pliku dla dokumentów aplikacji, struktura również wywołuje tej funkcji, dodając wpis do bazy danych rejestracji systemu Windows. Dzięki temu dokumentów, aby otworzyć Menedżera plików z systemu Windows.  
  
 Wywołanie tej funkcji tylko wtedy, gdy są wyprowadzanie klasy z `CDocTemplate`.  
  
##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition  
 Pobiera położenie pierwszego skojarzone z tym szablonem dokumentu.  
  
```  
virtual POSITION GetFirstDocPosition() const = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **pozycji** wartość, która może służyć do iterowania po listy dokumentów skojarzone z tym szablonem dokumentu; lub **NULL** Jeśli lista jest pusta.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby uzyskać położenie pierwszego dokumentu na liście dokumentów skojarzone z tym szablonem. Użyj **pozycji** wartość jako argument [CDocTemplate::GetNextDoc](#getnextdoc) do iterowania po listy dokumentów skojarzony z szablonem.  
  
 [CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md) i [CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md) zarówno zastąpienie tego czystej funkcji wirtualnej. Każda klasa pochodzi od `CDocTemplate` musi także zastępować tej funkcji.  
  
##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc  
 Pobiera element listy identyfikowane przez *RPO*, następnie ustawia *RPO* do **pozycji** wartość następnego wpisu na liście.  
  
```  
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego dokumentu na liście dokumentów skojarzone z tym szablonem.  
  
### <a name="parameters"></a>Parametry  
 *RPO*  
 Odwołanie do **pozycji** wartość zwrócona przez poprzednie wywołanie [GetFirstDocPosition](#getfirstdocposition) lub `GetNextDoc`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli element pobrane przez ostatnie na liście jest następnie nowa wartość *RPO* ustawiono **NULL**.  
  
 Można użyć `GetNextDoc` w pętli do przodu iteracji, jeśli ustanowić położenie początkowe w wyniku wywołania [GetFirstDocPosition](#getfirstdocposition).  
  
 Upewnij się, że Twoje **pozycji** wartość reprezentuje prawidłową pozycją na liście. Jeśli jest nieprawidłowa wersja do debugowania programu Microsoft Foundation Class Library potwierdzeń.  
  
##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame  
 Inicjuje okno ramowe i opcjonalnie umożliwia widoczne.  
  
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
 Dokument, z którą jest skojarzone ramki. Może być **NULL**.  
  
 *bMakeVisible*  
 Wskazuje, czy ramki powinien być widoczny i aktywne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie **IntitialUpdateFrame** po utworzeniu nowej ramki z `CreateNewFrame`. Wywołanie tej funkcji powoduje, że widoki w danym przedziale ramki do odbierania ich `OnInitialUpdate` wywołania. Ponadto jeśli nie ma wcześniej aktywny widok, widok głównej okno ramowe jest uaktywniona; podstawowy widok jest widokiem o identyfikatorze podrzędnych **AFX_IDW_PANE_FIRST**. Ponadto okno ramowe stają się widoczne czy `bMakeVisible` jest różna od zera. Jeśli *bMakeVisible* wynosi zero, bieżący fokus i wyświetlany stan okno ramowe zostanie zmieniona.  
  
 Nie jest konieczne do wywołania tej funkcji, korzystając z programu framework implementacja nowy plik i Otwórz plik.  
  
##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate  
 Ładuje zasobów dla danego `CDocTemplate` lub klasy.  
  
```  
virtual void LoadTemplate();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by załadować zasobów dla danego `CDocTemplate` lub klasy. Zazwyczaj jest to podczas konstruowania, z wyjątkiem gdy szablon jest budowany globalnie. W takim przypadku wywołania `LoadTemplate` jest opóźnione aż do [CWinApp::AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) jest wywoływana.  
  
##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType  
 Określa stopień zaufania pasuje do typu dokumentu i ten szablon.  
  
```  
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,  
    CDocument*& rpDocMatch);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPathName*  
 Nazwa ścieżki pliku, którego typ jest ustalany.  
  
 *rpDocMatch*  
 Wskaźnik do dokumentu, który jest przypisany pasującego dokumentu, jeśli plik określony przez *lpszPathName* jest już otwarty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od **zaufania** wyliczenia, który jest zdefiniowany w następujący sposób:  
  
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
 Ta funkcja służy do określenia typu dokumentu szablon używany do otwierania pliku. Jeśli aplikacja obsługuje wiele typów plików, na przykład służy tej funkcji do określenia, który szablonów dokumentów dostępnych jest odpowiednie dla danego pliku, wywołując `MatchDocType` dla każdego szablonu Włącz i wybieranie szablonów zgodnie z zwracana wartość zaufania.  
  
 Jeśli plik określony przez *lpszPathName* jest już otwarty, funkcja zwraca **CDocTemplate::yesAlreadyOpen** i kopiuje plik **CDocument** obiekt do obiekt w *rpDocMatch*.  
  
 Jeśli plik nie jest otwarty, ale rozszerzenie w *lpszPathName* określonego przez rozszerzenie **CDocTemplate::filterExt**, funkcja zwraca **CDocTemplate::yesAttemptNative** i ustawia *rpDocMatch* do **NULL**. Aby uzyskać więcej informacji na temat **CDocTemplate::filterExt**, zobacz [CDocTemplate::GetDocString](#getdocstring).  
  
 Jeśli żaden przypadek ma wartość PRAWDA, funkcja zwraca **CDocTemplate::yesAttemptForeign**.  
  
 Domyślna implementacja zwraca **CDocTemplate::maybeAttemptForeign** lub **CDocTemplate::maybeAttemptNative**. Zastąp tę funkcję, aby wdrożyć logikę dopasowywanie typu odpowiedniego do aplikacji, być może przy użyciu tych dwóch wartości z **zaufania** wyliczenia.  
  
##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile  
 Otwiera plik określony przez ścieżkę.  
  
```  
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;  
 
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,  
    BOOL bAddToMRU) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszPathName*  
 Wskaźnik do ścieżki pliku, który zawiera dokument, aby go otworzyć.  
  
 [in] *bAddToMRU*  
 `TRUE` Wskazuje, że dokument jest jednym z najbardziej aktualną plików; `FALSE` wskazuje dokumentu nie jest jednym z najnowszych plików.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do dokumentu, którego plik ma nazwę przez *lpszPathName*; `NULL` w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Otwiera plik, w których ścieżka jest określona przez *lpszPathName*. Jeśli *lpszPathName* jest `NULL`, zostanie utworzony nowy plik, zawierający typu skojarzone z tym szablonem dokumentu.  
  
##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument  
 Usuwa dokumentu wskazywana przez *pDoc* z listy dokumentów skojarzone z tym szablonem.  
  
```  
virtual void RemoveDocument(CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskaźnik do dokumentu, który ma zostać usunięty.  
  
### <a name="remarks"></a>Uwagi  
 Klasy pochodne `CMultiDocTemplate` i `CSingleDocTemplate` przesłonić tę funkcję. Jeśli pochodzi własne klasy szablonów dokumentów z `CDocTemplate`, klasy pochodne muszą przesłaniać tej funkcji.  
  
##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified  
 Zapisuje wszystkie dokumenty, które zostały zmodyfikowane.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Niezerowa w przypadku powodzenia; w przeciwnym razie 0.  
  
##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo  
 Określa zasoby dla kontenerów OLE podczas edycji elementu OLE w miejscu.  
  
```  
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDOleInPlaceContainer*  
 Identyfikator zasoby używane po aktywowaniu osadzonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić zasobów do użycia, kiedy obiekt OLE jest aktywowana w miejscu. Te zasoby mogą obejmować menu i tabele akceleratora. Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) funkcji aplikacji.  
  
 Menu skojarzone z *nIDOleInPlaceContainer* zawiera separatorów umożliwiających menu aktywowanego elementu w miejscu do scalenia z menu kontenera aplikacji. Aby uzyskać więcej informacji dotyczących scalania menu serwera i kontener, zobacz artykuł [menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle  
 Wywołanie tej funkcji, aby załadować dokument domyślny tytuł i wyświetl ją w pasku tytułu dokumentu.  
  
```  
virtual void SetDefaultTitle(CDocument* pDocument) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pDocument*  
 Wskaźnik do dokumentu jest tytuł której ma zostać ustawiona.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje na domyślny tytuł, zobacz opis **CDocTemplate::docName** w [CDocTemplate::GetDocString](#getdocstring).  
  
##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo  
 Określa klasy i zasobów, gdy dokument serwera jest osadzony lub edycji w miejscu.  
  
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
 Identyfikator zasobów używanych w przypadku osadzonego obiektu aktywacji w miejscu.  
  
 *pOleFrameClass*  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury zawierającej informacje o klasie dla obiekt window ramki tworzone podczas aktywacji w miejscu występuje.  
  
 *pOleViewClass*  
 Wskaźnik do `CRuntimeClass` struktury zawierającej informacje o klasie dla obiekt widoku tworzone podczas aktywacji w miejscu występuje.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich umożliwia identyfikowanie zasobów, które będą używane przez aplikację serwera, gdy użytkownik zażąda aktywację, osadzonego obiektu. Te zasoby składają się z menu i tabele akceleratora. Ta funkcja jest zazwyczaj wywoływana `InitInstance` aplikacji.  
  
 Menu skojarzone z *nIDOleInPlaceServer* zawiera separatorów umożliwiających menu serwera można scalić menu kontenera. Aby uzyskać więcej informacji dotyczących scalania menu serwera i kontener, zobacz artykuł [menu i zasoby (OLE)](../../mfc/menus-and-resources-ole.md).  
  
##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame  
 Tworzy ramkę podrzędnego używany do podglądu rozbudowanego.  
  
```  
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,  
    CDocument* pDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do nadrzędnego okna (zazwyczaj udostępnianych przez powłokę).  
  
 *pDoc*  
 Wskaźnik do obiektu dokumentu, którego zawartość zostanie wyświetlona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nieprawidłowy wskaźnik do `CFrameWnd` obiekt, lub `NULL` Jeśli tworzenie zakończy się niepowodzeniem.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo  
 Konfiguruje poza Obsługa podglądu procesu.  
  
```  
void SetPreviewInfo(
    UINT nIDPreviewFrame,  
    CRuntimeClass* pPreviewFrameClass = NULL,  
    CRuntimeClass* pPreviewViewClass = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDPreviewFrame*  
 Określa identyfikator zasobu ramki podglądu.  
  
 *pPreviewFrameClass*  
 Określa wskaźnik do struktury informacji środowiska uruchomieniowego klasy ramki w wersji zapoznawczej.  
  
 *pPreviewViewClass*  
 Określa wskaźnik do struktury informacji klasy środowiska uruchomieniowego widoku podglądu.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [Cdocument — klasa](../../mfc/reference/cdocument-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CScrollView](../../mfc/reference/cscrollview-class.md)   
 [Klasa CEditView](../../mfc/reference/ceditview-class.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Klasa CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
