---
title: Praca z dokumentami i widokami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], documents
- MFC [C++], views
- views [C++], MFC
- documents [C++], MFC
ms.assetid: 349b142d-1c5a-4b99-9de4-241e41d3d2f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c3879c6a29f95cc908d12c0b899214b521f46686
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060446"
---
# <a name="working-with-documents-and-views"></a>Praca z dokumentami i widokami

Biblioteka Microsoft Foundation Classes (MFC) opiera się na architektury dokument/widok dla wielu funkcji. Zazwyczaj dokument przechowuje swoje dane, a widokiem wyświetla go w obrębie obszaru klienckiego okna ramki i zarządza nimi interakcji użytkownika z danymi. Widok komunikuje się z dokumentu do aktualizacji danych. Klasy bazy danych można użyć w strukturze lub bez niego.

Aby uzyskać więcej informacji na temat Używanie klas baz danych w ramach zobacz [MFC: Używanie klas bazy danych z dokumentami i widokami](../../data/mfc-using-database-classes-with-documents-and-views.md).

Domyślnie Kreator aplikacji MFC tworzy szkielet aplikacji bez użycia obsługi bazy danych. Jednak można wybrać opcje do uwzględnienia obsługi minimalny bazy danych lub bardziej szczegółowy pomocy technicznej, które są oparte na formularzach. Aby uzyskać więcej informacji o opcjach Kreatora aplikacji, zobacz [obsługi bazy danych, Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

Umożliwia także klas baz danych bez korzystania z architektury pełny dokument/widok. Aby uzyskać więcej informacji, zobacz [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Zobacz też

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)