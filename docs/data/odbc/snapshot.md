---
title: Migawki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23d4d3fcfac5e5d714d658dfe4161c77377b9361
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064917"
---
# <a name="snapshot"></a>Migawka

Migawka to zestaw rekordów, które odzwierciedla widok statyczny danych, która istniała w momencie utworzenia migawki. Po otwarciu migawki i Przenieś do wszystkich rekordów, zawiera zestaw rekordów i ich wartości nie należy zmieniać dopóki odbudować migawki przez wywołanie metody `Requery`.

> [!NOTE]
>  Ten temat dotyczy klas MFC ODBC. Jeśli używasz klas MFC DAO zamiast klas MFC ODBC, zobacz [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) opis zestawów rekordów typu migawka.

Można utworzyć migawki można aktualizować lub tylko do odczytu z klasami bazy danych. W przeciwieństwie do dynamicznego można aktualizować migawka nie oddaje zmiany do rejestrowania wartości wprowadzone przez innych użytkowników, ale będzie odzwierciedlał, aktualizacji i usunięć wprowadzone przez program. Liczba rekordów dodanych do migawki nie stanie się widoczna do migawki, dopóki nie zostanie wywołana `Requery`.

> [!TIP]
>  Migawka jest kursor statyczny ODBC. Kursory statyczne nie uzyskać wiersz danych do momentu przewiń do tego rekordu. Aby upewnić się, że od razu pobierane są wszystkie rekordy, można przewiń do końca rekordów, a następnie przewiń do pierwszego rekordu, który chcesz wyświetlić. Należy jednak pamiętać, że przewijając do końca pociąga za sobą dodatkowe koszty i może obniżyć wydajność.

Migawki są najbardziej przydatne, gdy będą potrzebne dane pozostają z ustaloną podczas operacji, podczas generowania raportu lub wykonywania obliczeń. Mimo tego źródła danych można rozdzielić znacznie z migawek, dzięki czemu możesz chcieć od czasu do czasu ponownie skompilować.

Obsługa migawki opiera się na z biblioteki kursorów ODBC, która udostępnia Kursory statyczne i umieszczony aktualizacji (wymagane dla updateability) dla dowolnego sterownika poziomu 1. Biblioteka kursorów biblioteki DLL muszą zostać załadowane w pamięci dla tej obsługi. Podczas konstruowania `CDatabase` obiektu, a następnie wywołać jej `OpenEx` funkcji członkowskiej, należy określić `CDatabase::useCursorLib` opcji *dwOptions* parametru. Jeśli wywołasz `Open` funkcja elementu członkowskiego, z biblioteki kursorów jest ładowany przez domyślny. Jeśli używasz zestawów dynamicznych zamiast migawki, nie chcesz spowodować załadowanie biblioteki kursora.

Migawki są dostępne tylko wtedy, gdy załadowano z biblioteki kursorów ODBC, kiedy `CDatabase` został skonstruowany obiekt lub sterownik ODBC, którego używasz obsługuje Kursory statyczne.

> [!NOTE]
>  W przypadku niektórych sterowników ODBC migawek (Kursory statyczne) może nie być można aktualizować. Sprawdź dokumentację sterownik dla obsługiwanych typów kursora i typy współbieżności, które obsługują. Aby zagwarantować migawek można aktualizować, upewnij się, załadować z biblioteki kursorów do pamięci podczas tworzenia `CDatabase` obiektu. Aby uzyskać więcej informacji, zobacz [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Jeśli chcesz użyć migawek i zestawy dynamiczne, należy utworzyć je na dwóch różnych `CDatabase` obiektów (w dwóch różnych połączeń).

Aby uzyskać więcej informacji na temat udostępniania migawek właściwości z wszystkich zestawów rekordów, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać więcej informacji na temat ODBC i migawki, łącznie z biblioteki kursorów ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)