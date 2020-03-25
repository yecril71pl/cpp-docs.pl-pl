---
title: Źródło danych (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
ms.openlocfilehash: ed9eeb8f5ef0d53846761062cf2c6575d2eaf9e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213307"
---
# <a name="data-source-odbc"></a>Źródło danych (ODBC)

Ten temat dotyczy klas MFC ODBC.

W terminologii bazy danych, źródłem danych jest określony zestaw danych, informacje wymagane do uzyskania dostępu do tych danych oraz lokalizacja źródła danych, które można opisać przy użyciu nazwy źródła danych. Aby można było korzystać z klasy [CDatabase](../../mfc/reference/cdatabase-class.md), źródło danych musi być skonfigurowane za pośrednictwem administratora Open Database Connectivity (ODBC). Przykłady źródeł danych obejmują zdalną bazę danych działającą w Microsoft SQL Server przez sieć lub plik programu Microsoft Access w katalogu lokalnym. Z poziomu aplikacji możesz uzyskać dostęp do dowolnego źródła danych, dla którego masz sterownik ODBC.

W aplikacji można jednocześnie korzystać z co najmniej jednego źródła danych reprezentowanego przez obiekt `CDatabase`. Można także mieć wiele jednoczesnych połączeń z dowolnym źródłem danych. Możesz połączyć się ze zdalnym i lokalnymi źródłami danych, w zależności od zainstalowanych sterowników i możliwości sterowników ODBC. Aby uzyskać więcej informacji na temat źródeł danych i administratora ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [administrator ODBC](../../data/odbc/odbc-administrator.md).

W poniższych tematach opisano więcej informacji o źródłach danych:

- [Źródło danych: zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)

- [Źródło danych: określanie schematu źródła danych (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
