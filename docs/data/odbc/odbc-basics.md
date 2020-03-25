---
title: Podstawy ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
ms.openlocfilehash: 042b1ce6d12e4f4a2be57c0e2e8e01d9750f5357
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213216"
---
# <a name="odbc-basics"></a>Podstawy ODBC

Ten temat zawiera podstawowe informacje dotyczące Open Database Connectivity (ODBC):

- [Jak działa ODBC z klasami baz danych](../../data/odbc/odbc-and-the-database-classes.md)

- [Jak sterowniki ODBC działają z dynamicznymi](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [Jakie składniki ODBC potrzebne do rozdzielenia z aplikacjami](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

Warto również zapoznać się z tematem [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Źródła danych ODBC są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektów dostępu do danych MFC (DAO).

> [!NOTE]
> Klasy MFC ODBC obsługują kodowanie Unicode i wielowątkowość. Aby uzyskać więcej informacji na temat obsługi wielowątkowości, zobacz [klasy i wątki ODBC](../../data/odbc/odbc-classes-and-threads.md)

ODBC jest interfejsem na poziomie wywołań, który umożliwia aplikacjom dostęp do danych w dowolnej bazie danych, dla której istnieje sterownik ODBC. Korzystając z ODBC, można tworzyć aplikacje bazy danych z dostępem do dowolnej bazy danych, dla której użytkownik końcowy ma sterownik ODBC. ODBC oferuje interfejs API, który umożliwia aplikacji niezależne od systemu zarządzania bazami danych (DBMS).

ODBC jest częścią bazy danych Microsoft Windows Open Services Architecture (WOSA), która jest interfejsem, który umożliwia aplikacjom klasycznym opartym na systemie Windows łączenie się z wieloma środowiskami obliczeniowymi bez ponownego zapisywania aplikacji dla każdej platformy.

Poniżej przedstawiono składniki ODBC:

- INTERFEJS API ODBC

   Biblioteka wywołań funkcji, zestaw kodów błędów oraz standardowa składnia [SQL](../../data/odbc/sql.md) służąca do uzyskiwania dostępu do danych w systemie DBMS.

- Menedżer sterowników ODBC

   Biblioteka dołączana dynamicznie (biblioteki odbc32. dll), która ładuje sterowniki ODBC bazy danych w imieniu aplikacji. Ta biblioteka DLL jest niewidoczna dla aplikacji.

- Sterowniki baz danych ODBC

   Co najmniej jedna biblioteka DLL, która przetwarza wywołania funkcji ODBC dla określonych systemów DBMS. Aby zapoznać się z listą dostarczonych sterowników, zobacz [listę sterowników ODBC](../../data/odbc/odbc-driver-list.md).

- [Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

   Biblioteka dołączana dynamicznie (Odbccr32. dll), która znajduje się między menedżerem sterowników ODBC a sterownikami i obsługuje przewijanie danych.

- [Administrator ODBC](../../data/odbc/odbc-administrator.md)

   Narzędzie służące do konfigurowania systemu DBMS, aby było dostępne jako źródło danych dla aplikacji.

Aplikacja uzyskuje niezależność od systemów DBMS przez przechodzenie przez sterownik ODBC przeznaczony dla systemu DBMS zamiast pracy bezpośrednio z systemem DBMS. Sterownik tłumaczy wywołania na polecenia, których może używać System DBMS, upraszczając pracę dewelopera i udostępniając go dla szerokiego zakresu źródeł danych.

Klasy baz danych obsługują wszystkie źródła danych, dla których masz sterownik ODBC. Może to obejmować na przykład relacyjną bazę danych, indeksowaną bazę danych metody dostępu sekwencyjnego (ISAM), arkusz kalkulacyjny programu Microsoft Excel lub plik tekstowy. Sterowniki ODBC zarządzają połączeniami ze źródłem danych, a SQL służy do wybierania rekordów z bazy danych.

Aby uzyskać listę sterowników ODBC uwzględnionych w tej wersji programu Visual C++ i uzyskać informacje o uzyskiwaniu dodatkowych sterowników, zobacz [Lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
