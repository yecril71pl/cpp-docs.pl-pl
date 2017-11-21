---
title: "ODBC: Biblioteka kursorów ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a704a4904683d2b1a448e9f5f327723b7681c96b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC: biblioteka kursorów ODBC
W tym temacie opisano z biblioteki kursorów ODBC oraz wyjaśniono, jak z niego korzystać. Aby uzyskać więcej informacji, zobacz:  
  
-   [Sterowniki ODBC — Biblioteka kursorów i poziomu 1](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [Aktualizacje pozycjonowane i kolumn znaczników czasu](#_core_positioned_updates_and_timestamp_columns)  
  
-   [Korzystanie z biblioteki kursorów](#_core_using_the_cursor_library)  
  
 Biblioteka kursorów ODBC jest biblioteki dołączanej (dynamicznie DLL), znajdujący się między Menedżera sterowników ODBC i sterownikami. W kategoriach ODBC sterownik przechowuje kursora prowadzącego do śledzenia jej położenie w zestawie rekordów. Kursor oznacza pozycję w zestawie, do którego ma już przewijane — bieżącego rekordu.  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Sterowniki ODBC — Biblioteka kursorów i poziomu 1  
 Biblioteka kursorów ODBC zapewnia sterowniki poziomu 1 następujące nowe funkcje:  
  
-   Przewijanie do przodu i do tyłu. Poziom 2 sterowniki nie ma potrzeby z biblioteki kursorów, ponieważ są one już przewijanego.  
  
-   Obsługa migawki. Biblioteka kursorów zarządza buforu zawierającego rekordy tworzenia migawki. Bufor odzwierciedla usunięcia programu i edycji rekordów, ale nie dodawania, usuwania ani zmiany innych użytkowników. W związku z tym migawki jest tylko jako bieżący jako Biblioteka kursorów buforu. Bufor również nie odzwierciedla własne dodatki do czasu wywołania **Requery**. Zestawy dynamiczne nie należy używać z biblioteki kursorów.  
  
 Biblioteka kursorów daje migawek (są statyczne kursory), nawet jeśli nie są zwykle obsługiwane przez sterownik. Jeśli sterownik obsługuje już są statyczne kursory, zbędna, nie można załadować z biblioteki kursorów, aby uzyskać pomoc techniczną migawki. Jeśli korzystasz z biblioteki kursorów, można użyć tylko migawki i zestawy rekordów tylko do przodu. Jeśli sterownik sieci obsługuje zestawów dynamicznych (KEYSET_DRIVEN kursory) i chcesz używać ich, nie może używać z biblioteki kursorów. Jeśli chcesz używać migawek i zestawów dynamicznych, należy utworzyć je na dwóch różnych `CDatabase` obiekty (w dwóch różnych połączeń), jeśli sterownik nie obsługuje jednocześnie.  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a>Aktualizacje pozycjonowane i kolumn znaczników czasu  
  
> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas MFC obiekt DAO (Data Access).  
  
> [!NOTE]
>  Jeśli sterownik ODBC obsługuje **SQLSetPos**, które MFC używa, ten temat nie dotyczy.  
  
 Większość sterowników poziomu 1 nie obsługują aktualizacje pozycjonowane. Takie sterowniki polegają na Biblioteka kursorów emulować możliwości sterowniki poziomu 2, w tym zakresie. Biblioteka kursorów emuluje Obsługa aktualizacji pozycjonowane wykonując przeszukane aktualizacji niezmiennych pól.  
  
 W niektórych przypadkach zestaw rekordów mogą zawierać kolumny znaczników czasu jako jeden z tych pól niezmiennych. Dwa problemach przy użyciu zestawów rekordów MFC z tabel zawierających kolumny znaczników czasu.  
  
 Pierwszą kwestią dotyczącą dotyczy można aktualizować migawek w tabelach mających kolumny znaczników czasu. Jeśli tabeli, z którym powiązany jest migawki zawiera kolumnę znaczników czasu, należy wywołać **Requery** po wywołaniu metody **Edytuj** i **aktualizacji**. Jeśli nie, nie można go edytować tego samego ponownie. Podczas wywoływania **Edytuj** , a następnie **aktualizacji**, zapisywania rekordu w źródle danych i zaktualizowaniu kolumny znaczników czasu. Jeśli nie zostanie wywołana **Requery**, wartość sygnatury czasowej rekordu w migawki nie zgadza się odpowiednie sygnatury czasowej w źródle danych. Podczas próby zaktualizowania rekordu ponownie źródła danych może nie zezwalaj na aktualizację z powodu niezgodności.  
  
 Drugi problem dotyczy ograniczenia klasy [ctime —](../../atl-mfc-shared/reference/ctime-class.md) w przypadku użycia z `RFX_Date` funkcji do przekazywania informacji datę i godzinę do lub z tabeli. Przetwarzanie `CTime` obiektu powoduje pewne nadmiarowe obciążenie w formie przetwarzania bardzo pośrednie podczas transferu danych. Zakres dat `CTime` obiektów może być również zbyt ograniczanie dla niektórych aplikacji. Nowa wersja `RFX_Date` funkcja przyjmuje ODBC **TIMESTAMP_STRUCT** parametru zamiast `CTime` obiektu. Aby uzyskać więcej informacji, zobacz `RFX_Date` w [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołania MFC*.  

  
##  <a name="_core_using_the_cursor_library"></a>Korzystanie z biblioteki kursorów  
 Podczas połączenia ze źródłem danych, wywołując [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) lub [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) — można określić, czy do korzystania z biblioteki kursorów dla źródła danych. Jeśli zostanie tworzenie migawek dla tego źródła danych, określ **CDatabase::useCursorLib** opcji w `dwOptions` parametr `OpenEx` lub określ **TRUE** dla  **bUseCursorLib** parametr **Otwórz** (wartość domyślna to **TRUE**). Jeśli sterownik ODBC obsługuje zestawów dynamicznych i chcesz otworzyć zestawów dynamicznych w źródle danych, nie należy używać z biblioteki kursorów (maski jego funkcjonalność sterownika potrzebne dla zestawów dynamicznych). W takim przypadku nie należy określać **CDatabase::useCursorLib** w `OpenEx` lub określ **FALSE** dla **bUseCursorLib** parametru w **Otwórz**.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)