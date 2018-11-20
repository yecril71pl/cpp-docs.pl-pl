---
title: Źródła i sesje danych
ms.date: 11/19/2018
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
ms.openlocfilehash: c43061ccb462fe472821c76251430b5e3b0f0809
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175304"
---
# <a name="data-sources-and-sessions"></a>Źródła i sesje danych

Na poniższej ilustracji przedstawiono klas, które obsługują łączenie się i uzyskiwania dostępu do źródła danych. Każda klasa zależy od standardowej implementacji składnika OLE DB.

![Klasy danych źródła i sesji](../../data/oledb/media/vcdatasourcesessionclasses.gif "klas danych źródła i sesji") <br/>
Klasy sesji i źródła danych

Dostępne są następujące klasy:

- [CDataSource](../../data/oledb/cdatasource-class.md) tej klasy tworzy wystąpienie obiektu źródła danych, które tworzy i zarządza nimi połączenie ze źródłem danych za pośrednictwem dostawcy OLE DB. Źródło danych ma informacje, takie jak adres i uwierzytelniania informacje o źródle danych w postaci ciągu połączenia.

   Warto również zauważyć, że klasa pomocy [CEnumerator](../../data/oledb/cenumerator-class.md) jest często używana, zanim wszystkie połączenie zostanie nawiązane, aby uzyskać listę dostępnych dostawców zarejestrowanych w systemie. Dzięki temu można wybrać dostawcę jako źródła danych. Na przykład **właściwości Linku danych** okno dialogowe korzysta z tej klasy do wypełniania listy dostawców na **dostawców** kartę. Jego jest równa `SQLBrowseConnect` lub `SQLDriverConnect` funkcji.

- [CSession](../../data/oledb/csession-class.md) tej klasy tworzy wystąpienie obiektu sesji, który reprezentuje sesję jednolity dostęp do źródła danych. Jednak można utworzyć wiele sesji na źródle danych. Dla każdej sesji można utworzyć zestawy wierszy polecenia i innych obiektów dostępu do danych ze źródła danych. Sesja obsługuje transakcji.

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)