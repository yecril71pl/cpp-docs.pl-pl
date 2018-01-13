---
title: "Zmiany wprowadzone w kodzie domyślnym (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: record views [C++], customizing default code
ms.assetid: 9992ed37-a6bf-45a5-a572-5c14e42b6628
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 197277a68131c9d63e3eab2f1404cf97169be1f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)
[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapisuje klasy rekordów dla Ciebie, który wybiera wszystkie rekordy w jednej tabeli. Często można zmodyfikować zachowanie na co najmniej jeden z następujących sposobów:  
  
-   Ustaw filtr lub porządek sortowania dla zestawu rekordów. To zrobić w `OnInitialUpdate` po, ale przed wysłaniem konstruowania obiektu zestawu rekordów jego **Otwórz** została wywołana funkcja elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) i [zestaw rekordów: sortowanie rekordów (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).  
  
-   Parametryzacja zestawu rekordów. Określ wartość rzeczywisty parametr środowiska wykonawczego po filtru. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   Ciąg SQL dostosowane, aby przekazać [Otwórz](../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego. Omówienie co można wykonać za pomocą tej metody, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)