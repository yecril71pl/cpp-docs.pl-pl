---
title: "Używanie widoku rekordu (dostęp do danych MFC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d37f40169330fe878eee326628bd26bef9ca8d8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-record-view--mfc-data-access"></a>Używanie widoku rekordu (dostęp do danych MFC)
W tym temacie wyjaśniono, jak często mogą dostosować domyślny kod dla widoków rekordów, które kreator zapisuje dla Ciebie. Zazwyczaj chcesz ograniczyć wybór rekordów z [filtru](../data/odbc/recordset-filtering-records-odbc.md) lub [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), być może [sortowania](../data/odbc/recordset-sorting-records-odbc.md) rekordów, dostosowywanie instrukcji SQL.  
  
 Przy użyciu `CRecordView` jest znacznie taki sam, jak za pomocą [CFormView](../mfc/reference/cformview-class.md). Podstawowe podejście jest użyć widoku rekordu do wyświetlania i prawdopodobnie aktualizacji rekordów jednym zestawie rekordów. Ponadto warto również za pomocą innych zestawów rekordów, zgodnie z opisem w [widoków rekordów: wypełnianie pola listy z drugiego zestawu wierszy](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)