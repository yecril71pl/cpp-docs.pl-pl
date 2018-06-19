---
title: Źródła danych (ODBC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 842a8bf3faadcf96b4f44441e45dc94d5679f9f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087877"
---
# <a name="data-source-odbc"></a>Źródło danych (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W terminologii baz danych źródła danych jest określony zbiór danych, informacje wymagane do uzyskania dostępu do danych oraz lokalizację źródła danych, które można opisać za pomocą nazwy źródła danych. Aby pracować z klasy [cdatabase —](../../mfc/reference/cdatabase-class.md), źródło danych musi być taki, który został skonfigurowany przez administratora otwarte połączenie bazy danych (ODBC). Przykładami źródeł danych zdalnej bazy danych z programu Microsoft SQL Server w sieci lub pliku programu Microsoft Access w katalogu lokalnym. Z aplikacji można uzyskać dostępu do dowolnego źródła danych, dla którego masz sterownik ODBC.  
  
 Może mieć co najmniej jedno źródło danych active w aplikacji w tym samym czasie, z których każdy reprezentowany przez `CDatabase` obiektu. Można również mieć wiele równoczesnych połączeń do dowolnego źródła danych. Można nawiązać zdalnego, jak również do źródeł danych lokalnych, w zależności od zainstalowanych sterowników oraz możliwości sterowników ODBC. Aby uzyskać więcej informacji dotyczących źródła danych i ODBC Administrator, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC Administrator](../../data/odbc/odbc-administrator.md).  
  
 W poniższych tematach opisano więcej informacji o źródłach danych:  
  
-   [Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)