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
ms.openlocfilehash: 597b3870dbfc70b6e1ac392a45491ee0f1804c2f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055428"
---
# <a name="schema--mfc-data-access"></a>Schemat (dostęp do danych MFC)

Schemat bazy danych w tym artykule opisano bieżącej struktury tabele i widoki bazy danych w bazie danych. Ogólnie rzecz biorąc kodu generowane przez kreatora przyjęto założenie, że schematu dla tabeli lub tabel, które uzyskują dostęp do zestawu rekordów nie ulegnie zmianie, ale klas baz danych poradzenie sobie z niektórych zmiany schematu, takie jak dodawanie, zmienianie kolejności lub usuwanie niepowiązanych kolumn. Jeśli zmieni się tabeli, należy ręcznie zaktualizować zestaw rekordów w tabeli, a następnie ponownie skompilować aplikację.

Można także uzupełnić kod generowane przez kreatora, aby poradzić sobie z bazą danych, którego schemat jest całkowicie nieznany w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Zobacz też

[Programowanie (MFC/ATL) dostępu do danych](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Zestaw rekordów (ODBC)](../data/odbc/recordset-odbc.md)