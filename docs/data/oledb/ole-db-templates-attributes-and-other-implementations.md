---
title: Szablony i atrybuty OLE DB oraz inne implementacje
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 217db304c7d0b5723b7af383e07290f160cc9465
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500919"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>Szablony i atrybuty OLE DB oraz inne implementacje

## <a name="atl-ole-db-templates"></a>Szablony OLE DB ATL

Szablony OLE DB, które są częścią ATL (Active Template Library), ułatwiają korzystanie z wysokiej wydajności OLE DBj bazy danych, zapewniając klasy, które implementują wiele powszechnie używanych interfejsów OLE DB. Wraz z tą biblioteką szablonów jest dostępna obsługa Kreatora tworzenia OLE DB aplikacji początkowych.

Ta biblioteka szablonów zawiera dwie części:

- **OLE DB Szablony konsumentów** Służy do implementowania aplikacji klienta OLE DB.

- **Szablony dostawców OLE DB** Służy do implementowania aplikacji serwera OLE DB (dostawcy).

Aby korzystać z szablonów OLE DB, należy zapoznać się z szablonami języka C++, COM i OLE DB. Jeśli nie znasz OLE DB, zobacz [OLE DB Dokumentacja programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming).

Aby uzyskać więcej informacji, możesz:

- Zapoznaj się z tematami dotyczącymi [szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md) lub [szablonów dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

- Utwórz [klienta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md) lub [OLE DB dostawcę](../../data/oledb/creating-an-ole-db-provider.md).

- Zobacz listę [klas konsumenckich OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) lub [OLE DB klas dostawcy](../../data/oledb/ole-db-provider-templates-reference.md).

- Zapoznaj się z listą [przykładów OLE DB szablonów](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB).

- Zobacz [odwołanie OLE DB programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (w Windows SDK).

## <a name="ole-db-attributes"></a>Atrybuty OLE DB

[OLE DB atrybuty konsumenta](../../windows/attributes/ole-db-consumer-attributes.md) zapewniają wygodny sposób tworzenia OLE DB konsumentów. Atrybuty OLE DB wstrzyknąć kod na podstawie [szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) do tworzenia roboczych OLE DB odbiorców i dostawców. Jeśli konieczne jest określenie funkcji nieobsługiwanych przez atrybuty, można użyć szablonów OLE DB w połączeniu z atrybutami w kodzie.

## <a name="mfc-ole-db-classes"></a>Klasy MFC OLE DB

Biblioteka MFC ma jedną klasę [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), która wyświetla rekordy bazy danych w kontrolkach. Widok to widok formularza połączony bezpośrednio z `CRowset` obiektem i wyświetla pola `CRowset` obiektu w kontrolkach szablonu okna dialogowego. Udostępnia również domyślną implementację do przechodzenia do pierwszego, następnego, poprzedniego lub ostatniego rekordu oraz interfejs do aktualizowania rekordu aktualnie w widoku. Aby uzyskać więcej informacji, zobacz `COleDBRecordView`.

## <a name="ole-db-sdk-interfaces"></a>Interfejsy zestawu SDK OLE DB

W przypadkach, w których szablony OLE DB nie obsługują funkcji OLE DB, należy użyć samych interfejsów OLE DB. Aby uzyskać więcej informacji, zobacz [OLE DB dereferencja programisty](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)
