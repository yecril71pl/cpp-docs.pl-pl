---
title: Zmiany wprowadzone w kodzie domyślnym (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e647f6350819fa2cccb5f8319f95fbac16ca19fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088368"
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)
[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapisuje klasy rekordów dla Ciebie, który wybiera wszystkie rekordy w jednej tabeli. Często można zmodyfikować zachowanie na co najmniej jeden z następujących sposobów:  
  
-   Ustaw filtr lub porządek sortowania dla zestawu rekordów. To zrobić w `OnInitialUpdate` po, ale przed wysłaniem konstruowania obiektu zestawu rekordów jego **Otwórz** została wywołana funkcja elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) i [zestaw rekordów: sortowanie rekordów (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).  
  
-   Parametryzacja zestawu rekordów. Określ wartość rzeczywisty parametr środowiska wykonawczego po filtru. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   Ciąg SQL dostosowane, aby przekazać [Otwórz](../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego. Omówienie co można wykonać za pomocą tej metody, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)