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
ms.openlocfilehash: 51524604cad34ace18ffda2b5f48cc3c5fd89ad7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213099"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: biblioteka kursorów ODBC

W tym temacie opisano bibliotekę kursorów ODBC i wyjaśniono, jak jej używać. Aby uzyskać więcej informacji, zobacz:

- [Biblioteka kursorów i sterowniki ODBC na poziomie 1](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Aktualizacje pozycjonowane i kolumny sygnatur czasowych](#_core_positioned_updates_and_timestamp_columns)

- [Korzystanie z biblioteki kursorów](#_core_using_the_cursor_library)

Biblioteka kursorów ODBC jest biblioteką dołączaną dynamicznie (DLL), która znajduje się między menedżerem sterowników ODBC a sterownikiem. W terminologii ODBC sterownik zachowuje kursor, aby śledzić jego położenie w zestawie rekordów. Kursor oznacza pozycję w zestawie rekordów, do której został już przewinięty — bieżący rekord.

##  <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Biblioteka kursorów i sterowniki ODBC na poziomie 1

Biblioteka kursorów ODBC zapewnia na poziomie 1 Sterowniki następujące nowe możliwości:

- Przewijanie do przodu i do tyłu. Sterowniki poziomu 2 nie potrzebują biblioteki kursorów, ponieważ są już przewijane.

- Obsługa migawek. Biblioteka kursorów zarządza buforem zawierającym rekordy migawki. Ten bufor odzwierciedla usunięcia i modyfikacje programu dla rekordów, ale nie dodawania, usuwania lub edycji innych użytkowników. W związku z tym migawka jest obecna tylko jako bieżąca jako bufor biblioteki kursora. Bufor nie odzwierciedla także własnych dodatków do momentu wywołania `Requery`. Zestawy dynamiczne nie korzystają z biblioteki kursorów.

Biblioteka kursorów zawiera migawki (Kursory statyczne), nawet jeśli nie są zwykle obsługiwane przez sterownik. Jeśli sterownik obsługuje już statyczne kursory, nie trzeba ładować biblioteki kursorów w celu uzyskania obsługi migawek. W przypadku korzystania z biblioteki kursorów można używać tylko migawek i zestawów rekordów tylko do przodu. Jeśli sterownik obsługuje zestawy dynamiczne (KEYSET_DRIVEN kursory) i chcesz ich używać, nie należy używać biblioteki kursorów. Jeśli chcesz użyć migawek i zestawów dynamicznych, musisz oprzeć je na dwóch różnych obiektach `CDatabase` (dwa różne połączenia), chyba że sterownik obsługuje oba te elementy.

##  <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Aktualizacje pozycjonowane i kolumny sygnatur czasowych

> [!NOTE]
>  Źródła danych ODBC są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektów dostępu do danych MFC (DAO).

> [!NOTE]
>  Jeśli sterownik ODBC obsługuje `SQLSetPos`, których MFC używa, jeśli są dostępne, ten temat nie dotyczy użytkownika.

Większość sterowników poziomu 1 nie obsługuje aktualizacji pozycjonowanych. Takie sterowniki polegają na bibliotece kursorów do emulowania możliwości sterowników poziomu 2 w tym zakresie. Biblioteka kursorów emuluje obsługę aktualizacji pozycjonowanych przez przeszukaną aktualizację pól, w których nie można zmieniać.

W niektórych przypadkach zestaw rekordów może zawierać kolumnę sygnatury czasowej jako jedną z niezmienionych pól. Dwa problemy powstają w przypadku używania zestawów rekordów MFC z tabelami zawierającymi kolumny sygnatur czasowych.

Pierwszy problem dotyczy migawek aktualizowalnych w tabelach z kolumnami sygnatur czasowych. Jeśli tabela, do której jest związana migawka, zawiera kolumnę znaczników czasu, należy wywołać `Requery` po wywołaniu `Edit` i `Update`. W przeciwnym razie może nie być możliwe ponowne edytowanie tego samego rekordu. Po wywołaniu `Edit`, a następnie `Update`, rekord jest zapisywana w źródle danych, a kolumna sygnatura czasowa zostanie zaktualizowana. Jeśli nie wywołasz `Requery`, wartość sygnatury czasowej dla rekordu w migawce nie jest już zgodna z sygnaturą czasową w źródle danych. Podczas próby zaktualizowania rekordu źródło danych może nie zezwalać na aktualizację ze względu na niezgodność.

Drugi problem dotyczy ograniczeń klasy [CTime](../../atl-mfc-shared/reference/ctime-class.md) , gdy jest używany z funkcją `RFX_Date` do przenoszenia informacji o godzinie i dacie do lub z tabeli. Przetwarzanie `CTime` obiektu nakłada pewne obciążenie w formie dodatkowego przetwarzania pośredniego podczas transferu danych. Zakres dat `CTime` obiektów może być również zbyt ograniczony w przypadku niektórych aplikacji. Nowa wersja funkcji `RFX_Date` pobiera parametr ODBC *TIMESTAMP_STRUCT* zamiast obiektu `CTime`. Aby uzyskać więcej informacji, zobacz `RFX_Date` in [MACROS and Globals](../../mfc/reference/mfc-macros-and-globals.md) in *MFC Reference*.

##  <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Korzystanie z biblioteki kursorów

Po nawiązaniu połączenia ze źródłem danych — przez wywołanie [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) — można określić, czy ma być używana biblioteka kursorów dla źródła danych. Jeśli tworzysz migawki w tym źródle danych, określ opcję `CDatabase::useCursorLib` w parametrze `dwOptions`, aby `OpenEx` lub określić wartość TRUE dla parametru *bUseCursorLib* w celu `Open` (wartość domyślna to true). Jeśli sterownik ODBC obsługuje zestawy dynamiczne i chcesz otworzyć zestawy dynamiczne w źródle danych, nie używaj biblioteki kursorów (maskuje niektóre funkcje sterownika wymagane przez zestawy dynamiczne). W takim przypadku nie należy określać `CDatabase::useCursorLib` w `OpenEx` lub określić wartość FALSE dla parametru *bUseCursorLib* w `Open`.

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
