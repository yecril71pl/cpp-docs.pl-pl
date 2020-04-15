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
ms.openlocfilehash: 6f965b90e1e0bbcfd3ad04bb5b40644d61050b2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367162"
---
# <a name="record-field-exchange-rfx"></a>Wymiana pól rekordów (RFX)

Klasy bazy danych MFC ODBC automatyzują przenoszenie danych między źródłem danych a obiektem [zestawem rekordów.](../../data/odbc/recordset-odbc.md) Po wyprowadzeniu klasy z [CRecordset](../../mfc/reference/crecordset-class.md) i nie używać pobierania wiersza zbiorczego, dane są przesyłane przez mechanizm wymiany pól rekordów (RFX).

> [!NOTE]
> Jeśli zaimplementowano pobieranie wiersza `CRecordset` zbiorczego w klasie pochodnej, struktura używa mechanizmu zbiorczej wymiany pól rekordów (Bulk RFX) do przesyłania danych. Aby uzyskać więcej informacji, zobacz [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

RFX jest podobny do wymiany danych dialogowych (DDX). Przenoszenie danych między źródłem danych a członkami danych pola zestawu rekordów wymaga wielu wywołań funkcji [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) w zbiorze rekordów oraz znacznej interakcji między platformą a [odbc.](../../data/odbc/odbc-basics.md) Mechanizm RFX jest bezpieczny dla typu i pozwala zaoszczędzić pracę `::SQLBindCol`wywoływania funkcji ODBC, takich jak . Aby uzyskać więcej informacji na temat DDX, zobacz [Okno Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md).

RFX jest w większości przezroczysty dla Ciebie. Jeśli deklarujesz swoje klasy recordset za pomocą Kreatora aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta odbc MFC),](../../mfc/reference/adding-an-mfc-odbc-consumer.md)RFX jest wbudowany w nich automatycznie. Klasa zestawu rekordów musi pochodzić `CRecordset` z klasy podstawowej dostarczonej przez platformę. Kreator aplikacji MFC umożliwia utworzenie początkowej klasy pliku recordset. **Dodaj klasę** umożliwia dodawanie innych klas akcesoryjnych, zgodnie z potrzebami. Aby uzyskać więcej informacji i przykładów, zobacz [Dodawanie konsumenta odbc MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Należy ręcznie dodać niewielką ilość kodu RFX w trzech przypadkach, jeśli chcesz:

- Użyj sparametryzowanych zapytań. Aby uzyskać więcej informacji, zobacz [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

- Wykonywanie sprzężeń (przy użyciu jednego akumulatu rekordów dla kolumn z dwóch lub więcej tabel). Aby uzyskać więcej informacji, zobacz [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Dynamiczne powiąż kolumny danych. Jest to mniej powszechne niż parametryzacja. Aby uzyskać więcej informacji, zobacz [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Jeśli potrzebujesz bardziej zaawansowanego zrozumienia RFX, zobacz [Wymiana pól rekordu: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).

Następujące tematy wyjaśniają szczegóły korzystania z obiektów programu recordset:

- [Wymiana pól rekordów: używanie RFX](../../data/odbc/record-field-exchange-using-rfx.md)

- [Wymiana pól rekordów: używanie funkcji RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)

- [Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[MFC ODBC zużywają](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Obsługa bazy danych, kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
