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
ms.openlocfilehash: a7e97781d245e236c57942db15d61080d6418cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209277"
---
# <a name="using-stored-procedures"></a>korzystanie z procedur składowanych

Procedura składowana jest obiektem wykonywalnym przechowywanym w bazie danych. Wywołanie procedury składowanej jest podobne do wywołania polecenia SQL. Korzystanie z procedur składowanych w źródle danych (zamiast wykonywania lub przygotowywania instrukcji w aplikacji klienckiej) może zapewnić kilka korzyści, w tym wyższą wydajność, zmniejszenie obciążenia sieci oraz lepszą spójność i dokładność.

Procedura składowana może zawierać dowolną liczbę parametrów wejściowych lub wyjściowych (w tym zero) i może przekazać wartość zwracaną. Można użyć wartości parametrów kodu twardego jako konkretnych wartości danych lub znacznika parametru (znak zapytania "?").

> [!NOTE]
>  Procedury składowane SQL Server CLR utworzone przy C++ użyciu wizualizacji muszą być kompilowane za pomocą opcji kompilatora `/clr:safe`.

Dostawca OLE DB dla SQL Server (SQLOLEDB) obsługuje następujące mechanizmy, za pomocą których procedury składowane zwracają dane:

- Każda instrukcja **SELECT** w procedurze generuje zestaw wyników.

- Procedura może zwracać dane za pomocą parametrów wyjściowych.

- Procedura może mieć kod powrotu typu Integer.

> [!NOTE]
> Nie można użyć procedur składowanych z dostawcą OLE DB dla aparatu Jet, ponieważ ten dostawca nie obsługuje procedur składowanych. ciągi zapytań mogą dotyczyć tylko stałych.

## <a name="see-also"></a>Zobacz też

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
