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
ms.openlocfilehash: a18b4bb1e544f2cc3d033d58a1c6c1a26eec98dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changes-you-might-make-to-the-default-code--mfc-data-access"></a>Zmiany wprowadzane w kodzie domyślnym (dostęp do danych MFC)
[Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md) zapisuje klasy rekordów dla Ciebie, który wybiera wszystkie rekordy w jednej tabeli. Często można zmodyfikować zachowanie na co najmniej jeden z następujących sposobów:  
  
-   Ustaw filtr lub porządek sortowania dla zestawu rekordów. To zrobić w `OnInitialUpdate` po, ale przed wysłaniem konstruowania obiektu zestawu rekordów jego **Otwórz** została wywołana funkcja elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: filtrowanie rekordów (ODBC)](../data/odbc/recordset-filtering-records-odbc.md) i [zestaw rekordów: sortowanie rekordów (ODBC)](../data/odbc/recordset-sorting-records-odbc.md).  
  
-   Parametryzacja zestawu rekordów. Określ wartość rzeczywisty parametr środowiska wykonawczego po filtru. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
-   Ciąg SQL dostosowane, aby przekazać [Otwórz](../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego. Omówienie co można wykonać za pomocą tej metody, zobacz [SQL: dostosowywanie Your zestawu rekordów instrukcji SQL (ODBC)](../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoku rekordu](../data/using-a-record-view-mfc-data-access.md)