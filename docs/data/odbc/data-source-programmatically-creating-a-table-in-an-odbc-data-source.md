---
title: Programowe tworzenie tabeli w źródle danych ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213281"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Źródło danych: programowe tworzenie tabeli w źródle danych ODBC

W tym temacie wyjaśniono, jak utworzyć tabelę dla źródła danych za pomocą funkcji składowej `ExecuteSQL` klasy `CDatabase`, przekazując funkcję do ciągu, który zawiera **CREATE TABLE** instrukcję SQL.

Aby uzyskać ogólne informacje o źródłach danych ODBC w MFC, zobacz [Data Source (ODBC)](../../data/odbc/data-source-odbc.md). [Źródło danych tematu: programowe Konfigurowanie źródła danych ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) opisuje Tworzenie źródeł danych.

Po ustanowieniu źródła danych można łatwo tworzyć tabele przy użyciu funkcji składowej `ExecuteSQL` i **CREATE TABLE** instrukcji SQL. Na przykład jeśli masz obiekt `CDatabase` o nazwie `myDB`, możesz użyć następującego kodu MFC, aby utworzyć tabelę:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Ten przykład kodu tworzy tabelę o nazwie "BIURAs" w połączeniu ze źródłem danych programu Microsoft Access obsługiwanym przez `myDB`; tabela zawiera dwa pola "OfficeID" i "OfficeName".

> [!NOTE]
>  Typy pól określone w instrukcji SQL **CREATE TABLE** mogą się różnić w zależności od używanego sterownika ODBC. Program Microsoft Query (dystrybuowany z Visual C++ 1,5) jest jednym ze sposobów wykrywania, jakie typy pól są dostępne dla źródła danych. W programie Microsoft Query kliknij pozycję **plik**, kliknij pozycję **Table_Definition**, wybierz tabelę ze źródła danych i poszukaj typu wyświetlanego w polu kombi **Typ** . Istnieje również składnia SQL do tworzenia indeksów.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
