---
title: "Źródła i sesje danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data sources [C++], OLE DB
- connections [C++], data source
- OLE DB consumer templates [C++], data sources
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2bb675897e29a26446b3070b2192b4f5c3e8fd2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-sources-and-sessions"></a>Źródła i sesje danych
Na poniższej ilustracji przedstawiono klasy, które obsługuje połączenie i dostęp do źródła danych. Każda klasa zależy od standardowej implementacji składnika OLE DB.  
  
 ![Klasy danych źródła i sesji](../../data/oledb/media/vcdatasourcesessionclasses.gif "vcdatasourcesessionclasses")  
Źródło danych i klasy sesji  
  
 Występują następujące klasy:  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md) obiektu źródła danych, które tworzy i którymi zarządza połączenia ze źródłem danych za pośrednictwem dostawcy OLE DB tworzy wystąpienie tej klasy. Źródło danych ma informacje, takie jak adres i uwierzytelniania informacje o źródle danych w postaci ciągu połączenia.  
  
     Warto również zauważyć, że klasa pomocy [CEnumerator](../../data/oledb/cenumerator-class.md) jest często używana, zanim wszystkie połączenie zostanie nawiązane, aby uzyskać listę dostępnych dostawców zarejestrowanych w systemie. Dzięki temu można wybrać dostawcę jako źródła danych. Na przykład **właściwości Linku danych** okno dialogowe korzysta z tej klasy do wypełnienia listy dostawców na **dostawców** kartę. Jest to równoważne **procedura SQLBrowseConnect** lub **SQLDriverConnect** funkcji.  
  
-   [CSession](../../data/oledb/csession-class.md) obiektu sesji, który reprezentuje sesję pojedynczy dostęp do źródła danych tworzy wystąpienie tej klasy. Można jednak utworzyć wiele sesji, w źródle danych. Dla każdej sesji można utworzyć zestawy wierszy poleceń i inne obiekty dostępu do danych ze źródła danych. Sesja obsługuje transakcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)