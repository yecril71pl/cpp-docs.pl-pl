---
title: korzystanie z procedur składowanych
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 2c0c1c71103384439d0b7b94f942e1b5a6d9e651
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536161"
---
# <a name="using-stored-procedures"></a>korzystanie z procedur składowanych

Procedura składowana jest obiekt pliku wykonywalnego, przechowywane w bazie danych. Wywoływanie procedury składowanej jest podobny do wywoływania za pomocą polecenia SQL. Korzystanie z procedur składowanych w źródle danych (zamiast wykonywania lub Trwa przygotowywanie do instrukcji w aplikacji klienckiej) zapewnia kilka korzyści, w tym wyższej wydajności, obciążenie sieci mniejsze i ulepszona spójność i dokładność.

Procedura składowana może mieć dowolną liczbę (w tym zero) danych wejściowych lub wyjściowych, parametrów i przekazać wartość zwracaną. Możesz albo wartości parametru twardych kodu, jak określone dane wartości lub użyć znaczników parametru (znak zapytania "?").

> [!NOTE]
>  Procedury przechowywane utworzone za pomocą języka Visual C++ muszą być skompilowane przy użyciu programu SQL Server CLR `/clr:safe` — opcja kompilatora.

Dostawca OLE DB dla programu SQL Server (SQLOLEDB) obsługuje następujących mechanizmów, które przechowywane Użyj procedur, aby zwrócić dane:

- Każdy **wybierz** instrukcji w procedurze generuje zestaw wyników.

- Procedura może zwrócić danych za pośrednictwem parametrów wyjściowych.

- Procedura może mieć kod powrotny liczby całkowitej.

> [!NOTE]
> Nie można użyć procedur składowanych z dostawcy OLE DB dla aparatu Jet ponieważ ten dostawca nie obsługuje procedury składowane; dozwolone są tylko zmienne w ciągach zapytań.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)