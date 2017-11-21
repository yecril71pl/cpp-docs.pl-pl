---
title: "Źródła danych (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0236c8684c37b0378dd7ebead37d2c9c44cf1d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-odbc"></a>Źródło danych (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W terminologii baz danych źródła danych jest określony zbiór danych, informacje wymagane do uzyskania dostępu do danych oraz lokalizację źródła danych, które można opisać za pomocą nazwy źródła danych. Aby pracować z klasy [cdatabase —](../../mfc/reference/cdatabase-class.md), źródło danych musi być taki, który został skonfigurowany przez administratora otwarte połączenie bazy danych (ODBC). Przykładami źródeł danych zdalnej bazy danych z programu Microsoft SQL Server w sieci lub pliku programu Microsoft Access w katalogu lokalnym. Z aplikacji można uzyskać dostępu do dowolnego źródła danych, dla którego masz sterownik ODBC.  
  
 Może mieć co najmniej jedno źródło danych active w aplikacji w tym samym czasie, z których każdy reprezentowany przez `CDatabase` obiektu. Można również mieć wiele równoczesnych połączeń do dowolnego źródła danych. Można nawiązać zdalnego, jak również do źródeł danych lokalnych, w zależności od zainstalowanych sterowników oraz możliwości sterowników ODBC. Aby uzyskać więcej informacji dotyczących źródła danych i ODBC Administrator, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC Administrator](../../data/odbc/odbc-administrator.md).  
  
 W poniższych tematach opisano więcej informacji o źródłach danych:  
  
-   [Źródło danych: Zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Źródło danych: Określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)