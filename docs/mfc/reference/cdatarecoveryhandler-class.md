---
title: Klasa CDataRecoveryHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e038cc779f2a007d680eb8b2577881a55b81d4c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076675"
---
# <a name="cdatarecoveryhandler-class"></a>Klasa CDataRecoveryHandler

`CDataRecoveryHandler` Automatycznie zapisuje i przywraca dokumenty, jeśli aplikacja niespodziewanie kończy pracę.

## <a name="syntax"></a>Składnia

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Konstruuje `CDataRecoveryHandler` obiektu.|

### <a name="methods"></a>Metody

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Automatycznie zapisuje każdy plik zarejestrowane w usłudze `CDataRecoveryHandler` klasy.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Automatycznie zapisuje określonego dokumentu.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Dodanie dokumentu do listy otwartych dokumentów.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Usuwa wszystkie bieżące pliki automatycznie zapisany.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Usuwa plik określony automatycznie zapisany.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje nazwę skojarzone z nazwą pliku dokumentu podany plik automatycznego zapisu.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Zwraca przedział między prób zapisywania.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Zwraca ścieżkę do plików automatycznie zapisany.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Pobiera nazwę dokumentu z `CDocument` obiektu.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Pobiera tytuł normalne dla określonego dokumentu.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Tworzy i zwraca tytuł dokumentu odzyskane.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Pobiera identyfikator unikatowy ponownego uruchomienia aplikacji.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Wskazuje, czy `CDataRecoveryHandler` wykonuje automatycznego zapisywania na bieżącym wykonywania pętli bezczynności.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Wskazuje, czy Menedżera ponownego uruchamiania spowodowane wyjścia z aplikacji.|
|[CDataRecoveryHandler::Initialize](#initialize)|Inicjuje `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Wyświetlane jest okno dialogowe dla użytkownika, dla każdego dokumentu, który `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce, aby przywrócić automatycznie zapisany dokument.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Na liście otwartym dokumencie ładuje z rejestru.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Usuwa podany dokument z listy otwartych dokumentów.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Zostanie otwarty wcześniej otwartych dokumentów.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Przywraca dokumenty zapisana automatycznie na podstawie danych wejściowych użytkownika.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Zapisuje bieżącej listy otwartych dokumentów w rejestrze systemu Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Ustawia czas między cykle zapisywania w milisekundach.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Ustawia katalog, w którym są przechowywane pliki automatycznie zapisany.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Ustawia identyfikator unikatowy ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Zestawy czy `CDataRecoveryHandler` zapisuje informacje o otwartym dokumencie w rejestrze Windows podczas bieżącego cyklu bezczynności.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Określa, czy poprzednie zakończenia aplikacji zostało spowodowane przez Menedżera ponownego uruchamiania.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informacje dla dokumentu, ponieważ jest on zapisany.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Wskazuje, czy program obsługi odzyskiwania danych ponownie otwiera wcześniej otwartych dokumentów.|
|m_bSaveDocumentInfoOnIdle|Wskazuje, czy automatycznie danych odzyskiwania programu obsługi zapisuje dokumenty w następnej pętli bezczynności.|
|m_bShutdownByRestartManager|Wskazuje, czy Menedżera ponownego uruchamiania powoduje, że aplikacja zakończyć pracę.|
|m_dwRestartManagerSupportFlags|Zawiera flagi wskazujące na to, co obsługi Menedżera ponownego uruchamiania aplikacji.|
|m_lstAutosavesToDelete|Lista plików automatycznie zapisany, które nie zostały usunięte, gdy oryginalne dokumenty zostały zamknięte. Kiedy aplikacja kończy działanie, ponownych prób Menedżera ponownego uruchamiania, usuwając pliki.|
|m_mapDocNameToAutosaveName|Mapa nazw dokumentów z nazwami plików automatycznie zapisany.|
|m_mapDocNameToDocumentPtr|Mapa nazw dokumentów do [CDocument](../../mfc/reference/cdocument-class.md) wskaźników.|
|m_mapDocNameToRestoreBool|Mapa nazw dokumentów, aby parametr logiczny, który wskazuje, czy mają zostać przywrócone automatycznie zapisany dokument.|
|m_mapDocumentPtrToDocName|Mapa `CDocument` wskaźniki do nazw dokumentów.|
|m_mapDocumentPtrToDocTitle|Mapa `CDocument` wskaźniki do tytuły dokumentu. Te tytuły są używane do zapisywania plików.|
|m_nAutosaveInterval|Czas w milisekundach między automatycznie zapisuje.|
|m_nTimerID|Identyfikator czasomierza zapisywania.|
|m_strAutosavePath|Lokalizacja, w którym są przechowywane w dokumentach automatycznie zapisany.|
|m_strRestartIdentifier|Reprezentacja ciągu identyfikatora GUID dla Menedżera ponownego uruchamiania.|

## <a name="remarks"></a>Uwagi

Korzysta z Menedżera ponownego uruchamiania `CDataRecoveryHandler` klasy, aby zachować wszystkie otwarte dokumenty i zapisywania ich śledzenie zgodnie z potrzebami. Aby włączyć automatyczne zapisywanie, użyj [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) metody. Określa, że ta metoda `CDataRecoveryHandler` do wykonywania automatycznego zapisywania na następnej pętli bezczynności. Wywołuje Menedżera ponownego uruchamiania `SetSaveDocumentInfoOnIdle` podczas `CDataRecoveryHandler` należy wykonać zapisywania.

Wszystkie metody `CDataRecoveryHandler` klasy są wirtualne. Zastępowanie metody tej klasy, aby utworzyć własny obsługi odzyskiwania danych niestandardowych. Jeśli nie możesz utworzyć własne obsługi odzyskiwania danych lub ponownie uruchom Menedżera nie tworzy CDataRecoveryHandler. [Klasa CWinApp](../../mfc/reference/cwinapp-class.md) tworzy `CDataRecoveryHandler` obiektu, ponieważ jest to wymagane.

Przed użyciem `CDataRecoveryHandler` obiektu, należy wywołać [CDataRecoveryHandler::Initialize](#initialize).

Ponieważ `CDataRecoveryHandler` klasy jest ściśle połączony Menedżera ponownego uruchamiania `CDataRecoveryHandler` zależy od parametrów globalnych `m_dwRestartManagerSupportFlags`. Ten parametr określa, jakie uprawnienia ma Menedżera ponownego uruchamiania i sposób jej interakcji z aplikacją. Aby dołączyć Menedżera ponownego uruchamiania do istniejącej aplikacji, musisz przypisać `m_dwRestartManagerSupportFlags` odpowiednią wartość w Konstruktorze głównej aplikacji. Aby uzyskać więcej informacji na temat używania Menedżera ponownego uruchamiania, zobacz [porady: Dodawanie obsługi Menedżera ponownego uruchomienia](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

Automatycznie zapisuje każdy plik zarejestrowane w usłudze `CDataRecoveryHandler` klasy.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli `CDataRecoveryHandler` zapisane dokumenty; Wartość FALSE, jeśli dowolny dokument nie został zapisany.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość PRAWDA, jeśli nie ma żadnych dokumentów, które muszą zostać zapisane. Również zwraca wartość TRUE bez zapisywania dokumentów, jeśli pobieranie `CWinApp` lub `CDocManager` dla aplikacja generuje błąd.

Aby użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL musi być ustawiona w `m_dwRestartManagerSupportFlags`. Zobacz [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) Aby uzyskać więcej informacji.

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

Automatycznie zapisuje określonego dokumentu.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do `CDocument` do zapisania.|
|*bResetModifiedFlag*|[in] Wartość TRUE wskazuje, że `CDataRecoveryHandler` uwzględnia *pDocument* do zmodyfikowania; Wartość FALSE wskazuje, że struktura uwzględnia *pDocument* jako niezmodyfikowany. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji na temat wpływu tej flagi.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ustawiono flagi odpowiednie i *pDocument* jest prawidłowym `CDocument` obiektu.

### <a name="remarks"></a>Uwagi

Każdy `CDocument` obiekt ma flagę wskazującą, czy został zmieniony od ostatniego zapisu. Użyj [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) do ustalenia stanu tej flagi. Jeśli `CDocument` nie zmienił się od ostatniego zapisu `AutosaveDocumentInfo` usuwa wszystkie pliki automatycznie zapisany dla tego dokumentu. Jeśli dokument został zmieniony od ostatniego zapisu, zamykając go monituje użytkownika o zapisanie dokumentu przed zamknięciem.

> [!NOTE]
>  Za pomocą *bResetModifiedFlag* można zmienić stanu dokumentu do niezmodyfikowanego może spowodować, że użytkownikowi utraty niezapisanych danych. Jeśli framework uwzględnia dokumentu w niezmienionej postaci, zamykając go nie będzie monitował użytkownika, aby zapisać.

Ta metoda wyrzuca wyjątek z [ASERCJA](diagnostic-services.md#assert) — makro Jeśli *pDocument* nie jest prawidłowym `CDocument` obiektu.

Aby użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL musi być ustawiona w *m_dwRestartManagerSupportFlags*.

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

Konstruuje `CDataRecoveryHandler` obiektu.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*dwRestartManagerSupportFlags*|[in] Wskazuje, które opcje Menedżera ponownego uruchamiania są obsługiwane.|
|*nAutosaveInterval*|[in] Czas między automatycznie zapisuje. Ten parametr jest w milisekundach.|

### <a name="remarks"></a>Uwagi

Struktura MFC automatycznie tworzy `CDataRecoveryHandler` obiektu dla twojej aplikacji, gdy używasz **nowy projekt** kreatora. Chyba że dostosowywania zachowania w zakresie odzyskiwania danych lub Menedżera ponownego uruchamiania, nie należy tworzyć `CDataRecoveryHandler` obiektu.

##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

Dodanie dokumentu do listy otwartych dokumentów.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do `CDocument`. Ta metoda tworzy informacje dokument na temat tego `CDocument`.|

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda sprawdza, czy *pDocument* jest już na liście dokumentów przed dodaniem dokumentu. Jeśli *pDocument* jest już na liście, ta metoda usuwa skojarzony plik automatycznie zapisany *pDocument*.

Aby użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL musi być ustawiona w *m_dwRestartManagerSupportFlags*.

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

Usuwa wszystkie bieżące pliki automatycznie zapisany.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość PRAWDA.

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

Usuwa plik określony automatycznie zapisany.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strAutosavedFile*|[in] Ciąg, który zawiera nazwę pliku automatycznie zapisany.|

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie można usunąć pliku automatycznie zapisany, zapisuje nazwę pliku na liście. Destruktor dla `CDataRecoveryHandler` próbuje usunąć każdy plik automatycznie zapisany określone na tej liście.

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

Generuje nazwę skojarzone z nazwą pliku dokumentu podany plik automatycznego zapisu.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parametry

*strDocumentName*<br/>
[in] Ciąg, który zawiera nazwę dokumentu. `GenerateAutosaveFileName` używa tej nazwy dokumentu, można wygenerować odpowiedniego nazwy pliku zapisywania.

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku zapisywania wygenerowany na podstawie *strDocumentName*.

### <a name="remarks"></a>Uwagi

Każda nazwa dokumentu zawiera mapowanie jeden do jednego z nazwą pliku zapisywania.

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

Zwraca przedział między prób zapisywania.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Wartość zwracana

Próbuje liczbę milisekund między zapisywania.

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

Zwraca ścieżkę do plików automatycznie zapisany.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Lokalizacja, w którym są przechowywane w dokumentach automatycznie zapisany.

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

Pobiera nazwę dokumentu z `CDocument` obiektu.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do `CDocument`. `GetDocumentListName` pobiera nazwę dokumentu z tym `CDocument`.|

### <a name="return-value"></a>Wartość zwracana

Nazwa dokumentu z *pDocument*.

### <a name="remarks"></a>Uwagi

`CDataRecoveryHandler` Używa nazwy dokumentu jako klucz w *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*, i *m_mapDocNameToRestoreBool*. Włącz te parametr `CDataRecoveryHandler` do monitorowania `CDocument` obiektów, nazwę pliku zapisywania i zapisywania ustawień.

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

Pobiera tytuł normalne dla określonego dokumentu.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do `CDocument`.|

### <a name="return-value"></a>Wartość zwracana

Normalne tytuł dla określonego dokumentu.

### <a name="remarks"></a>Uwagi

Normalne tytuł dokumentu jest zazwyczaj nazwa pliku dokumentu bez ścieżki. Jest to tytuł w **nazwy pliku** pole **Zapisz jako** okno dialogowe.

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

Tworzy i zwraca tytuł dokumentu odzyskane.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parametry

*strDocumentTitle*<br/>
[in] Normalne tytuł dokumentu.

### <a name="return-value"></a>Wartość zwracana

Tytuł dokumentu odzyskane.

### <a name="remarks"></a>Uwagi

Domyślnie odzyskane tytuł dokumentu jest normalne tytuł zawierający **[odzyskano]** dołączone do niego. Odzyskane tytuł jest wyświetlany użytkownikowi podczas `CDataRecoveryHandler` zapytania użytkownika, aby przywrócić automatycznie zapisany dokumentów.

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

Pobiera identyfikator unikatowy ponownego uruchomienia aplikacji.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator unikatowy ponownego uruchomienia.

### <a name="remarks"></a>Uwagi

Identyfikator ponowne uruchomienie jest unikatowy dla każdego wykonania aplikacji.

`CDataRecoveryHandler` Informacje są przechowywane w rejestrze o aktualnie otwarte dokumenty. Gdy Menedżera ponownego uruchamiania kończy działanie aplikacji i ponownie go uruchamia, dostarcza mu identyfikator ponownego uruchomienia, aby `CDataRecoveryHandler`. `CDataRecoveryHandler` Używa identyfikatora ponownego uruchomienia można pobrać listy wcześniej otwartych dokumentów. Dzięki temu `CDataRecoveryHandler` próby znajdowania i przywracania plików automatycznie zapisany.

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Wskazuje, czy `CDataRecoveryHandler` wykonuje automatycznego zapisywania na bieżącym wykonywania pętli bezczynności.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje `CDataRecoveryHandler` automatycznie zapisuje w bieżącym pętli bezczynności. Wartość FALSE wskazuje, że nie ma.

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

Wskazuje, czy Menedżera ponownego uruchamiania spowodowane wyjścia z aplikacji.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że Menedżera ponownego uruchamiania przyczyną aplikacji zakończyć działanie; Wartość FALSE wskazuje, czy nie.

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

Inicjuje `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli inicjowanie zakończy się; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Proces inicjowania ładuje ścieżki do przechowywania plików zapisywania z rejestru. Jeśli `Initialize` metody nie można odnaleźć tego katalogu lub jeśli ścieżka ma wartość NULL, `Initialize` kończy się niepowodzeniem i zwraca `FALSE`.

Użyj [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) Aby zmienić ścieżkę zapisywania po inicjuje aplikację `CDataRecoveryHandler`.

`Initialize` Metoda również uruchamia czasomierz monitorowanie sytuacji zapisywania dalej. Użyj [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) Aby zmienić interwał zapisywania po inicjuje aplikację `CDataRecoveryHandler`.

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Wyświetlane jest okno dialogowe dla użytkownika, dla każdego dokumentu, który `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce, aby przywrócić automatycznie zapisany dokument.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Uwagi

Jeśli aplikacja jest Unicode, ta metoda Wy Wyświetla [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) dla użytkownika. W przeciwnym razie środowisko wykorzystuje [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) kwerendy użytkownika.

Po `QueryRestoreAutosavedDocuments` gromadzi wszystkie odpowiedzi od użytkownika, przechowuje informacje w zmiennej składowej *m_mapDocNameToRestoreBool*. Ta metoda nie przywraca dokumenty automatycznie zapisany.

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

Na liście otwartym dokumencie ładuje z rejestru.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że `ReadOpenDocumentList` załadować informacji dla co najmniej jednego dokumentu z rejestru; Wartość FALSE wskazuje, że żadne informacje dokument został załadowany.

### <a name="remarks"></a>Uwagi

Ta funkcja ładuje informacje Otwórz dokument z rejestru i zapisuje go w zmiennej składowej *m_mapDocNameToAutosaveName*.

Po `ReadOpenDocumentList` ładuje wszystkie dane, usuwa z rejestru informacji o dokumencie.

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

Usuwa podany dokument z listy otwartych dokumentów.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do dokumentu, aby usunąć.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli *pDocument* został usunięty z listy; Wartość FALSE, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Po użytkownik zamknie dokumentu, struktura używa tej metody, aby usunąć go z listy otwartych dokumentów.

Jeśli `RemoveDocumentInfo` nie można odnaleźć *pDocument* na liście otwartych dokumentów, nic nie robi i zwraca wartość TRUE.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

Zostanie otwarty wcześniej otwartych dokumentów.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli co najmniej jeden dokument został otwarty; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje otwarcie najnowszych zapisywania wcześniej otwartych dokumentów. Jeśli dokument nie został zapisany lub zapisana, automatycznie `ReopenPreviousDocuments` otwiera pusty dokument oparty na szablonie dla tego typu pliku.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*. Jeśli ten parametr nie jest ustawiona, `ReopenPreviousDocuments` nic nie robi i zwraca wartość FALSE.

Jeśli nie ma żadnych dokumentów przechowywanych w listy wcześniej otwartych dokumentów `ReopenPreviousDocuments` nic nie robi i zwraca wartość FALSE.

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

Przywraca dokumenty zapisana automatycznie na podstawie danych wejściowych użytkownika.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda pomyślnie przywraca dokumenty.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) ustalenie, dokumenty, które użytkownik chce, aby przywrócić. Jeśli użytkownik zdecyduje się nie przywrócić dokument automatycznie zapisany `RestoreAutosavedDocuments` usuwa plik automatycznego zapisu. W przeciwnym razie `RestoreAutosavedDocuments` zastępuje otwartym dokumencie wersją automatycznie zapisany.

Aby użyć tej metody, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES lub AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES musi być ustawiona w `m_dwRestartManagerSupportFlags`.

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

Zapisuje bieżącej listy otwartych dokumentów w rejestrze systemu Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli nie ma żadnych otwartych dokumentów, aby zapisać lub zostały pomyślnie zapisane. Wartość FALSE, jeśli istnieją dokumenty, aby zapisać do rejestru, ale nie zostały zapisane, ponieważ wystąpił błąd.

### <a name="remarks"></a>Uwagi

Wywołuje Menedżera ponownego uruchamiania `SaveOpenDocumentList` gdy aplikacja jest nieoczekiwanie zamykany lub kiedy wychodzi dla uaktualnienie. Po ponownym uruchomieniu aplikacji używa [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) można pobrać listy otwartych dokumentów.

Ta metoda zapisuje tylko listy otwartych dokumentów. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) jest odpowiedzialny za zapisywanie dokumentów, samodzielnie.

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

Ustawia czas między cykle zapisywania w milisekundach.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*nAutosaveInterval*<br/>
[in] Nowy interwał automatycznego zapisu w milisekundach.

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

Ustawia katalog, w którym są przechowywane pliki automatycznie zapisany.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strAutosavePath*|[in] Ścieżka, w którym są przechowywane pliki zapisywania.|

### <a name="remarks"></a>Uwagi

Zmienianie katalogu zapisywania nie przenosi aktualnie automatycznie zapisany plików.

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

Ustawia identyfikator unikatowy ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler`.

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*strRestartIdentifier*|[in] Unikatowy identyfikator dla Menedżera ponownego uruchamiania.|

### <a name="remarks"></a>Uwagi

Menedżera ponownego uruchamiania rejestruje informacje o otwartych dokumentów w rejestrze. Te informacje są przechowywane z identyfikatorem unikatowy ponowne uruchomienie jako klucz. Ponieważ identyfikator ponowne uruchomienie jest unikatowy dla każdego wystąpienia aplikacji, wielu wystąpień aplikacji może zostać nieoczekiwanie i Menedżera ponownego uruchamiania może odzyskać każdego z nich.

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Zestawy czy `CDataRecoveryHandler` zapisuje informacje o otwartym dokumencie w rejestrze Windows podczas bieżącego cyklu bezczynności.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bSaveOnIdle*|[in] Wartość TRUE, aby zapisać informacji o dokumencie podczas bieżącego cyklu bezczynności; Wartość FAŁSZ, aby nie wykonywać zapisywania.|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

Określa, czy poprzednie zakończenia aplikacji zostało spowodowane przez Menedżera ponownego uruchamiania.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*bShutdownByRestartManager*|[in] Wartość TRUE, aby wskazać, że Menedżera ponownego uruchamiania leży aplikacji zakończyć działanie; Wartość FALSE, aby wskazać, że aplikacja zakończyła pracę z innego powodu.|

### <a name="remarks"></a>Uwagi

Struktura działa inaczej w zależności od tego, czy poprzednie zakończenia był nieoczekiwany lub czy został on zainicjowany przez Menedżera ponownego uruchamiania.

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

Aktualizuje informacje dla dokumentu, ponieważ jest on zapisany.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*pDocument*|[in] Wskaźnik do zapisanego dokumentu.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda usunięte automatycznie zapisany dokument i zaktualizować informacje na temat dokumentu; Wartość FALSE, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Po użytkownik zapisze dokument, aplikacja usuwa plik automatycznie zapisany, ponieważ nie jest już potrzebny. `UpdateDocumentInfo` Usuwa plik automatycznie zapisany przez wywołanie metody [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` następnie dodaje informacje z *pDocument* listę aktualnie otwartych dokumentów, ponieważ `RemoveDocumentInfo` usuwa te informacje, ale zapisanego dokumentu jest wciąż otwarty.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Instrukcje: dodawanie obsługi menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)

