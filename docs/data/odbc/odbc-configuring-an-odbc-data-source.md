---
title: 'ODBC: Konfigurowanie źródła danych ODBC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9a0cd385596f62432f16b7e5abc4259a267dd76
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080315"
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC: konfigurowanie źródła danych ODBC

Aby użyć [źródła danych](../../data/odbc/data-source-odbc.md) z aplikacją, zostały opracowane, należy użyć Administratora ODBC do jego konfiguracji. ODBC Administrator śledzi informacje o dostępnych źródeł danych i parametry połączenia w rejestrze systemu Windows. Użyj Administratora ODBC i dodawanie, modyfikowanie i usuwanie źródeł danych w **źródeł danych** okno dialogowe i w celu dodawania i usuwania sterowników ODBC.

> [!NOTE]
>  Te informacje dotyczą użycia klas MFC obiekt DAO (Data Access) uzyskać dostęp do ODBC i przy użyciu klas MFC ODBC.

ODBC Administrator jest automatycznie instalowany z obsługi bazy danych biblioteki Microsoft Foundation Classes (MFC). Aby uzyskać więcej informacji na temat programu Administratora ODBC, zobacz [Administratora ODBC](../../data/odbc/odbc-administrator.md) i system ODBC API Pomoc online.

Aby uzyskać informacje o sposobie pisania programów ODBC do instalacji i administrowania dla aplikacji baz danych MFC[techniczne 48 Uwaga](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)<br/>
[ODBC: bezpośrednie wywoływanie funkcji ODBC API](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)