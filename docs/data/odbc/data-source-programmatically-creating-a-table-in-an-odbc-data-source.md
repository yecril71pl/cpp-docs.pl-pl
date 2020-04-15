---
title: Programowo Tworzenie tabeli w źródle danych ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358837"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Źródło danych: programowe tworzenie tabeli w źródle danych ODBC

W tym temacie wyjaśniono, jak utworzyć tabelę dla źródła danych, przy użyciu funkcji `ExecuteSQL` elementu członkowskiego klasy `CDatabase`, przekazując funkcję ciąg, który zawiera **instrukcję SQL CREATE TABLE.**

Aby uzyskać ogólne informacje o źródłach danych ODBC w MFC, zobacz [Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md). Temat [Źródło danych: Programowo Konfigurowanie źródła danych ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) opisuje tworzenie źródeł danych.

Po ustanowieniu źródła danych można łatwo utworzyć tabele przy użyciu funkcji `ExecuteSQL` elementu członkowskiego i instrukcji CREATE **TABLE** SQL. Na przykład, jeśli `CDatabase` miałeś `myDB`obiekt o nazwie , można użyć następującego kodu MFC, aby utworzyć tabelę:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

W tym przykładzie kodu tworzy tabelę o nazwie "BIURA" w połączeniu źródła danych programu Microsoft Access obsługiwane przez `myDB`; tabela zawiera dwa pola "OfficeID" i "OfficeName".

> [!NOTE]
> Typy pól określone w instrukcji **SQL CREATE TABLE** mogą się różnić w zależności od używanego sterownika ODBC. Program Microsoft Query (dystrybuowany z programem Visual C++ 1.5) jest jednym ze sposobów odnajdywanie, jakie typy pól są dostępne dla źródła danych. W programie Microsoft Query kliknij pozycję **Plik**, kliknij **pozycję Table_Definition**, wybierz tabelę ze źródła danych i spójrz na typ wyświetlany w polu kombi **Typ.** Istnieje również składnia SQL do tworzenia indeksów.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
