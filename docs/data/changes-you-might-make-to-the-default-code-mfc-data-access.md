---
title: Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
ms.openlocfilehash: 5b8b118c5320e57f2bae5925d3df98650b0288c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611396"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)

[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapisuje klasy zestawu rekordów dla Ciebie, który wybiera wszystkie rekordy w jednej tabeli. Często można zmodyfikować zachowanie na co najmniej jeden z następujących sposobów:

- Ustaw filtr lub porządek sortowania dla zestawu rekordów. To zrobić w `OnInitialUpdate` po obiekt zestawu rekordów jest konstruowany lecz przed jego `Open` funkcja członkowska jest wywoływana. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) i [zestaw rekordów: sortowanie rekordów (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).

- Parametryzacja zestawu rekordów. Określ wartość rzeczywistego parametru czasu wykonywania, po przekroczeniu filtru. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

- Przekazać niestandardowe parametry SQL do [Otwórz](../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego. Omówienie co można wykonać za pomocą tej metody, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Zobacz też

[Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)