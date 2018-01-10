---
title: "Korzystanie z procedur składowanych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 093cbd3d2ae101bbc06c45a920f8a2c108eb3bfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-stored-procedures"></a>korzystanie z procedur składowanych
Procedura składowana jest obiektem pliku wykonywalnego, przechowywane w bazie danych. Wywołanie procedury składowanej jest podobny do wywoływania polecenia SQL. Korzystanie z procedur składowanych w źródle danych (zamiast wykonywania lub przygotowywanie do instrukcji w aplikacji klienckiej) zapewniają wiele korzyści, w tym większą wydajność, obciążenie sieci obniżona, ulepszona spójność i dokładność.  
  
 Procedura składowana może mieć dowolną liczbę (w tym zero) wejściowy lub parametry wyjściowe i można przekazać wartości zwracanej. Można albo wartości parametrów kodu twardych określonych danych wartości lub użyć znacznika parametr (znak zapytania "?").  
  
> [!NOTE]
>  Procedury składowane utworzone za pomocą języka Visual C++ musi być kompilowana przy użyciu programu SQL Server CLR **/CLR: Safe** — opcja kompilatora.  
  
 Dostawca OLE DB dla programu SQL Server (SQLOLEDB) obsługuje następujące mechanizmy, które przechowywane Użyj procedur, aby zwrócić dane:  
  
-   Każdy instrukcji SELECT w procedurze generuje zestawu wyników.  
  
-   Procedura może zwrócić danych za pomocą parametrów wyjściowych.  
  
-   Procedura może mieć całkowitą kod powrotu.  
  
> [!NOTE]
>  Nie można użyć procedur składowanych z dostawcy OLE DB dla Jet ponieważ ten dostawca nie obsługuje procedur składowanych; dozwolone są tylko zmienne w ciągi zapytań.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)