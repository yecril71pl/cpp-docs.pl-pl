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
ms.openlocfilehash: c44e34023ecdeb994ea3a60ea3b699cd5b1488a3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023831"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach bazy danych MFC ODBC zestawów dynamicznych są zestawów rekordów przy użyciu właściwości dynamicznych; pozostają one zsynchronizowane ze źródłem danych w określony sposób. MFC zestawów dynamicznych (ale nie tylko do przodu zestawy rekordów) wymaga sterownika ODBC przy użyciu interfejsu API 2 poziom zgodności. Jeśli sterownik dla Twojego [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z interfejsem API 1 poziom ustawić, można nadal używać migawek można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać zestawów dynamicznych, gdy obsługuje pobierania rozszerzonych i kluczy.

W terminologii ODBC migawki i zestawów dynamicznych są określane jako kursorów. Kursor jest mechanizm używany do śledzenia jego pozycja w zestawie rekordów. Aby uzyskać więcej informacji na temat wymagania dotyczące sterownika dla zestawów dynamicznych, zobacz [dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz [Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) zestawu SDK w dokumentacji MSDN.

> [!NOTE]
>  Zestawy rekordów można aktualizować, sterownik ODBC musi obsługiwać obu instrukcji update pozycjonowane lub `::SQLSetPos` funkcji interfejsu API ODBC. Jeśli obie są obsługiwane, MFC wykorzystuje `::SQLSetPos` w celu zwiększenia wydajności. Alternatywnie dla migawki, można użyć z biblioteki kursorów, który obsługuje wymagane dla migawek można aktualizować (Kursory statyczne i instrukcjach update pozycjonowane).

## <a name="see-also"></a>Zobacz także

[Podstawy ODBC](../../data/odbc/odbc-basics.md)