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
ms.openlocfilehash: ed7098600126005978c8b017e7db378fca4c1a68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213242"
---
# <a name="dynaset"></a>Zestaw dynamiczny

W tym temacie opisano zestawy dynamiczne i omówiono ich [dostępność](#_core_availability_of_dynasets).

> [!NOTE]
>  Ten temat dotyczy klas MFC ODBC, w tym [CRecordset](../../mfc/reference/crecordset-class.md). Aby uzyskać informacje na temat zestawów dynamicznych w klasach DAO, zobacz [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Za pomocą obiektów DAO można otwierać zestawy rekordów typu dynamiczny.

Dynamiczny jest zestawem rekordów z właściwościami dynamicznymi. W trakcie okresu istnienia obiekt zestawu rekordów w trybie dynamicznym (zwykle nazywany zestawem dynamicznym) pozostaje zsynchronizowany ze źródłem danych w następujący sposób. W środowisku wielodostępnym inni użytkownicy mogą edytować lub usuwać rekordy, które znajdują się w dynamicznym spisie, lub dodawać rekordy do tabeli, którą reprezentuje zestaw dynamiczny. Rejestruje, że aplikacja dodaje lub usuwa z zestawu rekordów są odzwierciedlone w zestawie dynamicznym. Rekordy dodawane przez innych użytkowników do tabeli nie zostaną odzwierciedlone w dynamicznym, dopóki nie zostanie odbudowany zestaw dynamiczny przez wywołanie jego `Requery` funkcji członkowskiej. Gdy inni użytkownicy usuwają rekordy, kod MFC pomija operacje usuwania w zestawie rekordów. Zmiany edytowane przez innych użytkowników w istniejących rekordach są uwzględniane w zestawie dynamicznym, gdy tylko przewiniesz do rekordu, którego to dotyczy.

Podobnie zmiany wprowadzane do rekordów w dynamicznym programie są odzwierciedlone w zestawach dynamicznych używanych przez innych użytkowników. Rekordy dodawane przez użytkownika nie są uwzględniane w zestawach dynamicznych innych użytkowników, dopóki nie ponowią kwerendy ich zestawów dynamicznych. Rekordy, które usuniesz, są oznaczane jako usunięte w innych zestawach rekordów użytkowników. Jeśli masz wiele połączeń z tą samą bazą danych (wielu `CDatabase` obiektów), zestawy rekordów skojarzone z tymi połączeniami mają taki sam stan jak zestawy rekordów innych użytkowników.

Zestawy dynamiczne są najbardziej cenne, gdy dane muszą być dynamiczne, jako (na przykład) w systemie rezerwacji linii lotniczej.

> [!NOTE]
> Aby korzystać z zestawów dynamicznych, musisz mieć sterownik ODBC dla źródła danych, które obsługuje zestawy dynamiczne, a Biblioteka kursora ODBC nie może być ładowana. Aby uzyskać więcej informacji, zobacz [dostępność zestawów dynamicznych](#_core_availability_of_dynasets).

Aby określić, że zestaw rekordów jest dynamiczny, Przekaż `CRecordset::dynaset` jako pierwszy parametr do `Open` funkcji składowej obiektu zestawu rekordów.

> [!NOTE]
> W przypadku aktualizowalnych zestawów dynamicznych sterownik ODBC musi obsługiwać ustawione instrukcje aktualizacji lub funkcję `::SQLSetPos` ODBC API. Jeśli obie są obsługiwane, MFC używa `::SQLSetPos` w celu zwiększenia wydajności.

##  <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dostępność zestawów dynamicznych

Klasy baz danych MFC obsługują zestawy dynamiczne, jeśli spełnione są następujące wymagania:

- DLL biblioteki kursora ODBC nie może być używana dla tego źródła danych.

   Jeśli Biblioteka kursorów jest używana, maskuje pewne funkcje podstawowego sterownika ODBC, który jest niezbędny do obsługi systemu dynamicznego. Jeśli chcesz używać zestawów dynamicznych (a sterownik ODBC ma funkcje wymagane dla zestawów dynamicznych, zgodnie z opisem w dalszej części tej sekcji), możesz wywołać MFC, aby nie ładować biblioteki kursora podczas tworzenia obiektu `CDatabase`. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) oraz funkcja [OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [Open](../../mfc/reference/cdatabase-class.md#open) member klasy `CDatabase`.

   W terminologii ODBC, zestawy dynamiczne i migawki są określane jako kursory. Kursor jest mechanizmem służącym do śledzenia jego pozycji w zestawie rekordów.

- Sterownik ODBC dla źródła danych musi obsługiwać kursory oparte na zestawie kluczy.

   Kursory sterowane zestawem kluczy zarządzają danymi z tabeli przez pobranie i przechowywanie zestawu kluczy. Klucze są używane do uzyskiwania bieżących danych z tabeli, gdy użytkownik przewinie do określonego rekordu. Aby określić, czy sterownik obsługuje tę obsługę, wywołaj funkcję interfejsu API `::SQLGetInfo` ODBC z parametrem *SQL_SCROLL_OPTIONS* .

   Jeśli spróbujesz otworzyć dynamiczny, bez obsługi zestawu kluczy, uzyskasz `CDBException` z AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED wartością kodu powrotu.

- Sterownik ODBC dla źródła danych musi obsługiwać rozszerzone pobieranie.

   Rozszerzone pobieranie to możliwość przewijania do tyłu i do przodu w wyniku rekordów zapytania SQL. Aby określić, czy sterownik obsługuje tę możliwość, wywołaj funkcję interfejsu API `::SQLGetFunctions` ODBC z parametrem *SQL_API_SQLEXTENDEDFETCH* .

Jeśli chcesz, aby możliwe było aktualizowalne zestawy dynamiczne (lub migawki), sterownik ODBC musi również obsługiwać funkcję `::SQLSetPos` ODBC API lub aktualizacje położenia. Funkcja `::SQLSetPos` umożliwia MFC aktualizowanie źródła danych bez wysyłania instrukcji SQL. Jeśli ta obsługa jest dostępna, MFC używa jej w preferencjach, aby wprowadzać aktualizacje przy użyciu języka SQL. Aby określić, czy sterownik obsługuje `::SQLSetPos`, wywołaj `::SQLGetInfo` z parametrem *SQL_POS_OPERATIONS* .

Aktualizacje pozycjonowane używają składni SQL (w postaci, w **której bieżąca** \<cursorname >) do identyfikowania konkretnego wiersza w tabeli w źródle danych. Aby określić, czy sterownik obsługuje aktualizacje rozmieszczone, wywołaj `::SQLGetInfo` z parametrem *SQL_POSITIONED_STATEMENTS* .

Ogólnie zestawy dynamiczne MFC (ale nie tylko zestaw rekordów) wymagają sterownika ODBC z zgodnym z interfejsem API poziomu 2. Jeśli sterownik źródła danych jest zgodny z zestawem interfejsów API poziomu 1, nadal można używać zarówno migawek, jak i tylko do odczytu, jak i zestawów rekordów, ale nie zestawów dynamicznych. Jednak sterownik Level 1 może obsługiwać zestawy dynamiczne, jeśli obsługuje rozszerzone pobieranie i kursory oparte na zestawie kluczy. Aby uzyskać więcej informacji na temat poziomów zgodności ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Jeśli chcesz użyć migawek i zestawów dynamicznych, musisz oprzeć je na dwóch różnych obiektach `CDatabase` (dwa różne połączenia).

W przeciwieństwie do migawek, które używają magazynu pośredniego obsługiwanego przez bibliotekę kursora ODBC, zestawy dynamiczne pobierają rekord bezpośrednio ze źródła danych, gdy tylko przewiniesz do niego. Pozwala to zachować rekordy początkowo wybrane przez zestaw dynamiczny ze źródłem danych.

Aby uzyskać listę sterowników ODBC uwzględnionych w tej wersji programu Visual C++ i uzyskać informacje o uzyskiwaniu dodatkowych sterowników, zobacz [Lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
