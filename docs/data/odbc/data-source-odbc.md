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
ms.openlocfilehash: 6ad24a7be5c46c8019b22629003306ea99c56fd3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106975"
---
# <a name="data-source-odbc"></a>Źródło danych (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
W warunkach bazy danych źródła danych jest określony zbiór danych, informacje wymagane do dostępu do danych i lokalizacja źródła danych, które można opisać za pomocą nazwy źródła danych. Aby pracować z klasą [CDatabase](../../mfc/reference/cdatabase-class.md), źródło danych musi być taki, który został skonfigurowany przez administratora Open Database Connectivity (ODBC). Przykładami źródeł danych zdalnej bazy danych, systemem Microsoft SQL Server w sieci lub plik programu Microsoft Access w katalogu lokalnym. Z poziomu aplikacji dostęp do dowolnego źródła danych, do której masz sterownika ODBC.  
  
Może mieć co najmniej jedno źródło danych aktywnych w aplikacji w tym samym czasie, każdy jest reprezentowany przez `CDatabase` obiektu. Również może mieć wiele jednoczesnych połączeń, do żadnego źródła danych. Można nawiązać zdalnego oraz ze źródłami danych lokalnych, w zależności od zainstalowanych sterowników i możliwości sterowników ODBC. Aby uzyskać więcej informacji na temat źródeł danych i Administratora ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [Administratora ODBC](../../data/odbc/odbc-administrator.md).  
  
W poniższych tematach opisano bardziej o źródłach danych:  
  
- [Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
- [Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)