---
title: Zestaw dynamiczny
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 21c47546d14d9a121bdd0698fe96eb133dbc44a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395888"
---
# <a name="dynaset"></a>Zestaw dynamiczny

W tym temacie opisano zestawów dynamicznych i omówiono ich [dostępności](#_core_availability_of_dynasets).

> [!NOTE]
>  Ten temat dotyczy klas MFC ODBC, w tym [CRecordset](../../mfc/reference/crecordset-class.md). Aby uzyskać informacji na temat zestawów dynamicznych klas DAO, zobacz [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Za pomocą DAO możesz otworzyć dynamicznego zestawy rekordów.

Dynamiczny jest zestaw rekordów za pomocą właściwości dynamicznych. Jego okres istnienia obiektu zestawu rekordów w trybie dynamiczny (zazwyczaj nazywany dynamiczny) jest synchronizowany ze źródłem danych w następujący sposób. W środowisku wielodostępnym inni użytkownicy mogą edytować usuwania rekordów, które znajdują się w Twojej dynamiczny lub dodawanie rekordów do tabeli, która reprezentuje Twojego zestawu dynamicznego. Rejestruje aplikację dodaje lub usuwa z zestawu rekordów są odzwierciedlane w Twojego zestawu dynamicznego. Rekordy, które inni użytkownicy, Dodaj do tabeli nie zostaną odzwierciedlone w swojej dynamiczny, dopóki odbudować dynamiczny przez wywołanie jego `Requery` funkcja elementu członkowskiego. Inni użytkownicy usunięcie rekordów kodu MFC nakłada się na usuwania w twoim zestawie rekordów. Innym użytkownikom edytowanie zmiany w istniejących rekordach są odzwierciedlane w swojej dynamiczny, jak najszybciej przewiń rekordem dotyczy.

Podobnie zmiany wprowadzone do rekordów w dynamiczny są odzwierciedlane w zestawy dynamiczne używane przez innych użytkowników. Rekordy, które możesz dodać nie są odzwierciedlane w zestawie dynamicznym innych użytkowników, do momentu ich requery ich zestawów dynamicznych. Rekordy, które możesz usunąć są oznaczone jako "usunięte" w zestawach rekordów innych użytkowników. Jeśli masz wiele połączeń do tej samej bazy danych (wiele `CDatabase` obiektów), zestawie rekordów skojarzonych z tych połączeń jest taki sam jak zestawy rekordów innych użytkowników.

Zestawy dynamiczne są najbardziej przydatne, gdy dane muszą być dynamiczne, jako (na przykład) system rezerwacji linii lotniczych.

> [!NOTE]
> Aby korzystać z zestawów dynamicznych, konieczne jest posiadanie sterownika ODBC dla źródła danych, która obsługuje zestawów dynamicznych i nie muszą być ładowane z biblioteki kursorów ODBC. Aby uzyskać więcej informacji, zobacz [dostępność zestawów dynamicznych](#_core_availability_of_dynasets).

Aby określić, czy zestaw rekordów jest dynamiczny, należy przekazać `CRecordset::dynaset` jako pierwszy parametr `Open` funkcja elementu członkowskiego obiektu zestawu rekordów.

> [!NOTE]
> Dla zestawów dynamicznych nadaje się do aktualizacji, sterownik ODBC musi obsługiwać obu instrukcji update pozycjonowane lub `::SQLSetPos` funkcji interfejsu API ODBC. Jeśli obie są obsługiwane, MFC wykorzystuje `::SQLSetPos` w celu zwiększenia wydajności.

##  <a name="_core_availability_of_dynasets"></a> Dostępność zestawów dynamicznych

Klasy bazy danych MFC obsługuje zestawów dynamicznych, jeśli są spełnione następujące wymagania:

- Z biblioteki kursorów ODBC biblioteki DLL nie może być używany dla tego źródła danych.

   Jeśli jest używany z biblioteki kursorów, maskuje niektóre funkcje podstawowego sterownika ODBC, które są niezbędne do obsługi zestawu dynamicznego. Jeśli chcesz używać zestawów dynamicznych (i sterownik ODBC ma funkcje wymagane dla zestawów dynamicznych, zgodnie z opisem w dalszej części tej sekcji), może spowodować MFC nie jest ładowany z biblioteki kursorów, tworząc `CDatabase` obiektu. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [Otwórz](../../mfc/reference/cdatabase-class.md#open) funkcji składowej klasy typu `CDatabase`.

   W terminologii ODBC migawki i zestawów dynamicznych są określane jako kursorów. Kursor jest mechanizm używany do śledzenia jego pozycja w zestawie rekordów.

- Sterownik ODBC dla źródła danych musi obsługiwać kursory oparte na zestawie kluczy.

   Kursory oparte na zestawie kluczy zarządzanie danymi z tabeli, pobierania i przechowywania zestawu kluczy. Klucze są używane do uzyskania bieżących danych z tabeli, gdy użytkownik przewija widok na określonego rekordu. Aby ustalić, czy sterownik udostępnia tę obsługę, należy wywołać `::SQLGetInfo` funkcji interfejsu API ODBC za pomocą *SQL_SCROLL_OPTIONS* parametru.

   Jeśli spróbujesz otworzyć dynamiczny bez obsługi zestawu kluczy, możesz uzyskać `CDBException` AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED wartością kodu powrotnego.

- Sterownik ODBC dla źródła danych musi obsługiwać pobierania rozszerzonej.

   Podczas pobierania rozszerzonej jest możliwość przewiń do tyłu, a także przekazywać za pośrednictwem rekordów wynikowy zapytania SQL. Aby sprawdzić, czy sterownik obsługuje tę możliwość, należy wywołać `::SQLGetFunctions` funkcji interfejsu API ODBC za pomocą *SQL_API_SQLEXTENDEDFETCH* parametru.

Jeśli chcesz można aktualizować zestawów dynamicznych (lub migawki, istotnego dla badania) sterownika ODBC również musi obsługiwać albo `::SQLSetPos` funkcji interfejsu API ODBC lub Aktualizacje pozycjonowane. `::SQLSetPos` Dzięki funkcji MFC, aby zaktualizować źródła danych bez wysyłania instrukcji języka SQL. Jeśli ta funkcja jest dostępna, MFC wykorzystuje mieszcząca wprowadzania aktualizacji przy użyciu języka SQL. Aby ustalić, czy sterownik obsługuje `::SQLSetPos`, wywołaj `::SQLGetInfo` z *SQL_POS_OPERATIONS* parametru.

Aktualizacje pozycjonowane przy użyciu składni SQL (w postaci **WHERE CURRENT OF** \<cursorname >) do identyfikowania określonego wiersza w tabeli w źródle danych. Aby sprawdzić, czy sterownik obsługuje aktualizacje pozycjonowane, należy wywołać `::SQLGetInfo` z *SQL_POSITIONED_STATEMENTS* parametru.

Ogólnie rzecz biorąc zestawów dynamicznych MFC (ale nie tylko do przodu zestawy rekordów) wymaga sterownika ODBC przy użyciu zgodność interfejsu API na poziomie 2. Sterownik dla źródła danych jest zgodny z poziomu 1 zestawu interfejsów API, można nadal używać migawek można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać zestawów dynamicznych, gdy obsługuje pobieranie rozszerzone i kursory oparte na zestawie kluczy. Aby uzyskać więcej informacji na temat poziomów zgodności ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Jeśli chcesz użyć migawek i zestawy dynamiczne, należy utworzyć je na dwóch różnych `CDatabase` obiektów (w dwóch różnych połączeń).

W przeciwieństwie do migawki, korzystających z magazynu pośredniego utrzymywane przez z biblioteki kursorów ODBC, zestawów dynamicznych pobrać rekord bezpośrednio ze źródła danych, jak szybko przewiń do niego. Dzięki temu rekordy pierwotnie wybranych przez dynamiczny zsynchronizowane ze źródłem danych.

Lista sterowników ODBC zawarte w tej wersji programu Visual C++ i informacji na temat uzyskiwania dodatkowych sterowników, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Zobacz także

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)