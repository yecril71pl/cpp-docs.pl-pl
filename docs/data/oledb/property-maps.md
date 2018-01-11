---
title: "Mapy właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 05bd576e6e55c94306a8dd648c57a4d606bed696
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="property-maps"></a>Mapy właściwości
Oprócz sesji, wierszy i obiektu polecenia opcjonalne każdy dostawca obsługuje co najmniej jednej właściwości. Te właściwości są definiowane w mapy właściwości zawarte w plikach nagłówka utworzone przez kreatora dostawcy bazy danych OLE. Każdy plik nagłówka zawiera mapy dla właściwości w grupie właściwości OLE DB zdefiniowane dla obiektu lub obiektów zdefiniowanych w tym pliku. Plik nagłówka, która zawiera obiekt źródła danych zawiera także mapę właściwości dla [właściwości DataSource](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx). Session.h zawiera mapę właściwości dla [właściwości sesji](https://msdn.microsoft.com/en-us/library/ms714221.aspx). Obiekt zestawu wierszy i polecenia znajdują się w pliku jeden nagłówek o nazwie *projectname*RS.h. Te właściwości są elementami członkowskimi [właściwości zestawu wierszy](https://msdn.microsoft.com/en-us/library/ms711252.aspx) grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)