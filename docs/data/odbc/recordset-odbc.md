---
title: "Zestaw rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 668cd4b2f27c2cde18528c0eb2d4d661160c4e4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-odbc"></a>Zestaw rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 A [crecordset —](../../mfc/reference/crecordset-class.md) obiekt reprezentuje zestaw rekordów wybrane źródła danych. Rekordy można z:  
  
-   Tabela.  
  
-   Zapytanie.  
  
-   Procedury przechowywanej, która uzyskuje dostęp do co najmniej jedna tabela.  
  
 Przykład zestawu rekordów z tabeli jest "wszystkich klientów", który uzyskuje dostęp do tabeli klienta. Przykładem kwerendy jest "wszystkie faktury Jan Nowak". Przykład zestawu rekordów, oparty na procedurze składowanej (nazywane również wstępnie zdefiniowanego zapytania) to "wszystkie konta delinquent," który wywołuje procedurę przechowywaną w bazie danych zaplecza. Zestaw rekordów może dołączyć do co najmniej dwie tabele z tego samego źródła danych, ale nie tabel z różnych źródeł danych.  
  
> [!NOTE]
>  Aby dowiedzieć się, jak wyprowadzanie klas rekordów z kreatorów, zobacz [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) i [obsługi bazy danych, Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md).  
  
> [!NOTE]
>  Niektóre sterowniki ODBC obsługuje widoków bazy danych. Widok, w tym sensie jest kwerenda pierwotnie utworzone SQL `CREATE VIEW` instrukcji. Kreatorów aktualnie nie obsługują widoków, ale istnieje możliwość kodu ta obsługa samodzielnie.  
  
##  <a name="_core_recordset_capabilities"></a>Możliwości zestawu rekordów  
 Wszystkie obiekty rekordów mają następujące możliwości:  
  
-   Jeśli źródło danych nie jest tylko do odczytu, można określić, że można zestawu rekordów [aktualizowalnych](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [appendable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), lub w trybie tylko do odczytu. Jeśli zestaw rekordów jest aktualizowalne, możesz wybrać pesymistyczne lub optymistycznej [blokowania](../../data/odbc/recordset-locking-records-odbc.md) przedstawić metody, sterownik dostarcza odpowiednią obsługę blokowania. Jeśli źródło danych jest tylko do odczytu, zestaw rekordów będą tylko do odczytu.  
  
-   Można wywołać elementu członkowskiego funkcji [przewijania](../../data/odbc/recordset-scrolling-odbc.md) za pośrednictwem wybranych rekordów.  
  
-   Możesz [filtru](../../data/odbc/recordset-filtering-records-odbc.md) rekordów, aby ograniczyć, które rekordy są wybierane spośród dostępnych.  
  
-   Możesz [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) rekordy w kolejności rosnącej lub malejącej, oparte na co najmniej jedną kolumnę.  
  
-   Możesz [parametryzacja](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) rekordów do kwalifikowania rekordów zaznaczenie w czasie wykonywania.  
  
##  <a name="_core_snapshots_and_dynasets"></a>Migawki i zestawów dynamicznych  
 Istnieją dwa główne typy zestawy rekordów: [migawki](../../data/odbc/snapshot.md) i [zestawów dynamicznych](../../data/odbc/dynaset.md). Są obsługiwane przez klasę `CRecordset`. Każdy udostępnia typowe cechy wszystkie zestawy rekordów, ale każdy rozszerzają często używane funkcje w specjalne sposób. Migawki Podaj widok statyczny danych, a także są przydatne w przypadku raportów i innych sytuacjach, w których chcesz widok danych znajdowały się w określonym czasie. Zestawy dynamiczne są przydatne, gdy wymagane są aktualizacje wprowadzone przez innych użytkowników, aby były widoczne w zestawie rekordów bez konieczności requery lub Odśwież zestaw rekordów. Migawki i zestawów dynamicznych może być można aktualizować lub tylko do odczytu. Do uwzględnienia rekordy dodane lub usunięte przez innych użytkowników, zadzwoń [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).  
  
 `CRecordset`Umożliwia również dwa typy zestawów rekordów: dynamiczne zestawy rekordów i zestawy rekordów tylko do przodu. Dynamiczne zestawy rekordów są podobne do zestawów dynamicznych; jednak dynamiczne zestawy rekordów odzwierciedla wszystkie rekordy dodane lub usunięte bez wywoływania elementu `CRecordset::Requery`. Z tego powodu dynamiczne zestawy rekordów są zazwyczaj kosztowne względem czasu przetwarzania w systemie DBMS i wiele sterowników ODBC ich nie obsługują. Z kolei zestawy rekordów tylko do przodu, podaj najbardziej wydajne dostęp do danych dla zestawów rekordów, które nie wymagają aktualizacji lub przewijanie do tyłu. Na przykład można użyć do migracji danych z jednego źródła danych do innego, gdzie należy tylko przenieść dane znajdujące się w kierunku do przodu rekordów. Aby użyć rekordów, należy wykonać obie następujące czynności:  
  
-   Przekaż opcję **CRecordset::forwardOnly** jako `nOpenType` parametr [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego.  
  
-   Określ **CRecordset::readOnly** w `dwOptions` parametr **Otwórz**.  
  
    > [!NOTE]
    >  Uzyskać informacje o pomocy technicznej dynamiczny, wymagania dotyczące sterownika ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md). Lista sterowników ODBC zawarte w tej wersji programu Visual C++ oraz informacje na temat uzyskiwania dodatkowe sterowniki, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).  
  
