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
ms.openlocfilehash: d9fad26440cea2c8ec2efd7d07dacb83547252e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089236"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Wymagania dotyczące sterownika ODBC dla zestawów dynamicznych
Klasy baz danych MFC ODBC zestawy dynamiczne są zestawów rekordów za pomocą właściwości dynamicznych; pozostają one zsynchronizowane ze źródłem danych w określony sposób. Zestawy dynamiczne MFC (ale nie Progresywne zestawy rekordów) wymaga sterownika ODBC z interfejsu API 2 poziom zgodności. Jeśli sterownik sieci [źródła danych](../../data/odbc/data-source-odbc.md) jest zgodny z interfejsem API 1 poziom ustawiona, można nadal używać migawek zarówno można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 można obsługuje zestawów dynamicznych, jeśli obsługuje rozszerzonych pobierania i kursory oparte na zestawie kluczy.  
  
 W terminologii ODBC zestawów dynamicznych i migawki są określane jako kursorów. Kursor jest mechanizmem używanym w celu śledzenia jej położenie w zestawie rekordów. Aby uzyskać więcej informacji na temat wymagania dotyczące sterownika dla zestawów dynamicznych, zobacz [dynamiczny](../../data/odbc/dynaset.md). Aby uzyskać więcej informacji na temat kursorów, zobacz [Otwórz połączenie bazy danych (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) zestawu SDK w dokumentacji MSDN.  
  
> [!NOTE]
>  Można aktualizować zestawów rekordów, sterownik ODBC musi obsługiwać albo instrukcji update rozmieszczanych lub **:: SQLSetPos** funkcji interfejsu API ODBC. Jeśli są obsługiwane, używa MFC **:: SQLSetPos** w celu zwiększenia wydajności. Alternatywnie migawek, można użyć z biblioteki kursorów, które obsługuje wymagane dla migawek można aktualizować (Kursory statyczne i instrukcje pozycjonowane aktualizacji).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)