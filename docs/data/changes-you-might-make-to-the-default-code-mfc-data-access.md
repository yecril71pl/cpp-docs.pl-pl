---
title: Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: fc448ae1e13025a83b33386c2845bdf7bb4d5eec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038638"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)

[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapisuje klasy zestawu rekordów dla Ciebie, który wybiera wszystkie rekordy w jednej tabeli. Często można zmodyfikować zachowanie na co najmniej jeden z następujących sposobów:

- Ustaw filtr lub porządek sortowania dla zestawu rekordów. To zrobić w `OnInitialUpdate` po obiekt zestawu rekordów jest konstruowany lecz przed jego `Open` funkcja członkowska jest wywoływana. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Filtrowanie rekordów (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) i [zestaw rekordów: Sorting Records (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametryzacja zestawu rekordów. Określ wartość rzeczywistego parametru czasu wykonywania, po przekroczeniu filtru. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Przekazać niestandardowe parametry SQL do [Otwórz](../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego. Omówienie co można wykonać za pomocą tej metody, zobacz [SQL: Dostosowywanie instrukcji SQL zestawu rekordów (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Zobacz także

[Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)