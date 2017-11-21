---
title: "Programowe tworzenie tabeli w źródle danych ODBC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8009d587007e618bfecf46911c5b30486cf1aba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>Źródło danych: programowe tworzenie tabeli w źródle danych ODBC
W tym temacie wyjaśniono, jak utworzyć tabelę danych źródle, przy użyciu `ExecuteSQL` funkcji członkowskiej klasy `CDatabase`, przekazywanie funkcji ciąg, który zawiera **CREATE TABLE** instrukcji SQL.  
  
 Aby uzyskać ogólne informacje o w MFC ODBC — źródła danych, zobacz [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md). Temat [źródła danych: programowe Konfigurowanie źródła danych ODBC](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) opisano tworzenie źródła danych.  
  
 Jeśli masz nawiązane źródła danych, można łatwo utworzyć tabele przy użyciu `ExecuteSQL` funkcji członkowskiej i **CREATE TABLE** instrukcji SQL. Na przykład, jeśli masz `CDatabase` obiektu o nazwie `myDB`, można użyć poniższego kodu MFC, aby utworzyć tabelę:  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 Ten przykład kodu tworzy tabeli o nazwie "Oddziałów" dla połączenia źródła danych programu Microsoft Access obsługiwanego przez `myDB`; tabela zawiera dwa pola "OfficeID" i "OfficeName."  
  
> [!NOTE]
>  Typy pól określone w **CREATE TABLE** instrukcji SQL może być różny w zależności od sterownika ODBC, którego używasz. Program Microsoft Query (rozpowszechnianej za pomocą programu Visual C++ 1.5) jest jednym ze sposobów odnajdywanie, jakie typy pól są dostępne dla źródła danych. W programie Microsoft Query, kliknij przycisk **pliku**, kliknij przycisk **Table_Definition**, wybierz tabelę ze źródła danych i przyjrzyj się typ pokazano **typu** pola kombi. Istnieje również składni SQL do tworzenia indeksów.  
  
## <a name="see-also"></a>Zobacz też  
 [Źródła danych (ODBC)](../../data/odbc/data-source-odbc.md)