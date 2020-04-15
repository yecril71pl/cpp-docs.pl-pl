---
title: Klasa CDataRecoveryHandler
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321932"
---
# <a name="cdatarecoveryhandler-class"></a>Klasa CDataRecoveryHandler

Automatyczne `CDataRecoveryHandler` wysady dokumentów i przywraca je, jeśli aplikacja nieoczekiwanie kończy działanie.

## <a name="syntax"></a>Składnia

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Konstruuje `CDataRecoveryHandler` obiekt.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Automatycznie przesyła każdy plik zarejestrowany `CDataRecoveryHandler` w klasie.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Automatyczne wysuwa określony dokument.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Dodaje dokument do listy otwartych dokumentów.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Usuwa wszystkie bieżące automatycznie uratowane pliki.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Usuwa określony plik automatycznie kasowy.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje nazwę pliku automatycznego zasłaniania skojarzonego z podaną nazwą pliku dokumentu.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Zwraca interwał między próbami automatycznego wsefotu.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Zwraca ścieżkę automatycznie zapisanych plików.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Pobiera nazwę dokumentu z `CDocument` obiektu.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Pobiera normalny tytuł dla określonego dokumentu.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Tworzy i zwraca tytuł odzyskanego dokumentu.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Pobiera unikatowy identyfikator ponownego uruchomienia aplikacji.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Wskazuje, `CDataRecoveryHandler` czy wykonuje autopis w bieżącej pętli bezczynnej.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Wskazuje, czy menedżer ponownego uruchamiania spowodował wyjście aplikacji.|
|[CDataRecoveryHandler::Inicjalizuj](#initialize)|Inicjuje `CDataRecoveryHandler`plik .|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Wyświetla użytkownikowi okno dialogowe dla każdego `CDataRecoveryHandler` dokumentu, który został automatycznie wypisyny. Okno dialogowe określa, czy użytkownik chce przywrócić automatycznie wydany dokument.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Ładuje listę otwartych dokumentów z rejestru.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Usuwa dostarczony dokument z otwartej listy dokumentów.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Otwiera wcześniej otwarte dokumenty.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Przywraca automatycznie uratowane dokumenty na podstawie danych wejściowych użytkownika.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Zapisuje bieżącą listę otwartych dokumentów w rejestrze systemu Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Ustawia czas między cyklami automatycznego wstawienia w milisekundach.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Ustawia katalog, w którym są przechowywane automatycznie zapisane pliki.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Ustawia unikatowy identyfikator ponownego uruchomienia `CDataRecoveryHandler`dla tego wystąpienia pliku .|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Określa, `CDataRecoveryHandler` czy informacje o otwartym dokumencie są zapisywane w rejestrze systemu Windows podczas bieżącego cyklu bezczynności.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Określa, czy poprzednie wyjście aplikacji było spowodowane przez menedżera ponownego uruchamiania.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informacje dotyczące dokumentu, ponieważ użytkownik go zapisał.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Wskazuje, czy program obsługi odzyskiwania danych ponownie otwiera wcześniej otwarte dokumenty.|
|m_bSaveDocumentInfoOnIdle|Wskazuje, czy program obsługi odzyskiwania danych automatycznie przesyła dokumenty w następnej pętli bezczynności.|
|m_bShutdownByRestartManager|Wskazuje, czy menedżer ponownego uruchamiania powoduje, że aplikacja do zakończenia.|
|m_dwRestartManagerSupportFlags|Flagi wskazujące, jaką obsługę zapewnia menedżer ponownego uruchamiania dla aplikacji.|
|m_lstAutosavesToDelete|Lista automatycznie wypisanych plików, które nie zostały usunięte po zamknięciu oryginalnych dokumentów. Po zamknięciu aplikacji menedżer ponownego uruchamiania ponawia usuwanie plików.|
|m_mapDocNameToAutosaveName|Mapa nazw dokumentów do nazw plików automatycznieawanych.|
|m_mapDocNameToDocumentPtr|Mapa nazw dokumentów do wskaźników [CDocument.](../../mfc/reference/cdocument-class.md)|
|m_mapDocNameToRestoreBool|Mapa nazwy dokumentu do parametru logicznego, który wskazuje, czy przywrócić automatycznie wydany dokument.|
|m_mapDocumentPtrToDocName|Mapa `CDocument` wskaźników do nazw dokumentów.|
|m_mapDocumentPtrToDocTitle|Mapa `CDocument` wskaźników do tytułów dokumentów. Tytuły te są używane do zapisywania plików.|
|m_nAutosaveInterval|Czas w milisekundach między autosaves.|
|m_nTimerID|Identyfikator czasomierza automatycznegoave.|
|m_strAutosavePath|Lokalizacja, w której przechowywane są automatycznie zapisane dokumenty.|
|m_strRestartIdentifier|Reprezentacja ciągu identyfikatora GUID dla menedżera ponownego uruchamiania.|

## <a name="remarks"></a>Uwagi

Menedżer ponownego uruchamiania `CDataRecoveryHandler` używa klasy do śledzenia wszystkich otwartych dokumentów i automatycznego ich przechowywania w razie potrzeby. Aby włączyć autopis, należy użyć [metody CDataRecoveryHandler::SetSaveDocumentInfoOnIdle.](#setsavedocumentinfoonidle) Ta metoda kieruje `CDataRecoveryHandler` do wykonania autosave na następnej pętli bezczynnego. Menedżer ponownego `SetSaveDocumentInfoOnIdle` uruchamiania `CDataRecoveryHandler` wywołuje, gdy należy wykonać autopis.

Wszystkie metody klasy `CDataRecoveryHandler` są wirtualne. Zastąd w tej klasie należy zastąpić metody tworzenia własnego niestandardowego programu obsługi odzyskiwania danych. Jeśli nie utworzysz własnego programu obsługi odzyskiwania danych lub menedżera ponownego uruchamiania, nie należy tworzyć wystąpienia CDataRecoveryHandler. [Klasa CWinApp](../../mfc/reference/cwinapp-class.md) tworzy `CDataRecoveryHandler` obiekt, jak jest to wymagane.

Aby można było `CDataRecoveryHandler` użyć obiektu, należy wywołać [CDataRecoveryHandler::Initialize](#initialize).

Ponieważ `CDataRecoveryHandler` klasa jest ściśle połączona z `CDataRecoveryHandler` menedżerem ponownego `m_dwRestartManagerSupportFlags`uruchamiania, zależy od parametru globalnego . Ten parametr określa, jakie uprawnienia ma menedżer ponownego uruchamiania i jak współdziała z aplikacją. Aby włączyć menedżera ponownego uruchamiania do istniejącej `m_dwRestartManagerSupportFlags` aplikacji, należy przypisać odpowiednią wartość w konstruktorze aplikacji głównej. Aby uzyskać więcej informacji na temat korzystania z menedżera ponownego uruchamiania, zobacz [Jak: Dodawanie pomocy technicznej menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdatarecovery.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo

Automatycznie przesyła każdy plik zarejestrowany `CDataRecoveryHandler` w klasie.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, `CDataRecoveryHandler` jeśli zapisane wszystkie dokumenty; FAŁSZ, jeśli żaden dokument nie został zapisany.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość PRAWDA, jeśli nie ma żadnych dokumentów, które muszą zostać zapisane. Zwraca również wartość TRUE bez zapisywania `CWinApp` `CDocManager` żadnych dokumentów, jeśli pobieranie lub dla aplikacji generuje błąd.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL w `m_dwRestartManagerSupportFlags`pliku . Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie pomocy technicznej menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo

Automatyczne wysuwa określony dokument.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do `CDocument` zapisywania.|
|*bResetModifiedFlag*|[w] TRUE wskazuje, `CDataRecoveryHandler` że uważa *pDocument* do zmodyfikowania; FALSE wskazuje, że struktura uważa *pDocument* za niezmodyfikowane. Zobacz uwagi sekcji, aby uzyskać więcej informacji na temat wpływu tej flagi.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ustawiono odpowiednie flagi, a `CDocument` *pDocument* jest prawidłowym obiektem.

### <a name="remarks"></a>Uwagi

Każdy `CDocument` obiekt ma flagę, która wskazuje, czy został zmieniony od ostatniego zapisu. Użyj [CDocument::IsModified,](../../mfc/reference/cdocument-class.md#ismodified) aby określić stan tej flagi. Jeśli `CDocument` a nie uległa zmianie `AutosaveDocumentInfo` od czasu ostatniego zapisu, usuwa wszystkie automatycznie zapisane pliki dla tego dokumentu. Jeśli dokument uległ zmianie od czasu ostatniego zapisu, zamknięcie go monituje użytkownika o zapisanie dokumentu przed zamknięciem.

> [!NOTE]
> Za pomocą *bResetModifiedFlag,* aby zmienić stan dokumentu na niezmodyfikowany może spowodować utratę niezapisanych danych użytkownika. Jeśli struktura uważa dokument niezmodyfikowany, zamknięcie go nie monituje użytkownika, aby zapisać.

Ta metoda zgłasza wyjątek z makrą [ASSERT,](diagnostic-services.md#assert) jeśli `CDocument` *pDocument* nie jest prawidłowym obiektem.

Aby użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL muszą być ustawione w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler

Konstruuje `CDataRecoveryHandler` obiekt.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*dwRestartManagerSupportLags*|[w] Wskazuje, które opcje menedżera ponownego uruchamiania są obsługiwane.|
|*nAutosaveInterval*|[w] Czas między autosaves. Ten parametr jest w milisekundach.|

### <a name="remarks"></a>Uwagi

Struktura MFC automatycznie tworzy `CDataRecoveryHandler` obiekt dla aplikacji podczas korzystania z kreatora **Nowego projektu.** Jeśli nie dostosowujesz zachowania odzyskiwania danych lub menedżera ponownego `CDataRecoveryHandler` uruchamiania, nie należy tworzyć obiektu.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo

Dodaje dokument do listy otwartych dokumentów.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do `CDocument`. Ta metoda tworzy informacje `CDocument`o dokumencie dla tego .|

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda sprawdza, czy *pDocument* jest już na liście dokumentów, zanim doda dokument. Jeśli *pDocument* jest już na liście, ta metoda usuwa automatycznieaved plik skojarzony z *pDocument*.

Aby użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL muszą być ustawione w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles

Usuwa wszystkie bieżące automatycznie uratowane pliki.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile

Usuwa określony plik automatycznie kasowy.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strAutosavedFile*|[w] Ciąg zawierający nazwę pliku automatycznie wypisanego.|

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie może usunąć automatycznie zapisanego pliku, zapisuje nazwę pliku na liście. Destruktor próbuje `CDataRecoveryHandler` usunąć każdy plik automatycznieaved określony na tej liście.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName

Generuje nazwę pliku automatycznego zasłaniania skojarzonego z podaną nazwą pliku dokumentu.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parametry

*nazwa strDocumentName*<br/>
[w] Ciąg zawierający nazwę dokumentu. `GenerateAutosaveFileName`używa tej nazwy dokumentu do wygenerowania odpowiedniej nazwy pliku automatycznego za pomocą automatycznego wsłania.

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku automatycznego wypisu wygenerowana z *pliku strDocumentName*.

### <a name="remarks"></a>Uwagi

Każda nazwa dokumentu ma mapowanie jeden do jednego z nazwą pliku automatycznegoave.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval

Zwraca interwał między próbami automatycznego wsefotu.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba milisekund między próbami automatycznego własnania.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath

Zwraca ścieżkę automatycznie zapisanych plików.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Lokalizacja, w której przechowywane są automatycznie zapisane dokumenty.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName

Pobiera nazwę dokumentu z `CDocument` obiektu.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do `CDocument`. `GetDocumentListName`pobiera nazwę dokumentu z `CDocument`tego pliku .|

### <a name="return-value"></a>Wartość zwracana

Nazwa dokumentu z *pliku pDocument*.

### <a name="remarks"></a>Uwagi

Używa `CDataRecoveryHandler` nazwy dokumentu jako klucza w *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*i *m_mapDocNameToRestoreBool*. Te parametry `CDataRecoveryHandler` umożliwiają `CDocument` monitorowanie obiektów, nazwę pliku automatycznego akcesji i ustawienia automatycznego wypisu.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle

Pobiera normalny tytuł dla określonego dokumentu.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do `CDocument`.|

### <a name="return-value"></a>Wartość zwracana

Normalny tytuł dla określonego dokumentu.

### <a name="remarks"></a>Uwagi

Normalnym tytułem dokumentu jest zwykle nazwa pliku dokumentu bez ścieżki. Jest to tytuł w polu **Nazwa pliku** okna dialogowego **Zapisywanie jako.**

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle

Tworzy i zwraca tytuł odzyskanego dokumentu.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parametry

*strDocumentTitle (Tytuł)*<br/>
[w] Normalny tytuł dokumentu.

### <a name="return-value"></a>Wartość zwracana

Odzyskany tytuł dokumentu.

### <a name="remarks"></a>Uwagi

Domyślnie odzyskany tytuł dokumentu jest normalnym tytułem z dołączanym do niego **[odzyskanym].** Odzyskany tytuł jest wyświetlany użytkownikowi, `CDataRecoveryHandler` gdy użytkownik wysyła zapytanie o przywrócenie automatycznie wydanych dokumentów.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier

Pobiera unikatowy identyfikator ponownego uruchomienia aplikacji.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator ponownego uruchomienia.

### <a name="remarks"></a>Uwagi

Identyfikator ponownego uruchomienia jest unikatowy dla każdego wykonania aplikacji.

Przechowuje `CDataRecoveryHandler` informacje w rejestrze o aktualnie otwartych dokumentach. Gdy menedżer ponownego uruchamiania kończy działanie aplikacji i uruchamia ją ponownie, dostarcza identyfikator ponownego uruchomienia do `CDataRecoveryHandler`pliku . Identyfikator `CDataRecoveryHandler` ponownego uruchomienia używa do pobierania listy wcześniej otwartych dokumentów. Dzięki temu `CDataRecoveryHandler` można spróbować znaleźć i przywrócić automatycznie odpisane pliki.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Wskazuje, `CDataRecoveryHandler` czy wykonuje autopis w bieżącej pętli bezczynnej.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Wartość zwracana

WARTOŚĆ TRUE `CDataRecoveryHandler` wskazuje automatyczne wysuwa się na bieżącą pętlę bezczynności; FALSE oznacza, że nie.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager

Wskazuje, czy menedżer ponownego uruchamiania spowodował wyjście aplikacji.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Wartość zwracana

TRUE wskazuje, że menedżer ponownego uruchamiania spowodował wyjście aplikacji; FALSE wskazuje, że nie.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CDataRecoveryHandler::Inicjalizuj

Inicjuje `CDataRecoveryHandler`plik .

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Proces inicjowania ładuje ścieżkę do przechowywania plików automatycznego zapisywania z rejestru. Jeśli `Initialize` metoda nie może odnaleźć tego `Initialize` katalogu `FALSE`lub ścieżka ma wartość NULL, kończy się niepowodzeniem i zwraca .

Użyj [CDataRecoveryHandler::SetAutosavePath,](#setautosavepath) aby zmienić ścieżkę automatycznego `CDataRecoveryHandler`zapisu po zainicjowaniu przez aplikację pliku .

Metoda `Initialize` uruchamia również czasomierz do monitorowania, gdy wystąpi następny autopis. Użyj [CDataRecoveryHandler::SetAutosaveInterval,](#setautosaveinterval) aby zmienić interwał automatycznego `CDataRecoveryHandler`zapisu po zainicjowaniu przez aplikację pliku .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Wyświetla użytkownikowi okno dialogowe dla każdego `CDataRecoveryHandler` dokumentu, który został automatycznie wypisyny. Okno dialogowe określa, czy użytkownik chce przywrócić automatycznie wydany dokument.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Uwagi

Jeśli aplikacja jest Unicode, ta metoda wyświetla [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) do użytkownika. W przeciwnym razie struktura używa [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) do kwerendy użytkownika.

Po `QueryRestoreAutosavedDocuments` zebraniu wszystkich odpowiedzi od użytkownika, przechowuje informacje w zmiennej członkowskiej *m_mapDocNameToRestoreBool*. Ta metoda nie przywraca automatycznie wypisanych dokumentów.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList

Ładuje listę otwartych dokumentów z rejestru.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

WARTOŚĆ TRUE `ReadOpenDocumentList` oznacza, że załadowano informacje dla co najmniej jednego dokumentu z rejestru; FALSE wskazuje, że nie załadowano żadnych informacji o dokumencie.

### <a name="remarks"></a>Uwagi

Ta funkcja ładuje informacje o otwartym dokumencie z rejestru i przechowuje je w zmiennej członkowskiej *m_mapDocNameToAutosaveName*.

Po `ReadOpenDocumentList` załadowaniu wszystkich danych usuwa informacje o dokumencie z rejestru.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo

Usuwa dostarczony dokument z otwartej listy dokumentów.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do dokumentu do usunięcia.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, *jeśli pDocument* został usunięty z listy; FAŁSZ, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Gdy użytkownik zamyka dokument, struktura używa tej metody, aby usunąć go z listy otwartych dokumentów.

Jeśli `RemoveDocumentInfo` nie można znaleźć *pDocument* na liście otwartych dokumentów, nie robi nic i zwraca wartość TRUE.

Aby użyć tej metody, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musi być ustawiona w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments

Otwiera wcześniej otwarte dokumenty.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli otwarto co najmniej jeden dokument; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera najnowsze zapisywanie wcześniej otwartych dokumentów. Jeśli dokument nie został zapisany lub `ReopenPreviousDocuments` automatycznie zapisany, otwiera pusty dokument na podstawie szablonu dla tego typu pliku.

Aby użyć tej metody, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musi być ustawiona w *m_dwRestartManagerSupportFlags*. Jeśli ten parametr nie `ReopenPreviousDocuments` jest ustawiony, nic nie robi i zwraca WARTOŚĆ FAŁSZ.

Jeśli na liście wcześniej otwartych dokumentów nie ma `ReopenPreviousDocuments` żadnych dokumentów, nic nie robi i zwraca WARTOŚĆ FAŁSZU.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments

Przywraca automatycznie uratowane dokumenty na podstawie danych wejściowych użytkownika.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda pomyślnie przywraca dokumenty.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CDataRecoveryHandler::QueryRestoreAutosavedDocuments,](#queryrestoreautosaveddocuments) aby określić, które dokumenty użytkownik chce przywrócić. Jeśli użytkownik zdecyduje się nie przywracać automatycznie `RestoreAutosavedDocuments` kasowego dokumentu, usuwa plik automatycznego zasłaniania. W `RestoreAutosavedDocuments` przeciwnym razie zastępuje otwarty dokument wersją automatycznie wypisaną.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES lub AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES `m_dwRestartManagerSupportFlags`w pliku .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList

Zapisuje bieżącą listę otwartych dokumentów w rejestrze systemu Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli nie ma otwartych dokumentów do zapisania lub jeśli zostały pomyślnie zapisane. FAŁSZ, jeśli istnieją dokumenty do zapisania w rejestrze, ale nie zostały zapisane, ponieważ wystąpił błąd.

### <a name="remarks"></a>Uwagi

Menedżer ponownego `SaveOpenDocumentList` uruchamiania wywołuje, gdy aplikacja kończy się nieoczekiwanie lub gdy kończy pracę w celu uaktualnienia. Po ponownym uruchomieniu aplikacji używa [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) do pobierania listy otwartych dokumentów.

Ta metoda zapisuje tylko listę otwartych dokumentów. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) jest odpowiedzialny za zapisywanie dokumentów siebie.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval

Ustawia czas między cyklami automatycznego wstawienia w milisekundach.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*nAutosaveInterval*<br/>
[w] Nowy interwał automatycznego własnopisu w milisekundach.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath

Ustawia katalog, w którym są przechowywane automatycznie zapisane pliki.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strAutosavePath (Ścieżka strAutosavePath)*|[w] Ścieżka, w której są przechowywane pliki automatycznego zapisu.|

### <a name="remarks"></a>Uwagi

Zmiana katalogu automatycznego zawijania nie powoduje przeniesienia aktualnie automatycznie zaaklonych plików.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier

Ustawia unikatowy identyfikator ponownego uruchomienia `CDataRecoveryHandler`dla tego wystąpienia pliku .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strRestartIdentifier (identyfikowacz)*|[w] Unikatowy identyfikator menedżera ponownego uruchamiania.|

### <a name="remarks"></a>Uwagi

Menedżer ponownego uruchamiania rejestruje informacje o otwartych dokumentach w rejestrze. Te informacje są przechowywane z unikatowym identyfikatorem ponownego uruchomienia jako klucz. Ponieważ identyfikator ponownego uruchamiania jest unikatowy dla każdego wystąpienia aplikacji, wiele wystąpień aplikacji może nieoczekiwanie zakończyć działanie, a menedżer ponownego uruchamiania może odzyskać każdy z nich.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Określa, `CDataRecoveryHandler` czy informacje o otwartym dokumencie są zapisywane w rejestrze systemu Windows podczas bieżącego cyklu bezczynności.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bSaveOnIdle (Niesłychane)*|[w] PRAWDA, aby zapisać informacje o dokumencie podczas bieżącego cyklu bezczynnego; FALSE, aby nie wykonywać zapisywania.|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager

Określa, czy poprzednie wyjście aplikacji było spowodowane przez menedżera ponownego uruchamiania.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bShutdownByRestartManager*|[w] TRUE, aby wskazać, że menedżer ponownego uruchamiania spowodował działanie aplikacji; FALSE, aby wskazać, że aplikacja została zakończona z innego powodu.|

### <a name="remarks"></a>Uwagi

Struktura zachowuje się inaczej w zależności od tego, czy poprzednie wyjście było nieoczekiwane lub czy zostało zainicjowane przez menedżera ponownego uruchamiania.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo

Aktualizuje informacje dotyczące dokumentu, ponieważ użytkownik go zapisał.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Pdocument*|[w] Wskaźnik do zapisanego dokumentu.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda usunęła automatycznie wydany dokument i zaktualizowała informacje o dokumencie; FAŁSZ, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Gdy użytkownik zapisuje dokument, aplikacja usuwa automatycznie zapisywany plik, ponieważ nie jest już potrzebny. `UpdateDocumentInfo`usuwa automatycznie zapisowy plik, wywołując [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`następnie dodaje informacje z *pDocument* do listy aktualnie otwartych dokumentów, ponieważ `RemoveDocumentInfo` usuwa te informacje, ale zapisany dokument jest nadal otwarty.

Aby użyć tej metody, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES musi być ustawiona w *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Instrukcje: dodawanie obsługi menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)
