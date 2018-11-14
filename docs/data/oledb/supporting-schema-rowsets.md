---
title: Obsługa zestawów wierszy schematu
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 6046bcb1b99e446974a3b4fae11d0021778bf526
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556884"
---
# <a name="supporting-schema-rowsets"></a>Obsługa zestawów wierszy schematu

Zestawy wierszy schematu umożliwiają klientom uzyskiwanie informacji na temat magazynu danych nie wiedząc o tym wewnętrzna struktura lub schematu. Na przykład magazyn danych może być tabel zorganizowane w hierarchii zdefiniowanej przez użytkownika, więc będzie żaden sposób zapewnić znajomości schematu z wyjątkiem sytuacji, zapoznając się go. (Inny przykład kreatorów Visual C++ Użyj zestawów wierszy schematu do generowania metody dostępu dla użytkownika). Aby zezwolić na odbiorców to zrobić, obiekt sesji dostawcy udostępnia metody na [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) interfejsu. W aplikacji Visual C++, możesz użyć [idbschemarowsetimpl —](../../data/oledb/idbschemarowsetimpl-class.md) klasy do zaimplementowania `IDBSchemaRowset`.

`IDBSchemaRowsetImpl` obsługuje następujące metody:

- [Checkrestrictions —](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) sprawdza poprawność ograniczenia względem wierszy schematu.

- [Createschemarowset —](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementuje funkcji twórcy obiektu COM dla obiektu określonego przez parametr szablonu.

- [Setrestrictions —](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) określa ograniczenia, które obsługują w zestawie wierszy z określonego schematu.

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) zwraca zestaw wierszy schematu (dziedziczone z interfejsu).

- [Getschemas —](../../data/oledb/idbschemarowsetimpl-getschemas.md) zwraca listę zestawów wierszy schematu jest dostępny za pomocą `IDBSchemaRowsetImpl::GetRowset` (dziedziczone z interfejsu).

## <a name="atl-ole-db-provider-wizard-support"></a>Obsługa kreatora dla dostawcy bazy danych ATL OLE

**Kreator biblioteki ATL OLE DB Provider** tworzy trzy klasy schematu w pliku nagłówkowym sesji:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

W ramach tych zajęć, odpowiadanie na żądania klientów informacji o schemacie; należy zwrócić uwagę na to, że specyfikacji OLE DB wymaga obsługiwane tych zestawów wierszy schematu trzy:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** obsługuje żądania na potrzeby informacji o tabeli (DBSCHEMA_TABLES zestawu wierszy schematu).

- **C**<em>ShortName</em>**SessionColSchemaRowset** obsługuje żądania, aby uzyskać informacje o kolumnach (zestawu wierszy schematu DBSCHEMA_COLUMNS). Kreator dostarcza przykładowe implementacje dla tych klas, które zwracają informacje o schemacie dla dostawcy systemu DOS.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** obsługuje żądania, aby uzyskać informacje o schemacie o typie dostawcy (DBSCHEMA_PROVIDER_TYPES zestawu wierszy schematu). Domyślna implementacja kreatora zwraca wartość S_OK.

Można dostosować te klasy do obsługi informacji o schemacie odpowiedniego dostawcy:

- W **C**<em>ShortName</em>**SessionTRSchemaRowset**, należy wypełnić pola wykazu, tabeli i opis (`trData.m_szType`, `trData.m_szTable`i `trData.m_szDesc`). Przykład generowane przez Kreatora używa tylko jeden wiersz (tabela). Innych dostawców rozwiązań może zwrócić więcej niż jedną tabelą.

- W **C**<em>ShortName</em>**SessionColSchemaRowset**, przekazać nazwę tabeli jako `DBID`.

## <a name="setting-restrictions"></a>Ustawianie ograniczeń

