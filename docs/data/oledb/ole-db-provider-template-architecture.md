---
title: Architektura szablonu dostawcy OLE DB
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 89e07f95853c3611b7cceaef3f247c220c630add
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509550"
---
# <a name="ole-db-provider-template-architecture"></a>Architektura szablonu dostawcy OLE DB

## <a name="data-sources-and-sessions"></a>Źródła i sesje danych

Architektura dostawcy OLE DB obejmuje obiekt źródła danych i co najmniej jedną sesję. Obiekt źródła danych jest początkowym obiektem, który musi utworzyć wystąpienie każdego dostawcy. Gdy aplikacja klienta wymaga danych, współtworzy obiekt źródła danych, aby uruchomić dostawcę. Obiekt źródła danych tworzy obiekt sesji (przy użyciu `IDBCreateSession` interfejsu), za pośrednictwem którego odbiorca nawiązuje połączenie z obiektem źródła danych. Programiści ODBC mogą traktować obiekt źródła danych jako równoznaczny z `HENV` i obiektem sesji jako odpowiednikiem `HDBC` .

![Architektura dostawcy](../../data/oledb/media/vc4twb1.gif "Architektura dostawcy")

Wraz z plikami źródłowymi utworzonymi przez **Kreatora dostawcy OLE DB**szablony OLE DB implementują obiekt źródła danych. Sesja jest obiektem, który odnosi się do OLE DB `TSession` .

## <a name="mandatory-and-optional-interfaces"></a>Interfejsy obowiązkowe i opcjonalne

Szablony dostawcy OLE DB zapewniają implementacje wdrożone we wszystkich wymaganych interfejsach. Interfejsy obowiązkowe i opcjonalne są zdefiniowane przez OLE DB dla kilku typów obiektów:

- [Źródło danych](../../data/oledb/data-source-object-interfaces.md)

- [Sesja](../../data/oledb/session-object-interfaces.md)

- [Zestawu wierszy](../../data/oledb/rowset-object-interfaces.md)

- [Polecenie](../../data/oledb/command-object-interfaces.md)

- [Transakcja](../../data/oledb/transaction-object-interfaces.md)

Szablony dostawcy OLE DB nie implementują obiektów Row i Storage.

Poniższa tabela zawiera listę obowiązkowych i opcjonalnych interfejsów dla obiektów wymienionych powyżej, zgodnie z [dokumentacją zestawu OLE DB 2,6 SDK](/previous-versions/windows/desktop/ms722784(v=vs.85)).

