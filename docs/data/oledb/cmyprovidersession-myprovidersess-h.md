---
title: CMyProviderSession (MyProviderSess.H) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6bc3a9d377592b16c7e90cf0e75a6fba0eb00a64
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340130"
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H zawiera deklarację i implementację obiektu sesji OLE DB. Obiekt źródła danych tworzy obiekt sesji i reprezentuje konwersacje między: klienta oraz dostawcy. Kilka jednoczesnych sesji może być otwarty dla jednego źródła danych. Na liście dziedziczenia dla `CMyProviderSession` poniżej:  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSession  
class ATL_NO_VTABLE CMyProviderSession :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IGetDataSourceImpl<CMyProviderSession>,  
   public IOpenRowsetImpl<CMyProviderSession>,  
   public ISessionPropertiesImpl<CMyProviderSession>,  
   public IObjectWithSiteSessionImpl<CMyProviderSession>,  
   public IDBSchemaRowsetImpl<CMyProviderSession>,  
   public IDBCreateCommandImpl<CMyProviderSession, CMyProviderCommand>  
```  
  
 Dziedziczy obiektu session `IGetDataSource`, `IOpenRowset`, `ISessionProperties`, i `IDBCreateCommand`. `IGetDataSource` Interfejs umożliwia sesję, aby pobrać źródła danych, w której został utworzony. Jest to przydatne, jeśli zajdzie potrzeba przywrócenia właściwości źródła danych, który został utworzony lub inne informacje, które źródło danych może zapewnić. `ISessionProperties` Interfejs obsługuje wszystkie właściwości dla tej sesji. `IOpenRowset` i `IDBCreateCommand` interfejsy są używane do wykonania pracy bazy danych. Jeśli dostawca obsługuje poleceń, implementuje `IDBCreateCommand` interfejsu. Służy do tworzenia obiektu polecenia, które można wykonać polecenia. Dostawca zawsze implementuje `IOpenRowset` obiektu. Służy do generowania prosty zestaw wierszy od dostawcy. Jest domyślnego zestawu wierszy (na przykład `"select * from mytable"`) od dostawcy.  
  
 Kreator generuje również trzy klasy sesji: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, i `CMyProviderSessionTRSchema`. Sesje te są używane do zestawów wierszy schematu. Zestawy wierszy schematu umożliwiają dostawcy w celu zwracania metadanych do użytkownika bez konsumenta o do wykonywania zapytań lub pobierania danych. Pobieranie metadanych może być znacznie szybciej niż wykrywanie możliwości dostawców.  
  
 Specyfikacja OLE DB wymaga, aby dostawców Implementowanie `IDBSchemaRowset` typów zestawów wierszy schematu obsługę trzech interfejsu: DBSCHEMA_COLUMNS DBSCHEMA_PROVIDER_TYPES i DBSCHEMA_TABLES. Kreator generuje implementacje dla każdego zestawu wierszy schematu. Każda klasa generowane przez kreatora zawiera `Execute` metody. W tym `Execute` metody mogą zwracać dane do dostawcy o tym, które tabele, kolumny i typy danych obsługują. Te dane, zwykle jest znany w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)