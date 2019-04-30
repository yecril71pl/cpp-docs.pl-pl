---
title: Dostęp do ODBC i SQL
ms.date: 11/04/2016
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
ms.openlocfilehash: 7a539d911bbf4f4d9582da0ebedaeffaa0d8fa7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396005"
---
# <a name="access-to-odbc-and-sql"></a>Dostęp do ODBC i SQL

Bibliotekę Microsoft Foundation Class hermetyzuje wiele wywołań interfejsu API Windows i nadal pozwala wywoływać żadnych funkcji Windows API bezpośrednio. Klasy bazy danych zapewniają elastyczność tych samych w odniesieniu do interfejsu API ODBC. Gdy klas baz danych włączyć osłonę z wiele złożoności ODBC, można wywołać funkcji ODBC API bezpośrednio z dowolnego miejsca w programie.

Podobnie, klas baz danych włączyć osłony dla możesz z konieczności współpracy z bardzo z [SQL](../../data/odbc/sql.md), ale można użyć programu SQL bezpośrednio, jeśli chcesz. Można dostosować obiekty zestawu rekordów, przekazując własne instrukcje SQL (lub jej części ustawienie domyślna deklaracja) po otwarciu zestawu rekordów. Można również ustawić jako wywołania SQL bezpośrednio przy użyciu [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) funkcji składowej klasy typu [CDatabase](../../mfc/reference/cdatabase-class.md).

Aby uzyskać więcej informacji, zobacz [ODBC: Interfejsu API ODBC wywołania funkcji bezpośrednio](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) i [SQL: Wykonywanie bezpośrednich wywołań SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).

## <a name="see-also"></a>Zobacz także

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)