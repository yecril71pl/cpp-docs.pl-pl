---
title: Tworzenie aktualizowalnego dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbf1c696a66024ec1d3b3022b1e3a03445e9b6fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043303"
---
# <a name="creating-an-updatable-provider"></a>Tworzenie aktualizowalnego dostawcy

Visual C++ obsługuje aktualizowalni dostawcy lub dostawców, które można zaktualizować (zapisu) do magazynu danych. W tym temacie omówiono sposób tworzenia aktualizowalni dostawcy za pomocą szablonów OLE DB.  
  
W tym temacie założono, że rozpoczynasz korzystanie z dostawcy wymagającego. Istnieją dwa kroki, aby tworzenie aktualizowalnego dostawcy. Należy najpierw zdecyduj, jak dostawca wprowadzi zmiany w przechowalni danych; ściślej mówiąc czy zmiany mają być wykonywane od razu lub odroczone do czasu wydano polecenie aktualizacji. Sekcja "[tworzenie aktualizowalnego dostawcy](#vchowmakingprovidersupdatable)" opisano zmiany i ustawienia, które należy wykonać w kodzie dostawcy.  
  
Następnie należy musi upewnij się, że Twój dostawca zawiera wszystkie funkcje do obsługi wszystkich danych, które użytkownik może zażądać jej. Jeśli użytkownik chce, aby zaktualizować magazynu danych, dostawca musi zawierać kod, który utrzymuje danych do magazynu danych. Na przykład może użyć biblioteki wykonawczej języka C lub MFC do wykonywania takich operacji na źródle danych. Sekcja "[zapisu w źródle danych](#vchowwritingtothedatasource)" opisano, jak zapisać źródła danych, postępowania z wartościami NULL i domyślne i Ustaw flagi kolumny.  
  
> [!NOTE]
>  [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) jest przykładem aktualizowalnego dostawcy. UpdatePV jest taka sama, jak MyProv, ale z obsługą nadaje się do aktualizacji.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Tworzenie aktualizowalnego dostawcy  

Klucz w tworzenie aktualizowalnego dostawcy jest zrozumienie, jakie operacje ma dostawcy do wykonania w magazynie danych oraz sposób dostawcy w celu przeprowadzania tych operacji. W szczególności poważnym problemem jest, czy aktualizacje do magazynu danych mają być wykonywane od razu lub odroczone (wsadowe) do momentu wydano polecenie aktualizacji.  
  
Należy najpierw określić, czy chcesz dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl` w swojej klasy zestawu wierszy. W zależności od tego, który z nich wybierzesz do zaimplementowania, będzie mieć wpływ na funkcjonalność z trzech metod: `SetData`, `InsertRows`, i `DeleteRows`.  
  
- Jeśli dziedziczą z [irowsetchangeimpl —](../../data/oledb/irowsetchangeimpl-class.md), wywoływanie tych trzech metod natychmiast zmienia się z magazynem danych.  
  
- Jeśli dziedziczą z [irowsetupdateimpl —](../../data/oledb/irowsetupdateimpl-class.md), metody Odrocz zmiany w magazynie danych, dopóki nie zostanie wywołana `Update`, `GetOriginalData`, lub `Undo`. Jeśli aktualizacja obejmuje kilka zmian, są wykonywane w trybie wsadowym (Zauważ, że przetwarzanie wsadowe zmiany można dodać pamięć znaczne obciążenie).  
  
Należy pamiętać, że `IRowsetUpdateImpl` pochodzi od klasy `IRowsetChangeImpl`. W efekcie `IRowsetUpdateImpl` zapewnia zmienić możliwości, a także możliwości usługi batch.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Do obsługi aktualizacji w dostawcy  
  
1. W klasie wierszy dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl`. Te klasy oferują interfejsy odpowiednie zmiany do magazynu danych:  
  
     **Dodawanie IRowsetChange**  
  
     Dodaj `IRowsetChangeImpl` na swój łańcuch dziedziczenia, za pomocą tego formularza:  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Również dodać `COM_INTERFACE_ENTRY(IRowsetChange)` do `BEGIN_COM_MAP` sekcji klasy zestawu wierszy.  
  
     **Dodawanie IRowsetUpdate**  
  
     Dodaj `IRowsetUpdate` na swój łańcuch dziedziczenia, za pomocą tego formularza:  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Należy usunąć `IRowsetChangeImpl` wiersz z swój łańcuch dziedziczenia. To jeden wyjątek od dyrektywy wcześniej wspomniano, musi zawierać kod `IRowsetChangeImpl`.  
  
