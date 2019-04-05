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
ms.openlocfilehash: b5704c10393026a14ac66b632559fc376f008f8b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041539"
---
# <a name="accessing-xml-data"></a>Uzyskiwanie dostępu do danych XML

Istnieją dwa odrębne metody pobierania danych XML ze źródła danych: jeden używa [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) i innych zastosowań [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).

|Funkcja|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Ilość przesyłanych danych|Pobiera dane ze wszystkich kolumn i wierszy jednocześnie.|Pobiera dane ze wszystkich kolumn, ale tylko jeden wiersz w danym momencie. Musisz przejść wierszy przy użyciu metod, takich jak `MoveNext`.|
|Formatowanie ciągu|Program SQL Server formaty ciągu XML i wysyła go do użytkownika.|Pobiera dane wierszy w formacie natywnym (żądań, które dostawcy wysyłać je jako ciągi Unicode), a następnie kompiluje ciąg zawierający dane w formacie XML.|
|Kontrola nad formatowaniem|Masz pewien poziom kontroli nad sposób formatowania ciągu XML, ustawiając niektórych właściwości specyficzne dla programu SQL Server 2000.|Nie masz żadnych kontrolę nad formatem ciągu XML wygenerowany.|

Gdy `CStreamRowset` umożliwia więcej ogólną wydajność pobierania danych w formacie XML, jest ona obsługiwana tylko przez program SQL Server 2000.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Trwa pobieranie danych XML przy użyciu cstreamrowset —

Należy określić [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) jako typ zestawu wierszy w swojej `CCommand` lub `CTable` deklaracji. Umożliwia on własne metody dostępu lub brak akcesora na przykład:

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

—lub—

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Zwykle, gdy zostanie wywołana `CCommand::Open` (określający, na przykład `CRowset` jako `TRowset` klasy), otrzymuje `IRowset` wskaźnika. `ICommand::Execute` Zwraca `IRowset` wskaźnika, który jest przechowywany w `m_spRowset` członkiem `CRowset` obiektu. Metody takie jak `MoveFirst`, `MoveNext`, i `GetData` za pomocą tego wskaźnika do pobierania danych.

Z drugiej strony, gdy zostanie wywołana `CCommand::Open` (ale Określa `CStreamRowset` jako `TRowset` klasy), `ICommand::Execute` zwraca `ISequentialStream` wskaźnika, który jest przechowywany w `m_spStream` element członkowski danych [cstreamrowset —](../../data/oledb/cstreamrowset-class.md). Następnie użyj `Read` metody do pobierania danych (ciąg Unicode) w formacie XML. Na przykład:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 nie, formatowanie, XML i zwraca wszystkie kolumny i wszystkie wiersze z wierszy jako jeden ciąg XML.

Aby uzyskać przykłady dotyczące używania `Read` metody, zobacz **Dodawanie obsługę języka XML do konsumenta** w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).

> [!NOTE]
> Obsługa języka XML przy użyciu `CStreamRowset` projektów w programach SQL Server 2000 tylko i wymaga, aby miał dostawcy OLE DB dla programu SQL Server 2000 (zainstalowaną z programem MDAC).

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Trwa pobieranie danych XML przy użyciu CXMLAccessor

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) umożliwia dostęp do danych ze źródła danych jako dane ciągu w przypadku nie znajomości schematu magazynu danych. `CXMLAccessor` działa jak `CDynamicStringAccessorW` z tą różnicą, że pierwsza konwertuje wszystkie dane używane z magazynu danych jako danych (oznakowany) w formacie XML. Nazwy tagów XML jako najdokładniej dopasować nazw kolumn w magazynie danych.

Użyj `CXMLAccessor` tak jak inne akcesora przekazanie jej jako parametr szablonu `CCommand` lub `CTable`:

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Użyj [getxmlrowdata —](../../data/oledb/cxmlaccessor-getxmlrowdata.md) do pobierania danych z tabeli o jeden wiersz w danym momencie, a następnie przejdź wierszy przy użyciu metod, takich jak `MoveNext`, na przykład:

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

Możesz użyć [getxmlcolumndata —](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) można pobrać informacji o kolumnie (typ danych) jako dane ciągu w formacie XML.

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)