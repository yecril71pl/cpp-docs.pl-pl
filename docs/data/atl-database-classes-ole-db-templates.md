---
title: Klasy baz danych ATL (Szablony OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: 76e9f49d4b394d0c807ca1f3d103ff325ded8a09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213502"
---
# <a name="atl-database-classes-ole-db-templates"></a>Klasy baz danych ATL (Szablony OLE DB)

Firma Microsoft oferuje kilka implementacji OLE DB, zestaw interfejsów COM, który zapewnia jednolity dostęp do danych w różnych źródłach i formatach informacyjnych.

Szablony OLE DB są C++ szablonami w ATL, które ułatwiają korzystanie z OLE DB technologii bazy danych przez dostarczanie klas, które implementują wiele powszechnie używanych interfejsów OLE DB.

Ta biblioteka szablonów zawiera dwie części:

- [OLE DB Szablony konsumentów](../data/oledb/ole-db-consumer-templates-cpp.md) Służy do implementowania aplikacji klienta OLE DB.

- [Szablony dostawców OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) Służy do implementowania aplikacji serwera OLE DB (dostawcy).

Ponadto [atrybuty konsumenta OLE DB](../windows/ole-db-consumer-attributes.md) zapewniają wygodny sposób tworzenia OLE DB konsumentów. Atrybuty OLE DB wstrzykiwają kod na podstawie szablonów konsumentów OLE DB do tworzenia roboczych OLE DB konsumentów.

Należy pamiętać, że biblioteka MFC zawiera jedną klasę [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), która wyświetla rekordy bazy danych w kontrolkach. Widok to widok formularza połączony bezpośrednio z obiektem `CRowset` i wyświetla pola obiektu `CRowset` w kontrolkach szablonu okna dialogowego.

Aby uzyskać więcej informacji, zobacz [programowanie OLE DB](../data/oledb/ole-db-programming.md) i [OLE DB Przewodnik programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Zobacz też

[Tworzenie konsumenta OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Tworzenie dostawcy OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Szablony dostawców OLE DB — dokumentacja](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Przykłady szablonów OLE DB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
