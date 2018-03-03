---
title: Migawki | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c31e08fdda3cef526f46946e45ef956f9ad1adaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="snapshot"></a>Migawka
Migawka jest zestaw rekordów, które odzwierciedla widok statyczny danych, który istniał w momencie utworzenia migawki. Po otwarciu migawki i Przenieś do wszystkich rekordów, zestaw rekordów zawiera i ich wartości nie należy zmieniać dopóki odbudować migawki przez wywołanie metody **Requery**.  
  
> [!NOTE]
>  Ten temat dotyczy klasach MFC ODBC. Jeśli korzystasz z klas MFC DAO zamiast klasy MFC ODBC, zobacz [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) opis zestawów rekordów typu migawka.  
  
 Można utworzyć migawki można aktualizować lub w trybie tylko do odczytu z klasami baz danych. W odróżnieniu od dynamiczny można aktualizować migawka nie oddaje zmiany do rejestrowania wartości wprowadzone przez innych użytkowników, ale odzwierciedla, aktualizacje i usunięcia wykonywane przez program. Rekordów dodawanych do migawki nie staną się widoczne dla migawki do czasu wywołania **Requery**.  
  
> [!TIP]
>  Migawka jest statyczny kursorów ODBC. Kursory statyczne nie uzyskać wiersz danych do czasu przewiń do tego rekordu. Aby upewnić się, że natychmiast pobierane są wszystkie rekordy, można przewiń do końca zestawu rekordów, a następnie przewiń do pierwszej rekord, który chcesz wyświetlić. Należy jednak pamiętać, że przewijania na końcu pociąga za sobą dodatkowe koszty i można obniżyć wydajność.  
  
 Migawki są najbardziej przydatna, gdy potrzebne są dane pozostają z ustaloną podczas działania, jak podczas generowania raportu lub wykonywanie obliczeń. Mimo tego źródła danych można różni się znacznie z migawki, należy go odbudować od czasu do czasu.  
  
 Obsługa migawki jest oparta na z biblioteki kursorów ODBC, który zapewnia są statyczne kursory oraz umieszczony (wymagane dla czy można je aktualizować) aktualizacje dla dowolnego sterownika poziomu 1. Biblioteka kursorów DLL musi zostać załadowany w pamięci dla tej obsługi. Podczas konstruowania `CDatabase` obiekt i wywołanie jego `OpenEx` funkcji członkowskiej, należy określić **CDatabase::useCursorLib** opcji `dwOptions` parametru. Jeśli należy wywołać **Otwórz** funkcji członkowskiej, z biblioteki kursorów jest domyślnie ładowany. Jeśli korzystasz z zestawów dynamicznych zamiast migawki, nie chcesz spowodować załadowanie biblioteki kursora.  
  
 Migawki są dostępne tylko wtedy, gdy Biblioteka kursorów ODBC został załadowany, kiedy `CDatabase` obiekt został skonstruowany lub sterownika ODBC, czy używasz obsługuje są statyczne kursory.  
  
> [!NOTE]
>  W przypadku niektórych sterowników ODBC migawek (są statyczne kursory) może nie być można aktualizować. Sprawdź dokumentację sterownik dla obsługiwanych typów kursor i typy współbieżności, które obsługują. Aby zagwarantować migawek można aktualizować, upewnij się, Biblioteka kursorów zostały załadowane do pamięci podczas tworzenia `CDatabase` obiektu. Aby uzyskać więcej informacji, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Jeśli chcesz używać migawek i zestawów dynamicznych, należy utworzyć je na dwóch różnych `CDatabase` obiekty (w dwóch różnych połączeń).  
  
 Aby uzyskać więcej informacji o udziale migawki właściwości z wszystkich zestawów rekordów, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać więcej informacji na temat ODBC i migawki, łącznie z biblioteki kursorów ODBC zobacz [ODBC](../../data/odbc/odbc-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)