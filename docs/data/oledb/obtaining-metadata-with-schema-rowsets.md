---
title: Uzyskiwanie metadanych za pomocą zestawów wierszy schematu
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: cb0f7813a351f272d5417955fb98719d889a64ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561216"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Uzyskiwanie metadanych za pomocą zestawów wierszy schematu

Czasami zachodzi potrzeba uzyskania informacji o dostawcy, zestawu wierszy, tabeli, kolumny lub inne informacje o bazie danych bez konieczności otwierania zestawu wierszy. Dane dotyczące struktury bazy danych jest nazywane metadanych i mogą być pobierane przez wiele różnych sposobów. Jedną z metod jest używać zestawów wierszy schematu.

Szablony OLE DB zapewniają zestaw klas, które można pobrać informacji o schemacie; w ramach tych zajęć, tworzenie zestawów wierszy schematu wstępnie zdefiniowanych i są wymienione w [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Jeśli używasz OLAP, a niektóre z zestawów wierszy nie są obsługiwane przez klasy zestawów wierszy schematu (na przykład możesz mieć różną liczbą kolumn), należy rozważyć użycie `CManualAccessor` lub `CDynamicAccessor`. Możesz przewijać kolumny i umożliwia obsługę typów danych dla każdej kolumny w instrukcji case.

## <a name="catalogschema-model"></a>Model katalogu/schematu

ANSI SQL definiuje model schematu/katalogu dla magazynów danych; OLE DB używa tego modelu. W tym modelu katalogów (baz danych) ma schematów i schematy istnieją tabele.

- **Wykaz** wykaz jest inną nazwę dla bazy danych. Jest to kolekcja powiązanych schematów. Aby wyświetlić listę katalogów (baz danych) należących do danego źródła danych, należy użyć [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Ponieważ wiele baz danych mają tylko jeden katalog, metadanych jest czasami nazywane informacji o schemacie.

- **Schemat** schemat jest kolekcją obiektów bazy danych, które należą do firmy lub zostały utworzone przez określonego użytkownika. Aby wyświetlić listę schematów należących do danego użytkownika, należy użyć [CSchemata](../../data/oledb/cschemata-cschematainfo.md).

   W programie Microsoft SQL Server i ODBC 2.x, schemat jest właścicielem (na przykład dbo jest nazwa schematu typowe). Ponadto program SQL Server metadane są przechowywane w tabelach: jedna tabela zawiera listę wszystkich tabel, a inna tabela zawiera listę wszystkich kolumn. Nie ma odpowiednika, do schematu w bazie danych programu Microsoft Access.

- **Tabela** tabele są kolekcjami kolumn uporządkowane według określonych zamówień. Aby wyświetlić listę tabel zdefiniowanych w danym katalogu (baza danych) i informacje na temat tych tabel, należy użyć [CTables](../../data/oledb/ctables-ctableinfo.md)).

## <a name="restrictions"></a>Ograniczenia

Po wykonaniu zapytania dotyczącego informacji o schemacie, można użyć ograniczenia, aby określić typ informacji, w którym chcesz wziąć. Można potraktować ograniczenia, jak filtr lub kwalifikatora w zapytaniu. Na przykład w zapytaniu:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` to ograniczenie. Jest to prosty przykład za pomocą tylko jednego ograniczenia; klasy zestawów wierszy schematu obsługuje kilka ograniczeń.

[Klasy typedef zestawów wierszy schematu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) hermetyzacji wszystkich zestawów wierszy schematu OLE DB, dzięki czemu dostęp do zestawu wierszy schematu, podobnie jak inne wierszy przy uruchamianiu i otwierając ją. Na przykład klasa typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) jest zdefiniowany jako:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

[CRestrictions](../../data/oledb/crestrictions-class.md) klasa zapewnia obsługę ograniczeń. Po utworzeniu wystąpienia zestaw wierszy schematu, wywołaj [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Ta metoda zwraca zestaw wyników, oparte na ograniczenia, które określisz.

Aby określić ograniczenia, zapoznaj się [zestawów wierszy schematu B: dodatku](/previous-versions/windows/desktop/ms712921) i poszukiwanie zestawu wierszy, którego używasz. Na przykład `CColumns` odpowiada [zestawu wierszy kolumn](/previous-versions/windows/desktop/ms723052\(v%3dvs.85\)); tego tematu spowoduje wyświetlenie listy kolumn ograniczeń w zestawie wierszy kolumn: TABLE_CATALOG, TABLE_SCHEMA, nazwa_tabeli COLUMN_NAME. Należy przestrzegać tej kolejności określania Twojej ograniczenia.

Tak, na przykład, jeśli chcesz ograniczyć, nazwa tabeli nazwa_tabeli to trzecia kolumna ograniczenia, a następnie wywołania `Open`, określając nazwę odpowiedniej tabeli jako trzeci parametr ograniczenia, jak pokazano w poniższym przykładzie.

### <a name="to-use-schema-rowsets"></a>Aby używać zestawów wierszy schematu

1. Uwzględnić plik nagłówka `Atldbsch.h` (należy `Atldbcli.h` również obsługę klientów).

1. Utwórz wystąpienie obiektu zestawu wierszy schematu, użytkownika lub dokumentu pliku nagłówka. Jeśli chcesz informacji z tabeli, należy zadeklarować `CTables` obiektu; informacje o kolumnach, zadeklarować `CColumns` obiektu. W tym przykładzie pokazano, jak można pobrać kolumn w tabeli Autorzy:

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. Do pobierania informacji, na przykład dostęp do elementu członkowskiego odpowiednie dane obiektu zestawu wierszy schematu `ColumnSchemaRowset.m_szColumnName`. Ten element członkowski danych odnosi się do COLUMN_NAME. Aby wyświetlić każdy element członkowski danych odnosi się do kolumny OLE DB, zobacz [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).

Dla odwołania do zestawu wierszy schematu klasy typedef podane w szablonach OLE DB (zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Aby uzyskać więcej informacji na temat zestawów wierszy schematu OLE DB, w tym kolumny ograniczenia zobacz [zestawów wierszy schematu B: dodatku](/previous-versions/windows/desktop/ms712921) w **OLE DB Podręcznik programisty**.

Bardziej złożone przykłady sposobów użycia klasy zestawów wierszy schematu, zobacz [CatDB](https://github.com/Microsoft/VCSamples) i [DBViewer](https://github.com/Microsoft/VCSamples) przykłady.

Aby uzyskać informacje dotyczące obsługi dostawcy zestawów wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)