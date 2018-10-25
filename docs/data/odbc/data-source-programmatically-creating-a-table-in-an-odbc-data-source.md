---
title: Programowe tworzenie tabeli w źródle danych ODBC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9917e6885e1c15950032bfd5ca983cc932c44a3c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064839"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Źródło danych: programowe tworzenie tabeli w źródle danych ODBC

W tym temacie wyjaśniono, jak utworzyć tabelę danych źródła, za pomocą `ExecuteSQL` funkcji składowej klasy typu `CDatabase`, przekazując ciąg, który zawiera funkcję **CREATE TABLE** instrukcji SQL.

Aby uzyskać ogólne informacje na temat źródeł danych ODBC w MFC, zobacz [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md). Temat [źródła danych: programowe Konfigurowanie źródła danych ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) opisano tworzenie źródła danych.

W przypadku źródła danych ustanowione możesz łatwo tworzyć tabele za pomocą `ExecuteSQL` funkcja elementu członkowskiego i **CREATE TABLE** instrukcji SQL. Na przykład, jeśli masz `CDatabase` obiektu o nazwie `myDB`, można użyć następujących kodu MFC do tworzenia tabeli:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

Ten przykład kodu tworzy tabelę o nazwie "Oddziałów" w Microsoft Access połączenia ze źródłem danych obsługiwane przez `myDB`; tabela zawiera dwa pola "OfficeID" i "OfficeName."

> [!NOTE]
>  Typy pól określonych w **CREATE TABLE** instrukcji SQL może się różnić w zależności sterownika ODBC, którego używasz. Program Microsoft Query (rozpowszechniać za pomocą programu Visual C++ 1.5) jest jednym ze sposobów, aby dowiedzieć się, jakie typy pól są dostępne dla źródła danych. W programie Microsoft Query, kliknij przycisk **pliku**, kliknij przycisk **Table_Definition**, wybierz tabelę ze źródła danych i spójrz na typ objętego **typu** pola kombi. Aby utworzyć indeksy istnieje również składni języka SQL.

## <a name="see-also"></a>Zobacz też

[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)