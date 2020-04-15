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
ms.openlocfilehash: c612e8ea91882a6e744a8f47afe0decbeba85358
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367214"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach bazy danych MFC ODBC zestawy dynasets są zestawami rekordów o właściwościach dynamicznych; pozostają one zsynchronizowane ze źródłem danych w określony sposób. Zestawy dynasetów MFC (ale nie tylko do przodu) wymagają sterownika ODBC o zgodności interfejsu API poziomu 2. Jeśli sterownik [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z zestawem interfejsu API poziomu 1, nadal można używać zarówno aktualizacji, jak i migawek tylko do odczytu oraz zestawów rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać dynasets, jeśli obsługuje rozszerzone pobieranie i kursory oparte na zestawie kluczy.

W terminologii ODBC dynasets i migawki są określane jako kursory. Kursor jest mechanizmem używanym do śledzenia jego pozycji w ach. Aby uzyskać więcej informacji na temat wymagań dotyczących sterowników dla zestawów dynaset, zobacz [Dynaset](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz [open database connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) SDK w dokumentacji MSDN.

> [!NOTE]
> W przypadku aktualizacji zestawy rekordów sterownik ODBC musi obsługiwać `::SQLSetPos` instrukcje aktualizacji pozycjonowane lub funkcji interfejsu API ODBC. Jeśli oba są obsługiwane, MFC używa `::SQLSetPos` wydajności. Alternatywnie w przypadku migawek można użyć biblioteki kursora, która zapewnia wymaganą obsługę migawek podlegaalnych aktualizacji (kursorów statycznych i instrukcji aktualizacji pozycjonowanych).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
