---
title: CMyProviderSession (MyProviderSess.H) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyprovidersession
- myprovidersess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4ffb1a0ca8e9a2cd5b90d33c21423beb0969a4f4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="cmyprovidersession-myprovidersessh"></a>CMyProviderSession (MyProviderSess.H)
MyProviderSess.H zawiera deklarację i implementację dla obiekt sesji OLE DB. Obiekt źródła danych tworzy obiekt sesji i przedstawia konwersację między klienta oraz dostawcy. Kilka jednoczesnych sesji może być otwarty dla jednego źródła danych. Na liście dziedziczenia `CMyProviderSession` następuje:  
  
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
  
 Obiekt sesji dziedziczy **IGetDataSource**, `IOpenRowset`, **ISessionProperties**, i **IDBCreateCommand**. **IGetDataSource** interfejs umożliwiający sesji do pobrania źródła danych, który go utworzył. Jest to przydatne, jeśli chcesz pobrać właściwości źródła danych, który został utworzony lub inne informacje, które zapewniają źródła danych. **ISessionProperties** interfejs obsługuje wszystkie właściwości w sesji. `IOpenRowset` i **IDBCreateCommand** interfejsy są używane w pracy bazy danych. Jeśli dostawca obsługuje poleceń, implementuje **IDBCreateCommand** interfejsu. Jest on użyty do utworzenia obiektu polecenia, które można wykonać polecenia. Dostawca zawsze implementuje `IOpenRowset` obiektu. Służy do generowania prosty zestaw wierszy od dostawcy. Jest wierszy domyślnej (na przykład `"select * from mytable"`) od dostawcy.  
  
 Kreator również generuje trzy klasy sesji: `CMyProviderSessionColSchema`, `CMyProviderSessionPTSchema`, i `CMyProviderSessionTRSchema`. Sesje te są używane dla zestawów wierszy schematu. Zestawy wierszy schematu umożliwiają dostawcy do zwracania metadanych do użytkownika bez konsumenta konieczności wykonania zapytania lub pobierania danych. Pobieranie metadanych może być znacznie szybciej niż wykrywania możliwości dostawców.  
  
 Specyfikacja OLE DB wymaga, aby implementowanie dostawcy **IDBSchemaRowset** typów zestawu wierszy schematu Obsługa trzech interfejsu: **DBSCHEMA_COLUMNS**, **DBSCHEMA_PROVIDER_TYPES** , i `DBSCHEMA_TABLES`. Kreator generuje implementacji dla każdego zestawu wierszy schematu. Każda klasa generowane przez kreatora zawiera `Execute` metody. W tym `Execute` metoda może zwracać dane do dostawcy, o których tabel, kolumn i typy danych obsługiwane. Te dane zwykle jest znany w czasie kompilacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)