|Składnik|Interfejs|Komentarz|
|---------------|---------------|-------------|
|[Źródło danych](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md))|wypełnione `IDBCreateSession`<br /><br /> wypełnione `IDBInitialize`<br /><br /> wypełnione `IDBProperties`<br /><br /> wypełnione `IPersist`<br /><br /> obowiązkowe `IConnectionPointContainer`<br /><br /> obowiązkowe `IDBAsynchStatus`<br /><br /> obowiązkowe `IDBDataSourceAdmin`<br /><br /> obowiązkowe `IDBInfo`<br /><br /> obowiązkowe `IPersistFile`<br /><br /> obowiązkowe `ISupportErrorInfo`|Połączenie od konsumenta do dostawcy. Obiekt służy do określania właściwości połączenia, takich jak identyfikator użytkownika, hasło i nazwa źródła danych. Obiekt może być również używany do administrowania źródłem danych (tworzenie, aktualizowanie, usuwanie, tabele itd.).|
|[Sesja](../../data/oledb/session-object-interfaces.md) ([CSession](./cdataconnection-class.md#op_csession_amp))|wypełnione `IGetDataSource`<br /><br /> wypełnione `IOpenRowset`<br /><br /> wypełnione `ISessionProperties`<br /><br /> obowiązkowe `IAlterIndex`<br /><br /> obowiązkowe `IAlterTable`<br /><br /> obowiązkowe `IBindResource`<br /><br /> obowiązkowe `ICreateRow`<br /><br /> obowiązkowe `IDBCreateCommand`<br /><br /> obowiązkowe `IDBSchemaRowset`<br /><br /> obowiązkowe `IIndexDefinition`<br /><br /> obowiązkowe `ISupportErrorInfo`<br /><br /> obowiązkowe `ITableCreation`<br /><br /> obowiązkowe `ITableDefinition`<br /><br /> obowiązkowe `ITableDefinitionWithConstraints`<br /><br /> obowiązkowe `ITransaction`<br /><br /> obowiązkowe `ITransactionJoin`<br /><br /> obowiązkowe `ITransactionLocal`<br /><br /> obowiązkowe `ITransactionObject`|Obiekt sesji jest jedną konwersacją między odbiorcą i dostawcą. Jest on podobny do ODBC `HSTMT` , ponieważ może istnieć wiele równoczesnych sesji.<br /><br /> Obiekt Session to podstawowy link do uzyskiwania OLE DB funkcji. Aby uzyskać dostęp do obiektu polecenia, transakcji lub zestawu wierszy, należy przejść przez obiekt sesji.|
|[Zestaw wierszy](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|wypełnione `IAccessor`<br /><br /> wypełnione `IColumnsInfo`<br /><br /> wypełnione `IConvertType`<br /><br /> wypełnione `IRowset`<br /><br /> wypełnione `IRowsetInfo`<br /><br /> obowiązkowe `IChapteredRowset`<br /><br /> obowiązkowe `IColumnsInfo2`<br /><br /> obowiązkowe `IColumnsRowset`<br /><br /> obowiązkowe `IConnectionPointContainer`<br /><br /> obowiązkowe `IDBAsynchStatus`<br /><br /> obowiązkowe `IGetRow`<br /><br /> obowiązkowe `IRowsetChange`<br /><br /> obowiązkowe `IRowsetChapterMember`<br /><br /> obowiązkowe `IRowsetCurrentIndex`<br /><br /> obowiązkowe `IRowsetFind`<br /><br /> obowiązkowe `IRowsetIdentity`<br /><br /> obowiązkowe `IRowsetIndex`<br /><br /> obowiązkowe `IRowsetLocate`<br /><br /> obowiązkowe `IRowsetRefresh`<br /><br /> obowiązkowe `IRowsetScroll`<br /><br /> obowiązkowe `IRowsetUpdate`<br /><br /> obowiązkowe `IRowsetView`<br /><br /> obowiązkowe `ISupportErrorInfo`<br /><br /> obowiązkowe `IRowsetBookmark`|Obiekt zestawu wierszy jest danymi ze źródła danych. Obiekt jest używany do powiązań tych danych i wszystkich operacji podstawowych (aktualizacja, pobieranie, przenoszenie i inne) danych. Zawsze masz obiekt zestawu wierszy, aby zachować dane i manipulować nimi.|
|[Polecenie](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md))|wypełnione `IAccessor`<br /><br /> wypełnione `IColumnsInfo`<br /><br /> wypełnione `ICommand`<br /><br /> wypełnione `ICommandProperties`<br /><br /> wypełnione `ICommandText`<br /><br /> wypełnione `IConvertType`<br /><br /> obowiązkowe `IColumnsRowset`<br /><br /> obowiązkowe `ICommandPersist`<br /><br /> obowiązkowe `ICommandPrepare`<br /><br /> obowiązkowe `ICommandWithParameters`<br /><br /> obowiązkowe `ISupportErrorInfo`<br /><br /> obowiązkowe `ICommandStream`|Obiekt Command obsługuje operacje na danych, takich jak zapytania. Może obsłużyć sparametryzowane lub niesparametryzowane instrukcje.<br /><br /> Obiekt Command jest również odpowiedzialny za obsługę powiązań dla parametrów i kolumn danych wyjściowych. Powiązanie to struktura, która zawiera informacje o sposobie pobierania kolumny w zestawie wierszy. Zawiera informacje, takie jak liczba porządkowa, typ danych, długość i stan.|
|[Transakcja](../../data/oledb/transaction-object-interfaces.md) (opcjonalnie)|wypełnione `IConnectionPointContainer`<br /><br /> wypełnione `ITransaction`<br /><br /> obowiązkowe `ISupportErrorInfo`|Obiekt Transaction definiuje niepodzielną jednostkę pracy w źródle danych i określa, jak te jednostki pracy odnoszą się do siebie. Ten obiekt nie jest bezpośrednio obsługiwany przez szablony dostawcy OLE DB (oznacza to, że tworzysz własny obiekt).|

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Mapy właściwości](../../data/oledb/property-maps.md)

- [Rekord użytkownika](../../data/oledb/user-record.md)

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Interfejsy OLE DB](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
