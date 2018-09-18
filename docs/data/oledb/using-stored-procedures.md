---
title: Korzystanie z procedur składowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7b68e7494303e06245a713abc8f1d6e0424773e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114647"
---
# <a name="using-stored-procedures"></a>korzystanie z procedur składowanych

Procedura składowana jest obiekt pliku wykonywalnego, przechowywane w bazie danych. Wywoływanie procedury składowanej jest podobny do wywoływania za pomocą polecenia SQL. Korzystanie z procedur składowanych w źródle danych (zamiast wykonywania lub Trwa przygotowywanie do instrukcji w aplikacji klienckiej) zapewnia kilka korzyści, w tym wyższej wydajności, obciążenie sieci mniejsze i ulepszona spójność i dokładność.  
  
Procedura składowana może mieć dowolną liczbę (w tym zero) danych wejściowych lub wyjściowych, parametrów i przekazać wartość zwracaną. Możesz albo wartości parametru twardych kodu, jak określone dane wartości lub użyć znaczników parametru (znak zapytania "?").  
  
> [!NOTE]
>  Procedury przechowywane utworzone za pomocą języka Visual C++ muszą być skompilowane przy użyciu programu SQL Server CLR `/clr:safe` — opcja kompilatora.  
  
Dostawca OLE DB dla programu SQL Server (SQLOLEDB) obsługuje następujących mechanizmów, które przechowywane Użyj procedur, aby zwrócić dane:  
  
- Co instrukcja SELECT w procedurze generuje zestaw wyników.  
  
- Procedura może zwrócić danych za pośrednictwem parametrów wyjściowych.  
  
- Procedura może mieć kod powrotny liczby całkowitej.  
  
> [!NOTE]
>  Nie można użyć procedur składowanych z dostawcy OLE DB dla aparatu Jet ponieważ ten dostawca nie obsługuje procedury składowane; dozwolone są tylko zmienne w ciągach zapytań.  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)