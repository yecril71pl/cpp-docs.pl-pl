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
ms.openlocfilehash: 81b1f6d06d909b5b046703b97c4574270efbdd46
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591727"
---
# <a name="odbc-basics"></a>Podstawy ODBC

Ten temat zawiera podstawowe informacje z Open Database Connectivity (ODBC):

- [Jak działa ODBC z klasami bazy danych](../../data/odbc/odbc-and-the-database-classes.md)

- [Jak sterowniki ODBC odnoszą się do zestawów dynamicznych](../../data/odbc/odbc-driver-requirements-for-dynasets.md)

- [Jakie ODBC — składniki potrzebne do ponownej dystrybucji ze swoimi aplikacjami](../../data/odbc/redistributing-odbc-components-to-your-customers.md)

Należy również przeczytać temat pokrewny [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub przy użyciu klas MFC obiekt DAO (Data Access).

> [!NOTE]
> Klasy MFC ODBC obsługują standardu Unicode i wielowątkowości. Aby uzyskać więcej informacji na temat obsługi wielowątkowości, zobacz [klasy i wątki ODBC](../../data/odbc/odbc-classes-and-threads.md)

ODBC jest interfejsu poziom wywołań, który umożliwia aplikacjom dostęp do danych w dowolnej bazie danych, dla których ma sterownika ODBC. Przy użyciu interfejsu ODBC, możesz tworzyć aplikacje bazy danych dzięki dostępowi do każdej bazy danych, dla którego użytkownikowi końcowemu ma sterownik ODBC. ODBC udostępnia interfejs API, który umożliwia aplikacji niezależnie od system zarządzania bazami danych źródła (danych DBMS).

ODBC jest bazy danych programu Microsoft Windows otwórz usług architektury (WOSA), czyli interfejsu, który umożliwia oparte na Windows aplikacji klasycznych, połączyć się z wielu środowiskach obliczeniowych bez konieczności ponownego zapisu aplikacji dla każdej platformy.

Poniżej przedstawiono składniki ODBC:

- INTERFEJSU API ODBC

   Wywołuje bibliotekę funkcji, zestaw kodów błędów i standard [SQL](../../data/odbc/sql.md) składni do uzyskiwania dostępu do danych dotyczących systemów DBMS.

- Menedżer sterowników ODBC

   Biblioteka dołączana dynamicznie (Odbc32.dll), który ładuje sterowników ODBC w imieniu aplikacji. Ta biblioteka DLL jest niewidoczny dla aplikacji.

- Sterowników ODBC

   Jeden lub więcej bibliotek DLL, które przetwarzają wywołania funkcji ODBC dla określonych systemów DBMS. Aby uzyskać listę sterowników dostarczony, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

- [Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

   Biblioteka dołączana dynamicznie (Odbccr32.dll), znajduje się między Menedżera sterowników ODBC i sterowników, który obsługuje przewijanie danych.

- [Administrator ODBC](../../data/odbc/odbc-administrator.md)

   Narzędzie używane podczas konfigurowania DBMS, aby udostępnić go jako źródło danych dla aplikacji.

Aplikacja uzyskuje niezależność od systemów DBMS pracy za pośrednictwem sterownika ODBC napisanych specjalnie dla systemu DBMS, a nie praca bezpośrednio z systemu DBMS. Sterownik tłumaczy wywołuje polecenia użyć jego DBMS, upraszczanie pracy dewelopera i udostępniając szerokiej gamy źródeł danych.

Klasy bazy danych obsługują dowolnego źródła danych, do której masz sterownika ODBC. Na przykład może to obejmować, relacyjnej bazy danych, bazę danych indeksowane metody dostępu sekwencyjnego (ISAM), arkusz kalkulacyjny programu Excel lub plik tekstowy. Sterowniki ODBC Zarządzanie połączenia ze źródłem danych, a SQL służy do wybierania rekordów z bazy danych.

Lista sterowników ODBC zawarte w tej wersji programu Visual C++ i informacji na temat uzyskiwania dodatkowych sterowników, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)