Obsługa zestawów wierszy schematu bardzo ważnym pojęciem jest ustawienie ograniczenia, które można zrobić za pomocą `SetRestrictions`. Ograniczenia pozwala użytkownikom można pobrać tylko pasujących wierszy (na przykład znaleźć wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne, a w przypadku, w których żaden nie jest obsługiwane (ustawienie domyślne), zwracane są wszystkie dane zawsze. Na przykład dostawca, który obsługuje ograniczenia zobacz [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki.

## <a name="setting-up-the-schema-map"></a>Konfigurowanie Mapa schematu

Skonfiguruj Mapa schematu, taką jak ta w Session.h w UpdatePV:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Aby obsługiwać `IDBSchemaRowset`, musi obsługiwać DBSCHEMA_TABLES DBSCHEMA_COLUMNS i DBSCHEMA_PROVIDER_TYPES. Możesz dodać zestawy wierszy schematu dodatkowe według uznania.

Deklarowanie klasy zestawu wierszy schematu z `Execute` metody takie jak `CUpdateSessionTRSchemaRowset` w `UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` dziedziczy `IDBSchemaRowsetImpl`, więc posiada wartość ograniczenia obsługi metod. Za pomocą `CSchemaRowsetImpl`, Zadeklaruj trzy klasy podrzędnej (wymienione w powyższej Mapa schematu): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, i `CUpdateSessionPTSchemaRowset`. Każda z tych klas podrzędnych ma `Execute` metoda, która obsługuje jego odpowiedniego zestawu ograniczeń (kryteria wyszukiwania). Każdy `Execute` metoda porównuje wartości *cRestrictions* i *rgRestrictions* parametrów. Zobacz opis tych parametrów w [setrestrictions —](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).

Aby uzyskać więcej informacji o tym, które odpowiadają ograniczenia wierszy określonego schematu, zobacz tabelę wierszy schematu identyfikatorów GUID w [IDBSchemaRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms713686(v=vs.85)) w **OLE DB Podręcznik programisty** w zestawie Windows SDK .

Na przykład jeśli ograniczenia nazwa_tabeli jest obsługiwana przez DBSCHEMA_TABLES, czy wykonaj następujące czynności:

Najpierw wyszukać DBSCHEMA_TABLES i zobacz, że obsługuje ona cztery ograniczenia (w kolejności).

|Ograniczenie zestawu wierszy schematu|Wartość ograniczenia|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (binarne 1)|
|TABLE_SCHEMA|0x2 (binarne 10)|
|TABLE_NAME|0x4 (binarne 100)|
|TABLE_TYPE|0x8 (binarne 1000)|

Następnie jest jeden bit dla każdego ograniczenia. Ponieważ chcemy obsługują tylko nazwa_tabeli zwróci 0x4 w `rgRestrictions` elementu. Jeśli obsługiwany jest TABLE_CATALOG i nazwa_tabeli, zwróci 0x5 (binarne 101).

Domyślnie implementacja zwraca wartość 0 (nie obsługuje żadnych ograniczeń) dla każdego żądania. UpdatePV znajduje się przykład dostawcy, który obsługuje ograniczenia.

### <a name="example"></a>Przykład

Ten kod jest pobierana z [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki. `UpdatePv` obsługuje trzy zestawów wierszy schematu wymagane: DBSCHEMA_TABLES DBSCHEMA_COLUMNS i DBSCHEMA_PROVIDER_TYPES. Jako przykład sposób implementacji Obsługa schematu w dostawcy ten temat przeprowadzi Cię przez Implementowanie DBSCHEMA_TABLE zestawu wierszy.

> [!NOTE]
> Przykładowy kod różnić się od wymienione tutaj; w przykładowym kodzie powinno być traktowane jako bardziej aktualnej wersji.

Pierwszym krokiem podczas dodawania obsługi schematu jest ustalenie, ograniczenia, które zamierzasz obsługiwać. Aby określić ograniczenia, które są dostępne dla użytkownika zestaw wierszy schematu, Przyjrzyj się specyfikacji OLE DB dla definicji `IDBSchemaRowset`. Następujące główne definicji jest wyświetlana tabela zawierający nazwę zestawu wierszy schematu, liczba ograniczeń i kolumn ograniczeń. Wybierz zestaw wierszy schematu, potrzebne do obsługi i zanotuj liczbę ograniczenia i ograniczenie kolumny. Na przykład DBSCHEMA_TABLES obsługuje cztery ograniczenia (TABLE_CATALOG TABLE_SCHEMA, nazwa_tabeli i TABLE_TYPE):

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

Bit reprezentuje każda kolumna ograniczeń. Jeśli chcesz obsługiwać ograniczenie (oznacza to, że można tworzyć zapytania przez niego), ustaw ten bit na 1. Jeśli nie chcesz obsługiwać ograniczenie, należy ustawić na zero tego bitu. W wierszu kodu powyżej `UpdatePV` obsługuje ograniczenia nazwa_tabeli i TABLE_TYPE na DBSCHEMA_TABLES zestawu wierszy. Są to czwarta ograniczenia (maska bitowa 1000) i innych (maska bitowa 100). W związku z tym, maski bitów dla `UpdatePv` 1100 (lub 0x0C):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

Następujące `Execute` funkcji jest podobne do tych w regularnych zestawów wierszy. Masz trzy argumenty: *pcRowsAffected*, *cRestrictions*, i *rgRestrictions*. *PcRowsAffected* zmienna jest parametrem wyjściowym, dostawca może zwracać liczbę wierszy w zestawie wierszy schematu. *CRestrictions* parametr jest parametrem wejściowym zawierający liczba ograniczeń przekazywane przez klienta do dostawcy. *RgRestrictions* parametr jest tablicą wartości Wariant, używane do przechowywania wartości ograniczeń.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*CRestrictions* zmienna jest oparta na całkowita liczba ograniczeń dla zestawu wierszy schematu, niezależnie od tego, czy dostawca obsługuje je. Ponieważ UpdatePv obsługuje dwa ograniczenia (trzecia i czwarta), ten kod wyszukuje tylko *cRestrictions* wartość większą lub równą 3.

Wartość ograniczenia nazwa_tabeli jest przechowywana w *rgRestrictions [2]* (ponownie trzeci ograniczenie w tablicę indeksowaną od zera jest 2). Sprawdź, czy ograniczenia nie jest VT_EMPTY do faktycznie jego obsługi. Należy pamiętać, że VT_NULL nie jest równa VT_EMPTY. VT_NULL określa wartość prawidłowym ograniczeniem.

`UpdatePv` Definicja Nazwa tabeli jest w pełni kwalifikowaną ścieżkę do pliku tekstowego. Wyodrębnianie wartości ograniczenia, a następnie spróbuj otworzyć plik, aby upewnić się, że plik istnieje. Jeśli plik nie istnieje, należy zwrócić S_OK. Może to wydawać się nieco z poprzednimi wersjami, ale jaki kod naprawdę informuje użytkownika jest istnienie żadnych tabel obsługiwanych przez nazwę, który został określony. Zwracany S_OK oznacza, że kod wykonany prawidłowo.

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

Obsługa ograniczeń czwarty (TABLE_TYPE) jest podobny do trzeciego ograniczeń. Sprawdź, czy wartość nie jest VT_EMPTY. To ograniczenie zwraca tylko typ tabeli, tabeli. Aby określić prawidłowe wartości dla DBSCHEMA_TABLES, Szukaj w **dodatek B** z **OLE DB Podręcznik programisty** w sekcji wierszy tabeli.

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

Jest to, gdzie rzeczywiście utworzeniu wpisu wiersza w zestawie wierszy. Zmienna `trData` odpowiada `CTABLESRow`, struktury, zdefiniowanych w szablonach dostawcy OLE DB. `CTABLESRow` odnosi się do definicji zestawu wierszy tabeli w **dodatek B** specyfikacji OLE DB. Masz tylko jeden wiersz, aby dodać, ponieważ w danym momencie może obsługiwać tylko jedną tabelę.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` Ustawia tylko dla trzech kolumnach: nazwa_tabeli, TABLE_TYPE i opis. Zanotuj wartości kolumn, dla których zwrócić informacje, ponieważ ta informacja będzie potrzebna podczas implementowania `GetDBStatus`:

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` Funkcja ważne jest, aby poprawnego działania zestawu wierszy schematu. Ponieważ dane dla każdej kolumny nie są zwracane w zestawie wierszy w TABELACH, należy określić kolumny, które zwracają dane, które nie obsługują.

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

Ponieważ Twoje `Execute` funkcja zwraca dane dla pól nazwa_tabeli, TABLE_TYPE i opis zestawu wierszy w TABELACH, możesz zobaczyć w **dodatek B** specyfikacji OLE DB oraz w (licząc od góry w dół) czy są one liczby porządkowe, 3, 4 i 6. Dla każdego z tych kolumn Zwróć DBSTATUS_S_OK. W przypadku wszystkich innych kolumn zwracają DBSTATUS_S_ISNULL. Ważne jest zwrócić ten stan, ponieważ użytkownik może ich nie zrozumieć to wartość, którą należy zwrócić wartość NULL lub jest coś innego. Ponownie należy pamiętać, że wartość NULL nie jest odpowiednikiem pustego.

Aby uzyskać więcej informacji na temat interfejsu zestawu wierszy schematu OLE DB, zobacz [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) interfejsu w **OLE DB Podręcznik programisty**.

Aby dowiedzieć się jak klienci mogą korzystać `IDBSchemaRowset` metod, zobacz [uzyskiwanie metadanych za pomocą zestawów wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Na przykład dostawcy, który obsługuje zestawów wierszy schematu zobacz [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) próbki.

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
