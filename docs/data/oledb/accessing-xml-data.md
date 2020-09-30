---
title: Uzyskiwanie dostępu do danych XML
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: 437f1d103420ec5727294894c02587c68cffbdda
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509125"
---
# <a name="accessing-xml-data"></a>Uzyskiwanie dostępu do danych XML

Istnieją dwie osobne metody pobierania danych XML ze źródła danych: jeden używa [CStreamRowset](../../data/oledb/cstreamrowset-class.md) , a drugi korzysta z [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).

|Funkcjonalność|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Ilość przesłanych danych|Pobiera dane ze wszystkich kolumn i wierszy jednocześnie.|Pobiera dane ze wszystkich kolumn, ale tylko jeden wiersz jednocześnie. Należy nawigować po wierszach przy użyciu metod, takich jak `MoveNext` .|
|Formatowanie ciągu|SQL Server formatuje ciąg XML i wysyła go do konsumenta.|Pobiera dane zestawu wierszy w formacie natywnym (żądania wysyłane przez dostawcę jako ciągi Unicode), a następnie kompiluje ciąg przechowujący dane w formacie XML.|
|Kontrola nad formatowaniem|Istnieje pewien poziom kontroli nad sposobem formatowania ciągu XML przez ustawienie niektórych właściwości specyficznych dla SQL Server 2000.|Nie ma kontroli nad formatem wygenerowanego ciągu XML.|

`CStreamRowset`Zapewnia to bardziej wydajny sposób pobierania danych w formacie XML, który jest obsługiwany tylko przez SQL Server 2000.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Pobieranie danych XML przy użyciu CStreamRowset

Należy określić [CStreamRowset](../../data/oledb/cstreamrowset-class.md) jako typ zestawu wierszy w `CCommand` deklaracji lub `CTable` . Można go użyć z własnymi metodami dostępu lub bez metody dostępu, na przykład:

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

-lub-

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Zwykle w przypadku wywołania `CCommand::Open` (określenie, na przykład `CRowset` jako `TRowset` Klasa), pobiera `IRowset` wskaźnik. `ICommand::Execute` zwraca `IRowset` wskaźnik, który jest przechowywany w `m_spRowset` elemencie członkowskim `CRowset` obiektu. Metody takie jak `MoveFirst` , `MoveNext` i `GetData` używają tego wskaźnika do pobierania danych.

Z drugiej strony, gdy wywoływana `CCommand::Open` jest (ale określana `CStreamRowset` jako `TRowset` Klasa), `ICommand::Execute` zwraca `ISequentialStream` wskaźnik, który jest przechowywany w `m_spStream` elemencie członkowskim danych [CStreamRowset](../../data/oledb/cstreamrowset-class.md). Następnie użyj metody, `Read` Aby pobrać dane (ciąg Unicode) w formacie XML. Na przykład:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 wykonuje formatowanie XML i zwraca wszystkie kolumny i wszystkie wiersze zestawu wierszy jako jeden ciąg XML.

Aby zapoznać się z przykładem za pomocą `Read` metody, zobacz **Dodawanie obsługi XML do konsumenta** w [implementacji prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).

> [!NOTE]
> Obsługa XML przy użyciu `CStreamRowset` programu działa tylko z SQL Server 2000 i wymaga, aby dostawca OLE DB SQL Server 2000 (instalowany z MDAC).

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Pobieranie danych XML przy użyciu CXMLAccessor

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) umożliwia dostęp do danych ze źródła danych jako dane ciągu, gdy nie masz informacji o schemacie magazynu danych. `CXMLAccessor` działa tak, jak `CDynamicStringAccessorW` z tą różnicą, że dawniej konwertuje wszystkie dane, do których uzyskano dostęp z magazynu danych jako dane sformatowane w formacie XML. Nazwy tagów XML są zgodne z nazwami kolumn magazynu danych tak blisko jak to możliwe.

Użyj `CXMLAccessor` tak jak każdej innej klasy akcesora, przekazując ją jako parametr szablonu do `CCommand` lub `CTable` :

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Użyj [GetXMLRowData](./cxmlaccessor-class.md#getxmlrowdata) , aby pobrać dane z tabeli jeden wiersz jednocześnie i przechodź do wierszy przy użyciu metod takich jak `MoveNext` , na przykład:

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

Możesz użyć [GetXMLColumnData](./cxmlaccessor-class.md#getxmlcolumndata) , aby pobrać informacje o kolumnie (typie danych) jako dane ciągu w formacie XML.

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
