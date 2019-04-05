---
title: ODBC i klasy baz danych
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
ms.openlocfilehash: 7692a8128e3dac97c9107e986f6698db76c22c58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025993"
---
# <a name="odbc-and-the-database-classes"></a>ODBC i klasy baz danych

Klasy baz danych MFC ODBC hermetyzacji wywołania funkcji interfejsu API ODBC, należy zwykle czyniłyby samodzielnie w elemencie członkowskim funkcji [CDatabase](../../mfc/reference/cdatabase-class.md) i [CRecordset](../../mfc/reference/crecordset-class.md) klasy. Na przykład złożone sekwencje wywołania ODBC, powiązanie zwracane rekordy lokalizacji przechowywania, obsługa błędów i inne operacje są zarządzane automatycznie przez klasy bazy danych. W wyniku do manipulowania rekordów za pośrednictwem obiektu zestawu rekordów z użyciem znacznie prostsze interfejsu klasy.

> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub przy użyciu klas MFC obiekt DAO (Data Access).

Mimo że zapewniają funkcjonalność ODBC hermetyzacji klas baz danych, nie udostępniają one mapowanie jeden do jednego funkcji interfejsu API ODBC. Klasy bazy danych zapewnia wyższy poziom abstrakcji, modelowane po dostęp do danych obiektów znalezionych w Microsoft Access i Microsoft Visual Basic. Aby uzyskać więcej informacji, zobacz [ODBC i MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Zobacz także

[Podstawy ODBC](../../data/odbc/odbc-basics.md)