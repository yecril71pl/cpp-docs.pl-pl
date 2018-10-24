---
title: Programowanie OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB [C++]
- data access [C++], OLE DB programming
- OLE DB [C++], about OLE DB
ms.assetid: 52a80d66-17a9-43a1-9b90-392ae43cea2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2628756992298fa61bad070b72f66232d65bec5f
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990039"
---
# <a name="ole-db-programming"></a>Programowanie OLE DB

Microsoft OLE DB jest technologią starszą; w przypadku nowych aplikacji jest wymaganego dostępu do danych interfejsu API dla połączonych serwerów SQL. Wszystkie inne nowe aplikacje powinny używać ODBC. Bieżący dostawca OLE DB dla programu SQL Server jest SQLNCLI11. BIBLIOTEKI DLL. Dostawcy jest nadal wysyłania w programie SQL Server 2016. Ta dokumentacja jest przeznaczona dla deweloperów, którzy są utrzymywanie istniejących aplikacji, które już używają OLE DB.
  
Szablony OLE DB są szablonów języka C++, które ułatwiają technologii baz danych OLE DB o wysokiej wydajności wpisując klas które implementują wiele powszechnie używanych interfejsów OLE DB. Ta biblioteka szablonów jest podzielony na szablony konsumentów i dostawcy.  
  
Visual C++ ma również obsługę Kreatora tworzenia aplikacji starter OLE DB.  
  
Ponadto możesz użyć atrybutów do zaimplementowania szablony konsumentów OLE DB.  
  
|Aby dowiedzieć się więcej o|Zobacz|  
|-------------------------|---------|  
|Za pomocą szablonów konsumentów OLE DB (tematów pojęciowych)|[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)|  
|Za pomocą szablonów dostawców OLE DB (tematów pojęciowych)|[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)|  
|Klasy szablonów OLE DB i makra|[Szablony OLE DB — Kompendium](../../data/oledb/ole-db-templates.md) (Visual C++)|  
|Atrybuty konsumentów OLE DB|[Atrybuty konsumentów OLE DB](../../windows/ole-db-consumer-attributes.md)|  
|Interfejsy OLE DB|[Dokumentacja dotycząca OLE DB](/previous-versions/windows/desktop/ms713643(v%3dvs.85)) (w zestawie Windows SDK)| 
|Przykłady szablonów OLE DB|[Przykłady szablonów OLE DB](https://github.com/Microsoft/VCSamples)| 
|Dostęp do danych programowania — Przegląd (Visual C++)|[Programowanie dostępu do danych](../../data/data-access-programming-mfc-atl.md)|  
|Tematy dotyczące pojęć ODBC|[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)|  

## <a name="see-also"></a>Zobacz też  

[Dostęp do danych](../data-access-in-cpp.md)