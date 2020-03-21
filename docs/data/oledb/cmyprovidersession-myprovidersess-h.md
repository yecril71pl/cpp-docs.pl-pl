---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079755"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Niestandardowe* Sess. H zawiera deklarację i implementację dla obiektu sesji OLE DB. Obiekt źródła danych tworzy obiekt sesji i reprezentuje konwersację między odbiorcą i dostawcą. Kilka równoczesnych sesji może być otwartych dla jednego źródła danych. Lista dziedziczenia dla `CCustomSession` jest następująca:

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

Obiekt Session dziedziczy po `IGetDataSource`, `IOpenRowset`, `ISessionProperties`i `IDBCreateCommand`. Interfejs `IGetDataSource` umożliwia sesji do pobrania źródła danych, które je utworzyło. Jest to przydatne, jeśli trzeba uzyskać właściwości ze źródła danych, które zostało utworzone przez Ciebie, lub inne informacje, które może dostarczyć źródło danych. Interfejs `ISessionProperties` obsługuje wszystkie właściwości sesji. Interfejsy `IOpenRowset` i `IDBCreateCommand` służą do działania bazy danych. Jeśli dostawca obsługuje polecenia, implementuje interfejs `IDBCreateCommand`. Służy do tworzenia obiektu polecenia, który może wykonywać polecenia. Dostawca zawsze implementuje obiekt `IOpenRowset`. Służy do generowania zestawu wierszy od dostawcy. Jest to domyślny zestaw wierszy (na przykład `"select * from mytable"`) od dostawcy.

Kreator generuje również trzy klasy sesji: `CCustomSessionColSchema`, `CCustomSessionPTSchema`i `CCustomSessionTRSchema`. Te sesje są używane dla zestawów wierszy schematu. Zestawy wierszy schematu umożliwiają dostawcy zwracanie metadanych do konsumenta bez konieczności wykonywania zapytania lub pobierania danych. Pobieranie metadanych może być bardzo szybsze niż znalezienie możliwości dostawcy.

Specyfikacja OLE DB wymaga, aby dostawcy implementujący interfejs `IDBSchemaRowset` obsługiwały trzy typy zestawów wierszy schematu: DBSCHEMA_COLUMNS, DBSCHEMA_PROVIDER_TYPES i DBSCHEMA_TABLES. Kreator generuje implementacje dla każdego zestawu wierszy schematu. Każda Klasa generowana przez kreatora zawiera metodę `Execute`. W tej metodzie `Execute` można zwrócić do dostawcy dane dotyczące tabel, kolumn i typów danych obsługiwanych przez użytkownika. Te dane są znane w czasie kompilacji.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
