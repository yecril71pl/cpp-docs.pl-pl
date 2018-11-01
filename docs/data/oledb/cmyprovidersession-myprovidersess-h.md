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
ms.openlocfilehash: 75d0c8d871ca736be5e2c33829296b2760092e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568015"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*Niestandardowe*Sess.H zawiera deklarację i implementację obiektu sesji OLE DB. Obiekt źródła danych tworzy obiekt sesji i reprezentuje konwersacje między: klienta oraz dostawcy. Kilka jednoczesnych sesji może być otwarty dla jednego źródła danych. Na liście dziedziczenia dla `CCustomSession` poniżej:

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

Dziedziczy obiektu session `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, i `IDBCreateCommand`. `IGetDataSource` Interfejs umożliwia sesję, aby pobrać źródła danych, w której został utworzony. Jest to przydatne, jeśli zajdzie potrzeba przywrócenia właściwości źródła danych, który został utworzony lub inne informacje, które źródło danych może zapewnić. `ISessionProperties` Interfejs obsługuje wszystkie właściwości dla tej sesji. `IOpenRowset` i `IDBCreateCommand` interfejsy są używane do wykonania pracy bazy danych. Jeśli dostawca obsługuje poleceń, implementuje `IDBCreateCommand` interfejsu. Służy do tworzenia obiektu polecenia, które można wykonać polecenia. Dostawca zawsze implementuje `IOpenRowset` obiektu. Służy do generowania zestawu wierszy od dostawcy. Jest domyślnego zestawu wierszy (na przykład `"select * from mytable"`) od dostawcy.

Kreator generuje również trzy klasy sesji: `CCustomSessionColSchema`, `CCustomSessionPTSchema`, i `CCustomSessionTRSchema`. Sesje te są używane do zestawów wierszy schematu. Zestawy wierszy schematu umożliwiają dostawcy w celu zwracania metadanych do użytkownika bez konsumenta o do wykonywania zapytań lub pobierania danych. Pobieranie metadanych może być znacznie szybciej niż wyszukiwanie możliwości dostawcy.

Specyfikacja OLE DB wymaga, aby dostawców Implementowanie `IDBSchemaRowset` typów zestawów wierszy schematu obsługę trzech interfejsu: DBSCHEMA_COLUMNS DBSCHEMA_PROVIDER_TYPES i DBSCHEMA_TABLES. Kreator generuje implementacje dla każdego zestawu wierszy schematu. Każda klasa generowane przez kreatora zawiera `Execute` metody. W tym `Execute` metody mogą zwracać dane do dostawcy o tym, które tabele, kolumny i typy danych obsługują. Te dane, jest znany w czasie kompilacji.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
