---
title: 'ODBC: biblioteka kursorów ODBC'
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367178"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: biblioteka kursorów ODBC

W tym temacie opisano bibliotekę kursora ODBC i wyjaśniono, jak jej używać. Aby uzyskać więcej informacji, zobacz:

- [Biblioteka kursorów i sterowniki ODBC poziomu 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Aktualizacje pozycjonowane i kolumny sygnatury czasowej](#_core_positioned_updates_and_timestamp_columns)

- [Korzystanie z biblioteki kursorów](#_core_using_the_cursor_library)

Biblioteka kursora ODBC jest biblioteką łącza dynamicznego (DLL), która znajduje się między Menedżerem sterowników ODBC a sterownikiem. W warunkach ODBC kierowca utrzymuje kursor, aby śledzić jego pozycję w rekordze. Kursor oznacza pozycję w ach, do której został już przewinięty — bieżący rekord.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Biblioteka kursorów i sterowniki ODBC poziomu 1

Biblioteka kursorów ODBC zapewnia sterownikom poziomu 1 następujące nowe możliwości:

- Przewijanie do przodu i do tyłu. Sterowniki poziomu 2 nie potrzebują biblioteki kursorów, ponieważ są już przewijane.

- Obsługa migawek. Biblioteka kursorów zarządza buforem zawierającym rekordy migawki. Ten bufor odzwierciedla usunięcia i zmiany wprowadzone przez program do rekordów, ale nie dodawania, usunięcia lub zmiany innych użytkowników. W związku z tym migawka jest tylko tak bieżąca, jak bufor biblioteki kursora. Bufor również nie odzwierciedla własnych dodatków, `Requery`dopóki nie zadzwonisz . Dynasets nie używa biblioteki kursorów.

Biblioteka kursorów udostępnia migawki (kursory statyczne), nawet jeśli zwykle nie są obsługiwane przez sterownik. Jeśli sterownik obsługuje już kursory statyczne, nie trzeba ładować biblioteki kursorów, aby uzyskać obsługę migawki. Jeśli używasz biblioteki kursorów, można używać tylko migawek i rekordów tylko do przodu. Jeśli sterownik obsługuje dynasets (KEYSET_DRIVEN kursory) i chcesz ich używać, nie należy używać biblioteki kursorów. Jeśli chcesz używać zarówno migawek, jak i zestawów dynamicznych, należy oprzeć je na dwóch różnych `CDatabase` obiektach (dwa różne połączenia), chyba że sterownik obsługuje oba.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Aktualizacje pozycjonowane i kolumny sygnatury czasowej

> [!NOTE]
> Źródła danych ODBC są dostępne za pośrednictwem klas Odbc MFC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektu dostępu do danych MFC (DAO).

> [!NOTE]
> Jeśli sterownik ODBC `SQLSetPos`obsługuje , który MFC używa, jeśli jest dostępny, ten temat nie ma zastosowania do Ciebie.

Większość sterowników poziomu 1 nie obsługuje aktualizacji pozycjonowanych. Takie sterowniki polegają na bibliotece kursora, aby emulować możliwości sterowników poziomu 2 w tym zakresie. Biblioteka kursorów emuluje pozycjonowane wsparcie aktualizacji, wykonując przeszukiwaną aktualizację na niezmiennych polach.

W niektórych przypadkach znacznik rekordów może zawierać kolumnę sygnatury czasowej jako jedno z tych niezmiennych pól. Dwa problemy pojawiają się przy użyciu MFC recordsets z tabel, które zawierają kolumny sygnatury czasowej.

Pierwszy problem dotyczy można zaktualizować migawki w tabelach z kolumn sygnatury czasowej. Jeśli tabela, z którą powiązana jest migawka, `Requery` zawiera `Edit` kolumnę sygnatury czasowej, należy wywołać po wywołaniu i `Update`. Jeśli nie, może nie być możliwe ponowne edytowanie tego samego rekordu. Po `Edit` wywołaniu, `Update`a następnie rekord jest zapisywany w źródle danych, a kolumna sygnatury czasowej jest aktualizowana. Jeśli nie wywołasz `Requery`, wartość sygnatury czasowej rekordu w migawce nie jest już zgodna z odpowiednią sygnaturą czasową w źródle danych. Podczas próby ponownego zaktualizowania rekordu źródło danych może nie zezwalać na aktualizację z powodu niezgodności.

Drugi problem dotyczy ograniczeń klasy [CTime,](../../atl-mfc-shared/reference/ctime-class.md) gdy jest używana z funkcją `RFX_Date` do przesyłania informacji o czasie i dacie do lub z tabeli. Przetwarzanie `CTime` obiektu nakłada pewne obciążenie w postaci dodatkowego przetwarzania pośredniego podczas przesyłania danych. Zakres dat `CTime` obiektów może być również zbyt ograniczający dla niektórych aplikacji. Nowa wersja `RFX_Date` funkcji przyjmuje parametr *TIMESTAMP_STRUCT* ODBC zamiast `CTime` obiektu. Aby uzyskać więcej `RFX_Date` informacji, zobacz [makra i globals](../../mfc/reference/mfc-macros-and-globals.md) w *odwołaniu MFC*.

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Korzystanie z biblioteki kursorów

Po nawiązaniu połączenia ze źródłem danych — wywołując [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — można określić, czy należy używać biblioteki kursora dla źródła danych. Jeśli będziesz tworzyć migawki w tym źródle `CDatabase::useCursorLib` danych, `dwOptions` określ opcję w parametrze lub `OpenEx` określ wartość TRUE dla parametru *bUseCursorLib* `Open` (domyślną wartością jest PRAWDA). Jeśli sterownik ODBC obsługuje dynasets i chcesz otworzyć dynasets na źródle danych, nie należy używać biblioteki kursora (maskuje niektóre funkcje sterownika potrzebne dla dynasets). W takim przypadku nie `CDatabase::useCursorLib` `OpenEx` należy określać ani określać wartości FAŁSZ dla parametru *bUseCursorLib* w pliku `Open`.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
