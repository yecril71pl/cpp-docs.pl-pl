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
ms.openlocfilehash: e175a9b27cb19b0c2a67a08751b7a7717226ac55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435142"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: biblioteka kursorów ODBC

W tym temacie opisano z biblioteki kursorów ODBC oraz wyjaśniono, jak z niego korzystać. Aby uzyskać więcej informacji, zobacz:

- [Sterowniki ODBC — Biblioteka kursorów i poziomu 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Aktualizacje pozycjonowane i kolumn sygnatur czasowych](#_core_positioned_updates_and_timestamp_columns)

- [Korzystanie z biblioteki kursorów](#_core_using_the_cursor_library)

Z biblioteki kursorów ODBC jest biblioteki dołączanej (dynamicznie DLL), który znajduje się między Menedżera sterowników ODBC i sterowników. W warunkach ODBC sterownik obsługuje kursor do śledzenia jego pozycja w zestawie rekordów. Kursor oznacza pozycja w zestawie danych, do których już mają przewiniesz — bieżącego rekordu.

##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> Sterowniki ODBC — Biblioteka kursorów i poziomu 1

Z biblioteki kursorów ODBC zapewnia sterowniki poziomu 1 następujące nowe funkcje:

- Przewijanie do przodu i Wstecz. Sterowniki poziomu 2 nie ma potrzeby z biblioteki kursorów, ponieważ są one już przewijany.

- Obsługa migawki. Biblioteka kursorów zarządza bufor zawierającego rekordy migawki. Ten bufor odzwierciedla usunięcia programu i edytowanie rekordów, ale nie dodawania, usuwania ani przez innych użytkowników. W związku z tym migawka jest tylko jako bieżący jako bufor z biblioteki kursorów. Bufor również nie będzie odzwierciedlał własne dodatki do czasu wywołania `Requery`. Zestawy dynamiczne nie należy używać z biblioteki kursorów.

Biblioteka kursorów zapewnia migawek (Kursory statyczne), nawet jeśli nie są zazwyczaj obsługiwane przez sterownik. Jeśli sterownik obsługuje już Kursory statyczne, nie musisz załadować z biblioteki kursorów, aby uzyskać pomoc techniczną migawki. Jeśli korzystasz z biblioteki kursorów, można użyć tylko migawki i zestawy rekordów tylko do przodu. Jeśli sterownik sieci obsługuje zestawów dynamicznych (KEYSET_DRIVEN kursory) i chcesz umożliwić ich używanie, nie można używać z biblioteki kursorów. Jeśli chcesz użyć migawek i zestawy dynamiczne, należy utworzyć je na dwóch różnych `CDatabase` obiektów (w dwóch różnych połączeń), jeśli sterownik nie obsługuje obie.

##  <a name="_core_positioned_updates_and_timestamp_columns"></a> Aktualizacje pozycjonowane i kolumn sygnatur czasowych

> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub przy użyciu klas MFC obiekt DAO (Data Access).

> [!NOTE]
>  Jeśli sterownik ODBC obsługuje `SQLSetPos`, które MFC wykorzystuje, jeśli jest dostępny, w tym temacie nie ma zastosowania do użytkownika.

Większość sterowników poziom 1 nie obsługują aktualizacje pozycjonowane. Takie sterowniki korzystają z biblioteki kursorów do emulowania możliwości sterowników na poziomie 2 w związku z tym. Biblioteka kursorów emuluje obsługę aktualizacji pozycjonowane, wykonując wyszukiwanych aktualizacji niezmiennych pól.

W niektórych przypadkach zestaw rekordów może zawierać kolumny sygnatur czasowych jako jeden z tych pól niezmiennych. Przy użyciu zestawów rekordów MFC z tabelami, które zawierają kolumn sygnatur czasowych, wystąpią dwa problemy.

Pierwszy problem dotyczy można aktualizować migawek w tabelach mających kolumny sygnatur czasowych. Jeśli tabela, z którym powiązany jest migawek zawiera kolumnę sygnatur czasowych, należy wywołać `Requery` po wywołaniu metody `Edit` i `Update`. Jeśli nie, nie można ponownie edytować ten sam rekord. Gdy wywołujesz `Edit` i następnie `Update`rekordu są zapisywane do źródła danych i zaktualizowaniu kolumnę sygnatur czasowych. Jeśli nie zostanie wywołana `Requery`, wartość sygnatury czasowej dla rekordu w migawek nie jest już zgodny odpowiedniej sygnatury czasowej w źródle danych. Podczas próby ponownie zaktualizować rekord źródła danych może nie zezwalaj na aktualizację ze względu na niezgodność.

Drugi problem dotyczy ograniczenia klasy [CTime](../../atl-mfc-shared/reference/ctime-class.md) gdy jest używane z `RFX_Date` funkcję, aby przekazać informacje dotyczące godziny i daty do lub z tabeli. Przetwarzanie `CTime` obiektu nakłada pewne nadmiarowe obciążenie w postaci dodatkowych pośrednich przetwarzania podczas transferu danych. Zakres dat `CTime` obiektów może być również zbyt ograniczenie w niektórych aplikacjach. Nowa wersja `RFX_Date` funkcja przyjmuje ODBC *TIMESTAMP_STRUCT* parametr zamiast `CTime` obiektu. Aby uzyskać więcej informacji, zobacz `RFX_Date` w [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie MFC*.

##  <a name="_core_using_the_cursor_library"></a> Korzystanie z biblioteki kursorów

Po nawiązaniu połączenia ze źródłem danych, wywołując [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — można określić, czy ma być używany z biblioteki kursorów dla źródła danych. Jeśli zostanie utworzona migawek dla tego źródła danych, należy określić `CDatabase::useCursorLib` opcji `dwOptions` parametru, aby `OpenEx` lub określ wartość TRUE dla *bUseCursorLib* parametru, aby `Open` (wartość domyślna to WARTOŚĆ TRUE). Jeśli sterownik ODBC obsługuje zestawów dynamicznych i chcesz otworzyć zestawów dynamicznych w źródle danych, nie należy używać z biblioteki kursorów (go maskuje niektórych sterowników potrzebnych funkcji dla zestawów dynamicznych). W takiej sytuacji nie należy określać `CDatabase::useCursorLib` w `OpenEx` lub określić wartość FALSE dla *bUseCursorLib* parametru w `Open`.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)