##  <a name="_core_your_recordsets"></a>Zestawach rekordów  
 Dla każdego różne tabeli, widoku lub procedury przechowywanej, która ma dostęp do zwykle zdefiniuj klasę pochodzącą od `CRecordset`. (Wyjątkiem jest sprzężenia bazy danych, w której jeden zestaw rekordów reprezentuje kolumnę z dwóch lub więcej tabel). Gdy klasa wyprowadzona z zestawu rekordów, można włączać mechanizm pól rekordów (RFX) programu exchange lub mechanizm wymiany (zbiorczego RFX) pól rekordów zbiorczego, które są podobne do mechanizmu okna dialogowego danych programu exchange (DDX). RFX i RFX zbiorczego uprościć transferu danych ze źródła danych do zestawu rekordów; RFX dodatkowo przesyła dane z zestawu rekordów w źródle danych. Aby uzyskać więcej informacji, zobacz [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Obiekty zestawów rekordów umożliwia dostęp do wszystkich wybranych rekordów. Przewiń wiele rekordów przy użyciu `CRecordset` funkcje Członkowskie, takich jak `MoveNext` i `MovePrev`. W tym samym czasie obiekty zestawów rekordów reprezentuje tylko jeden z wybranych rekordów bieżącego rekordu. Należy zbadać pól bieżącego rekordu przez zadeklarowanie rekordów zmiennych Członkowskich klasy odpowiadające kolumn w tabeli lub rekordy, które wynikają z zapytań bazy danych. Uzyskać informacji o zestawie rekordów elementy członkowskie danych, zobacz [zestaw rekordów: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).  
  
 W poniższych tematach opisano szczegóły przy użyciu obiektów zestawu rekordów. Tematy są wyświetlane w kategorie funkcjonalne i kolejność przeglądania fizycznych, pozwalające sekwencyjnego odczytu.  
  
### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Tematy dotyczące sposobu otwierania, odczytywania i zamykanie zestawów rekordów  
  
-   [Zestaw rekordów: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [Zestaw rekordów: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [Zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [Zestaw rekordów: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [Zestaw rekordów: Zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [Zestaw rekordów: Filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [Zestaw rekordów: Sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Tematy dotyczące sposobu modyfikowania zestawy rekordów  
  
-   [Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [Zestaw rekordów: Blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [Zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### <a name="topics-about-somewhat-more-advanced-techniques"></a>Tematy dotyczące nieco bardziej zaawansowane techniki  
  
-   [Zestaw rekordów: Wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [Zestaw rekordów: Dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [Zestaw rekordów: Zbiorcze pobieranie rekordów (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [Zestaw rekordów: Praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [Zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### <a name="topics-about-how-recordsets-work"></a>Tematy dotyczące działania zestawy rekordów  
  
-   [Zestaw rekordów: Jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)