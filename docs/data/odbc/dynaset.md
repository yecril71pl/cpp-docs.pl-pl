---
title: Zestaw dynamiczny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec71b5b00b26564f9c8dc3c2d98f53f8182b0ca3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dynaset"></a>Zestaw dynamiczny
W tym temacie opisano zestawów dynamicznych i omówiono ich [dostępności](#_core_availability_of_dynasets).  
  
> [!NOTE]
>  Ten temat dotyczy klasy MFC ODBC, w tym [crecordset —](../../mfc/reference/crecordset-class.md). Aby uzyskać informacji na temat zestawów dynamicznych w klasach DAO, zobacz [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md). DAO można także otworzyć dynamicznego zestawów rekordów.  
  
 Zestaw dynamiczny jest zestaw rekordów z właściwości dynamicznych. Przez jego okres istnienia obiektu zestawu rekordów w trybie dynamiczny (zwykle nazywane dynamiczny) jest synchronizowany ze źródłem danych w następujący sposób. W środowisku wielodostępnym innych użytkowników może edytowanie lub usuwanie rekordów znajdujących się w sieci dynamiczny lub dodać rekordy do tabeli z dynamicznego reprezentowany przez. Rejestruje aplikację dodaje lub usuwa z zestawu rekordów są widoczne w Twojej dynamiczny. Rekordów dodawanych przez innych użytkowników do tabeli nie zostaną odzwierciedlone w Twojej dynamiczny, dopóki odbudować dynamiczny przez wywołanie jego **Requery** funkcję elementu członkowskiego. Gdy inni użytkownicy usuwania rekordów, kod MFC nakłada się na usunięć w twoim zestawie rekordów. Inni użytkownicy zmiany edycji istniejących rekordów są odzwierciedlane w Twojej dynamiczny, jak przewiń do odpowiednich rekordu.  
  
 Podobnie zmiany wprowadzone do rekordów w dynamiczny są uwzględniane w zestawie dynamicznym używane przez innych użytkowników. Rekordy dodane zostaną odzwierciedlone w zestawie dynamicznym innym użytkownikom ich requery ich zestawów dynamicznych. Należy usunąć rekordy są oznaczone jako "usunięte" w zestawach rekordów innych użytkowników. Jeśli masz wiele połączeń z tej samej bazy danych (wiele `CDatabase` obiektów), skojarzone z tymi połączeniami zestawów rekordów jest taki sam jak zestawy rekordów innych użytkowników.  
  
 Zestawy dynamiczne są najbardziej przydatna, gdy dane muszą być dynamiczne, jako (na przykład) system rezerwacji linii lotniczych.  
  
> [!NOTE]
>  Aby korzystać z zestawów dynamicznych, musi mieć sterownika ODBC dla źródła danych, która obsługuje zestawów dynamicznych i nie muszą być ładowane z biblioteki kursorów ODBC. Aby uzyskać więcej informacji, zobacz [dostępności zestawów dynamicznych](#_core_availability_of_dynasets).  
  
 Aby określić, czy zestaw rekordów jest dynamiczny, należy przekazać **CRecordset::dynaset** jako pierwszy parametr **Otwórz** funkcji członkowskiej klasy obiektu zestawu rekordów.  
  
> [!NOTE]
>  Dla zestawów dynamicznych nadaje się do aktualizacji, sterownik ODBC musi obsługiwać albo instrukcji update rozmieszczanych lub **:: SQLSetPos** funkcji interfejsu API ODBC. Jeśli są obsługiwane, używa MFC **:: SQLSetPos** w celu zwiększenia wydajności.  
  
##  <a name="_core_availability_of_dynasets"></a> Dostępność zestawów dynamicznych  
 Klasy baz danych MFC obsługuje zestawów dynamicznych, jeśli są spełnione następujące wymagania:  
  
-   Biblioteka kursorów ODBC biblioteki DLL nie może być używany dla tego źródła danych.  
  
     Jeśli jest używany z biblioteki kursorów, maski funkcjonalność podstawowego sterownika ODBC, które są niezbędne do obsługi dynamiczny. Jeśli chcesz użyć zestawów dynamicznych (i sterownik ODBC ma funkcje wymagane dla zestawów dynamicznych, zgodnie z opisem w dalszej części tej sekcji), może spowodować MFC nie jest ładowany z biblioteki kursorów, podczas tworzenia `CDatabase` obiektu. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [Otwórz](../../mfc/reference/cdatabase-class.md#open) funkcji członkowskiej klasy `CDatabase`.  
  
     W terminologii ODBC zestawów dynamicznych i migawki są określane jako kursorów. Kursor jest mechanizmem używanym w celu śledzenia jej położenie w zestawie rekordów.  
  
-   Sterownik ODBC dla źródła danych musi obsługiwać kursory oparte na zestawie kluczy.  
  
     Kursory oparte na zestawie kluczy zarządzać danymi z tabeli, pobieranie i Zapisywanie zestawu kluczy. Klucze są używane do uzyskania bieżących danych z tabeli, gdy użytkownik przewija na określony rekord. Aby ustalić, czy sterownik udostępnia tę obsługę, należy wywołać **:: SQLGetInfo** funkcji interfejsu API ODBC z **SQL_SCROLL_OPTIONS** parametru.  
  
     Jeśli użytkownik próbuje otworzyć dynamiczny bez obsługi zestawu kluczy, możesz uzyskać `CDBException` z wartość kodu powrotnego **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**.  
  
-   Sterownik ODBC dla źródła danych musi obsługiwać pobierania rozszerzonej.  
  
     Pobieranie rozszerzonej jest możliwość przewijanie do tyłu, a także przekazywanie przez rekordy wynikowy zapytania SQL. Aby sprawdzić, czy sterownik obsługuje tę możliwość, należy wywołać **:: SQLGetFunctions** funkcji interfejsu API ODBC z **SQL_API_SQLEXTENDEDFETCH** parametru.  
  
 Jeśli chcesz można aktualizować zestawów dynamicznych (lub migawki, istotnego dla badania), sterownik ODBC muszą również obsługiwać albo **:: SQLSetPos** funkcji interfejsu API ODBC lub Aktualizacje pozycjonowane. **:: SQLSetPos** dzięki funkcji MFC do aktualizowania źródła danych bez wysyłania instrukcji SQL. Jeśli usługa ta jest dostępna, MFC używa zamiast wprowadzania aktualizacji za pomocą programu SQL. Aby sprawdzić, czy sterownik obsługuje **:: SQLSetPos**, wywołaj **:: SQLGetInfo** z **SQL_POS_OPERATIONS** parametru.  
  
 Aktualizacje pozycjonowane ze składnią języka SQL (w postaci **WHERE CURRENT OF** \<cursorname >) do identyfikowania określonego wiersza w tabeli w źródle danych. Aby sprawdzić, czy sterownik obsługuje aktualizacje pozycjonowane, należy wywołać **:: SQLGetInfo** z **SQL_POSITIONED_STATEMENTS** parametru.  
  
 Ogólnie rzecz biorąc MFC zestawów dynamicznych (ale nie Progresywne zestawy rekordów) wymaga sterownika ODBC z poziomu 2 zgodność interfejsu API. Jeśli sterownik dla źródła danych jest zgodny z zestawem interfejsu API poziom 1, można nadal używać migawek zarówno można aktualizować i tylko do odczytu i zestawy rekordów tylko do przodu, ale nie zestawów dynamicznych. Jednak sterownik poziom 1 może obsługiwać zestawów dynamicznych, jeśli obsługuje rozszerzonych pobieranie i kursory oparte na zestawie kluczy. Aby uzyskać więcej informacji na temat poziomów zgodności ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).  
  
> [!NOTE]
>  Jeśli chcesz używać migawek i zestawów dynamicznych, należy utworzyć je na dwóch różnych `CDatabase` obiekty (w dwóch różnych połączeń).  
  
 W przeciwieństwie do migawki, korzystających z magazynu pośredniego obsługiwane przez ODBC — Biblioteka kursorów, zestawów dynamicznych pobrać rekordu bezpośrednio ze źródła danych, jak szybko przewiń do niego. Dzięki temu rekordy pierwotnie wybranej dynamiczny synchronizowane ze źródłem danych.  
  
 Lista sterowników ODBC zawarte w tej wersji programu Visual C++ oraz informacje na temat uzyskiwania dodatkowe sterowniki, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)