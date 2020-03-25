---
title: Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 3507a5ee7dcfb8bf4f4eee12ef9264c16ad904c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213112"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach baz danych MFC ODBC zestawy dynamiczne są zestawami rekordów z właściwościami dynamicznymi; pozostaną one zsynchronizowane ze źródłem danych w określony sposób. Zestawy dynamiczne MFC (ale nie tylko te zestawy rekordów) wymagają sterownika ODBC z zgodnym z interfejsem API poziomu 2. Jeśli sterownik [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z zestawem interfejsów API poziomu 1, nadal można używać zarówno migawek, jak i tylko do odczytu, jak i zestawów rekordów, ale nie zestawów dynamicznych. Jednak sterownik Level 1 może obsługiwać zestawy dynamiczne, jeśli obsługuje rozszerzone pobieranie i kursory z zestawem kluczy.

W terminologii ODBC, zestawy dynamiczne i migawki są określane jako kursory. Kursor jest mechanizmem służącym do śledzenia jego pozycji w zestawie rekordów. Aby uzyskać więcej informacji o wymaganiach dotyczących sterowników dla zestawów dynamicznych, zobacz [zestaw dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz zestaw SDK [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) w dokumentacji MSDN.

> [!NOTE]
>  W przypadku zestawów rekordów aktualizowalnych sterownik ODBC musi obsługiwać ustawione instrukcje aktualizacji lub funkcję `::SQLSetPos` ODBC API. Jeśli obie są obsługiwane, MFC używa `::SQLSetPos` w celu zwiększenia wydajności. Alternatywnie, w przypadku migawek można użyć biblioteki kursorów, która zapewnia wymaganą obsługę migawek aktualizowalnych (Kursory statyczne i instrukcje aktualizacji).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
