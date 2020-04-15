---
title: Tworzenie aktualizowalnego dostawcy
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365556"
---
# <a name="creating-an-updatable-provider"></a>Tworzenie aktualizowalnego dostawcy

Visual C++ obsługuje aktualizowanych dostawców lub dostawców, którzy mogą aktualizować (zapisywać do) magazynu danych. W tym temacie omówiono sposób tworzenia dostawców, które można aktualizować przy użyciu szablonów OLE DB.

W tym temacie przyjęto założenie, że zaczynasz od wykonalnego dostawcy. Istnieją dwa kroki do tworzenia dostawcy można aktualizować. Najpierw należy zdecydować, w jaki sposób dostawca będzie wprowadzać zmiany w magazynie danych; w szczególności, czy zmiany mają być wykonywane natychmiast lub odroczone do czasu wydania polecenia aktualizacji. W sekcji["Dokonywanie dostawców można aktualizować](#vchowmakingprovidersupdatable)" opisano zmiany i ustawienia, które należy wykonać w kodzie dostawcy.

Następnie należy upewnić się, że dostawca zawiera wszystkie funkcje do obsługi wszystko, co konsument może zażądać od niego. Jeśli konsument chce zaktualizować magazyn danych, dostawca musi zawierać kod, który utrzymuje dane do magazynu danych. Na przykład można użyć biblioteki czasu wykonywania języka C lub MFC do wykonywania takich operacji w źródle danych. W sekcji["Zapisywanie do źródła danych"](#vchowwritingtothedatasource)opisano sposób zapisu w źródle danych, radzenia sobie z wartościami NULL i wartościami domyślnymi oraz ustawiania flag kolumn.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) jest przykładem dostawcy można aktualizować. UpdatePV jest taka sama jak MyProv, ale z obsługą aktualizacji.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Aktualizowanie dostawców

Kluczem do dokonania dostawcy można aktualizować jest zrozumienie, jakie operacje mają być wykonywane przez dostawcę w magazynie danych i jak dostawca ma wykonywać te operacje. W szczególności głównym problemem jest to, czy aktualizacje magazynu danych mają być wykonywane natychmiast lub odroczone (wsadowe) do czasu wydania polecenia aktualizacji.

Najpierw należy zdecydować, czy `IRowsetChangeImpl` `IRowsetUpdateImpl` dziedziczyć z lub w klasie zestawu wierszy. W zależności od tego, które z nich zdecydujesz się wdrożyć, `InsertRows`funkcjonalność `DeleteRows`trzech metod będzie miała wpływ: `SetData`, , i .

- Jeśli dziedziczysz z [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), wywołanie tych trzech metod natychmiast zmienia magazyn danych.

- Jeśli dziedziczysz po [IRowsetUpdateImpl,](../../data/oledb/irowsetupdateimpl-class.md)metody odroczyć zmiany `Update`do `GetOriginalData`magazynu `Undo`danych, dopóki nie wywołasz , lub . Jeśli aktualizacja obejmuje kilka zmian, są one wykonywane w trybie wsadowym (należy pamiętać, że zmiany przetwarzania wsadowego można dodać znaczne obciążenie pamięci).

Należy `IRowsetUpdateImpl` zauważyć, `IRowsetChangeImpl`że pochodzi od . W `IRowsetUpdateImpl` związku z tym daje możliwość zmiany plus możliwości partii.

### <a name="to-support-updatability-in-your-provider"></a>Aby wspierać możliwość aktualizacji u dostawcy

1. W klasie zestawu wierszy `IRowsetChangeImpl` `IRowsetUpdateImpl`dziedzicz po lub . Te klasy zapewniają odpowiednie interfejsy do zmiany magazynu danych:

   **Dodawanie irowsetchange**

   Dodaj `IRowsetChangeImpl` do łańcucha dziedziczenia za pomocą tego formularza:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Dodaj `COM_INTERFACE_ENTRY(IRowsetChange)` również `BEGIN_COM_MAP` do sekcji w klasie zestawu wierszy.

   **Dodawanie irowsetupdate**

   Dodaj `IRowsetUpdate` do łańcucha dziedziczenia za pomocą tego formularza:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Należy usunąć `IRowsetChangeImpl` wiersz z łańcucha dziedziczenia. Ten jeden wyjątek od dyrektywy wcześniej wymienione `IRowsetChangeImpl`musi zawierać kod dla .

1. Dodaj do mapy COM`BEGIN_COM_MAP ... END_COM_MAP`następujące elementy ( ):

   |  Jeśli zaimplementujesz   |           Dodaj do mapy COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Jeśli zaimplementujesz | Dodaj do mapy zestawu właściwości |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. W poleceniu dodaj następujące elementy do`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`mapy zestawu właściwości ( ):

   |  Jeśli zaimplementujesz   |                                             Dodaj do mapy zestawu właściwości                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. Na mapie zestawu właściwości należy również uwzględnić wszystkie następujące ustawienia, które pojawiają się poniżej:

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

   Wartości używane w tych wywołaniach makrami można znaleźć, patrząc w obszarze Atldb.h dla identyfikatorów i wartości właściwości (jeśli atldb.h różni się od dokumentacji online, Atldb.h zastępuje dokumentację).

   > [!NOTE]
   > Wiele `VARIANT_FALSE` ustawień `VARIANT_TRUE` i są wymagane przez szablony OLE DB; specyfikacja OLE DB mówi, że mogą być odczytywane/zapisywane, ale szablony OLE DB mogą obsługiwać tylko jedną wartość.

   **Jeśli zaimplementujesz IRowsetChangeImpl**

   Jeśli zaimplementujesz, `IRowsetChangeImpl`należy ustawić następujące właściwości dla dostawcy. Właściwości te są używane głównie do `ICommandProperties::SetProperties`żądania interfejsów za pośrednictwem .

   - `DBPROP_IRowsetChange`: Ustawienie tego `DBPROP_IRowsetChange`automatycznie ustawia .

   - `DBPROP_UPDATABILITY`: Maska bitowa określająca obsługiwane `IRowsetChange` `SetData`metody `DeleteRows`na `InsertRow`: , , lub .

   - `DBPROP_CHANGEINSERTEDROWS`: Konsument `IRowsetChange::DeleteRows` może `SetData` dzwonić lub w przypadku nowo wstawionych wierszy.

   - `DBPROP_IMMOBILEROWS`: Zestaw wierszy nie zmieni kolejności wstawionych ani zaktualizowanych wierszy.

   **Jeśli zaimplementujesz IRowsetUpdateImpl**

   Jeśli zaimplementujesz `IRowsetUpdateImpl`, należy ustawić następujące właściwości na dostawcy, oprócz `IRowsetChangeImpl` ustawienia wszystkich właściwości dla wcześniej wymienionych:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Musi być READ_ONLY i VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: Musi być READ_ONLY i VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: Musi być READ_ONLY i VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Jeśli obsługujesz powiadomienia, możesz również mieć inne właściwości; zobacz sekcję `IRowsetNotifyCP` na tej liście.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Zapisywanie do źródła danych

Aby odczytać ze źródła danych, wywołaj `Execute` funkcję. Aby zapisać do źródła danych, wywołaj `FlushData` funkcję. (W sensie ogólnym flush oznacza zapisanie modyfikacji wprowadzonych w tabeli lub indeksie na dysku).

```cpp
FlushData(HROW, HACCESSOR);
```

Dojścia wiersza (HROW) i akcesor dojścia (HACCESSOR) argumenty pozwalają określić region do zapisu. Zazwyczaj można zapisać pojedyncze pole danych w danym momencie.

Metoda `FlushData` zapisuje dane w formacie, w którym został pierwotnie przechowywany. Jeśli ta funkcja nie zostanie zastąpiona, dostawca będzie działać poprawnie, ale zmiany nie zostaną opróżnione do magazynu danych.

### <a name="when-to-flush"></a>Kiedy opróżnić

Szablony dostawcy wywołać FlushData zawsze, gdy dane muszą być zapisywane w magazynie danych; zwykle (ale nie zawsze) występuje w wyniku wywołania następujących funkcji:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`(jeśli w wierszu są nowe dane do wstawienia)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Jak to działa

Konsument wykonuje wywołanie, które wymaga flush (takich jak Update) i to wywołanie jest przekazywane do dostawcy, który zawsze wykonuje następujące czynności:

- Wywołania `SetDBStatus` za każdym razem, gdy masz powiązaną wartość stanu.

- Sprawdza flagi kolumn.

- Połączenia `IsUpdateAllowed`.

Te trzy kroki pomagają zapewnić bezpieczeństwo. Następnie dostawca `FlushData`dzwoni .

### <a name="how-to-implement-flushdata"></a>Jak zaimplementować FlushData

Aby `FlushData`zaimplementować , należy wziąć pod uwagę kilka kwestii:

Upewniając się, że magazyn danych może obsługiwać zmiany.

Obsługa wartości NULL.

### <a name="handling-default-values"></a>Obsługa wartości domyślnych.

Aby zaimplementować własną `FlushData` metodę, musisz:

- Przejdź do klasy zestawu wierszy.

- W rowset klasy umieścić deklarację:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Zapewnienie wdrożenia `FlushData`pliku .

Dobra implementacja `FlushData` przechowuje tylko wiersze i kolumny, które są faktycznie aktualizowane. Za pomocą parametrów HROW i HACCESSOR można określić bieżący wiersz i kolumnę przechowywaną w celu optymalizacji.

Zazwyczaj największym wyzwaniem jest praca z własnym macierzystym magazynem danych. Jeśli to możliwe, spróbuj:

- Utrzymuj sposób zapisu w magazynie danych tak proste, jak to możliwe.

- Obsługa wartości NULL (opcjonalne, ale zalecane).

- Obsługa wartości domyślnych (opcjonalne, ale zalecane).

Najlepszą rzeczą do zrobienia jest mieć rzeczywiste określone wartości w magazynie danych dla wartości NULL i wartości domyślnych. Najlepiej jest, jeśli można ekstrapolować te dane. Jeśli nie, zaleca się, aby nie zezwalać na wartości NULL i wartości domyślne.

Poniższy przykład `FlushData` pokazuje, jak `RUpdateRowset` jest implementowany w klasie w `UpdatePV` próbce (zobacz Rowset.h w przykładowym kodzie):

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

### <a name="handling-changes"></a>Obsługa zmian

Aby dostawca mógł obsługiwać zmiany, należy najpierw upewnić się, że magazyn danych (na przykład plik tekstowy lub plik wideo) ma funkcje umożliwiające wprowadzanie na nim zmian. Jeśli tak nie jest, należy utworzyć ten kod oddzielnie od projektu dostawcy.

### <a name="handling-null-data"></a>Obsługa danych NULL

Możliwe, że użytkownik końcowy wyśle dane NULL. Podczas pisania wartości NULL do pól w źródle danych, mogą wystąpić potencjalne problemy. Wyobraź sobie aplikację do składania zamówień, która akceptuje wartości dla miasta i kodu pocztowego; może przyjąć jedną lub obie wartości, ale nie, ponieważ w takim przypadku dostawa byłaby niemożliwa. W związku z tym należy ograniczyć niektóre kombinacje wartości NULL w polach, które mają sens dla aplikacji.

Jako deweloper dostawcy należy wziąć pod uwagę, jak będzie przechowywać te dane, jak będzie odczytywać te dane z magazynu danych i jak określić, że do użytkownika. W szczególności należy rozważyć, jak zmienić stan danych zestawu wierszy danych w źródle danych (na przykład DataStatus = NULL). Użytkownik decyduje, jaką wartość zwrócić, gdy konsument uzyskuje dostęp do pola zawierającego wartość NULL.

Spójrz na kod w przykładzie UpdatePV; ilustruje, jak dostawca może obsługiwać dane NULL. W updatePV dostawca przechowuje dane NULL, zapisując ciąg "NULL" w magazynie danych. Podczas odczytywania danych NULL z magazynu danych, widzi ten ciąg, a następnie opróżnia bufor, tworząc ciąg NULL. Ma również zastąpienie, `IRowsetImpl::GetDBStatus` w którym zwraca DBSTATUS_S_ISNULL, jeśli ta wartość danych jest pusta.

### <a name="marking-nullable-columns"></a>Oznaczanie kolumn nullable

Jeśli również implementuje zestawy wierszy `IDBSchemaRowsetImpl`schematu (patrz ), implementacja powinna określić w DBSCHEMA_COLUMNS zestawu wierszy (zwykle oznaczone w dostawcy przez CxxxSchemaColSchemaRowset), że kolumna jest nullable.

Należy również określić, że wszystkie kolumny z dopuszczalnie do `GetColumnInfo`wartości null zawierają wartość DBCOLUMNFLAGS_ISNULLABLE w wersji programu .

W implementacji szablonów ole db, jeśli nie można oznaczyć kolumn jako nullable, dostawca zakłada, że muszą one zawierać wartość i nie pozwoli konsumentowi wysłać jej wartości null.

Poniższy przykład pokazuje, jak `CommonGetColInfo` funkcja jest implementowana w CUpdateCommand (zobacz UpProvRS.cpp) w UpdatePV. Należy zauważyć, jak kolumny mają ten DBCOLUMNFLAGS_ISNULLABLE dla kolumn nullable.

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

Podobnie jak w danych NULL, masz obowiązek radzić sobie ze zmianą wartości domyślnych.

Domyślnie `FlushData` i `Execute` jest powrót S_OK. W związku z tym jeśli nie zastąpisz tej funkcji, zmiany wydają się zakończyć się pomyślnie (S_OK zostaną zwrócone), ale nie zostaną przesłane do magazynu danych.

W `UpdatePV` próbce (w Rowset.h) `SetDBStatus` metoda obsługuje wartości domyślne w następujący sposób:

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

### <a name="column-flags"></a>Flagi kolumn

Jeśli obsługujesz wartości domyślne w kolumnach, należy ustawić \<go\>przy użyciu metadanych w klasie SchemaRowset klasy dostawcy. Ustaw `m_bColumnHasDefault = VARIANT_TRUE`.

Masz również obowiązek ustawić flagi kolumn, które są określone przy użyciu DBCOLUMNFLAGS wyliczonego typu. Flagi kolumn opisują charakterystyki kolumny.

Na przykład w `CUpdateSessionColSchemaRowset` klasie `UpdatePV` w (w Session.h) pierwsza kolumna jest konfigurajna w ten sposób:

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

Ten kod określa między innymi, że kolumna obsługuje domyślną wartość 0, że można ją zapisać i że wszystkie dane w kolumnie mają taką samą długość. Jeśli chcesz, aby dane w kolumnie miały zmienną długość, nie należy ustawiać tej flagi.

## <a name="see-also"></a>Zobacz też

[Tworzenie dostawcy ole db](creating-an-ole-db-provider.md)
