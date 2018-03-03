---
title: Klasa CDataRecoveryHandler | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35ede62ddb5fcfbc32fec37322985d40fffbbe44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdatarecoveryhandler-class"></a>Klasa CDataRecoveryHandler
`CDataRecoveryHandler` Autosaves dokumenty i przywraca je, jeśli nieoczekiwanym zamknięciu aplikacji.  
  
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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Autosaves zarejestrowany każdego pliku `CDataRecoveryHandler` klasy.|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Autosaves określonego dokumentu.|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Dodaje dokumentu do listy otwartych dokumentów.|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Usuwa wszystkie bieżące pliki automatycznie zapisany.|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Usuwa określony automatycznie zapisany plik.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Generuje nazwę dla pliku autosave skojarzone z nazwą pliku dostarczony dokument.|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Zwraca przedział między próby automatycznego zapisywania.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Zwraca ścieżkę do plików automatycznie zapisany.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Pobiera nazwę dokumentu z `CDocument` obiektu.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Pobiera tytuł normalne dla określonego dokumentu.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Tworzy i zwraca tytuł dokumentu odzyskane.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Pobiera identyfikator unikatowy ponownego uruchomienia aplikacji.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Wskazuje, czy `CDataRecoveryHandler` wykonuje autosave na bieżącej pętli bezczynności.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Wskazuje, czy Menedżer ponownego uruchamiania spowodowany aplikacji zakończyć.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Inicjuje `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Dla każdego dokumentu, który wyświetla okno dialogowe użytkownikowi `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce, aby przywrócić automatycznie zapisany dokument.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Ładuje na liście otwartych dokumentów z rejestru.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Usuwa dostarczony dokument na liście otwartych dokumentów.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Otwiera wcześniej otwartych dokumentów.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Przywraca dokumenty automatycznie zapisany oparte na danych wejściowych użytkownika.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Zapisuje bieżącą listę otwarte dokumenty w rejestrze systemu Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Ustawia czas między cykle automatycznego zapisywania w milisekundach.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Ustawia katalog, w którym są przechowywane pliki automatycznie zapisany.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Ustawia identyfikator unikatowy ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Ustawia czy `CDataRecoveryHandler` zapisuje informacje otwartego dokumentu do rejestru systemu Windows podczas bieżącego cyklu bezczynności.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Określa, czy poprzednie zakończenia aplikacji został spowodowany przez Menedżer ponownego uruchamiania.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aktualizuje informacje dla dokumentu, ponieważ jest on zapisany.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Wskazuje, czy program obsługi odzyskiwania danych ponownie otwiera wcześniej otwartych dokumentów.|  
|m_bSaveDocumentInfoOnIdle|Wskazuje, czy autosaves obsługi odzyskiwania danych dokumentów na następny pętli bezczynności.|  
|m_bShutdownByRestartManager|Wskazuje, czy Menedżer ponownego uruchamiania powoduje, że aplikacja zakończyć.|  
|m_dwRestartManagerSupportFlags|Zawiera flagi wskazujące co obsługi Menedżera ponownego uruchomienia aplikacji.|  
|m_lstAutosavesToDelete|Lista plików automatycznie zapisany, które nie zostały usunięte, gdy oryginalne dokumenty zostały zamknięte. Po zamknięciu aplikacji, ponowne próby ponownego uruchomienia Menedżera usuwania plików.|  
|m_mapDocNameToAutosaveName|Mapa nazwy dokumentu na nazwy plików automatycznie zapisany.|  
|m_mapDocNameToDocumentPtr|Mapa nazwy dokumentu do [CDocument](../../mfc/reference/cdocument-class.md) wskaźników.|  
|m_mapDocNameToRestoreBool|Mapa nazwy dokumentu do parametrów typu Boolean, która wskazuje, czy mają zostać przywrócone automatycznie zapisany dokument.|  
|m_mapDocumentPtrToDocName|Mapa `CDocument` wskaźniki do nazwy dokumentu.|  
|m_mapDocumentPtrToDocTitle|Mapa `CDocument` wskaźniki do tytuły dokumentu. Te tytuły są używane do zapisywania plików.|  
|m_nAutosaveInterval|Czas w milisekundach między autosaves.|  
|m_nTimerID|Identyfikator czasomierza automatycznego zapisywania.|  
|m_strAutosavePath|Lokalizacja przechowywania dokumentów automatycznie zapisany.|  
|m_strRestartIdentifier|Reprezentacja ciągu identyfikatora GUID dla Menedżera ponownego uruchomienia.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer ponownego uruchamiania używa `CDataRecoveryHandler` klasę, aby zachować śledzić wszystkie otwarte dokumenty i automatycznego zapisywania ich w razie potrzeby. Aby włączyć automatyczne zapisywanie, należy użyć [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) metody. Określa, że ta metoda `CDataRecoveryHandler` podczas automatycznego zapisywania dalej pętli bezczynności. Ponowne uruchomienie Menedżera wywołań `SetSaveDocumentInfoOnIdle` podczas `CDataRecoveryHandler` należy wykonać automatycznego zapisywania.  
  
 Wszystkie metody `CDataRecoveryHandler` klasy są wirtualnego. Przesłaniaj metody tej klasy, aby utworzyć własną obsługi odzyskiwania danych niestandardowych. Jeśli nie możesz utworzyć własne obsługi odzyskiwania danych lub ponownie uruchom Menedżera nie utworzyć wystąpienia CDataRecoveryHandler. [Cwinapp — klasa](../../mfc/reference/cwinapp-class.md) tworzy `CDataRecoveryHandler` obiekt zgodnie z wymaganiami.  
  
 Przed użyciem `CDataRecoveryHandler` obiektu, należy wywołać [CDataRecoveryHandler::Initialize](#initialize).  
  
 Ponieważ `CDataRecoveryHandler` klasy jest ściśle połączony Menedżer ponownego uruchamiania `CDataRecoveryHandler` zależy od parametrów globalnych `m_dwRestartManagerSupportFlags`. Ten parametr określa, jakie uprawnienia ma Menedżer ponownego uruchamiania i jak współdziała z aplikacją. Aby dołączyć Menedżer ponownego uruchamiania do istniejącej aplikacji, musisz przypisać `m_dwRestartManagerSupportFlags` odpowiednią wartość w Konstruktorze głównej aplikacji. Aby uzyskać więcej informacji o sposobie użycia Menedżera ponownego uruchomienia, zobacz [porady: Dodawanie obsługi Menedżera ponownego uruchomienia](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Autosaves zarejestrowany każdego pliku `CDataRecoveryHandler` klasy.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `CDataRecoveryHandler` zapisane dokumenty; `FALSE` jeżeli każdy dokument nie został zapisany.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `TRUE` Jeśli nie ma żadnych dokumentów, które muszą zostać zapisane. Również zwraca `TRUE` bez zapisywania dokumentów, jeśli pobieranie `CWinApp` lub `CDocManager` dla aplikacja generuje błąd.  
  
 Aby użyć tej metody, albo `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` lub `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` musi być ustawiona w `m_dwRestartManagerSupportFlags`. Zobacz [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) Aby uzyskać więcej informacji.  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
 Autosaves określonego dokumentu.  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do `CDocument` do zapisania.|  
|[in]`bResetModifiedFlag`|`TRUE`oznacza to, że `CDataRecoveryHandler` uwzględnia `pDocument` ma być zmodyfikowana; `FALSE` wskazuje, że uwzględnia platformę `pDocument` być zmodyfikowane. W sekcji uwag więcej informacji na temat wpływu tej flagi.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli odpowiednie flagi są ustawiane i `pDocument` jest prawidłową `CDocument` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Każdy `CDocument` obiekt ma flagę wskazującą, czy został zmieniony od ostatniego zapisu. Użyj [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) do ustalenia stanu tej flagi. Jeśli `CDocument` nie został zmieniony od ostatniego zapisu `AutosaveDocumentInfo` usuwa pliki automatycznie zapisany dokument. Jeśli dokument został zmieniony od ostatniego zapisu, jego zamknięciem monituje użytkownika o zapisanie dokumentu przed zamknięciem.  
  
> [!NOTE]
>  Przy użyciu `bResetModifiedFlag` można zmienić stanu dokumentu na niezmodyfikowanego może spowodować utratę niezapisanych danych użytkownika. Platformę uwzględnia dokumentu nie mają być modyfikowane, jego zamknięciem nie Monituj użytkownika, aby zapisać.  
  
 Ta metoda zgłasza wyjątek z [ASSERT](diagnostic-services.md#assert) makro Jeśli `pDocument` nie jest prawidłową `CDocument` obiektu.  
  
 Aby użyć tej metody, albo `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` lub `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` musi być ustawiona w `m_dwRestartManagerSupportFlags`.   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
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
|[in]`dwRestartManagerSupportFlags`|Wskazuje, które opcje Menedżer ponownego uruchamiania są obsługiwane.|  
|[in]`nAutosaveInterval`|Czas między autosaves. Ten parametr jest w milisekundach.|  
  
### <a name="remarks"></a>Uwagi  
 Struktura MFC automatycznie tworzy `CDataRecoveryHandler` obiektu dla aplikacji, korzystając z **nowy projekt** kreatora. O ile nie są Dostosowywanie zachowania danych odzyskiwania lub Menedżer ponownego uruchamiania, nie należy tworzyć `CDataRecoveryHandler` obiektu.  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 Dodaje dokumentu do listy otwartych dokumentów.  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do `CDocument`. Ta metoda tworzy informacji dokumentu dla tego `CDocument`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda sprawdza, czy `pDocument` znajduje się już na liście dokumentów przed dodaniem dokumentu. Jeśli `pDocument` znajduje się już na liście, ta metoda usuwa plik zapisana automatycznie skojarzone z `pDocument`.  
  
 Aby użyć tej metody, albo `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` lub `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` musi być ustawiona w `m_dwRestartManagerSupportFlags`. 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Usuwa wszystkie bieżące pliki automatycznie zapisany.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zawsze zwraca `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 Usuwa określony automatycznie zapisany plik.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`strAutosavedFile`|Ciąg, który zawiera nazwę pliku automatycznie zapisany.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zawsze zwracany `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda nie może usunąć pliku automatycznie zapisany, zapisuje nazwę pliku na liście. Destruktor dla elementu `CDataRecoveryHandler` próbuje usunąć każdego pliku automatycznie zapisany określone na tej liście.  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 Generuje nazwę dla pliku autosave skojarzone z nazwą pliku dostarczony dokument.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strDocumentName`  
 Ciąg zawierający nazwę dokumentu. `GenerateAutosaveFileName`używa tej nazwy dokumentu, aby wygenerować odpowiadającą jej nazwą pliku automatycznego zapisywania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa pliku autosave generowane na podstawie `strDocumentName`.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa każdego dokumentu ma mapowanie jeden do jednego z nazwą pliku automatycznego zapisywania.  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 Zwraca przedział między próby automatycznego zapisywania.  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba milisekund między autosave próbach.  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 Zwraca ścieżkę do plików automatycznie zapisany.  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Lokalizacja przechowywania dokumentów automatycznie zapisany.  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 Pobiera nazwę dokumentu z `CDocument` obiektu.  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do `CDocument`. `GetDocumentListName`pobiera nazwę dokumentu z tego `CDocument`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa dokumentu z `pDocument`.  
  
### <a name="remarks"></a>Uwagi  
 `CDataRecoveryHandler` Używa nazwy dokumentu jako klucz w `m_mapDocNameToAutosaveName`, `m_mapDocNameToDocumentPtr`, i `m_mapDocNameToRestoreBool`. Włącz te parametru `CDataRecoveryHandler` do monitorowania `CDocument` obiektów, nazwa pliku automatycznego zapisywania i ustawienia automatycznego zapisywania.  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 Pobiera tytuł normalne dla określonego dokumentu.  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do `CDocument`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Normalne tytuł dla określonego dokumentu.  
  
### <a name="remarks"></a>Uwagi  
 Normalne tytuł dokumentu jest zwykle nazwa pliku dokumentu bez ścieżki. To jest tytuł w **nazwę pliku** pole **Zapisz jako** okno dialogowe.  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 Tworzy i zwraca tytuł dokumentu odzyskane.  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`strDocumentTitle`  
 Normalne tytuł dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tytuł dokumentu odzyskane.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie odzyskane tytuł dokumentu jest normalne tytuł z **[odzyskać]** dołączone do niego. Odzyskane tytuł jest wyświetlany użytkownikowi po `CDataRecoveryHandler` wysyła zapytanie do użytkownika, aby przywrócić dokumenty automatycznie zapisany.  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 Pobiera identyfikator unikatowy ponownego uruchomienia aplikacji.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator unikatowy ponownego uruchomienia.  
  
### <a name="remarks"></a>Uwagi  
 Identyfikator ponowne uruchomienie jest unikatowy dla każdego wykonywania aplikacji.  
  
 `CDataRecoveryHandler` Informacje są przechowywane w rejestrze o aktualnie otwarte dokumenty. Po ponownym uruchomieniu Menedżera kończy pracę aplikacji i ponownie go uruchamia, podaje identyfikator ponownego uruchomienia, aby `CDataRecoveryHandler`. `CDataRecoveryHandler` Używa identyfikatora ponownego uruchomienia można pobrać listy wcześniej otwartych dokumentów. Dzięki temu `CDataRecoveryHandler` próby Znajdowanie i przywracanie plików automatycznie zapisany.  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Wskazuje, czy `CDataRecoveryHandler` wykonuje autosave na bieżącej pętli bezczynności.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Wskazuje `CDataRecoveryHandler` autosaves na bieżącej pętli bezczynności. `FALSE` wskazuje nie.  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 Wskazuje, czy Menedżer ponownego uruchamiania spowodowany aplikacji zakończyć.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Wskazuje, że Menedżer ponownego uruchamiania spowodował aplikacji zakończyć; `FALSE` wskazuje on nie.  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 Inicjuje `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli inicjowanie zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Proces inicjowania ładuje ścieżki do przechowywania plików autosave z rejestru. Jeśli `Initialize` metody nie można odnaleźć tego katalogu lub jeśli ścieżka nie jest `NULL`, `Initialize` nie powiedzie się i zwraca `FALSE`.  
  
 Użyj [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) zmienić ścieżkę autosave po inicjuje aplikacji `CDataRecoveryHandler`.  
  
 `Initialize` Metody również uruchamia czasomierz do monitorowania podczas następnego automatycznego zapisywania. Użyj [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) Aby zmienić interwał automatycznego zapisywania po inicjuje aplikacji `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Dla każdego dokumentu, który wyświetla okno dialogowe użytkownikowi `CDataRecoveryHandler` automatycznie zapisany. Okno dialogowe określa, czy użytkownik chce, aby przywrócić automatycznie zapisany dokument.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja jest Unicode, ta metoda Wyświetla [obiektu CTaskDialog](../../mfc/reference/ctaskdialog-class.md) dla użytkownika. W przeciwnym razie używa platformę [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) kwerenda użytkownika.  
  
 Po `QueryRestoreAutosavedDocuments` gromadzi wszystkie odpowiedzi od użytkownika, zapisuje informacje w zmiennej członkowskiej `m_mapDocNameToRestoreBool`. Ta metoda nie powoduje przywrócenia dokumenty automatycznie zapisany.  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 Ładuje na liście otwartych dokumentów z rejestru.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`oznacza to, że `ReadOpenDocumentList` załadować danych dla co najmniej jeden dokument z rejestru; `FALSE` wskazuje brak informacji dokument został załadowany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ładuje informacje Otwórz dokument z rejestru i zapisuje go w zmiennej członkowskiej `m_mapDocNameToAutosaveName`.  
  
 Po `ReadOpenDocumentList` ładuje wszystkie dane, informacje na temat dokumentu usuwa z rejestru.  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 Usuwa dostarczony dokument na liście otwartych dokumentów.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do dokumentu, aby usunąć.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli `pDocument` został usunięty z listy; `FALSE` Jeśli wystąpił błąd.  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik zamyka dokument, platformę używa tej metody, aby usunąć go z listy otwartych dokumentów.  
  
 Jeśli `RemoveDocumentInfo` nie można odnaleźć `pDocument` na liście otwartych dokumentów nie działa i zwraca `TRUE`.  
  
 Aby użyć tej metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musi być ustawiona w `m_dwRestartManagerSupportFlags`.   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 Otwiera wcześniej otwartych dokumentów.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli co najmniej jeden dokument został otwarty; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda powoduje otwarcie ostatniego zapisu wcześniej otwartych dokumentów. Jeśli dokument nie został zapisany lub zapisana, automatycznie `ReopenPreviousDocuments` otwiera pusty dokument oparty na szablonie dla danego typu pliku.  
  
 Aby użyć tej metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musi być ustawiona w `m_dwRestartManagerSupportFlags`. Jeśli ten parametr nie jest ustawiona, `ReopenPreviousDocuments` nie robi nic i zwraca `FALSE`.  
  
 Jeśli nie ma żadnych dokumentów przechowywanych w listy wcześniej otwartych dokumentów `ReopenPreviousDocuments` nie robi nic i zwraca `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 Przywraca dokumenty automatycznie zapisany oparte na danych wejściowych użytkownika.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda przywraca pomyślnie dokumentów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) ustalenie dokumenty, które użytkownik chce przywracania. Jeśli użytkownik zdecyduje się nie można przywrócić automatycznie zapisany dokument, `RestoreAutosavedDocuments` usuwa plik automatycznego zapisywania. W przeciwnym razie `RestoreAutosavedDocuments` zastępuje wersja zapisana automatycznie otwartego dokumentu.  
  
 Aby użyć tej metody, albo `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` lub `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` musi być ustawiona w `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Zapisuje bieżącą listę otwarte dokumenty w rejestrze systemu Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli nie ma żadnych otwartych dokumentów, aby zapisać lub zostały pomyślnie zapisane. `FALSE`Jeśli dokumentu nie można zapisać w rejestrze, ale nie zostały zapisane, ponieważ wystąpił błąd.  
  
### <a name="remarks"></a>Uwagi  
 Ponowne uruchomienie Menedżera wywołań `SaveOpenDocumentList` gdy aplikacja jest nieoczekiwanie zamykany lub gdy opuszcza do uaktualnienia. Po ponownym uruchomieniu aplikacji używa [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) można pobrać listy otwartych dokumentów.  
  
 Taka metoda ogranicza listy otwartych dokumentów. Metoda [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) jest odpowiedzialny za zapisywanie dokumentów, samodzielnie.  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 Ustawia czas między cykle automatycznego zapisywania w milisekundach.  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nAutosaveInterval`  
 Nowy autosave interwał w milisekundach.  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 Ustawia katalog, w którym są przechowywane pliki automatycznie zapisany.  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`strAutosavePath`|Ścieżka miejsca przechowywania plików automatycznego zapisywania.|  
  
### <a name="remarks"></a>Uwagi  
 Zmiana automatycznego zapisywania katalogu nie przenosi obecnie automatycznie zapisany plików.  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 Ustawia identyfikator unikatowy ponownego uruchomienia dla tego wystąpienia `CDataRecoveryHandler`.  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`strRestartIdentifier`|Unikatowy identyfikator dla Menedżera ponownego uruchomienia.|  
  
### <a name="remarks"></a>Uwagi  
 Menedżer ponownego uruchamiania rejestruje informacje o otwarte dokumenty w rejestrze. Te informacje są przechowywane w identyfikatorze unikatowy ponownego uruchomienia jako klucz. Ponowne uruchomienie identyfikator jest unikatowy dla każdego wystąpienia aplikacji, wiele wystąpień aplikacji może zostać nieoczekiwanie i Menedżer ponownego uruchamiania można odzyskać każdego z nich.  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 Ustawia czy `CDataRecoveryHandler` zapisuje informacje otwartego dokumentu do rejestru systemu Windows podczas bieżącego cyklu bezczynności.  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`bSaveOnIdle`|`TRUE`Aby zapisać informacje dokumentu w trakcie bieżącego cyklu bezczynności; `FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 Określa, czy poprzednie zakończenia aplikacji został spowodowany przez Menedżer ponownego uruchamiania.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`bShutdownByRestartManager`|`TRUE`Aby wskazać, że Menedżer ponownego uruchamiania spowodowane aplikacji zakończyć; `FALSE` aby wskazać, że aplikacja zakończył działanie z innego powodu.|  
  
### <a name="remarks"></a>Uwagi  
 Platformę zachowuje się inaczej w zależności od czy zakończenia poprzedniej był nieoczekiwany lub czy został zainicjowany przez Menedżera ponownego uruchomienia.  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 Aktualizuje informacje dla dokumentu, ponieważ jest on zapisany.  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|[in]`pDocument`|Wskaźnik do zapisanego dokumentu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli ta metoda usunięte automatycznie zapisany dokument i zaktualizowane informacje dokument; `FALSE` Jeśli wystąpił błąd.  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik zapisuje dokument, aplikacji usuwa plik automatycznie zapisany, ponieważ nie jest już potrzebne. `UpdateDocumentInfo`Usuwa plik automatycznie zapisany przez wywołanie metody [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`następnie dodaje informacje z `pDocument` do listy aktualnie otwarte dokumenty, ponieważ `RemoveDocumentInfo` usuwa te informacje, ale zapisanego dokumentu jest wciąż otwarty.  
  
 Aby użyć tej metody `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` musi być ustawiona w `m_dwRestartManagerSupportFlags`.   
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Instrukcje: dodawanie obsługi menedżera ponownego uruchamiania](../../mfc/how-to-add-restart-manager-support.md)

