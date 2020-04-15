---
title: ODBC i klasy baz danych
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 6511aab9bb048882fe9c3398dd17f769eb16220c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320062"
---
# <a name="odbc-and-the-database-classes"></a>ODBC i klasy baz danych

Klasy bazy danych MFC ODBC hermetyzują wywołania funkcji interfejsu API ODBC, które normalnie można wykonać w funkcjach członkowskich klas [CDatabase](../../mfc/reference/cdatabase-class.md) i [CRecordset.](../../mfc/reference/crecordset-class.md) Na przykład złożone sekwencje wywołań ODBC, powiązanie zwróconych rekordów z lokalizacjami magazynu, obsługa warunków błędów i inne operacje są zarządzane przez klasy bazy danych. W rezultacie używasz znacznie prostszy interfejs klasy do manipulowania rekordami za pośrednictwem obiektu zestaw rekordów.

> [!NOTE]
> Źródła danych ODBC są dostępne za pośrednictwem klas Odbc MFC, zgodnie z opisem w tym temacie lub za pośrednictwem klas obiektu dostępu do danych MFC (DAO).

Mimo że klasy bazy danych hermetyzują funkcje ODBC, nie zapewniają one mapowania jeden do jednego funkcji interfejsu API ODBC. Klasy bazy danych zapewniają wyższy poziom abstrakcji, modelowany po obiektach dostępu do danych znalezionych w programie Microsoft Access i Microsoft Visual Basic. Aby uzyskać więcej informacji, zobacz [ODBC i MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)
