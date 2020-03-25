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
ms.openlocfilehash: 0eac4f47c3d00c34c1aadaef18202a95f831ad82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209096"
---
# <a name="schema--mfc-data-access"></a>Schemat (dostęp do danych MFC)

Schemat bazy danych opisuje bieżącą strukturę tabel i widoków bazy danych w bazie danych programu. W ogólnym kodzie generowanym przez kreatora założono, że schemat tabeli lub tabel, do których uzyskuje dostęp zestaw rekordów, nie ulegnie zmianie, ale klasy bazy danych mogą dotyczyć niektórych zmian schematu, takich jak dodawanie, zmiana kolejności lub usuwanie kolumn niepowiązanych. W przypadku zmiany tabeli należy ręcznie zaktualizować zestaw rekordów dla tabeli, a następnie ponownie skompilować aplikację.

Możesz również uzupełnić kod wygenerowany przez kreatora, aby zająć się bazą danych, której schemat nie jest całkowicie znany w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

## <a name="see-also"></a>Zobacz też

[Programowanie dostępu do danych (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[SQL](../data/odbc/sql.md)<br/>
[Zestaw rekordów (ODBC)](../data/odbc/recordset-odbc.md)
