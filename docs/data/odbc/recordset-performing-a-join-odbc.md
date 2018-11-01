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
ms.openlocfilehash: 135992e7eebd56c985c24228370695f10ac6da3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523941"
---
# <a name="recordset-performing-a-join-odbc"></a>Zestaw rekordów: wykonywanie sprzężenia (ODBC)

Ten temat dotyczy klas MFC ODBC.

## <a name="what-a-join-is"></a>Co to jest elementem sprzężenia

Operacja join typowe zadania dostępu do danych umożliwia pracę przy użyciu danych z więcej niż jednej tabeli za pomocą obiektu jednym zestawie rekordów. Sprzęganie dwóch lub więcej tabel daje zestaw rekordów, który może zawierać kolumn z każdej tabeli, ale pojawia się jako pojedynczej tabeli z aplikacją. Czasami w sprzężeniu użyto wszystkie kolumny ze wszystkich tabel, ale czasami SQL **wybierz** używa klauzuli sprzężenia, tylko niektóre kolumny z każdej tabeli. Klasy baz danych obsługuje tylko do odczytu sprzężeń, ale nie można aktualizować sprzężenia.

Aby wybrać rekordy zawierające kolumny z połączonych tabel, potrzebne są następujące elementy:

- Lista tabelę zawierającą nazwy wszystkich tabel jest dołączony.

- Lista kolumn, zawierającą nazwy wszystkich kolumn uczestniczących w programie. Kolumny o takiej samej nazwie, ale z różnymi tabelami są kwalifikowane przez nazwę tabeli.

- Filtr (SQL **gdzie** klauzuli), który określa kolumny, na których są sprzężone tabele. Ten filtr ma postać "Table1.KeyCol = Table2.KeyCol" i faktycznie wykonuje sprzężenie.

Możesz dołączyć więcej niż dwie tabele w taki sam sposób, przez equating pary wiele kolumn, każda para dołączane za pomocą słowa kluczowego SQL **i**.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)