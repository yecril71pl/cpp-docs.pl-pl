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
ms.openlocfilehash: a92b8a7a7236a51c3506c4d46dad31a03b2f10d3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521586"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach bazy danych MFC ODBC zestawów dynamicznych są zestawów rekordów przy użyciu właściwości dynamicznych; pozostają one zsynchronizowane ze źródłem danych w określony sposób. MFC zestawów dynamicznych (ale nie tylko do przodu zestawy rekordów) wymaga sterownika ODBC przy użyciu interfejsu API 2 poziom zgodności. Jeśli sterownik dla Twojego [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z interfejsem API 1 poziom ustawić, można nadal używać migawek można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać zestawów dynamicznych, gdy obsługuje pobierania rozszerzonych i kluczy.

W terminologii ODBC migawki i zestawów dynamicznych są określane jako kursorów. Kursor jest mechanizm używany do śledzenia jego pozycja w zestawie rekordów. Aby uzyskać więcej informacji na temat wymagania dotyczące sterownika dla zestawów dynamicznych, zobacz [dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) zestawu SDK w dokumentacji MSDN.

> [!NOTE]
>  Zestawy rekordów można aktualizować, sterownik ODBC musi obsługiwać obu instrukcji update pozycjonowane lub `::SQLSetPos` funkcji interfejsu API ODBC. Jeśli obie są obsługiwane, MFC wykorzystuje `::SQLSetPos` w celu zwiększenia wydajności. Alternatywnie dla migawki, można użyć z biblioteki kursorów, który obsługuje wymagane dla migawek można aktualizować (Kursory statyczne i instrukcjach update pozycjonowane).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)