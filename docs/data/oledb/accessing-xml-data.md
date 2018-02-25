---
title: "Uzyskiwanie dostępu do danych XML | Dokumentacja firmy Microsoft"
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
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c25e5019ebe930cec1dc5cf7c547e9bc03a3ffa8
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="accessing-xml-data"></a>Uzyskiwanie dostępu do danych XML
Istnieją dwie metody oddzielne polegającym na pobieranie danych XML źródła danych: jeden używa [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) i innych celów [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Funkcja|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|Ilość danych przesyłanych|Pobiera dane ze wszystkich kolumn i wierszy jednocześnie.|Pobiera dane z wszystkich kolumn, ale tylko jeden wiersz jednocześnie. Musisz przejść wierszy przy użyciu metod, takich jak `MoveNext`.|  
|Ciąg formatowania|SQL Server formaty ciągu XML i wysyła go do użytkownika.|Pobiera dane zestawu wierszy w formacie native (liczba żądań, które dostawca wysłać jako ciągów Unicode), a następnie tworzy ciąg zawierający dane w formacie XML.|  
|Kontrola nad formatowania|Masz pewnego poziomu kontroli nad jak ciąg XML jest formatowany przy niektórych właściwości specyficzne dla programu SQL Server 2000.|Użytkownik nie kontrolują format wygenerowanego ciągu XML.|  
  
 Gdy `CStreamRowset` zawiera więcej ogólnej wydajny sposób pobierania danych w formacie XML, jest obsługiwana tylko przez program SQL Server 2000.  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>Pobieranie danych XML przy użyciu cstreamrowset —  
 Należy określić [cstreamrowset —](../../data/oledb/cstreamrowset-class.md) jako typ zestawu wierszy w Twojej `CCommand` lub `CTable` deklaracji. Służy on z własną metodę dostępu lub nie dostępu na przykład:  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 —lub—  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 Zwykle podczas wywoływania `CCommand::Open` (Określanie, na przykład `CRowset` jako `TRowset` klasy), uzyska `IRowset` wskaźnika. `ICommand::Execute` Zwraca `IRowset` wskaźnika, który jest przechowywany w `m_spRowset` członkiem `CRowset` obiektu. Metody, takie jak `MoveFirst`, `MoveNext`, i `GetData` za pomocą tego wskaźnika do pobierania danych.  
  
 Z drugiej strony, gdy jest wywoływana `CCommand::Open` (ale określ `CStreamRowset` jako `TRowset` klasy), `ICommand::Execute` zwraca `ISequentialStream` wskaźnika, który jest przechowywany w `m_spStream` elementu członkowskiego danych [cstreamrowset —](../../data/oledb/cstreamrowset-class.md). Następnie należy użyć `Read` metody do pobierania danych (ciąg Unicode) w formacie XML. Na przykład:  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 przeprowadza formatowanie XML i zwraca wszystkie kolumny i wszystkie wiersze z zestawu wierszy w postaci jednego ciągu XML.  
  
 Na przykład za pomocą `Read` metody, zobacz "Dodawanie XML pomocy technicznej do użytkownika" w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
>  Obsługa języka XML przy użyciu `CStreamRowset` działa tylko z programem SQL Server 2000 i mieć dostawcy OLE DB dla programu SQL Server 2000 (zainstalowaną z programem MDAC).  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Pobieranie danych XML przy użyciu CXMLAccessor  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) umożliwia dostęp do danych z źródła danych jako ciągu dane podczas nie znają schematu magazynu danych. `CXMLAccessor` jak działa `CDynamicStringAccessorW` z tą różnicą, że pierwsza konwertuje wszystkie dane uzyskiwane ze źródła danych jako dane (oznakowany) w formacie XML. Nazwy tagów XML możliwie najbardziej zgodne nazwy kolumn w magazynie danych.  
  
 Użyj `CXMLAccessor` jak w przypadku dowolnej klasy akcesor przekazaniem go jako parametr szablonu `CCommand` lub `CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 Użyj [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) do pobierania danych z tabeli o jeden wiersz w czasie, a następnie przejdź wierszy przy użyciu metod, takich jak `MoveNext`, na przykład:  
  
```  
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
  
 Można użyć [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) można pobrać informacji o kolumnie (typ danych) jako ciąg w formacie XML dane.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)