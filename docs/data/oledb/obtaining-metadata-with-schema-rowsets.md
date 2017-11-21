---
title: "Uzyskiwanie metadanych za pomocą zestawów wierszy schematu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a2a57fd92183c60e245ecdd1ba237da74c9e575b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Uzyskiwanie metadanych za pomocą zestawów wierszy schematu
Czasami trzeba uzyskać informacje o dostawcy, zestaw wierszy, tabeli, kolumny lub inne informacje z bazy danych bez konieczności otwierania w zestawie wierszy. Dane dotyczące struktury bazy danych jest nazywana metadanych i mogą być pobierane przez wiele różnych sposobów. Co metoda polega na użyciu zestawów wierszy schematu.  
  
 Szablony OLE DB udostępniają zestaw klas można pobrać informacji o schemacie; te klasy utworzyć zestawy wierszy schematu wstępnie zdefiniowane i znajduje się w [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Jeśli używasz OLAP i niektóre z zestawów wierszy nie są obsługiwane przez klasy zestawów wierszy schematu (na przykład można mieć różną liczbą kolumn), należy rozważyć użycie `CManualAccessor` lub `CDynamicAccessor`. Możesz przewijać kolumn i używać instrukcji case do obsługi typów danych dla każdej kolumny.  
  
## <a name="catalogschema-model"></a>Katalog/schematu modelu  
 ANSI SQL definiuje model katalogu/schematu dla magazynów danych; OLE DB używa tego modelu. W tym modelu katalogów (bazy danych) zawierać schematy i tabele zawierają schematów.  
  
-   **Katalog** wykazu jest inną nazwę dla bazy danych. Jest kolekcją schematów pokrewne. Aby wyświetlić listę katalogów (bazy danych) należące do źródła danych danego, użyj [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Ponieważ wiele baz danych mają tylko jeden katalog, metadane czasami nosi nazwę informacji o schemacie.  
  
-   **Schemat** schemat jest kolekcją obiektów bazy danych, które należą do firmy lub zostały utworzone przez określonego użytkownika. Aby wyświetlić listę schematów należących do danego użytkownika, należy użyć [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     W programie Microsoft SQL Server i ODBC 2.x, schemat jest właścicielem (na przykład dbo jest nazwą typowy schemat). Ponadto program SQL Server metadane są przechowywane w tabelach: jedna tabela zawiera listę wszystkich tabel i inna tabela zawiera listę wszystkich kolumn. Nie ma odpowiednika do schematu bazy danych programu Microsoft Access.  
  
-   **Tabela** tabele są kolekcjami elementów ułożone w określonej kolejności kolumn. Aby wyświetlić listę tabel zdefiniowanych w danym katalogu (baza danych) oraz informacje dotyczące tych tabel, należy użyć [CTables](../../data/oledb/ctables-ctableinfo.md)).  
  
## <a name="restrictions"></a>Ograniczenia  
 Kwerendę dla informacji o schemacie mogą umożliwia określenie typu danych, w której jesteś zainteresowany ograniczenia. Można potraktować ograniczeń jako filtr lub kwalifikator w zapytaniu. Na przykład w zapytaniu:  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name`jest to ograniczenie. To jest bardzo prosty przykład z tylko jednego ograniczenia; klasy zestawów wierszy schematu obsługuje kilka ograniczeń.  
  
 [Klasy typedef zestawów wierszy schematu](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) Hermetyzowanie wszystkie zestawy wierszy schematu OLE DB, aby uzyskać dostęp do zestawu wierszy schematu, podobnie jak inne zestawu wierszy, tworzenie wystąpień i otwarcie go. Na przykład klasa typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) jest zdefiniowany jako:  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md) klasa zapewnia obsługę ograniczeń. Po utworzeniu wystąpienia zestawu wierszy schematu wywołać [CRestrictions::Open](../../data/oledb/crestrictions-open.md). Ta metoda zwraca zestawu wyników w oparciu ograniczenia, które określisz.  
  
 Pozwala określić ograniczenia, zapoznaj się [zestawów wierszy schematu B: dodatku](http://go.microsoft.com/fwlink/?linkid=64681) i wyszukaj zestawu wierszy, którego używasz. Na przykład **CColumns** odpowiada [zestawu wierszy kolumn](http://go.microsoft.com/fwlink/?linkid=64682); ten temat zawiera listę ograniczenie kolumny zestawu wierszy kolumn: TABLE_CATALOG, TABLE_SCHEMA, nazwa_tabeli nazwa_kolumny. Wykonaj tej kolejności, określając z ograniczeniami.  
  
 Tak, na przykład, jeśli chcesz ograniczyć według nazwy tabeli, należy pamiętać, że nazwa_tabeli trzecia kolumna ograniczeń, a następnie wywołać **Otwórz**, określania nazwy tabeli, którą chcesz jako trzeci parametr ograniczenia, jak pokazano w poniższym przykładzie.  
  
#### <a name="to-use-schema-rowsets"></a>Aby użyć zestawów wierszy schematu  
  
1.  Musisz uwzględnić plik nagłówka Atldbsch.h (oczywiście potrzeby Atldbcli.h również obsługa klienta).  
  
2.  Utwórz wystąpienie obiektu zestawu wierszy schematu w konsumenta lub dokumentu pliku nagłówka. Jeśli chcesz, aby informacje dotyczące tabeli, należy zadeklarować **CTables** obiektu; informacji o kolumnie należy zadeklarować **CColumns** obiektu. W tym przykładzie pokazano, jak pobrać kolumn w tabeli, autorzy:  
  
    ```  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  Aby pobrać informacje, na przykład dostęp do elementu członkowskiego danych obiektu zestawu wierszy schematu `ColumnSchemaRowset.m_szColumnName`. Odpowiada to COLUMN_NAME. Aby sprawdzić, która kolumna OLE DB odpowiada każdy element członkowski danych, zobacz [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Dla odwołania do zestawu wierszy schematu klasy typedef podane w szablonach OLE DB (zobacz [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).  
  
 Aby uzyskać więcej informacji na temat zestawów wierszy schematu OLE DB, wraz z kolumnami ograniczeń, zobacz [zestawów wierszy schematu B: dodatku](http://go.microsoft.com/fwlink/?linkid=64681) w OLE DB Podręcznik programisty.  
  
 Bardziej złożone przykłady sposobów użycia klasy zestawów wierszy schematu można znaleźć [CatDB](http://msdn.microsoft.com/en-us/003d516b-2bf6-444e-8be5-4ebaa0b66046) i [DBViewer](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) próbek.  
  
 Aby uzyskać informacje dotyczące obsługi dostawcy zestawów wierszy schematu, zobacz [Obsługa zestawów wierszy schematu](../../data/oledb/supporting-schema-rowsets.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)