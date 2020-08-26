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
ms.openlocfilehash: 4bb4d4ddf291cb1efc01b887c54a6573c52df8dc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842926"
---
# <a name="cdatarecoveryhandler-class"></a>Klasa CDataRecoveryHandler

`CDataRecoveryHandler`Automatycznie zapisuje dokumenty i przywraca je w przypadku nieoczekiwanego zamknięcia aplikacji.

## <a name="syntax"></a>Składnia

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Konstruuje `CDataRecoveryHandler` obiekt.|

### <a name="methods"></a>Metody

|Nazwa|Opis|
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Automatycznie zapisuje każdy plik zarejestrowany w `CDataRecoveryHandler` klasie.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Automatycznie zapisuje określony dokument.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Dodaje dokument do listy otwartych dokumentów.|
|[CDataRecoveryHandler::D eleteAllAutosavedFiles](#deleteallautosavedfiles)|Usuwa wszystkie bieżące automatycznie zapisane pliki.|
|[CDataRecoveryHandler::D eleteAutosavedFile](#deleteautosavedfile)|Usuwa określony automatycznie zapisany plik.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje nazwę pliku Autozapisu skojarzonego z podaną nazwą pliku dokumentu.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Zwraca interwał między próbami automatycznego zapisywania.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Zwraca ścieżkę do automatycznie zapisywanych plików.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Pobiera nazwę dokumentu z `CDocument` obiektu.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Pobiera normalny tytuł określonego dokumentu.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Tworzy i zwraca tytuł odzyskiwanego dokumentu.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Pobiera unikatowy identyfikator ponownego uruchomienia aplikacji.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Wskazuje, czy `CDataRecoveryHandler` wykonuje Autozapis w bieżącej pętli bezczynności.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Wskazuje, czy Menedżer ponownego uruchamiania spowodował zakończenie działania aplikacji.|
|[CDataRecoveryHandler:: Initialize](#initialize)|Inicjuje `CDataRecoveryHandler` .|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Wyświetla okno dialogowe dla każdego dokumentu, który został `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce przywrócić automatycznie zapisany dokument.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Ładuje listę otwartych dokumentów z rejestru.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Usuwa podany dokument z listy otwartych dokumentów.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Otwiera wcześniej otwarte dokumenty.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Przywraca automatycznie zapisane dokumenty na podstawie danych wprowadzonych przez użytkownika.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Zapisuje bieżącą listę otwartych dokumentów w rejestrze systemu Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Ustawia czas między cyklami Autozapisu w milisekundach.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Ustawia katalog, w którym są przechowywane pliki automatycznie zapisane.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Ustawia unikatowy identyfikator ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler` .|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Określa, czy `CDataRecoveryHandler` zapisuje informacje o otwartym dokumencie w rejestrze systemu Windows w trakcie bieżącego cyklu bezczynności.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Określa, czy poprzednie wyjście aplikacji zostało spowodowane przez Menedżera ponownego uruchamiania.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informacje dla dokumentu, ponieważ Zapisano go przez użytkownika.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|-|-|
|m_bRestoringPreviousOpenDocs|Wskazuje, czy program obsługi odzyskiwania danych otwiera wcześniej otwarte dokumenty.|
|m_bSaveDocumentInfoOnIdle|Wskazuje, czy program obsługi odzyskiwania danych automatycznie zapisuje dokumenty w następnej pętli bezczynności.|
|m_bShutdownByRestartManager|Wskazuje, czy Menedżer ponownego uruchamiania powoduje zakończenie działania aplikacji.|
|m_dwRestartManagerSupportFlags|Flagi wskazujące wsparcie dla aplikacji przez Menedżera ponownego uruchamiania.|
|m_lstAutosavesToDelete|Lista automatycznie zapisywanych plików, które nie zostały usunięte, gdy oryginalne dokumenty zostały zamknięte. Po zakończeniu działania aplikacji Menedżer ponownego uruchamiania ponawia próbę usunięcia plików.|
|m_mapDocNameToAutosaveName|Mapa nazw dokumentów dla automatycznie zapisywanych nazw plików.|
|m_mapDocNameToDocumentPtr|Mapa nazw dokumentów dla wskaźników [CDocument](../../mfc/reference/cdocument-class.md) .|
|m_mapDocNameToRestoreBool|Mapa nazw dokumentów dla parametru Boolean wskazująca, czy ma zostać przywrócony automatycznie zapisany dokument.|
|m_mapDocumentPtrToDocName|Mapa `CDocument` wskaźników do nazw dokumentów.|
|m_mapDocumentPtrToDocTitle|Mapa `CDocument` wskaźników do tytułów dokumentów. Te tytuły są używane do zapisywania plików.|
|m_nAutosaveInterval|Czas (w milisekundach) między autozapisywaniem.|
|m_nTimerID|Identyfikator czasomierza automatycznego zapisywania.|
|m_strAutosavePath|Lokalizacja, w której są przechowywane dokumenty automatycznie zapisane.|
|m_strRestartIdentifier|Ciąg reprezentujący identyfikator GUID Menedżera ponownego uruchamiania.|

## <a name="remarks"></a>Uwagi

Menedżer ponownego uruchamiania używa `CDataRecoveryHandler` klasy do śledzenia wszystkich otwartych dokumentów i zapisywania ich w razie potrzeby. Aby włączyć funkcję Autozapisu, użyj metody [CDataRecoveryHandler:: SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) . Ta metoda kieruje `CDataRecoveryHandler` do wykonania Autozapisu w następnej pętli bezczynności. Menedżer ponownego uruchamiania wywołuje, `SetSaveDocumentInfoOnIdle` kiedy `CDataRecoveryHandler` powinien wykonać Autozapisywanie.

Wszystkie metody `CDataRecoveryHandler` klasy są wirtualne. Zastąp metody w tej klasie, aby utworzyć własną niestandardową procedurę obsługi odzyskiwania danych. Jeśli nie utworzysz własnego programu obsługi odzyskiwania danych lub Menedżera ponownego uruchamiania, nie uruchamiaj wystąpienia CDataRecoveryHandler. [Klasa CWinApp](../../mfc/reference/cwinapp-class.md) tworzy `CDataRecoveryHandler` obiekt, ponieważ jest on wymagany.

Aby można było użyć `CDataRecoveryHandler` obiektu, należy wywołać [CDataRecoveryHandler:: Initialize](#initialize).

Ponieważ `CDataRecoveryHandler` Klasa jest ściśle połączona z menedżerem ponownego uruchamiania, `CDataRecoveryHandler` zależy od parametru globalnego `m_dwRestartManagerSupportFlags` . Ten parametr określa, jakie uprawnienia ma Menedżer ponownego uruchomienia i w jaki sposób współdziała z Twoją aplikacją. Aby włączyć Menedżera ponownego uruchamiania do istniejącej aplikacji, należy przypisać `m_dwRestartManagerSupportFlags` odpowiednią wartość w konstruktorze głównej aplikacji. Aby uzyskać więcej informacji o sposobach korzystania z Menedżera ponownego uruchamiania, zobacz [How to: Add restart Manager support](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdatarecovery. h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a> CDataRecoveryHandler::AutosaveAllDocumentInfo

Automatycznie zapisuje każdy plik zarejestrowany w `CDataRecoveryHandler` klasie.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli `CDataRecoveryHandler` Zapisano wszystkie dokumenty; FAŁSZ, jeśli żaden dokument nie został zapisany.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość TRUE, jeśli nie ma dokumentów, które muszą zostać zapisane. Zwraca również wartość TRUE bez zapisywania jakichkolwiek dokumentów, jeśli pobieranie `CWinApp` lub `CDocManager` dla aplikacji generuje błąd.

Aby można było użyć tej metody, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL muszą być ustawione w `m_dwRestartManagerSupportFlags` . Aby uzyskać więcej informacji, zobacz [jak: Dodawanie obsługi Menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a> CDataRecoveryHandler::AutosaveDocumentInfo

Automatycznie zapisuje określony dokument.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do `CDocument` zapisania.

*bResetModifiedFlag*\
podczas Wartość TRUE wskazuje, `CDataRecoveryHandler` że *pDocument* ma być modyfikowany; Wartość FALSE wskazuje, że struktura traktuje *pDocument* w niemodyfikowane. Zobacz sekcję Uwagi, aby uzyskać więcej informacji na temat efektu tej flagi.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli są ustawione odpowiednie flagi, a *pDocument* jest prawidłowym `CDocument` obiektem.

### <a name="remarks"></a>Uwagi

Każdy `CDocument` obiekt ma flagę wskazującą, czy został zmieniony od ostatniego zapisu. Użyj [CDocument:: IsModified](../../mfc/reference/cdocument-class.md#ismodified) , aby określić stan tej flagi. Jeśli plik `CDocument` nie został zmieniony od ostatniego zapisu, program `AutosaveDocumentInfo` usunie wszystkie automatycznie zapisane pliki dla tego dokumentu. Jeśli dokument został zmieniony od czasu ostatniego zapisu, zamknięcie go wyświetli użytkownikowi komunikat, aby zapisać dokument przed zamknięciem.

> [!NOTE]
> Zmiana stanu dokumentu na Unmodified przy użyciu *bResetModifiedFlag* może spowodować utratę niezapisanych danych przez użytkownika. Jeśli struktura uzna dokument za niemodyfikowany, jego zamknięcie nie monituje użytkownika o zapisanie.

Ta metoda zgłasza wyjątek za pomocą makra [Assert](diagnostic-services.md#assert) , jeśli *pDocument* nie jest prawidłowym `CDocument` obiektem.

Aby można było użyć tej metody, należy ustawić AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a> CDataRecoveryHandler::CDataRecoveryHandler

Konstruuje `CDataRecoveryHandler` obiekt.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*dwRestartManagerSupportFlags*\
podczas Wskazuje, które opcje Menedżera ponownego uruchamiania są obsługiwane.

*nAutosaveInterval*\
podczas Czas między autozapisywaniem. Ten parametr jest w milisekundach.

### <a name="remarks"></a>Uwagi

Struktura MFC automatycznie tworzy `CDataRecoveryHandler` obiekt dla aplikacji podczas korzystania z kreatora **nowego projektu** . Jeśli nie dostosowano zachowania odzyskiwania danych lub Menedżera ponownego uruchamiania, nie należy tworzyć `CDataRecoveryHandler` obiektu.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a> CDataRecoveryHandler::CreateDocumentInfo

Dodaje dokument do listy otwartych dokumentów.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do `CDocument` . Ta metoda tworzy informacje o dokumencie `CDocument` .

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda sprawdza, czy *pDocument* znajduje się już na liście dokumentów przed dodaniem dokumentu. Jeśli *pDocument* znajduje się już na liście, ta metoda usuwa automatycznie zapisany plik skojarzony z *pDocument*.

Aby można było użyć tej metody, należy ustawić AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART lub AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a> CDataRecoveryHandler::D eleteAllAutosavedFiles

Usuwa wszystkie bieżące automatycznie zapisane pliki.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a> CDataRecoveryHandler::D eleteAutosavedFile

Usuwa określony automatycznie zapisany plik.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parametry

*strAutosavedFile*\
podczas Ciąg, który zawiera nazwę pliku, który jest automatycznie zapisany.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda nie może usunąć automatycznie zapisanego pliku, zapisze nazwę pliku na liście. Destruktor `CDataRecoveryHandler` próbuje usunąć każdy automatycznie zapisany plik określony na tej liście.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a> CDataRecoveryHandler::GenerateAutosaveFileName

Generuje nazwę pliku Autozapisu skojarzonego z podaną nazwą pliku dokumentu.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parametry

*strDocumentName*<br/>
podczas Ciąg, który zawiera nazwę dokumentu. `GenerateAutosaveFileName` używa tej nazwy dokumentu do wygenerowania odpowiedniej nazwy pliku Autozapisu.

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku Autozapisu wygenerowana z *strDocumentName*.

### <a name="remarks"></a>Uwagi

Każda nazwa dokumentu ma mapowanie jeden do jednego z nazwą pliku automatycznego zapisywania.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a> CDataRecoveryHandler::GetAutosaveInterval

Zwraca interwał między próbami automatycznego zapisywania.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba milisekund między kolejnymi próbami automatycznego zapisywania.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a> CDataRecoveryHandler::GetAutosavePath

Zwraca ścieżkę do automatycznie zapisywanych plików.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Lokalizacja, w której są przechowywane dokumenty automatycznie zapisane.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a> CDataRecoveryHandler::GetDocumentListName

Pobiera nazwę dokumentu z `CDocument` obiektu.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do `CDocument` . `GetDocumentListName` Pobiera nazwę dokumentu z tej `CDocument` .

### <a name="return-value"></a>Wartość zwracana

Nazwa dokumentu z *pDocument*.

### <a name="remarks"></a>Uwagi

`CDataRecoveryHandler`Używa nazwy dokumentu jako klucza w *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*i *m_mapDocNameToRestoreBool*. Ten parametr umożliwia `CDataRecoveryHandler` monitorowanie `CDocument` obiektów, nazwy pliku Autozapisu oraz ustawień Autozapisu.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a> CDataRecoveryHandler::GetNormalDocumentTitle

Pobiera normalny tytuł określonego dokumentu.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do `CDocument` .

### <a name="return-value"></a>Wartość zwracana

Normalny tytuł określonego dokumentu.

### <a name="remarks"></a>Uwagi

Normalny tytuł dokumentu jest zwykle nazwą pliku dokumentu bez ścieżki. Jest to tytuł w polu **Nazwa pliku** w oknie dialogowym **Zapisywanie jako** .

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a> CDataRecoveryHandler::GetRecoveredDocumentTitle

Tworzy i zwraca tytuł odzyskiwanego dokumentu.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parametry

*strDocumentTitle*<br/>
podczas Normalny tytuł dokumentu.

### <a name="return-value"></a>Wartość zwracana

Tytuł odzyskanego dokumentu.

### <a name="remarks"></a>Uwagi

Domyślnie odzyskany tytuł dokumentu jest normalnym tytułem z dodanym **[odzyskanym]** . Odzyskany tytuł jest wyświetlany użytkownikowi, gdy `CDataRecoveryHandler` wysyła zapytanie do użytkownika o przywrócenie automatycznie zapisywanych dokumentów.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a> CDataRecoveryHandler::GetRestartIdentifier

Pobiera unikatowy identyfikator ponownego uruchomienia aplikacji.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator ponownego uruchomienia.

### <a name="remarks"></a>Uwagi

Identyfikator ponownego uruchomienia jest unikatowy dla każdego wykonywania aplikacji.

`CDataRecoveryHandler`Informacje są przechowywane w rejestrze o aktualnie otwartych dokumentach. Gdy Menedżer ponownego uruchamiania opuszcza aplikację i uruchomi ją ponownie, dostarcza identyfikator ponownego uruchomienia do `CDataRecoveryHandler` . Program `CDataRecoveryHandler` używa identyfikatora ponownego uruchomienia w celu pobrania listy wcześniej otwartych dokumentów. Dzięki temu `CDataRecoveryHandler` można spróbować znaleźć i przywrócić automatycznie zapisane pliki.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a> CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Wskazuje, czy `CDataRecoveryHandler` wykonuje Autozapis w bieżącej pętli bezczynności.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że `CDataRecoveryHandler` AutoSave w bieżącej pętli bezczynności Wartość FALSE wskazuje, że nie.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a> CDataRecoveryHandler::GetShutdownByRestartManager

Wskazuje, czy Menedżer ponownego uruchamiania spowodował zakończenie działania aplikacji.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że Menedżer ponownego uruchamiania spowodował zakończenie działania aplikacji; Wartość FALSE wskazuje, że nie.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a> CDataRecoveryHandler:: Initialize

Inicjuje `CDataRecoveryHandler` .

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Proces inicjalizacji ładuje ścieżkę do przechowywania plików zapisywania z rejestru. Jeśli `Initialize` Metoda nie może znaleźć tego katalogu lub ścieżka ma wartość null, `Initialize` kończy się niepowodzeniem i zwraca wartość `FALSE` .

Użyj [CDataRecoveryHandler:: SetAutosavePath](#setautosavepath) , aby zmienić ścieżkę Autozapisu po zainicjowaniu aplikacji przez aplikację `CDataRecoveryHandler` .

`Initialize`Metoda uruchamia również czasomierz, aby monitorować czas następnego automatycznego zapisywania. Użyj [CDataRecoveryHandler:: SetAutosaveInterval](#setautosaveinterval) , aby zmienić interwał automatycznego zapisywania po zainicjowaniu aplikacji przez aplikację `CDataRecoveryHandler` .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a> CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Wyświetla okno dialogowe dla każdego dokumentu, który został `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce przywrócić automatycznie zapisany dokument.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Uwagi

Jeśli aplikacja jest w formacie Unicode, ta metoda wyświetla [obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) dla użytkownika. W przeciwnym razie struktura używa [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) do wykonywania zapytań dotyczących użytkownika.

Po `QueryRestoreAutosavedDocuments` zebraniu wszystkich odpowiedzi od użytkownika przechowuje informacje w zmiennej składowej *m_mapDocNameToRestoreBool*. Ta metoda nie przywraca automatycznie zapisywanych dokumentów.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a> CDataRecoveryHandler::ReadOpenDocumentList

Ładuje listę otwartych dokumentów z rejestru.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE wskazuje, że `ReadOpenDocumentList` załadowano informacje dla co najmniej jednego dokumentu z rejestru; Wartość FALSE wskazuje, że nie załadowano informacji o dokumencie.

### <a name="remarks"></a>Uwagi

Ta funkcja ładuje informacje o otwartym dokumencie z rejestru i zapisuje je w zmiennej składowej *m_mapDocNameToAutosaveName*.

Po `ReadOpenDocumentList` załadowaniu wszystkich danych informacje o dokumencie są usuwane z rejestru.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a> CDataRecoveryHandler::RemoveDocumentInfo

Usuwa podany dokument z listy otwartych dokumentów.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do dokumentu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli *pDocument* został usunięty z listy; Wartość FALSE, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Gdy użytkownik zamknie dokument, struktura używa tej metody, aby usunąć ją z listy otwartych dokumentów.

Jeśli `RemoveDocumentInfo` nie można znaleźć *pDocument* na liście otwartych dokumentów, nic nie robi i zwraca wartość true.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES w *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a> CDataRecoveryHandler::ReopenPreviousDocuments

Otwiera wcześniej otwarte dokumenty.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Wartość zwracana

Prawda jeśli co najmniej jeden dokument został otwarty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda otwiera najnowszy zapis poprzednio otwartych dokumentów. Jeśli dokument nie został zapisany lub automatycznie zapisany, `ReopenPreviousDocuments` otwiera pusty dokument na podstawie szablonu dla tego typu pliku.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES w *m_dwRestartManagerSupportFlags*. Jeśli ten parametr nie jest ustawiony, `ReopenPreviousDocuments` nie robi niczego i zwraca wartość false.

Jeśli na liście wcześniej otwartych dokumentów nie ma żadnych dokumentów, `ReopenPreviousDocuments` nic nie robi i zwróci wartość false.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a> CDataRecoveryHandler::RestoreAutosavedDocuments

Przywraca automatycznie zapisane dokumenty na podstawie danych wprowadzonych przez użytkownika.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda pomyślnie przywróci dokumenty.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [CDataRecoveryHandler:: QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) w celu określenia dokumentów, które użytkownik chce przywrócić. Jeśli użytkownik zdecyduje się nie przywrócić automatycznie zapisanego dokumentu, program `RestoreAutosavedDocuments` usunie ten plik. W przeciwnym razie program `RestoreAutosavedDocuments` zastąpi otwarty dokument wersją zapisaną automatycznie.

Aby można było użyć tej metody, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES lub AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES muszą być ustawione w `m_dwRestartManagerSupportFlags` .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a> CDataRecoveryHandler::SaveOpenDocumentList

Zapisuje bieżącą listę otwartych dokumentów w rejestrze systemu Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli nie ma otwartych dokumentów do zapisania lub jeśli zostały one pomyślnie zapisane. FAŁSZ Jeśli istnieją dokumenty do zapisania w rejestrze, ale nie zostały zapisane, ponieważ wystąpił błąd.

### <a name="remarks"></a>Uwagi

Menedżer ponownych uruchomień wywołuje się, `SaveOpenDocumentList` gdy aplikacja jest nieoczekiwanie zamykana lub kończy się w przypadku uaktualnienia. Po ponownym uruchomieniu aplikacji używa [CDataRecoveryHandler:: ReadOpenDocumentList](#readopendocumentlist) w celu pobrania listy otwartych dokumentów.

Ta metoda zapisuje tylko listę otwartych dokumentów. Metoda [CDataRecoveryHandler:: AutosaveDocumentInfo](#autosavedocumentinfo) jest odpowiedzialna za zapisanie samych dokumentów.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a> CDataRecoveryHandler::SetAutosaveInterval

Ustawia czas między cyklami Autozapisu w milisekundach.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parametry

*nAutosaveInterval*<br/>
podczas Nowy interwał Autozapisu w milisekundach.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a> CDataRecoveryHandler::SetAutosavePath

Ustawia katalog, w którym są przechowywane pliki automatycznie zapisane.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parametry

*strAutosavePath*\
podczas Ścieżka, w której są przechowywane pliki Autozapisu.

### <a name="remarks"></a>Uwagi

Zmiana katalogu automatycznego zapisywania nie powoduje przeniesienia obecnie automatycznie zapisywanych plików.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a> CDataRecoveryHandler::SetRestartIdentifier

Ustawia unikatowy identyfikator ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler` .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parametry

*strRestartIdentifier*\
podczas Unikatowy identyfikator Menedżera ponownego uruchamiania.

### <a name="remarks"></a>Uwagi

Menedżer ponownego uruchamiania rejestruje informacje o otwartych dokumentach w rejestrze. Te informacje są przechowywane z unikatowym identyfikatorem ponownego uruchomienia jako klucz. Ponieważ identyfikator ponownego uruchomienia jest unikatowy dla każdego wystąpienia aplikacji, wiele wystąpień aplikacji może się nieoczekiwanie zakończyć, a Menedżer ponownego uruchamiania może odzyskać każdą z nich.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a> CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Określa, czy `CDataRecoveryHandler` zapisuje informacje o otwartym dokumencie w rejestrze systemu Windows w trakcie bieżącego cyklu bezczynności.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parametry

*bSaveOnIdle*\
podczas Wartość TRUE, aby zapisać informacje o dokumencie podczas bieżącego cyklu bezczynności; Wartość FALSE, aby nie można było wykonać zapisywania.

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a> CDataRecoveryHandler::SetShutdownByRestartManager

Określa, czy poprzednie wyjście aplikacji zostało spowodowane przez Menedżera ponownego uruchamiania.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parametry

*bShutdownByRestartManager*\
podczas Wartość TRUE oznacza, że Menedżer ponownego uruchamiania spowodował zakończenie działania aplikacji; Wartość FALSE, aby wskazać, że aplikacja zakończyła się z innego powodu.

### <a name="remarks"></a>Uwagi

Struktura działa inaczej w zależności od tego, czy poprzednie zakończenie było nieoczekiwane, czy też zostało zainicjowane przez Menedżera ponownego uruchamiania.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a> CDataRecoveryHandler::UpdateDocumentInfo

Aktualizuje informacje dla dokumentu, ponieważ Zapisano go przez użytkownika.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parametry

*pDocument*\
podczas Wskaźnik do zapisanego dokumentu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda usunęła automatycznie zapisany dokument i zaktualizował informacje o dokumencie; Wartość FALSE, jeśli wystąpił błąd.

### <a name="remarks"></a>Uwagi

Gdy użytkownik zapisuje dokument, aplikacja usuwa automatycznie zapisany plik, ponieważ nie jest już potrzebne. `UpdateDocumentInfo` usuwa automatycznie zapisany plik przez wywołanie [CDataRecoveryHandler:: RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` następnie dodaje informacje z *pDocument* do listy obecnie otwartych dokumentów, ponieważ usuwa te `RemoveDocumentInfo` informacje, ale zapisany dokument jest nadal otwarty.

Aby użyć tej metody, należy ustawić AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES w *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Zobacz też

[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Instrukcje: Dodawanie obsługi Menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)
