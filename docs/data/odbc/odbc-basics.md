---
title: Podstawy ODBC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC cursor library [ODBC], ODBC components
- ODBC components
- ODBC components, required components
- ODBC, about ODBC
- ODBC, components
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 26a1554fec567762810f6bd48c8674ea048ce117
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-basics"></a>Podstawy ODBC
Ten temat zawiera podstawowe informacje dotyczące połączenia bazy danych Otwórz (ODBC):  
  
-   [Jak działa ODBC z klasami baz danych](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [Jak działają sterowników ODBC z zestawów dynamicznych](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [Jakie ODBC — składniki potrzebne do ponownej dystrybucji z aplikacjami](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 Należy również przeczytać temat powiązanych [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas MFC obiekt DAO (Data Access).  
  
> [!NOTE]
>  Klasy MFC ODBC obsługują standardu Unicode i wielowątkowości. Aby uzyskać więcej informacji na temat obsługi wielowątkowości, zobacz [klasy i wątki ODBC](../../data/odbc/odbc-classes-and-threads.md)  
  
 ODBC jest interfejsem poziom wywołania, który umożliwia aplikacjom dostęp do danych w każdej bazy danych, dla którego jest sterownik ODBC. Za pośrednictwem sterownika ODBC, można utworzyć bazy danych aplikacji z dostępem do dowolnej bazy danych, dla którego użytkownikowi końcowemu ma sterownik ODBC. ODBC udostępnia interfejs API, który pozwala aplikacji niezależnie od źródła system zarządzania bazami (danych DBMS).  
  
 ODBC jest części bazy danych programu Microsoft Windows otwórz usługi architektura (WOSA), czyli interfejsu, który umożliwia opartych na systemie Windows aplikacji klasycznych nawiązać połączenia z wielu środowiska obliczeniowe bez ponownego tworzenia aplikacji dla każdej platformy.  
  
 Poniżej przedstawiono składniki ODBC:  
  
-   INTERFEJSU API ODBC  
  
     Biblioteka funkcji wywołuje zestaw kodów błędów i standard [SQL](../../data/odbc/sql.md) składni do uzyskiwania dostępu do danych w systemach DBMS.  
  
-   Menedżera sterowników ODBC  
  
     Biblioteka DLL (Odbc32.dll), który ładuje sterowników ODBC w imieniu aplikacji. Ta biblioteka DLL jest niewidoczny dla aplikacji.  
  
-   ODBC — sterowniki bazy danych  
  
     Jeden lub więcej bibliotek DLL, które przetworzyć wywołania funkcji ODBC dla określonych systemach DBMS. Listę dostarczony sterowników, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).  
  
-   [Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     Biblioteka DLL (Odbccr32.dll), znajduje się między Menedżera sterowników ODBC i sterowników, który obsługuje przewijanie danych.  
  
-   [Administrator ODBC](../../data/odbc/odbc-administrator.md)  
  
     Narzędzie służące do konfigurowania systemu DBMS, aby udostępnić go jako źródło danych dla aplikacji.  
  
 Aplikacja uzyskuje niezależność od systemach DBMS pracy za pośrednictwem sterownika ODBC napisane specjalnie dla systemu DBMS, a nie praca bezpośrednio z systemu DBMS. Sterownik tłumaczy wywołuje polecenia, jego DBMS można użyć uproszczenie dewelopera pracy oraz udostępnianie go dla różnych źródeł danych.  
  
 Klasy baz danych obsługuje dowolnego źródła danych, dla którego masz sterownik ODBC. Na przykład może to obejmować, relacyjnej bazy danych, bazy danych indeksowane metody dostępu sekwencyjnego (ISAM), arkusz kalkulacyjny programu Microsoft Excel lub plik tekstowy. Sterowniki ODBC Zarządzanie połączenia ze źródłem danych, i umożliwia wybranie rekordy z bazy danych SQL.  
  
 Lista sterowników ODBC zawarte w tej wersji programu Visual C++ oraz informacje na temat uzyskiwania dodatkowe sterowniki, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)