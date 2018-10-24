---
title: Źródła i sesje danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a1904c0b0c416c216a28ddcaf7bb20ce408ba0a
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2018
ms.locfileid: "49989947"
---
# <a name="data-sources-and-sessions"></a>Źródła i sesje danych

Na poniższej ilustracji przedstawiono klas, które obsługują łączenie się i uzyskiwania dostępu do źródła danych. Każda klasa zależy od standardowej implementacji składnika OLE DB.  
  
![Klasy danych źródła i sesji](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
Klasy sesji i źródła danych  
  
Dostępne są następujące klasy:  
  
- [CDataSource](../../data/oledb/cdatasource-class.md) tej klasy tworzy wystąpienie obiektu źródła danych, które tworzy i zarządza nimi połączenie ze źródłem danych za pośrednictwem dostawcy OLE DB. Źródło danych ma informacje, takie jak adres i uwierzytelniania informacje o źródle danych w postaci ciągu połączenia.  
  
     Warto również zauważyć, że klasa pomocy [CEnumerator](../../data/oledb/cenumerator-class.md) jest często używana, zanim wszystkie połączenie zostanie nawiązane, aby uzyskać listę dostępnych dostawców zarejestrowanych w systemie. Dzięki temu można wybrać dostawcę jako źródła danych. Na przykład **właściwości Linku danych** okno dialogowe korzysta z tej klasy do wypełniania listy dostawców na **dostawców** kartę. Jego jest równa `SQLBrowseConnect` lub `SQLDriverConnect` funkcji.  
  
- [CSession](../../data/oledb/csession-class.md) tej klasy tworzy wystąpienie obiektu sesji, który reprezentuje sesję jednolity dostęp do źródła danych. Jednak można utworzyć wiele sesji na źródle danych. Dla każdej sesji można utworzyć zestawy wierszy polecenia i innych obiektów dostępu do danych ze źródła danych. Sesja obsługuje transakcji.  
  
## <a name="see-also"></a>Zobacz też  

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)