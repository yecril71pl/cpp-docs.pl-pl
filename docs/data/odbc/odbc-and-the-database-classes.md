---
title: ODBC i klasy baz danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database classes [C++], ODBC
- ODBC API functions [C++]
- ODBC classes [C++], MFC database classes
- MFC [C++], ODBC and
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9e179bf7570ba2ce53369d59c836e8accf91e8de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057948"
---
# <a name="odbc-and-the-database-classes"></a>ODBC i klasy baz danych

Klasy baz danych MFC ODBC hermetyzacji wywołania funkcji interfejsu API ODBC, należy zwykle czyniłyby samodzielnie w elemencie członkowskim funkcji [CDatabase](../../mfc/reference/cdatabase-class.md) i [CRecordset](../../mfc/reference/crecordset-class.md) klasy. Na przykład złożone sekwencje wywołania ODBC, powiązanie zwracane rekordy lokalizacji przechowywania, obsługa błędów i inne operacje są zarządzane automatycznie przez klasy bazy danych. W wyniku do manipulowania rekordów za pośrednictwem obiektu zestawu rekordów z użyciem znacznie prostsze interfejsu klasy.

> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub przy użyciu klas MFC obiekt DAO (Data Access).

Mimo że zapewniają funkcjonalność ODBC hermetyzacji klas baz danych, nie udostępniają one mapowanie jeden do jednego funkcji interfejsu API ODBC. Klasy bazy danych zapewnia wyższy poziom abstrakcji, modelowane po dostęp do danych obiektów znalezionych w Microsoft Access i Microsoft Visual Basic. Aby uzyskać więcej informacji, zobacz [ODBC i MFC](../../data/odbc/odbc-and-mfc.md).

## <a name="see-also"></a>Zobacz też

[Podstawy ODBC](../../data/odbc/odbc-basics.md)