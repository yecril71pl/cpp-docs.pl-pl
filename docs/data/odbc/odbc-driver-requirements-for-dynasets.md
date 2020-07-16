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
ms.openlocfilehash: 4c436764649a1aa418e12300809482b45224dd46
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403845"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach baz danych MFC ODBC zestawy dynamiczne są zestawami rekordów z właściwościami dynamicznymi; pozostaną one zsynchronizowane ze źródłem danych w określony sposób. Zestawy dynamiczne MFC (ale nie tylko te zestawy rekordów) wymagają sterownika ODBC z zgodnym z interfejsem API poziomu 2. Jeśli sterownik [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z zestawem interfejsów API poziomu 1, nadal można używać zarówno migawek, jak i tylko do odczytu, jak i zestawów rekordów, ale nie zestawów dynamicznych. Jednak sterownik Level 1 może obsługiwać zestawy dynamiczne, jeśli obsługuje rozszerzone pobieranie i kursory z zestawem kluczy.

W terminologii ODBC, zestawy dynamiczne i migawki są określane jako kursory. Kursor jest mechanizmem służącym do śledzenia jego pozycji w zestawie rekordów. Aby uzyskać więcej informacji o wymaganiach dotyczących sterowników dla zestawów dynamicznych, zobacz [zestaw dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz dokumentację [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) .

> [!NOTE]
> Aby można było aktualizować zestawy rekordów, sterownik ODBC musi obsługiwać ustawione instrukcje aktualizacji lub `::SQLSetPos` funkcję interfejsu API ODBC. Jeśli oba są obsługiwane, MFC używa `::SQLSetPos` do wydajności. Alternatywnie, w przypadku migawek można użyć biblioteki kursorów, która zapewnia wymaganą obsługę migawek aktualizowalnych (Kursory statyczne i instrukcje aktualizacji).

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje dotyczące ODBC](../../data/odbc/odbc-basics.md)
