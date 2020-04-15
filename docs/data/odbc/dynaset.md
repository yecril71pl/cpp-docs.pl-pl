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
ms.openlocfilehash: 2eb2447d1f984b7734d5e9c45087023e5a6f003f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371843"
---
# <a name="dynaset"></a>Zestaw dynamiczny

W tym temacie opisano dynasets i omówiono ich [dostępność](#_core_availability_of_dynasets).

> [!NOTE]
> Ten temat dotyczy klas MFC ODBC, w tym [CRecordset](../../mfc/reference/crecordset-class.md). Aby uzyskać informacje na temat dynasets w klasach DAO, zobacz [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Z DAO, można otworzyć dynaset typu recordsets.

Dynaset jest zestawem rekordów o właściwościach dynamicznych. W okresie jego istnienia obiekt zestawu rekordów w trybie dynaset (zwykle nazywany dynaset) pozostaje zsynchronizowany ze źródłem danych w następujący sposób. W środowisku dla wielu użytkowników inni użytkownicy mogą edytować lub usuwać rekordy, które znajdują się w zestawie dynamiki lub dodawać rekordy do tabeli, którą reprezentuje zestaw dynaset. Rekordy dodania aplikacji do zestawu rekordów lub ich usunięcia są odzwierciedlane w zestawie dynamicznym. Rekordy dodawanye przez innych użytkowników do tabeli nie zostaną odzwierciedlone w `Requery` zestawie dynamiki, dopóki nie odbudujesz zestawu dynaset, wywołując jego funkcję elementu członkowskiego. Gdy inni użytkownicy usuwają rekordy, kod MFC pomija usunięcia w pliku recordset. Zmiany edycji innych użytkowników w istniejących rekordach są odzwierciedlane w zestawie dynamiki zaraz po przewinięciu do rekordu, którego dotyczy problem.

Podobnie zmiany wprowadzone w rekordach w zestawie dynamiki są odzwierciedlane w zestawach dynasetów używanych przez innych użytkowników. Dodane rekordy nie są odzwierciedlane w dynasetach innych użytkowników, dopóki nie będą ponownie poddawać kwerendom. Usuwane rekordy są oznaczane jako "usunięte" w zestawy rekordów innych użytkowników. Jeśli masz wiele połączeń z tą `CDatabase` samą bazą danych (wiele obiektów), zestawy rekordów skojarzone z tymi połączeniami mają taki sam stan jak zestawy rekordów innych użytkowników.

Dynasets są najcenniejsze, gdy dane muszą być dynamiczne, jak (na przykład) w systemie rezerwacji linii lotniczych.

> [!NOTE]
> Aby używać dynasets, musi mieć sterownik ODBC dla źródła danych, który obsługuje dynasets i biblioteki kursora ODBC nie mogą być ładowane. Aby uzyskać więcej informacji, zobacz [Dostępność dynasetów](#_core_availability_of_dynasets).

Aby określić, że zestaw rekordów jest `CRecordset::dynaset` zestawem dynaset, należy przekazać jako pierwszy parametr funkcji `Open` elementu członkowskiego obiektu zestawu rekordów.

> [!NOTE]
> W przypadku aktualizacji dynasets sterownik ODBC musi obsługiwać instrukcje aktualizacji pozycjonowane lub funkcję INTERFEJSU API `::SQLSetPos` ODBC. Jeśli oba są obsługiwane, MFC używa `::SQLSetPos` wydajności.

## <a name="availability-of-dynasets"></a><a name="_core_availability_of_dynasets"></a>Dostępność dynasetów

Klasy bazy danych MFC obsługują zestawy dynasets, jeśli spełnione są następujące wymagania:

- Biblioteka DLL biblioteki kursorów ODBC nie może być używana dla tego źródła danych.

   Jeśli używana jest biblioteka kursorów, maskuje niektóre funkcje podstawowego sterownika ODBC, który jest niezbędny do obsługi dynaset. Jeśli chcesz użyć dynasets (a sterownik ODBC ma funkcje wymagane dla dynasets, jak opisano w pozostałej części tej sekcji), można spowodować `CDatabase` MFC nie załadować biblioteki kursora podczas tworzenia obiektu. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [Otwórz](../../mfc/reference/cdatabase-class.md#open) funkcję członkowu klasy `CDatabase`.

   W terminologii ODBC dynasets i migawki są określane jako kursory. Kursor jest mechanizmem używanym do śledzenia jego pozycji w ach.

- Sterownik ODBC dla źródła danych musi obsługiwać kursory oparte na zestawie kluczy.

   Kursory oparte na zestawie kluczy zarządzają danymi z tabeli, uzyskując i przechowując zestaw kluczy. Klucze są używane do uzyskiwania bieżących danych z tabeli, gdy użytkownik przewija do określonego rekordu. Aby ustalić, czy sterownik zapewnia `::SQLGetInfo` tę obsługę, należy wywołać funkcję INTERFEJSU API ODBC z *parametrem SQL_SCROLL_OPTIONS.*

   Jeśli spróbujesz otworzyć dynaset bez obsługi zestawu `CDBException` kluczy, otrzymasz z wartością kodu zwrotnego AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- Sterownik ODBC dla źródła danych musi obsługiwać pobieranie rozszerzone.

   Pobieranie rozszerzone to możliwość przewijania do tyłu, a także do przodu za pośrednictwem rekordów wynikowych kwerendy SQL. Aby ustalić, czy sterownik obsługuje `::SQLGetFunctions` tę zdolność, należy wywołać funkcję INTERFEJSU API ODBC z *parametrem SQL_API_SQLEXTENDEDFETCH.*

Jeśli chcesz aktualizować dynasets (lub migawki, o to chodzi), sterownik `::SQLSetPos` ODBC musi również obsługiwać funkcję INTERFEJSU API ODBC lub aktualizacje pozycjonowane. Funkcja `::SQLSetPos` umożliwia MFC zaktualizować źródło danych bez wysyłania instrukcji SQL. Jeśli ta obsługa jest dostępna, MFC używa go zamiast dokonywania aktualizacji przy użyciu języka SQL. Aby ustalić, czy `::SQLSetPos`sterownik `::SQLGetInfo` obsługuje, zadzwoń z *parametrem SQL_POS_OPERATIONS.*

Aktualizacje pozycjonowane używają składni SQL (formularza **WHERE CURRENT OF** \<cursorname>) do identyfikowania określonego wiersza w tabeli w źródle danych. Aby ustalić, czy sterownik obsługuje `::SQLGetInfo` aktualizacje pozycyjne, należy wywołać z *parametrem SQL_POSITIONED_STATEMENTS.*

Ogólnie rzecz biorąc dynasets MFC (ale nie do przodu tylko recordsets) wymagają sterownika ODBC z poziomu 2 zgodności interfejsu API. Jeśli sterownik źródła danych jest zgodny z zestawem interfejsu API poziomu 1, nadal można używać zarówno aktualizacji, jak i migawek tylko do odczytu oraz zestawów rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziomu 1 może obsługiwać zestawy dynamiki, jeśli obsługuje rozszerzone pobieranie i kursory oparte na zestawie kluczy. Aby uzyskać więcej informacji na temat poziomów zgodności z ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Jeśli chcesz używać zarówno migawek, jak i zestawów dynamicznych, należy je oprzeć na dwóch różnych `CDatabase` obiektach (dwóch różnych połączeniach).

W przeciwieństwie do migawek, które używają magazynu pośredniego obsługiwanego przez bibliotekę kursora ODBC, zestawy dynasets pobierają rekord bezpośrednio ze źródła danych zaraz po przewinięciu do niego. Spowoduje to synchronizację rekordów pierwotnie wybranych przez zestaw dynaset ze źródłem danych.

Aby uzyskać listę sterowników ODBC zawartych w tej wersji programu Visual C++ oraz informacje na temat uzyskiwania dodatkowych sterowników, zobacz [Lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
