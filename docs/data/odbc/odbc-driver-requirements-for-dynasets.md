---
title: Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e59e14f9dbd69104e4ae79de5f6f57de24267706
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064254"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych

W klasach bazy danych MFC ODBC zestawów dynamicznych są zestawów rekordów przy użyciu właściwości dynamicznych; pozostają one zsynchronizowane ze źródłem danych w określony sposób. MFC zestawów dynamicznych (ale nie tylko do przodu zestawy rekordów) wymaga sterownika ODBC przy użyciu interfejsu API 2 poziom zgodności. Jeśli sterownik dla Twojego [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z interfejsem API 1 poziom ustawić, można nadal używać migawek można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać zestawów dynamicznych, gdy obsługuje pobierania rozszerzonych i kluczy.

W terminologii ODBC migawki i zestawów dynamicznych są określane jako kursorów. Kursor jest mechanizm używany do śledzenia jego pozycja w zestawie rekordów. Aby uzyskać więcej informacji na temat wymagania dotyczące sterownika dla zestawów dynamicznych, zobacz [dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz [Open Database Connectivity (ODBC)](/previous-versions/windows/desktop/ms710252) zestawu SDK w dokumentacji MSDN.

> [!NOTE]
>  Zestawy rekordów można aktualizować, sterownik ODBC musi obsługiwać obu instrukcji update pozycjonowane lub `::SQLSetPos` funkcji interfejsu API ODBC. Jeśli obie są obsługiwane, MFC wykorzystuje `::SQLSetPos` w celu zwiększenia wydajności. Alternatywnie dla migawki, można użyć z biblioteki kursorów, który obsługuje wymagane dla migawek można aktualizować (Kursory statyczne i instrukcjach update pozycjonowane).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)