1. Dodaj następujący element do mapy COM (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |W przypadku zastosowania|Dodaj do mapy COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
1. W poleceniu, Dodaj następujący element do mapy zestaw właściwości (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |W przypadku zastosowania|Dodaj do mapy zestaw właściwości|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
1. Na mapie zestaw właściwości należy także uwzględnić wszystkie z następujących ustawień, w jakiej występują poniżej:  
  
    ```cpp  
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
  
     Można znaleźć wartości użyte w tych wywołań makra, wyszukując w Atldb.h identyfikatory właściwości i wartości (jeśli Atldb.h różni się od dokumentacji online, Atldb.h zastępuje dokumentacji).  
  
    > [!NOTE]
    >  Wiele `VARIANT_FALSE` i `VARIANT_TRUE` ustawienia są wymagane przez Szablony OLE DB; specyfikacji OLE DB mówi ich odczytu/zapisu, ale szablony OLE DB może obsługiwać tylko jedną wartość.  
  
     **W przypadku zaimplementowania irowsetchangeimpl —**  
  
     W przypadku zaimplementowania `IRowsetChangeImpl`, należy ustawić następujące właściwości w dostawcy usługi. Te właściwości są używane głównie do żądania interfejsów za pośrednictwem `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Ustawienie tym automatycznie ustawia `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Maska bitowa określenie obsługiwanych metod na `IRowsetChange`: `SetData`, `DeleteRows`, lub `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: Konsument może wywołać `IRowsetChange::DeleteRows` lub `SetData` dla nowo wstawione wiersze.  
  
    - `DBPROP_IMMOBILEROWS`: Zestaw wierszy nie mogli zmienić kolejności wstawionych lub zaktualizowanych wierszy.  
  
     **W przypadku zaimplementowania irowsetupdateimpl —**  
  
     W przypadku zaimplementowania `IRowsetUpdateImpl`, należy ustawić następujące właściwości w dostawcy usługi dodatkowo z ustawieniem dla wszystkich właściwości `IRowsetChangeImpl` wymienionych powyżej:  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OWNUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OTHERINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_REMOVEDELETED`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Jeśli obsługujesz powiadomienia, może również być pewne inne właściwości, jak również; zobacz sekcję dotyczącą `IRowsetNotifyCP` dla tej listy.  
  
##  <a name="vchowwritingtothedatasource"></a> Zapisywanie do źródła danych  

Aby zapoznać się ze źródła danych, należy wywołać `Execute` funkcji. Aby zapisać źródła danych, należy wywołać `FlushData` funkcji. (W ogólnym sensie opróżnienie oznacza, że aby zapisać zmiany wprowadzone do tabeli lub indeksu na dysku).  

```cpp

FlushData(HROW, HACCESSOR);  

```

Dojście do wiersza (HROW) i argumenty uchwytu (HACCESSOR) dostępu umożliwiają określenie obszaru do zapisu. Zazwyczaj można napisać jedno pole danych w danym momencie.

`FlushData` Metoda zapisuje dane w formacie, w której została oryginalnie zapisane. Jeśli nie zastąpisz tej funkcji, Twój dostawca będzie działać prawidłowo, ale zmiany nie zostaną opróżnione do magazynu danych.

### <a name="when-to-flush"></a>Kiedy opróżniania

Szablony dostawców wywołać flushdata — zawsze wtedy, gdy dane muszą być zapisywane do magazynu danych; to zwykle (ale nie zawsze) występuje w wyniku wywołania do następujących funkcji:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (jeśli ma nowych danych do wstawienia w wierszu)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Jak to działa

Użytkownik wywołuje wymagającego opróżniania (na przykład aktualizacja), a to wywołanie jest przekazywane do dostawcy, który zawsze wykonuje następujące czynności:

- Wywołania `SetDBStatus` zawsze, gdy ma wartość stanu granicy.

- Sprawdza, czy kolumna flagi.

- Wywołania `IsUpdateAllowed`.

Te trzy kroki pomagają zapewnić bezpieczeństwo. Następnie wywołuje dostawcę `FlushData`.

### <a name="how-to-implement-flushdata"></a>Jak zaimplementować flushdata —

Aby zaimplementować `FlushData`, należy wziąć pod uwagę kilka kwestii:

Upewnienie się, że magazyn danych może obsługiwać zmiany.

Obsługa wartości NULL.

### <a name="handling-default-values"></a>Obsługa wartości domyślne.

Aby zaimplementować metodę flushdata —, należy:

- Przejdź do swojej klasy zestawu wierszy.

- W zestawie wierszy klasy umieść deklaracji:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)  
   {  
      // Insert your implementation here and return an HRESULT.  
   }  
   ```

- Udostępnia implementację `FlushData`.

Dobre implementacji flushdata — przechowuje tylko wiersze i kolumny, które rzeczywiście zostały zaktualizowane. Parametry HROW i HACCESSOR służy do określenia bieżącego wiersza i kolumny są przechowywane na potrzeby optymalizacji.

Zazwyczaj największe wyzwanie współpracuje z własny magazyn danych w trybie macierzystym. Jeśli to możliwe spróbuj:

- Zachowaj metody zapisu ze swoim magazynem danych jest tak proste, jak to możliwe.

- Obsługa wartości NULL (opcjonalne, ale zalecany).

- Obsługa wartości domyślne (opcjonalne, ale zalecany).

Najlepiej, aby zrobić jest rzeczywiste wartości określonej w magazynie danych o wartości NULL i domyślne wartości. Najlepiej umożliwiają ekstrapolację tych danych. Jeśli nie, zalecana jest nie akceptuje wartości NULL i domyślne.

W poniższym przykładzie przedstawiono sposób `FlushData` jest zaimplementowana w klasie RUpdateRowset w przykładzie UpdatePV (patrz Rowset.h w przykładowym kodzie):

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

W przypadku dostawcy do obsługi zmian, należy najpierw upewnij się, że magazyn danych (np. plik tekstowy lub plik wideo) oferuje pozwalające na wprowadzanie zmian w niej. Jeśli nie, należy utworzyć kod oddzielnie z projektu dostawcy.

### <a name="handling-null-data"></a>Obsługa danych o wartości NULL

Istnieje możliwość, że użytkownik końcowy będzie wysyłać dane o wartości NULL. Kiedy piszesz wartości NULL do pól w źródle danych, może być potencjalne problemy. Wyobraź sobie sporządzania zamówienia aplikację, która akceptuje wartości miasta i kodu pocztowego; można go zaakceptować jednego lub obu tych wartości, ale nie ani, ponieważ w takim przypadku dostarczania byłyby niemożliwe. W związku z tym musisz ograniczyć niektóre kombinacje wartości NULL w polach, które mają sens dla swojej aplikacji.

Jako deweloper dostawcy należy wziąć pod uwagę, jak będą przechowywane te dane, jak odczyta dane z magazynu danych i jak można określić, że do użytkownika. W szczególności należy rozważyć sposób zmiany stanu danych wierszy danych w źródle danych (na przykład DataStatus = NULL). Możesz zdecydować, jaka wartość do zwrócenia, gdy użytkownik uzyskuje dostęp do pola zawierającego wartość NULL.

Spójrz na kod w przykładzie UpdatePV; przykład ilustruje jak dostawca może obsłużyć danych o wartości NULL. W UpdatePV dostawca przechowuje dane o wartości NULL, pisząc ciąg "NULL" w magazynie danych. Podczas wczytywania danych o wartości NULL z magazynu danych, będzie widział te parametry, a następnie opróżnia bufor, tworząc pusty ciąg. Ma on także nadpisanie `IRowsetImpl::GetDBStatus` w której ta zwraca DBSTATUS_S_ISNULL, jeśli ta wartość danych jest pusta.

### <a name="marking-nullable-columns"></a>Oznaczanie kolumn dopuszczających wartości null

Jeśli również wdrożenia zestawów wierszy schematu (zobacz `IDBSchemaRowsetImpl`), w zestawie wierszy DBSCHEMA_COLUMNS (zwykle oznaczony w dostawcy za CxxxSchemaColSchemaRowset) należy określić implementacji, że kolumna jest dopuszczającego wartość null.

Należy również określić, że wszystkie kolumny dopuszczające wartość null, zawierają wartość DBCOLUMNFLAGS_ISNULLABLE w używanej wersji programu `GetColumnInfo`.

W implementacji szablonów OLE DB do oznaczania kolumny jako dopuszczającego wartość null, w przeciwnym przypadku dostawcę założono, że musi zawierać wartość i nie zezwala, aby wysłać go wartości null.

W poniższym przykładzie pokazano sposób, w jaki `CommonGetColInfo` funkcja jest zaimplementowana w CUpdateCommand (patrz UpProvRS.cpp) w UpdatePV. Należy zauważyć, jak kolumny to DBCOLUMNFLAGS_ISNULLABLE dla kolumny dopuszczające wartość null.

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

Podobnie jak w przypadku danych o wartości NULL, masz odpowiedzialność, aby poradzić sobie ze zmianą wartości domyślne.

Domyślne ustawienie flushdata — i wykonywania jest do zwrócenia S_OK. W związku z tym, jeśli nie zastąpisz tej funkcji, zmiany będą widoczne powiodła się (S_OK zostaną zwrócone), ale nie będą przesyłane do magazynu danych.

W przykładzie UpdatePV (w Rowset.h) `SetDBStatus` obsługiwała wartości domyślne w następujący sposób:

```cpp
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

### <a name="column-flags"></a>Kolumna flagi

Jeśli są używane wartości domyślne na kolumn należy ustawić go za pomocą metadanych w \<klasa dostawcy\>SchemaRowset klasy. Ustaw `m_bColumnHasDefault` = VARIANT_TRUE.

Masz również odpowiedzialny za można ustawić flagi kolumny, które są określone, że za pomocą DBCOLUMNFLAGS Typ wyliczany. Flagi kolumnie opisano charakterystyki kolumny.

Na przykład w `CUpdateSessionColSchemaRowset` klasy UpdatePV (w Session.h), pierwsza kolumna skonfigurowano w ten sposób:

```cpp
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

Ten kod określa, między innymi, że kolumna obsługuje wartości domyślnej 0, że jest zapisywalny, i że wszystkie dane w kolumnie mają tę samą długość. Jeśli chcesz, aby dane w kolumnie o zmiennej długości, nie ustawi tę flagę.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy OLE DB](creating-an-ole-db-provider.md)