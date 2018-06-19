---
title: Schemat (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f7ba3e7b64a8c65678830593098ef658b3495c75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104701"
---
# <a name="schema--mfc-data-access"></a>Schemat (dostęp do danych MFC)
Schemat bazy danych w tym artykule opisano bieżącej struktury tabel i widoków bazy danych w bazie danych. Ogólnie rzecz biorąc kod generowane przez kreatora przyjęto założenie, że nie spowoduje zmiany schematu tabeli lub tabel, dostęp do zestawu rekordów, ale klasy baz danych może rozwiązać niektóre zmiany schematu, takie jak dodawanie, zmienianie kolejności lub usuwanie niepowiązanych kolumn. W przypadku zmiany tabeli, należy ręcznie zaktualizować rekordów dla tabeli, a następnie ponownie skompilować aplikację.  
  
 Można również uzupełnić radzenia sobie z bazy danych, których schematu nie jest całkowicie znany w czasie kompilacji kodu generowane przez kreatora. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych programowania (MFC/ATL)](../data/data-access-programming-mfc-atl.md)   
 [SQL](../data/odbc/sql.md)   
 [Zestaw rekordów (ODBC)](../data/odbc/recordset-odbc.md)