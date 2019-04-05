---
title: Schemat (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], database
- databases [C++], schema
- database schema [C++], about database schemas
- database schema [C++]
- schemas [C++], database
- structures [C++]
ms.assetid: 7d17e35f-1ccf-4853-b915-5b8c7a45b9ee
ms.openlocfilehash: cc333ee987ed0c6cba6cb11730d8f940e49d525d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039036"
---
# <a name="schema--mfc-data-access"></a>Schemat (dostęp do danych MFC)

Schemat bazy danych w tym artykule opisano bieżącej struktury tabele i widoki bazy danych w bazie danych. Ogólnie rzecz biorąc kodu generowane przez kreatora przyjęto założenie, że schematu dla tabeli lub tabel, które uzyskują dostęp do zestawu rekordów nie ulegnie zmianie, ale klas baz danych poradzenie sobie z niektórych zmiany schematu, takie jak dodawanie, zmienianie kolejności lub usuwanie niepowiązanych kolumn. Jeśli zmieni się tabeli, należy ręcznie zaktualizować zestaw rekordów w tabeli, a następnie ponownie skompilować aplikację.

Można także uzupełnić kod generowane przez kreatora, aby poradzić sobie z bazą danych, którego schemat jest całkowicie nieznany w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Dynamically Binding Data Columns (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Zobacz także

[Programowanie (MFC/ATL) dostępu do danych](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Zestaw rekordów (ODBC)](../data/odbc/recordset-odbc.md)