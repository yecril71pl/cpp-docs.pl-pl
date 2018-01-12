---
title: Programowanie OLE DB | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df532b1ffdc8eba635af93f34e0d77fd3da0d115
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-programming"></a>Programowanie OLE DB
Microsoft OLE DB jest technologią starszej wersji; w przypadku nowych aplikacji jest wymagany dostęp do danych interfejsu API dla połączonych serwerów SQL. Wszystkie inne nowe aplikacje powinny używać ODBC. Bieżący dostawca OLE DB dla programu SQL Server jest SQLNCLI11. BIBLIOTEKI DLL. Dostawca jest nadal wysyłania w programie SQL Server 2016. Ta dokumentacja jest przeznaczony dla deweloperów, którzy są zachowaniu istniejących aplikacji, które już używają OLE DB.
  
 Szablony OLE DB są szablonów C++, które ułatwiają z technologii bazy danych OLE DB wysokiej wydajności korzystanie przez zapewnienie klasy, które implementują wiele powszechnie używanych interfejsy OLE DB. Ta biblioteka szablonów jest podzielona na szablony klienta i dostawcy.  
  
 Visual C++ ma również obsługę Kreatora tworzenia aplikacji starter OLE DB.  
  
 Ponadto można użyć atrybutów do zaimplementowania szablony konsumentów OLE DB.  
  
|Aby dowiedzieć się więcej o|Zobacz|  
|-------------------------|---------|  
|Za pomocą szablonów konsumentów OLE DB (tematy dotyczące pojęć)|[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Za pomocą szablonów dostawców OLE DB (tematy dotyczące pojęć)|[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|Klasy szablonów OLE DB i makra|[Dokumentacja szablonów OLE DB](../../data/oledb/ole-db-templates.md) (Visual C++)|  
|Atrybuty konsumentów OLE DB|[Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md)|  
|Interfejsy OLE DB|[Podręcznik programisty OLE DB](https://msdn.microsoft.com/en-us/library/ms713643.aspx) (w zestawie SDK systemu Windows)|  
|Przykłady szablonów OLE DB|[Przykłady szablonów OLE DB](http://msdn.microsoft.com/en-us/08958863-0b5f-41ad-ae99-fca7440c553c)| 
|Omówienie programowania (Visual C++) dostępu do danych|[Programowanie dostępu do danych](../../data/data-access-programming-mfc-atl.md)|  
|Tematy dotyczące pojęć ODBC|[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych](../data-access-in-cpp.md)