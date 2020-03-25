---
title: Snapshot
ms.date: 11/04/2016
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
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212696"
---
# <a name="snapshot"></a>Snapshot

Migawka jest zestawem rekordów, który odzwierciedla statyczny widok danych, który istniał w momencie utworzenia migawki. Gdy otworzysz migawkę i przejdziesz do wszystkich rekordów, zestaw rekordów, które zawiera, i ich wartości nie zmieniają się, dopóki migawka nie zostanie odbudowana przez wywołanie `Requery`.

> [!NOTE]
>  Ten temat dotyczy klas MFC ODBC. Jeśli używasz klas MFC DAO zamiast klas MFC ODBC, zobacz [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) , aby uzyskać opis zestawów rekordów typu Snapshot.

Możliwe jest tworzenie migawek do aktualizacji lub tylko do odczytu z klasami baz danych. W przeciwieństwie do zestawu dynamicznego, aktualizowalna migawka nie odzwierciedla zmian wartości rekordów wprowadzonych przez innych użytkowników, ale odzwierciedla aktualizacje i usunięcia dokonane przez program. Rekordy dodane do migawki nie stają się widoczne dla migawki do momentu wywołania `Requery`.

> [!TIP]
>  Migawka jest statycznym kursorem ODBC. Kursory statyczne nie pobierają wiersza danych do momentu przewinięcia tego rekordu. Aby upewnić się, że wszystkie rekordy są pobierane natychmiast, można przewijać do końca zestawu rekordów, a następnie przewijać do pierwszego rekordu, który ma zostać wyświetlony. Należy jednak zauważyć, że przewijanie do końca wiąże się z dodatkowym obciążeniem i może obniżyć wydajność.

Migawki są najbardziej cenne, gdy potrzebne dane mają być stałe w trakcie operacji, tak jak podczas generowania raportu lub wykonywania obliczeń. Nawet dlatego źródło danych może znacząco rozróżnić się od migawki, dzięki czemu możesz chcieć ponownie skompilować ją od czasu do czasu.

Obsługa migawek jest oparta na bibliotece kursora ODBC, która zapewnia statyczne kursory i Aktualizacje pozycjonowane (potrzebne do aktualizacji) dla dowolnego sterownika poziomu 1. Biblioteka DLL biblioteki kursorów musi zostać załadowana do pamięci dla tej obsługi. Podczas konstruowania obiektu `CDatabase` i wywołania funkcji składowej `OpenEx` należy określić opcję `CDatabase::useCursorLib` parametru *dwOptions* . Jeśli wywołasz funkcję elementu członkowskiego `Open`, Biblioteka kursorów zostanie domyślnie załadowana. Jeśli używasz zestawów dynamicznych zamiast migawek, nie chcesz, aby Biblioteka kursorów została załadowana.

Migawki są dostępne tylko wtedy, gdy biblioteka kursorów ODBC została załadowana podczas konstruowania obiektu `CDatabase` lub używany sterownik ODBC obsługuje Kursory statyczne.

> [!NOTE]
>  W przypadku niektórych sterowników ODBC migawki (Kursory statyczne) mogą nie być aktualizowalne. Zapoznaj się z dokumentacją sterownika pod kątem obsługiwanych typów kursorów i typów współbieżności, które obsługują. W celu zagwarantowania migawek aktualizowalnych upewnij się, że podczas tworzenia obiektu `CDatabase` załadujesz bibliotekę kursorów do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Jeśli chcesz użyć migawek i zestawów dynamicznych, musisz oprzeć je na dwóch różnych obiektach `CDatabase` (dwa różne połączenia).

Aby uzyskać więcej informacji na temat migawek właściwości udostępnianych z wszystkimi zestawami rekordów, zobacz [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać więcej informacji na temat ODBC i migawek, w tym biblioteki kursora ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
