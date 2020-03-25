---
title: 'Zestaw rekordów: wykonywanie sprzężenia (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 7e8d42f2b96911cd57aca7c132b53ed7c10162be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212800"
---
# <a name="recordset-performing-a-join-odbc"></a>Zestaw rekordów: wykonywanie sprzężenia (ODBC)

Ten temat dotyczy klas MFC ODBC.

## <a name="what-a-join-is"></a>Co to jest połączenie

Operacja join, typowe zadanie dostępu do danych, umożliwia korzystanie z danych z więcej niż jednej tabeli przy użyciu jednego obiektu zestawu rekordów. Sprzęganie dwóch lub więcej tabel daje zestaw rekordów, który może zawierać kolumny z każdej tabeli, ale pojawia się jako pojedyncza tabela dla aplikacji. Czasami w sprzężeniu są wykorzystywane wszystkie kolumny ze wszystkich tabel, ale czasami klauzula **SELECT** języka SQL w sprzężeniu używa tylko niektórych kolumn z każdej tabeli. Klasy baz danych obsługują sprzężenia tylko do odczytu, ale nie są przyłączane do aktualizacji.

Aby wybrać rekordy zawierające kolumny z sprzężonych tabel, potrzebne są następujące elementy:

- Lista tabel zawierająca nazwy wszystkich połączonych tabel.

- Lista kolumn zawierająca nazwy wszystkich uczestniczących kolumn. Kolumny o tej samej nazwie, ale z różnych tabel, są kwalifikowane według nazwy tabeli.

- Filtr (klauzula **WHERE** SQL) określający kolumny, z którymi tabele są połączone. Ten filtr przyjmuje postać "Tabela1. KeyCol = tabela2. KeyCol" i faktycznie przyjmuje sprzężenie.

Można sprzęgać więcej niż dwie tabele w taki sam sposób, jak równe wiele par kolumn, każda para przyłączona przez słowo kluczowe SQL **i**.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
