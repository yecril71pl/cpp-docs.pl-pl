---
title: Obsługa zestawów wierszy schematu
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: f87e6cc0a307eed4f00f1fb90ac16a840a1759af
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509456"
---
# <a name="supporting-schema-rowsets"></a>Obsługa zestawów wierszy schematu

Zestawy wierszy schematu umożliwiają klientom pobieranie informacji o magazynie danych bez znajomości podstawowej struktury lub schematu. Na przykład magazyn danych może mieć tabele zorganizowane w hierarchię zdefiniowaną przez użytkownika, więc nie ma możliwości zapewnienia znajomości schematu, z wyjątkiem odczytywania go. (W innym przykładzie kreatory Visual C++ używają zestawów wierszy schematu do generowania metod dostępu dla konsumenta). Aby umożliwić konsumentowi wykonanie tej czynności, obiekt sesji dostawcy ujawnia metody w interfejsie [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) . W Visual C++ aplikacji należy użyć klasy [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) do zaimplementowania `IDBSchemaRowset` .

`IDBSchemaRowsetImpl` obsługuje następujące metody:

- [CheckRestrictions](./idbschemarowsetimpl-class.md#checkrestrictions) sprawdza ważność ograniczeń względem zestawu wierszy schematu.

- [CreateSchemaRowset](./idbschemarowsetimpl-class.md#createschemarowset) implementuje funkcję twórcy obiektów COM dla obiektu określonego przez parametr szablonu.

- [Setograniczenia](./idbschemarowsetimpl-class.md#setrestrictions) określa, które ograniczenia są obsługiwane dla określonego zestawu wierszy schematu.

- [IDBSchemaRowset:: GetRowset](./idbschemarowsetimpl-class.md#getrowset) zwraca zestaw wierszy schematu (Dziedziczony z interfejsu).

- [GetSchemas](./idbschemarowsetimpl-class.md#getschemas) zwraca listę zestawów wierszy schematu dostępnych przez program `IDBSchemaRowsetImpl::GetRowset` (Dziedziczony z interfejsu).

## <a name="atl-ole-db-provider-wizard-support"></a>Obsługa kreatora dostawcy OLE DB ATL

::: moniker range="vs-2019"

Kreator dostawcy OLE DB ATL nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

**Kreator dostawcy OLE DB ATL** tworzy trzy klasy schematu w pliku nagłówkowym sesji:

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

Te klasy odpowiadają na żądania klientów dotyczące informacji o schemacie; Należy zauważyć, że Specyfikacja OLE DB wymaga, aby te trzy zestawy wierszy schematu były obsługiwane:

- **C**<em>ShortName</em>**SessionTRSchemaRowset** obsługuje żądania dla informacji tabeli (zestaw wierszy schematu DBSCHEMA_TABLES).

- **C**<em>ShortName</em>**SessionColSchemaRowset** obsługuje żądania informacji o kolumnie (zestaw wierszy schematu DBSCHEMA_COLUMNS). Kreator dostarcza przykładowe implementacje dla tych klas, które zwracają informacje o schemacie dla dostawcy systemu DOS.

- **C**<em>ShortName</em>**SessionPTSchemaRowset** obsługuje żądania informacji o schemacie dotyczące typu dostawcy (zestaw wierszy schematu DBSCHEMA_PROVIDER_TYPES). Domyślna implementacja udostępniona przez kreatora zwraca S_OK.

Można dostosować te klasy do obsługi informacji o schemacie odpowiednich dla dostawcy:

- W języku **C**<em>ShortName</em>**SessionTRSchemaRowset**należy wypełnić pola wykazu, tabeli i opisu ( `trData.m_szType` , `trData.m_szTable` i `trData.m_szDesc` ). W przykładzie wygenerowanym przez kreatora jest wykorzystywany tylko jeden wiersz (tabela). Inni dostawcy mogą zwrócić więcej niż jedną tabelę.

- W **C**<em>ShortName</em>**SessionColSchemaRowset**, należy przekazać nazwę tabeli jako `DBID` .

::: moniker-end

## <a name="setting-restrictions"></a>Ustawienia ograniczeń

Ważnym pojęciem obsługi zestawu wierszy schematu jest ustawienie ograniczeń, które są używane `SetRestrictions` . Ograniczenia umożliwiają konsumentom pobieranie tylko pasujących wierszy (na przykład Znajdź wszystkie kolumny w tabeli "MyTable"). Ograniczenia są opcjonalne i w przypadku, gdy żaden z nich nie jest obsługiwany (wartość domyślna), wszystkie dane są zawsze zwracane. Aby zapoznać się z przykładem dostawcy, który obsługuje ograniczenia, zobacz przykład [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="setting-up-the-schema-map"></a>Konfigurowanie mapy schematów

Skonfiguruj mapę schematu, taką jak ta, w sesji Session. h w UpdatePV:

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

Aby obsługiwać `IDBSchemaRowset` , musisz obsługiwać DBSCHEMA_TABLES, DBSCHEMA_COLUMNS i DBSCHEMA_PROVIDER_TYPES. Możesz dodać dodatkowe zestawy wierszy schematu według własnego uznania.

Zadeklaruj klasę zestawu wierszy schematu za pomocą `Execute` metody, takiej jak `CUpdateSessionTRSchemaRowset` w `UpdatePV` :

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` dziedziczy po `IDBSchemaRowsetImpl` , więc ma wszystkie metody obsługi ograniczeń. Przy użyciu `CSchemaRowsetImpl` , deklaruj trzy klasy podrzędne (wymienione w mapowaniu schematu powyżej): `CUpdateSessionTRSchemaRowset` , `CUpdateSessionColSchemaRowset` , i `CUpdateSessionPTSchemaRowset` . Każda z tych klas podrzędnych ma `Execute` metodę, która obsługuje odpowiedni zestaw ograniczeń (kryteria wyszukiwania). Każda `Execute` Metoda porównuje wartości parametrów *cRestrictions* i *rgRestrictions* . Zobacz opis tych parametrów w temacie [setograniczenia](./idbschemarowsetimpl-class.md#setrestrictions).

Aby uzyskać więcej informacji o ograniczeniach odnoszących się do określonego zestawu wierszy schematu, zobacz tabelę identyfikatorów GUID zestawu wierszy w [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) w **dokumentacji programisty OLE DB** w Windows SDK.

Na przykład jeśli na DBSCHEMA_TABLES jest obsługiwane ograniczenie TABLE_NAME, należy wykonać następujące czynności:

Najpierw Znajdź DBSCHEMA_TABLES i sprawdź, czy obsługuje cztery ograniczenia (w kolejności).

|Ograniczenie zestawu wierszy schematu|Wartość ograniczenia|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (dane binarne 1)|
|TABLE_SCHEMA|0x2 (binarny 10)|
|TABLE_NAME|0x4 (binarny 100)|
|TABLE_TYPE|0x8 (binarny 1000)|

Następnie dla każdego ograniczenia istnieje jeden bit. Ponieważ chcesz obsługiwać tylko TABLE_NAME, zwróć wartość 0x4 w `rgRestrictions` elemencie. Jeśli obsługiwane są TABLE_CATALOG i TABLE_NAME, należy zwrócić 0x5 (binarny 101).

Domyślnie implementacja zwraca wartość 0 (nie obsługuje żadnych ograniczeń) dla każdego żądania. UpdatePV jest przykładem dostawcy, który obsługuje ograniczenia.

### <a name="example"></a>Przykład

Ten kod jest pobierany z przykładu [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) . `UpdatePv` obsługuje trzy wymagane zestawy wierszy schematu: DBSCHEMA_TABLES, DBSCHEMA_COLUMNS i DBSCHEMA_PROVIDER_TYPES. Przykładowo, jak zaimplementować obsługę schematu w ramach dostawcy, ten temat przeprowadzi Cię przez proces wdrażania zestawu wierszy DBSCHEMA_TABLE.

> [!NOTE]
> Przykładowy kod może się różnić od tego, co jest wymienione tutaj; przykładowy kod należy traktować jako nowszą wersję.

Pierwszym krokiem dodawania obsługi schematu jest określenie ograniczeń, które mają być obsługiwane. Aby określić, które ograniczenia są dostępne dla zestawu wierszy schematu, zapoznaj się ze specyfikacją OLE DBą dla definicji `IDBSchemaRowset` . Zgodnie z definicją główną można wyświetlić tabelę zawierającą nazwę zestawu wierszy schematu, liczbę ograniczeń i kolumny ograniczeń. Wybierz zestaw wierszy schematu, który ma być obsługiwany, i zanotuj liczbę ograniczeń i kolumn ograniczeń. Na przykład DBSCHEMA_TABLES obsługuje cztery ograniczenia (TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME i TABLE_TYPE):

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

Bit reprezentuje każdą kolumnę ograniczenia. Jeśli chcesz obsłużyć ograniczenie (to oznacza, możesz wykonać zapytania według niego), ustaw ten bit na 1. Jeśli nie chcesz obsłużyć ograniczenia, ustaw ten bit na zero. W wierszu kodu powyżej program `UpdatePV` obsługuje ograniczenia TABLE_NAME i TABLE_TYPE w zestawie wierszy DBSCHEMA_TABLES. Są to trzy ograniczenia (Maska bitowa 100) i czwarta (Maska bitów 1000). W związku z tym maska bitów dla `UpdatePv` jest 1100 (lub 0x0c):

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

Następująca `Execute` Funkcja jest podobna do tych w zwykłych zestawach wierszy. Masz trzy argumenty: *pcRowsAffected*, *cRestrictions*i *rgRestrictions*. Zmienna *pcRowsAffected* jest parametrem wyjściowym, który dostawca może zwrócić liczbę wierszy w zestawie wierszy schematu. Parametr *cRestrictions* jest parametrem wejściowym zawierającym liczbę ograniczeń przekazaną przez odbiorcę do dostawcy. Parametr *rgRestrictions* jest tablicą wartości wariantów, które zawierają wartości ograniczeń.

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

Zmienna *cRestrictions* jest oparta na łącznej liczbie ograniczeń zestawu wierszy schematu, niezależnie od tego, czy dostawca je obsługuje. Ponieważ UpdatePv obsługuje dwa ograniczenia (trzecia i czwarta), ten kod szuka tylko wartości *cRestrictions* większej lub równej 3.

Wartość ograniczenia TABLE_NAME jest przechowywana w *rgRestrictions [2]* (ponowne ograniczenie w tablicy opartej na zero to 2). Sprawdź, czy ograniczenie nie jest VT_EMPTY, aby było w rzeczywistości obsługiwane. Należy pamiętać, że VT_NULL nie jest równe VT_EMPTY. VT_NULL określa prawidłową wartość ograniczenia.

`UpdatePv`Definicja nazwy tabeli jest w pełni kwalifikowaną nazwą ścieżki do pliku tekstowego. Wyodrębnij wartość ograniczenia, a następnie spróbuj otworzyć plik, aby upewnić się, że plik rzeczywiście istnieje. Jeśli plik nie istnieje, zwróć S_OK. Może się wydawać, że jest to bit do tyłu, ale kod jest naprawdę informujący użytkownika, że nie ma żadnych obsługiwanych tabel o określonej nazwie. S_OK Return oznacza, że kod wykonywany prawidłowo.

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

Obsługa czwartego ograniczenia (TABLE_TYPE) jest podobna do trzeciego ograniczenia. Sprawdź, czy wartość nie jest VT_EMPTY. To ograniczenie zwraca tylko typ tabeli, tabelę. Aby określić prawidłowe wartości dla DBSCHEMA_TABLES, zapoznaj się z sekcją **B** **odwołania OLE DB programisty** w tabeli zestawów wierszy.

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

W tym miejscu jest tworzony wpis wiersza dla zestawu wierszy. Zmienna `trData` odpowiada `CTABLESRow` strukturze zdefiniowanej w szablonach dostawcy OLE DB. `CTABLESRow` odpowiada definicji zestawu wierszy tabel w **dodatku B** specyfikacji OLE DB. Masz tylko jeden wiersz do dodania, ponieważ w danym momencie można obsługiwać tylko jedną tabelę.

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` Ustawia tylko trzy kolumny: TABLE_NAME, TABLE_TYPE i opis. Zanotuj kolumny, dla których są zwracane informacje, ponieważ te informacje są potrzebne podczas implementacji `GetDBStatus` :

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

`GetDBStatus`Funkcja jest ważna dla poprawnej operacji zestawu wierszy schematu. Ponieważ nie są zwracane żadne dane dla każdej kolumny w zestawie wierszy, należy określić kolumny, dla których dane są zwracane, a które nie.

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

Ponieważ `Execute` Funkcja zwraca dane dla pól table_name, TABLE_TYPE i Description z zestawu wierszy tabel, można zajrzeć do **dodatku B** specyfikacji OLE DB i określić (poprzez zliczanie od góry), że są to liczby porządkowe 3, 4 i 6. Dla każdej z tych kolumn zwraca DBSTATUS_S_OK. Dla wszystkich innych kolumn zwraca DBSTATUS_S_ISNULL. Ważne jest, aby zwrócić ten stan, ponieważ konsument może nie rozumieć, że zwracana wartość ma wartość NULL lub coś innego. Należy pamiętać, że wartość NULL nie jest równoznaczna z wartością pustą.

Aby uzyskać więcej informacji na temat interfejsu zestawu wierszy schematu OLE DB, zobacz Interfejs [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) w **dokumentacji OLE DB programisty**.

Aby uzyskać informacje o sposobach używania `IDBSchemaRowset` metod przez odbiorców, zobacz [Uzyskiwanie metadanych z zestawami wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).

Aby zapoznać się z przykładem dostawcy, który obsługuje zestawy wierszy schematu, zobacz przykład [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

## <a name="see-also"></a>Zobacz też

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
