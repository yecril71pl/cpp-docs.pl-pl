---
title: Klasy baz danych ATL (Szablony OLE DB)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: dc016a5e1e1d9652f6a69f73b5760f42dec5e889
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222558"
---
# <a name="atl-database-classes-ole-db-templates"></a>Klasy baz danych ATL (Szablony OLE DB)

Firma Microsoft udostępnia kilka implementacji OLE DB, zbiór interfejsów COM, które udostępniają jednolity dostęp do danych z różnymi źródłami informacji i formatów.

Szablony OLE DB są szablonami języka C++ w ATL, które ułatwiają korzystanie, zapewniając klas implementujących wiele powszechnie używanych interfejsów OLE DB technologii baz danych OLE DB.

Ta biblioteka szablon zawiera dwie części:

- [Szablony konsumentów OLE DB](../data/oledb/ole-db-consumer-templates-cpp.md) używaną do zaimplementowania aplikacja kliencka (użytkownik) OLE DB.

- [Szablony dostawców OLE DB](../data/oledb/ole-db-provider-templates-cpp.md) używany do implementowania aplikacji serwera (dostawca) OLE DB.

Ponadto [atrybuty konsumentów OLE DB](../windows/ole-db-consumer-attributes.md) zapewniają wygodny sposób, aby utworzyć konsumentów OLE DB. Atrybuty OLE DB wstrzyknięcie kodu, w oparciu o szablony konsumentów OLE DB, aby utworzyć konsumentów OLE DB pracy.

Należy pamiętać, że biblioteka MFC zawiera jedną klasę [COleDBRecordView](../mfc/reference/coledbrecordview-class.md), który wyświetla rekordy bazy danych w kontrolkach. Widok jest podłączone bezpośrednio do widoku formularza `CRowset` obiektu, a następnie wyświetla pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego.

Aby uzyskać więcej informacji, zobacz [OLE DB programowania](../data/oledb/ole-db-programming.md) i [OLE DB przewodnik](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

## <a name="see-also"></a>Zobacz także

[Tworzenie konsumenta OLE DB](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[Tworzenie dostawcy OLE DB](../data/oledb/creating-an-ole-db-provider.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Szablony dostawców OLE DB — dokumentacja](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Przykłady szablonów OLE DB](https://github.com/Microsoft/VCSamples)
