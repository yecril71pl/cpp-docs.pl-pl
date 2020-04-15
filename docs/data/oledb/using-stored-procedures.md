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
ms.openlocfilehash: 436c796b24b0fa498f2b3f45e848392635b22a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376038"
---
# <a name="using-stored-procedures"></a>korzystanie z procedur składowanych

Procedura składowana jest obiektem wykonywalnym przechowywanym w bazie danych. Wywołanie procedury składowanej jest podobne do wywoływania polecenia SQL. Korzystanie z procedur przechowywanych w źródle danych (zamiast wykonywania lub przygotowywania instrukcji w aplikacji klienckiej) może zapewnić kilka korzyści, w tym wyższą wydajność, zmniejszenie obciążenia sieciowego oraz lepszą spójność i dokładność.

Procedura składowana może mieć dowolną liczbę (w tym zero) parametrów wejściowych lub wyjściowych i może przekazać wartość zwracaną. Można albo wartości parametrów kodu twardego jako określone wartości danych lub użyć znacznika parametru (znak zapytania '?').

> [!NOTE]
> Clr SQL Server procedury przechowywane utworzone przy użyciu `/clr:safe` języka Visual C++ muszą być kompilowane za pomocą opcji kompilatora.

Dostawca ole bazy danych dla programu SQL Server (SQLOLEDB) obsługuje następujące mechanizmy, które używane procedury do zwracania danych:

- Każda instrukcja **SELECT** w procedurze generuje zestaw wyników.

- Procedura może zwracać dane za pomocą parametrów wyjściowych.

- Procedura może mieć kod zwracany liczby całkowitej.

> [!NOTE]
> Nie można używać procedur przechowywanych z dostawcą ole bazy danych dla jet, ponieważ ten dostawca nie obsługuje procedur przechowywanych; tylko stałe są dozwolone w ciągach zapytań.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami dla konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
