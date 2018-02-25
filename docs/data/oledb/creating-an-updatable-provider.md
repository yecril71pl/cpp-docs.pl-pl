---
title: Tworzenie aktualizowalnego dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e243c7198b479bed226d4bd035297a12fc877de6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="creating-an-updatable-provider"></a>Tworzenie aktualizowalnego dostawcy
Visual C++ obsługuje aktualizowalni dostawcy lub dostawców, które mogą aktualizować (zapisu) magazynu danych. W tym temacie omówiono tworzenie aktualizowalnego dostawcy za pomocą szablonów OLE DB.  
  
 W tym temacie założono, czy rozpoczynasz pracę możliwego dostawcę. Istnieją dwa kroki, aby tworzenie aktualizowalnego dostawcy. Najpierw należy zdecydować, jak dostawca wprowadzi zmiany w magazynie danych; w szczególności zmiany realizowane natychmiast są czy odroczone do czasu wydano polecenie aktualizacji. Sekcja "[tworzenie aktualizowalnego dostawcy](#vchowmakingprovidersupdatable)" w tym artykule opisano zmiany i ustawienia, które należy wykonać w kodzie dostawcy.  
  
 Następnie należy upewnij się, że dostawca zawiera wszystkie funkcje do obsługi wszystkich danych, które użytkownik może zażądać go. Jeśli użytkownik chce zaktualizować źródła danych, dostawca musi zawierać kod, który będzie się powtarzał danych w magazynie danych. Na przykład można użyć biblioteki wykonawczej języka C lub MFC do wykonywania takich operacji na źródle danych. Sekcji "[zapisu w źródle danych](#vchowwritingtothedatasource)" opisano sposób zapisu w źródle danych, postępowania w przypadku **NULL** wartości domyślne i Ustaw flagi kolumny.  
  
> [!NOTE]
>  UpdatePV jest przykładem aktualizowalnego dostawcy. UpdatePV jest taka sama, jak MyProv, ale obsługa nadaje się do aktualizacji.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Tworzenie aktualizowalnego dostawcy  
 Klucz do tworzenie aktualizowalnego dostawcy jest zrozumienie operacje, jakie ma dostawcy do wykonywania w magazynie danych oraz sposób dostawcy do wykonywania tych operacji. W szczególności głównych problem jest czy aktualizacji do magazynu danych mają być wykonywane bezpośrednio lub odroczone (umieścić w zadaniu wsadowym) do momentu wydano polecenie aktualizacji.  
  
 Najpierw należy podjąć decyzję o dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl` w swojej klasy zestawu wierszy. W zależności od tego, która z tych wybierzesz do wdrożenia, będzie mieć wpływ na funkcjonalność z trzech metod: `SetData`, **InsertRows**, i `DeleteRows`.  
  
-   Jeśli dziedziczą z [irowsetchangeimpl —](../../data/oledb/irowsetchangeimpl-class.md), natychmiast wywoływania tych trzech metod zmiany do magazynu danych.  
  
-   Jeśli dziedziczą z [irowsetupdateimpl —](../../data/oledb/irowsetupdateimpl-class.md), metody mają być odroczone zmiany do magazynu danych do czasu wywołania **aktualizacji**, `GetOriginalData`, lub **Cofnij**. Jeśli aktualizacja obejmuje kilka zmian, są one wykonywane w trybie wsadowym (Zauważ, że przetwarzanie wsadowe zmiany można dodać pamięć znaczne).  
  
 Należy pamiętać, że `IRowsetUpdateImpl` pochodną `IRowsetChangeImpl`. W związku z tym `IRowsetUpdateImpl` pozwala zmienić możliwości oraz możliwości partii.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Do obsługi aktualizacji w dostawcy  
  
1.  W klasie wierszy dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl`. Te klasy zawierają odpowiednich interfejsów zmiany do magazynu danych:  
  
     **Dodawanie IRowsetChange**  
  
     Dodaj `IRowsetChangeImpl` Twojego łańcucha dziedziczenia za pomocą tego formularza:  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Dodaj również `COM_INTERFACE_ENTRY(IRowsetChange)` do `BEGIN_COM_MAP` części klasy zestawu wierszy.  
  
     **Dodawanie IRowsetUpdate**  
  
     Dodaj `IRowsetUpdate` Twojego łańcucha dziedziczenia za pomocą tego formularza:  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Należy usunąć `IRowsetChangeImpl` wiersz z Twojej łańcuch dziedziczenia. Ten jeden wyjątek dyrektywy wcześniej wymienionymi musi zawierać kod `IRowsetChangeImpl`.  
  
