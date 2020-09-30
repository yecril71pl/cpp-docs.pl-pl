---
title: Uzyskiwanie metadanych za pomocą zestawów wierszy schematu
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: 37418cc91913ed840d1601aab9005b476bf29ee0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508989"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Uzyskiwanie metadanych za pomocą zestawów wierszy schematu

Czasami trzeba uzyskać informacje o dostawcy, zestawie wierszy, tabeli, kolumnach lub innych informacjach o bazie danych bez otwierania zestawu wierszy. Dane dotyczące struktury bazy danych są nazywane metadanymi i mogą być pobierane przez wiele różnych metod. Jedną z metod jest użycie zestawów wierszy schematu.

Szablony OLE DB udostępniają zestaw klas do pobrania informacji o schemacie; klasy te tworzą wstępnie zdefiniowane zestawy wierszy schematu i są wymienione w [klasach zestawów wierszy schematu i klasach typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Jeśli używasz OLAP, a niektóre zestawy wierszy nie są obsługiwane przez klasy zestawów wierszy schematu (na przykład masz zmienną liczbę kolumn), należy rozważyć użycie `CManualAccessor` lub `CDynamicAccessor` . Można przewijać kolumny i instrukcje przypadków użycia, aby obsługiwać możliwe typy danych dla każdej kolumny.

## <a name="catalogschema-model"></a>Katalog/model schematu

ANSI SQL definiuje katalog/model schematu dla magazynów danych; OLE DB używa tego modelu. W tym modelu katalogi (bazy danych) mają tabele.

- **Wykaz** Katalog to inna nazwa bazy danych. Jest to kolekcja powiązanych schematów. Aby wyświetlić listę wykazów (bazy danych) należących do danego źródła danych, należy użyć [CCatalog](./schema-rowset-classes-and-typedef-classes.md#catalog). Ponieważ wiele baz danych ma tylko jeden wykaz, metadane są czasami nazywane informacjami o schemacie.

- **Schemat** Schemat to kolekcja obiektów bazy danych, które są własnością lub zostały utworzone przez określonego użytkownika. Aby wyświetlić listę schematów należących do danego użytkownika, użyj [CSchemata](./schema-rowset-classes-and-typedef-classes.md#schemata).

   W przypadku warunków Microsoft SQL Server i ODBC 2. x schemat jest właścicielem (na przykład, dbo jest typową nazwą schematu). Ponadto SQL Server przechowuje metadane w zestawie tabel: jedna tabela zawiera listę wszystkich tabel, a inna tabela zawiera listę wszystkich kolumn. Nie istnieje odpowiednik schematu bazy danych programu Microsoft Access.

- **Tabela** Tabele są kolekcjami kolumn uporządkowanych według określonych zamówień. Aby wyświetlić listę tabel zdefiniowanych w danym katalogu (bazę danych) i informacje o tych tabelach, użyj [CTables](./schema-rowset-classes-and-typedef-classes.md#table)).

## <a name="restrictions"></a>Ograniczenia

Podczas wykonywania zapytania o informacje o schemacie można użyć ograniczeń, aby określić typ informacji, które są interesujące. Można traktować ograniczenia jako filtr lub kwalifikator w zapytaniu. Na przykład w zapytaniu:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` jest ograniczeniem. Jest to prosty przykład z tylko jednym ograniczeniem; klasy zestawu wierszy schematu obsługują kilka ograniczeń.

[Klasy typedef zestawu wierszy schematu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) hermetyzują wszystkie OLE DB zestawów wierszy schematu, aby można było uzyskać dostęp do zestawu wierszy schematu tak jak każdy inny zestaw wierszy przez utworzenie wystąpienia i otwarcie go. Na przykład Klasa typedef [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns) jest zdefiniowana jako:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

Klasa [cRestrictions](../../data/oledb/crestrictions-class.md) dostarcza pomoc techniczną dotyczącą ograniczeń. Po utworzeniu wystąpienia zestawu wierszy schematu Wywołaj [CRestrictions:: Open](./crestrictions-class.md#open). Ta metoda zwraca zestaw wyników na podstawie ograniczeń, które określisz.

Aby określić ograniczenia, zobacz [dodatek B: zestawy wierszy schematu](/previous-versions/windows/desktop/ms712921(v=vs.85)) i wyszukanie zestawu wierszy, którego używasz. Na przykład `CColumns` odpowiada [zestawowi wierszy kolumn](/previous-versions/windows/desktop/ms723052(v=vs.85)). w tym temacie wymieniono kolumny ograniczeń w zestawie wierszy kolumn: TABLE_CATALOG, TABLE_SCHEMA, table_name column_name. Należy postępować zgodnie z poniższą kolejnością w temacie określanie ograniczeń.

Tak więc, na przykład, jeśli chcesz ograniczyć według nazwy tabeli, TABLE_NAME jest trzecią kolumną ograniczenia, a następnie Wywołaj `Open` , określając żądaną nazwę tabeli jako trzeci parametr ograniczenia, jak pokazano w poniższym przykładzie.

### <a name="to-use-schema-rowsets"></a>Aby użyć zestawów wierszy schematu

1. Dołącz plik nagłówka `Atldbsch.h` (potrzebne `Atldbcli.h` również do obsługi klienta).

1. Utworzenie wystąpienia obiektu zestawu wierszy schematu w pliku nagłówkowym użytkownika lub dokumentu. Jeśli chcesz uzyskać informacje o tabeli, zadeklaruj `CTables` obiekt; Jeśli chcesz uzyskać informacje o kolumnie, zadeklaruj `CColumns` obiekt. Ten przykład pokazuje, jak pobrać kolumny w tabeli autorów:

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

1. Aby pobrać informacje, uzyskaj dostęp do odpowiedniego elementu członkowskiego danych obiektu zestawu wierszy schematu, na przykład `ColumnSchemaRowset.m_szColumnName` . Ten element członkowski danych odnosi się do COLUMN_NAME. Aby sprawdzić, do której kolumny OLE DB każdy element członkowski danych odpowiada, zobacz [CColumns](./schema-rowset-classes-and-typedef-classes.md#columns).

Aby uzyskać odwołanie do zestawu wierszy schematu, klasy typedef dostępne w szablonach OLE DB (zobacz [klasy zestawów wierszy schematu i klasy typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Aby uzyskać więcej informacji na temat OLE DB zestawów wierszy schematu, w tym kolumn ograniczeń, zobacz [dodatek B: zestawy wierszy schematu](/previous-versions/windows/desktop/ms712921(v=vs.85)) w **Kompendium OLE DB programisty**.

Aby uzyskać bardziej skomplikowane przykłady użycia klas zestawu wierszy schematu, zobacz przykłady [catdb](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) i [dbview](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

Aby uzyskać informacje na temat obsługi dostawcy zestawów wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
