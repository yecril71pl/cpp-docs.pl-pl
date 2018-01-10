---
title: "Zestaw rekordów: Wykonywanie sprzężenia (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4091cd8e60eed569782021c811f12af227e79673
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-performing-a-join-odbc"></a>Zestaw rekordów: wykonywanie sprzężenia (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
## <a name="what-a-join-is"></a>Co to jest sprzężenia  
 Operacji tworzenia sprzężenia, typowe zadania dostępu do danych, umożliwia pracę z danymi z więcej niż jednej tabeli za pomocą obiektu jednego zestawu rekordów. Sprzęganie dwóch lub więcej tabel daje zestaw rekordów, który może zawierać kolumn z każdej tabeli, ale pojawia się jako pojedynczej tabeli, aby aplikacja. Czasami sprzężenie używa wszystkich kolumn ze wszystkich tabel, ale czasami SQL **wybierz** używa klauzuli sprzężenia, tylko niektóre kolumny w każdej tabeli. Klasy baz danych obsługuje tylko do odczytu sprzężeń, ale nie można aktualizować sprzężenia.  
  
 Aby wybrać rekordy zawierające kolumn z połączonych tabel, potrzebne są następujące elementy:  
  
-   Lista tabelę zawierającą nazwy wszystkich tabel jest dołączony.  
  
-   Lista kolumn, zawierającą nazwy wszystkich kolumn uczestniczących. Kolumny o tej samej nazwie, ale z różnych tabel są kwalifikowana przez nazwę tabeli.  
  
-   Filtr (SQL **gdzie** klauzuli), który określa kolumn, na których są sprzężone tabele. Ten filtr ma postać "Table1.KeyCol = Table2.KeyCol" i faktycznie wykonuje sprzężenie.  
  
 Można dołączyć więcej niż dwie tabele w taki sam sposób przez equating pary wiele kolumn, każda para dołączane za pomocą słowa kluczowego SQL **i**.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [Zestaw rekordów: Deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)