2.  Dodaj następującą wartość do mapy COM (**BEGIN_COM_MAP... END_COM_MAP**):  
  
    |W przypadku zastosowania|Dodaj na mapie modelu COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  W poleceniu, dodaj następującą wartość do mapy zestaw właściwości (**BEGIN_PROPSET_MAP... END_PROPSET_MAP**):  
  
    |W przypadku zastosowania|Dodaj do mapy zestaw właściwości|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  Na mapie zestaw właściwości należy także uwzględnić wszystkie następujące ustawienia pojawiających się poniżej:  
  
    ```  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     Można znaleźć wartości używanym w wywołaniach tych makr, przeszukując Atldb.h dla właściwości identyfikatorów i wartości (jeśli Atldb.h różni się od dokumentację w trybie online, Atldb.h zastępuje dokumentacji).  
  
    > [!NOTE]
    >  Duża liczba **wartość VARIANT_FALSE** i `VARIANT_TRUE` ustawienia są wymagane przez Szablony OLE DB; ze specyfikacją OLE DB mówi ich odczytu/zapisu, ale szablony OLE DB może obsługiwać tylko jedną wartość.  
  
     **W przypadku zastosowania irowsetchangeimpl —**  
  
     W przypadku zastosowania `IRowsetChangeImpl`, należy ustawić następujące właściwości w dostawcy. Te właściwości są używane głównie do żądania interfejsy za pośrednictwem **ICommandProperties::SetProperties**.  
  
    -   `DBPROP_IRowsetChange`: Ustawienie tym automatycznie ustawia **DBPROP_IRowsetChange**.  
  
    -   `DBPROP_UPDATABILITY`Maska bitowa określania obsługiwanych metod na `IRowsetChange`: `SetData`, `DeleteRows`, lub `InsertRow`.  
  
    -   `DBPROP_CHANGEINSERTEDROWS`: Konsument można wywołać **IRowsetChange::DeleteRows** lub `SetData` nowo wstawionych wierszy.  
  
    -   `DBPROP_IMMOBILEROWS`: Zestaw wierszy nie spowoduje zmiany kolejności wierszy wstawionych lub zaktualizowanych.  
  
     **W przypadku zastosowania irowsetupdateimpl —**  
  
     W przypadku zastosowania `IRowsetUpdateImpl`, należy ustawić następujące właściwości na dostawcy, oprócz z ustawieniem dla wszystkich właściwości `IRowsetChangeImpl` wymienionego powyżej:  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    -   `DBPROP_OWNUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    -   `DBPROP_OTHERINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    -   `DBPROP_OTHERUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    -   `DBPROP_REMOVEDELETED`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Jeśli obsługuje powiadomienia, można również zainstalować niektórych także inne właściwości; zobacz sekcję dotyczącą `IRowsetNotifyCP` dla tej listy.  
  
     Na przykład jak właściwości są ustawione, zobacz dla właściwości ustawić mapy **CUpdateCommand** (w Rowset.h) w [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
##  <a name="vchowwritingtothedatasource"></a> Zapisywanie do źródła danych  
 Aby odczytać ze źródła danych, należy wywołać **Execute** funkcji. Aby zapisać źródła danych, należy wywołać `FlushData` funkcji. (W tym sensie ogólne opróżnić sposób, aby zapisać zmiany wprowadzone w tabeli lub indeksu na dysku).  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 Dojście do wiersza (*HROW*) i dojście metody dostępu (*HACCESSOR*) argumenty umożliwiają określenie obszaru do zapisu. Zazwyczaj zapisu jedno pole danych w czasie.  
  
 `FlushData` Metody zapisuje dane w formacie, w którym była oryginalnie przechowywana. Jeśli ta funkcja nie jest zastąpienie, dostawcy usługi będą działać poprawnie, ale zmiany nie zostaną opróżnione do magazynu danych.  
  
### <a name="when-to-flush"></a>Kiedy opróżnić  
 Wywołanie szablony dostawcy `FlushData` zawsze, gdy dane muszą być zapisywane w magazynie danych; to zwykle (ale nie zawsze) występuje w wyniku wywołania następujące funkcje:  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** (jeśli istnieje nowych danych do wstawienia w wierszu)  
  
-   **IRowsetUpdate::Update**  
  
### <a name="how-it-works"></a>Jak to działa  
 Konsument nawiązuje połączenie, która wymaga opróżnienie (takich jak **aktualizacji**), a to wywołanie jest przekazywana do dostawcy, który zawsze wykonuje następujące czynności:  
  
-   Wywołania `SetDBStatus` zawsze, gdy ma wartość stanu, powiązany (zobacz *OLE DB programistów odwołanie*, rozdział 6, *części danych: Status*).  
  
-   Sprawdza, czy flagi kolumn.  
  
-   Wywołania `IsUpdateAllowed`.  
  
 Te trzy kroki szczebli do zapewnienia bezpieczeństwa. Następnie wywołania dostawcy `FlushData`.  
  
### <a name="how-to-implement-flushdata"></a>Jak zaimplementować FlushData  
 Aby zaimplementować `FlushData`, należy wziąć pod uwagę kilka kwestii:  
  
-   Upewnienie się, że magazyn danych można obsługiwać zmiany.  
  
-   Obsługa **NULL** wartości.  
  
-   Obsługa wartości domyślne.  
  
 Aby zaimplementować własne `FlushData` metody, konieczne jest:  
  
-   Przejdź do własnej klasy zestawu wierszy.  
  
-   W zestawie wierszy klasy umieścić deklaracji:  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   Udostępnij implementację `FlushData`.  
  
 Implementacja dobrej `FlushData` przechowuje tylko wiersze i kolumny, które faktycznie zostały zaktualizowane. Można użyć *HROW* i *HACCESSOR* parametrów do określenia bieżącego wiersza i kolumny są przechowywane na potrzeby optymalizacji.  
  
 Zazwyczaj największych wyzwanie pracuje magazynie danych w trybie macierzystym. Jeśli to możliwe spróbuj:  
  
-   Zachowaj metody zapisywanie w magazynie danych, wystarczy.  
  
-   Obsługa **NULL** wartości (opcjonalne, ale zaleca).  
  
-   Obsługa wartości domyślnej (opcjonalne, ale zaleca).  
  
 Najlepiej, aby zrobić ma rzeczywiste wartości określonej w magazynie danych dla **NULL** i wartości domyślnych. Najlepiej umożliwiają ekstrapolację tych danych. Jeśli nie, zaleca się nie mógł **NULL** i wartości domyślnych.  
  
 W poniższym przykładzie przedstawiono sposób `FlushData` jest zaimplementowana w `RUpdateRowset` klasy w [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) próbki (zobacz Rowset.h w przykładowym kodzie):  
  
```cpp
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
...  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");  
  
    USES_CONVERSION;  
    enum {  
        sizeOfString = 256,  
        sizeOfFileName = MAX_PATH  
    };  
    FILE*    pFile = NULL;  
    TCHAR    szString[sizeOfString];  
    TCHAR    szFile[sizeOfFileName];  
    errcode  err = 0;  
  
    ObjectLock lock(this);  
  
    // From a filename, passed in as a command text,   
    // scan the file placing data in the data array.  
    if (m_strCommandText == (BSTR)NULL)  
    {  
        ATLTRACE( "RRowsetUpdate::FlushData -- "  
                  "No filename specified\n");  
        return E_FAIL;  
    }  
  
    // Open the file  
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));  
    if ((szFile[0] == _T('\0')) ||   
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))  
    {  
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");  
        return DB_E_NOTABLE;  
    }  
  
    // Iterate through the row data and store it.  
    for (long l=0; l<m_rgRowData.GetSize(); l++)  
    {  
        CAgentMan am = m_rgRowData[l];  
  
        _putw((int)am.dwFixed, pFile);  
  
        if (_tcscmp(&am.szCommand[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szText[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
  
        if (_tcscmp(&am.szText2[0], _T("")) != 0)  
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);  
        else  
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));  
        _fputts(szString, pFile);  
    }  
  
    if (fflush(pFile) == EOF || fclose(pFile) == EOF)  
    {  
        ATLTRACE("RRowsetUpdate::FlushData -- "  
                 "Couldn't flush or close file\n");  
    }  
  
    return S_OK;  
}  
```  
  
### <a name="handling-changes"></a>Obsługa zmiany  
 W przypadku dostawcy obsługiwać zmiany, należy najpierw upewnij się, że urządzenia umożliwiające można wprowadzać zmiany w nim ma magazynie danych (na przykład pliku tekstowego lub pliku wideo). Jeśli nie, należy utworzyć ten kod oddzielnie z projektu dostawcy.  
  
### <a name="handling-null-data"></a>Obsługa danych o wartości NULL  
 Istnieje możliwość, że użytkownik końcowy będzie wysyłać **NULL** danych. Podczas zapisu **NULL** wartości pola w źródle danych, może być potencjalne problemy. Wyobraź sobie kolejność podejmowania aplikację, która akceptuje wartości miejscowość i kod pocztowy; może go zaakceptować jednego lub obu tych wartości, ale nie ani, ponieważ w takim przypadku dostarczania byłoby niemożliwe. W związku z tym musi obejmować niektórych kombinacji **NULL** wartości w polach odpowiednich dla aplikacji.  
  
 Jako deweloper dostawcy należy wziąć pod uwagę, jak będą przechowywane te dane, jak będzie odczytywania danych z magazynu danych i jak można określić, że użytkownikowi. W szczególności należy rozważyć sposób zmiany stanu danych wierszy danych w źródle danych (na przykład DataStatus = **NULL**). Zdecyduj, jaka wartość do zwrócenia, gdy klient uzyskuje dostęp do pole zawierające **NULL** wartość.  
  
 Sprawdź kod w [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) przykładowa; przedstawiono, jak można obsługiwać dostawcę **NULL** danych. W UpdatePV, dostawca przechowuje **NULL** danych, wpisując ciąg "NULL" w magazynie danych. Gdy odczytuje **NULL** magazyn danych z danych, widzi tego ciągu, a następnie opróżnia bufor, tworzenie **NULL** ciągu. Ma również zastępująca `IRowsetImpl::GetDBStatus` , w którym zwraca **DBSTATUS_S_ISNULL** Jeśli tę wartość w danych jest pusta.  
  
### <a name="marking-nullable-columns"></a>Oznaczenie kolumny dopuszczające wartość null  
 Jeśli także implementować zestawów wierszy schematu (zobacz `IDBSchemaRowsetImpl`), implementacji należy określić w **DBSCHEMA_COLUMNS** zestawu wierszy (zwykle oznaczony u dostawcy przez **C***xxx*** SchemaColSchemaRowset**) czy kolumna jest null.  
  
 Należy również określić, że wszystkie wartości null w kolumnach **DBCOLUMNFLAGS_ISNULLABLE** wartość w używanej wersji `GetColumnInfo`.  
  
 W implementacji szablonów OLE DB Jeśli nie można oznaczyć kolumny jako wartości null, dostawca założono, że musi zawierać wartość i nie zezwala na konsumentów do wysyłania wartości null.  
  
 W poniższym przykładzie przedstawiono sposób **CommonGetColInfo** funkcji jest zaimplementowana w **CUpdateCommand** (zobacz UpProvRS.cpp) w UpdatePV. Należy zwrócić uwagę, jak ma to kolumny **DBCOLUMNFLAGS_ISNULLABLE** dla kolumn o wartości null.  
  
```cpp
/////////////////////////////////////////////////////////////////////////////  
// CUpdateCommand (in UpProvRS.cpp)  
  
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)  
{  
    static ATLCOLUMNINFO _rgColumns[6];  
    ULONG ulCols = 0;  
  
    if (bBookmark)  
    {  
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,  
                            sizeof(DWORD), DBTYPE_BYTES,  
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,  
                            DBCOLUMNFLAGS_ISBOOKMARK)  
        ulCols++;  
    }  
  
    // Next set the other columns up.  
    // Add a fixed length entry for OLE DB conformance testing purposes  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,  
                        10, 255, GUID_NULL, CAgentMan, dwFixed,   
                        DBCOLUMNFLAGS_WRITE |   
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)  
    ulCols++;  
  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szCommand,  
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,   
                        255, 255, GUID_NULL, CAgentMan, szText,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szCommand2,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,  
                        255, 255, GUID_NULL, CAgentMan, szText2,   
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)  
    ulCols++;  
  
    if (pcCols != NULL)  
    {  
        *pcCols = ulCols;  
    }  
  
    return _rgColumns;  
}  
```  
  
### <a name="default-values"></a>Wartości domyślne  
 Jak **NULL** danych, ma obowiązek postępowania w przypadku zmiany wartości domyślne.  
  
 Domyślne ustawienie `FlushData` i **Execute** powinien zwrócić `S_OK`. W związku z tym, jeśli ta funkcja nie jest zastąpienie, zmiany są wyświetlane powiodła się (`S_OK` zostanie zwrócony), ale nie będą przesyłane do magazynu danych.  
  
 W [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) przykładowa (w Rowset.h) `SetDBStatus` obsługiwała wartości domyślne w następujący sposób:  
  
```  
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,  
                            ATLCOLUMNINFO* pColInfo)  
{  
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);  
  
    void* pData = NULL;  
    char* pDefaultData = NULL;  
    DWORD* pFixedData = NULL;  
  
    switch (*pdbStatus)  
    {  
        case DBSTATUS_S_DEFAULT:  
            pData = (void*)&m_rgRowData[pRow->m_iRowset];  
            if (pColInfo->wType == DBTYPE_STR)  
            {  
                pDefaultData = (char*)pData + pColInfo->cbOffset;  
                strcpy_s(pDefaultData, "Default");  
            }  
            else  
            {  
                pFixedData = (DWORD*)((BYTE*)pData +   
                                          pColInfo->cbOffset);  
                *pFixedData = 0;  
                return S_OK;  
            }  
            break;  
        case DBSTATUS_S_ISNULL:  
        default:  
            break;  
    }  
    return S_OK;  
}  
```  
  
### <a name="column-flags"></a>Flagi kolumn  
 Jeśli są używane wartości domyślne na kolumn należy ustawić go przy użyciu metadanych w  **\< ***klasa dostawcy***> SchemaRowset** klasy. Ustaw *m_bColumnHasDefault* = `VARIANT_TRUE`.  
  
 Masz również odpowiedzialność można ustawić flagi kolumny, które są określone za pomocą **DBCOLUMNFLAGS** typ wyliczeniowy. Flagi kolumn opisano charakterystyki kolumny.  
  
 Na przykład w `CUpdateSessionColSchemaRowset` klasy w [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) (Session.h), pierwsza kolumna skonfigurowano w ten sposób:  
  
```  
// Set up column 1  
trData[0].m_ulOrdinalPosition = 1;  
trData[0].m_bIsNullable = VARIANT_FALSE;  
trData[0].m_bColumnHasDefault = VARIANT_TRUE;  
trData[0].m_nDataType = DBTYPE_UI4;  
trData[0].m_nNumericPrecision = 10;  
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |  
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;  
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));  

m_rgRowData.Add(trData[0]);  
```  
  
 Ten kod określa, między innymi, że kolumna obsługuje wartości domyślnej 0, aby było ono zapisywalny, i że wszystkie dane w kolumnie mają taką samą długość. Jeśli chcesz, aby dane w kolumnie o zmiennej długości, nie będzie ustawienia tej flagi.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie dostawcy OLE DB](../../data/oledb/creating-an-ole-db-provider.md)