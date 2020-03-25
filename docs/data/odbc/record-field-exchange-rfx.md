---
title: Wymiana pól rekordów (RFX)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
ms.openlocfilehash: e1ba9f29ebf2cb3b1f94620e815882c850bbc7cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213060"
---
# <a name="record-field-exchange-rfx"></a>Wymiana pól rekordów (RFX)

Klasy baz danych MFC ODBC automatyzują przeniesienie danych między źródłem danych a obiektem [zestawu rekordów](../../data/odbc/recordset-odbc.md) . Podczas wyprowadzania klasy z [CRecordset](../../mfc/reference/crecordset-class.md) i nie używaj pobierania wierszy zbiorczych dane są przesyłane przez mechanizm wymiany pól rekordów (RFX).

> [!NOTE]
>  Jeśli zaimplementowano pobieranie wierszy zbiorczych w klasie pochodnej `CRecordset`, struktura używa mechanizmu wymiany zbiorczych pól rekordów (bulk RFX) do transferowania danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX przypomina wymianę danych okna dialogowego (DDX). Przeniesienie danych między źródłem danych a elementami członkowskimi danych pola zestawu rekordów wymaga wielu wywołań funkcji [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) zestawu rekordów i znacznej interakcji między platformą i [ODBC](../../data/odbc/odbc-basics.md). Mechanizm RFX jest bezpieczny dla typów i zapisuje zadania wywoływania funkcji ODBC, takich jak `::SQLBindCol`. Aby uzyskać więcej informacji na temat DDX, zobacz temat [wymiana i walidacja danych w oknie dialogowym](../../mfc/dialog-data-exchange-and-validation.md).

RFX jest w większości przezroczyste dla Ciebie. W przypadku deklarowania klas zestawu rekordów przy użyciu Kreatora aplikacji MFC lub **dodawania klasy** (zgodnie z opisem w temacie [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) RFX jest automatycznie wbudowany. Klasa zestawu rekordów musi pochodzić od klasy bazowej `CRecordset` dostarczonej przez platformę. Kreator aplikacji MFC umożliwia utworzenie początkowej klasy zestawu rekordów. Opcja **Dodaj klasę** umożliwia dodanie innych klas zestawu rekordów w miarę potrzeb. Aby uzyskać więcej informacji i przykładów, zobacz [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Należy ręcznie dodać niewielką ilość kodu RFX w trzech przypadkach, gdy chcesz:

- Użyj zapytań sparametryzowanych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Wykonaj sprzężenia (przy użyciu jednego zestawu rekordów dla kolumn z dwóch lub więcej tabel). Aby uzyskać więcej informacji, zobacz [zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Dynamiczne wiązanie kolumn danych. Jest to mniej typowe niż parametryzacja. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Jeśli potrzebujesz bardziej zaawansowanej wiedzy na temat RFX, zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

W poniższych tematach opisano szczegóły dotyczące korzystania z obiektów zestawu rekordów:

- [Wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Wymiana pól rekordów: używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Korzystanie z MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
