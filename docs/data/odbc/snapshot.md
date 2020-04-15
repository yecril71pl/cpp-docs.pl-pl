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
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366905"
---
# <a name="snapshot"></a>Snapshot

Migawka jest zestawem rekordów, który odzwierciedla statyczny widok danych, jak istniał w momencie utworzenia migawki. Po otwarciu migawki i przejściu do wszystkich rekordów, zestaw rekordów, które zawiera, a ich wartości nie zmieniają się, dopóki nie odbudujesz migawki przez wywołanie `Requery`.

> [!NOTE]
> Ten temat dotyczy klas MFC ODBC. Jeśli używasz klas DAO MFC zamiast klas ODBC MFC, zobacz [CDaoRecordset::Otwórz](../../mfc/reference/cdaorecordset-class.md#open) opis zestawów rekordów typu migawki.

Można utworzyć migawki można aktualizować lub tylko do odczytu z klas bazy danych. W przeciwieństwie do dynaset, migawka można aktualizować nie odzwierciedla zmian wartości rekordów wprowadzonych przez innych użytkowników, ale odzwierciedla aktualizacje i usunięcia dokonane przez program. Rekordy dodane do migawki nie stają się `Requery`widoczne dla migawki, dopóki nie zostanie wywołana .

> [!TIP]
> Migawka jest kursorem statycznym ODBC. Kursory statyczne w rzeczywistości nie otrzymują wiersza danych, dopóki nie przewiniesz do tego rekordu. Aby upewnić się, że wszystkie rekordy są natychmiast pobierane, można przewinąć do końca pliku recordset, a następnie przewinąć do pierwszego rekordu, który chcesz wyświetlić. Należy jednak pamiętać, że przewijanie do końca pociąga za sobą dodatkowe obciążenie i może obniżyć wydajność.

Migawki są najcenniejsze, gdy dane są stałe podczas operacji, jak podczas generowania raportu lub wykonywania obliczeń. Mimo to źródło danych może znacznie odbiegać od migawki, więc można od czasu do czasu odbudować go.

Obsługa migawek jest oparta na bibliotece kursora ODBC, która zapewnia statyczne kursory i aktualizacje pozycjonowane (potrzebne do aktualizacji) dla dowolnego sterownika poziomu 1. Biblioteka DLL biblioteki kursorów musi zostać załadowana do pamięci dla tej obsługi. Podczas `CDatabase` konstruowania obiektu `OpenEx` i wywołania jego `CDatabase::useCursorLib` funkcji elementu członkowskiego, należy określić opcję *dwOptions* parametru. Jeśli wywołasz `Open` funkcję elementu członkowskiego, biblioteka kursorów jest ładowana domyślnie. Jeśli używasz dynasets zamiast migawek, nie chcesz powodować biblioteki kursor do załadowania.

Migawki są dostępne tylko wtedy, gdy biblioteka `CDatabase` kursora ODBC została załadowana podczas konstruowania obiektu lub używany sterownik ODBC obsługuje kursory statyczne.

> [!NOTE]
> W przypadku niektórych sterowników ODBC migawki (kursory statyczne) mogą nie być aktualizowane. Sprawdź w dokumentacji sterownika obsługiwane typy kursorów i typy współbieżności, które obsługują. Aby zagwarantować można aktualizować migawki, podczas tworzenia `CDatabase` obiektu należy załadować bibliotekę kursora do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Jeśli chcesz używać zarówno migawek, jak i zestawów dynamicznych, należy je oprzeć na dwóch różnych `CDatabase` obiektach (dwóch różnych połączeniach).

Aby uzyskać więcej informacji na temat właściwości migawek współużytkuje wszystkie zestawy rekordów, zobacz [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać więcej informacji na temat odbc i migawek, w tym Biblioteki kursora ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
