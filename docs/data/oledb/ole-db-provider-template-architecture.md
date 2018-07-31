---
title: Architektura szablonu dostawcy OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2ce756cbeae87c33ec612b8c2665f27249e9ecf7
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339942"
---
# <a name="ole-db-provider-template-architecture"></a>Architektura szablonu dostawcy OLE DB
## <a name="data-sources-and-sessions"></a>Źródła i sesje danych  
 Architektura dostawcy OLE DB zawiera obiekt źródła danych i co najmniej jednej sesji. Obiekt źródła danych jest początkowa obiekt, który każdy dostawca musi utworzyć wystąpienie. Gdy aplikacja konsumenta musi danych, wspólnie tworzy obiekt źródła danych można uruchomić dostawcy. Obiekt źródła danych tworzy obiekt sesji (za pomocą `IDBCreateSession` interfejsu) za pomocą której użytkownik łączy się z obiektu źródła danych. Programiści ODBC można traktować obiektu źródła danych jako równoważne `HENV` i obiektu sesji jako odpowiednik `HDBC`.  
  
 ![Architektura dostawcy](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 Wraz z plików źródłowych, tworzone przez kreatora dostawcy bazy danych OLE szablony OLE DB implementuje obiektu źródła danych. Sesja jest obiektem, który odpowiada OLE DB `TSession`.  
  
## <a name="mandatory-and-optional-interfaces"></a>Interfejsy obowiązkowych i opcjonalnych  
 Szablony dostawców OLE DB zapewniają to wstępnie spakowane zestawy implementacje dla wszystkich wymaganych interfejsów. Interfejsy obowiązkowe i opcjonalne są definiowane przez OLE DB dla kilku typów obiektów:  
  
-   [Źródło danych](../../data/oledb/data-source-object-interfaces.md)  
  
-   [Sesja](../../data/oledb/session-object-interfaces.md)  
  
-   [Zestaw wierszy](../../data/oledb/rowset-object-interfaces.md)  
  
-   [Polecenie](../../data/oledb/command-object-interfaces.md)  
  
-   [Transakcja](../../data/oledb/transaction-object-interfaces.md)  
  
 Należy pamiętać, szablony dostawców OLE DB nie należy implementować wiersza i przechowywania obiektów.  
  
 Poniższa tabela zawiera listę obowiązkowych i opcjonalnych interfejsów obiektów wymienione powyżej, zgodnie z opisem w [OLE DB 2.6 dokumentacji zestawu SDK](https://msdn.microsoft.com/library/ms722784.aspx).  
  
|Składnik|Interface|Komentarz|  
|---------------|---------------|-------------|  
|[Źródło danych](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|[wymagane] `IDBCreateSession`<br /><br /> [wymagane] `IDBInitialize`<br /><br /> [wymagane] `IDBProperties`<br /><br /> [wymagane] `IPersist`<br /><br /> [opcjonalnie] `IConnectionPointContainer`<br /><br /> [opcjonalnie] `IDBAsynchStatus`<br /><br /> [opcjonalnie] `IDBDataSourceAdmin`<br /><br /> [opcjonalnie] `IDBInfo`<br /><br /> [opcjonalnie] `IPersistFile`<br /><br /> [opcjonalnie] `ISupportErrorInfo`|Połączenie od użytkownika dostawcy. Obiekt jest używany do określania właściwości połączenia, takie jak nazwa źródłowego Identyfikatora, hasła i dane użytkownika. Obiekt można także do administrowania źródła danych (Tworzenie, aktualizowanie, usuwanie tabel i tak dalej).|  
|[Sesja](../../data/oledb/session-object-interfaces.md) ([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[wymagane] `IGetDataSource`<br /><br /> [wymagane] `IOpenRowset`<br /><br /> [wymagane] `ISessionProperties`<br /><br /> [opcjonalnie] `IAlterIndex`<br /><br /> [opcjonalnie] `IAlterTable`<br /><br /> [opcjonalnie] `IBindResource`<br /><br /> [opcjonalnie] `ICreateRow`<br /><br /> [opcjonalnie] `IDBCreateCommand`<br /><br /> [opcjonalnie] `IDBSchemaRowset`<br /><br /> [opcjonalnie] `IIndexDefinition`<br /><br /> [opcjonalnie] `ISupportErrorInfo`<br /><br /> [opcjonalnie] `ITableCreation`<br /><br /> [opcjonalnie] `ITableDefinition`<br /><br /> [opcjonalnie] `ITableDefinitionWithConstraints`<br /><br /> [opcjonalnie] `ITransaction`<br /><br /> [opcjonalnie] `ITransactionJoin`<br /><br /> [opcjonalnie] `ITransactionLocal`<br /><br /> [opcjonalnie] `ITransactionObject`|Obiekt sesji reprezentuje pojedynczy konwersacje między: klienta oraz dostawcy. Przypomina nieco ODBC `HSTMT` , może istnieć wiele jednoczesnych sesji aktywnych.<br /><br /> Obiekt sesji jest linku podstawowego, aby uzyskać dostęp do funkcji OLE DB. Aby przejść do polecenia, transakcji lub obiektu zestawu wierszy, można przejść przez obiekt sesji.|  
|[Zestaw wierszy](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[wymagane] `IAccessor`<br /><br /> [wymagane] `IColumnsInfo`<br /><br /> [wymagane] `IConvertType`<br /><br /> [wymagane] `IRowset`<br /><br /> [wymagane] `IRowsetInfo`<br /><br /> [opcjonalnie] `IChapteredRowset`<br /><br /> [opcjonalnie] `IColumnsInfo2`<br /><br /> [opcjonalnie] `IColumnsRowset`<br /><br /> [opcjonalnie] `IConnectionPointContainer`<br /><br /> [opcjonalnie] `IDBAsynchStatus`<br /><br /> [opcjonalnie] `IGetRow`<br /><br /> [opcjonalnie] `IRowsetChange`<br /><br /> [opcjonalnie] `IRowsetChapterMember`<br /><br /> [opcjonalnie] `IRowsetCurrentIndex`<br /><br /> [opcjonalnie] `IRowsetFind`<br /><br /> [opcjonalnie] `IRowsetIdentity`<br /><br /> [opcjonalnie] `IRowsetIndex`<br /><br /> [opcjonalnie] `IRowsetLocate`<br /><br /> [opcjonalnie] `IRowsetRefresh`<br /><br /> [opcjonalnie] `IRowsetScroll`<br /><br /> [opcjonalnie] `IRowsetUpdate`<br /><br /> [opcjonalnie] `IRowsetView`<br /><br /> [opcjonalnie] `ISupportErrorInfo`<br /><br /> [opcjonalnie] `IRowsetBookmark`|Obiektu zestawu wierszy reprezentuje dane ze źródła danych. Obiekt jest odpowiedzialny za powiązań danych i wszystkie podstawowe operacje (aktualizacja, pobieranie, przenoszenia i inne), na tych danych. Zawsze masz obiektu zestawu wierszy, aby zawierało i manipulowanie danymi.|  
|[Polecenie](../../data/oledb/command-object-interfaces.md) ([CCommand](http://msdn.microsoft.com/52bef5da-c1a0-4223-b4e6-9e464b6db409))|[wymagane] `IAccessor`<br /><br /> [wymagane] `IColumnsInfo`<br /><br /> [wymagane] `ICommand`<br /><br /> [wymagane] `ICommandProperties`<br /><br /> [wymagane] `ICommandText`<br /><br /> [wymagane] `IConvertType`<br /><br /> [opcjonalnie] `IColumnsRowset`<br /><br /> [opcjonalnie] `ICommandPersist`<br /><br /> [opcjonalnie] `ICommandPrepare`<br /><br /> [opcjonalnie] `ICommandWithParameters`<br /><br /> [opcjonalnie] `ISupportErrorInfo`<br /><br /> [opcjonalnie] `ICommandStream`|Obiekt polecenia obsługuje operacje na danych, takich jak zapytania. Może obsługiwać instrukcji sparametryzowanych lub bez parametrów.<br /><br /> Obiekt polecenia jest również odpowiedzialny za obsługę powiązania parametrów i kolumn danych wyjściowych. Powiązanie to struktura, która zawiera informacje dotyczące sposobu kolumną w zestawie wierszy, powinny zostać pobrane. Zawiera on informacje, takie jak liczba porządkowa, typ danych, długość i stanu.|  
|[Transakcja](../../data/oledb/transaction-object-interfaces.md) (opcjonalnie)|[wymagane] `IConnectionPointContainer`<br /><br /> [wymagane] `ITransaction`<br /><br /> [opcjonalnie] `ISupportErrorInfo`|Obiekt transakcji definiuje pojedynczej Atomowej jednostki pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie nawzajem. Ten obiekt nie jest bezpośrednio obsługiwany przez Szablony dostawców OLE DB (czyli tworzenia własnego obiektu).|  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Mapy właściwości](../../data/oledb/property-maps.md)  
  
-   [Rekord użytkownika](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB interfejsów](https://msdn.microsoft.com/library/ms709709.aspx)