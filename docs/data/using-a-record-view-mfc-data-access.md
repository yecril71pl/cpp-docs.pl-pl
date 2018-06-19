---
title: Używanie widoku rekordu (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 23dd3335f6c77a3efec26f13e78824806f05821a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104646"
---
# <a name="using-a-record-view--mfc-data-access"></a>Używanie widoku rekordu (dostęp do danych MFC)
W tym temacie wyjaśniono, jak często mogą dostosować domyślny kod dla widoków rekordów, które kreator zapisuje dla Ciebie. Zazwyczaj chcesz ograniczyć wybór rekordów z [filtru](../data/odbc/recordset-filtering-records-odbc.md) lub [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), być może [sortowania](../data/odbc/recordset-sorting-records-odbc.md) rekordów, dostosowywanie instrukcji SQL.  
  
 Przy użyciu `CRecordView` jest znacznie taki sam, jak za pomocą [CFormView](../mfc/reference/cformview-class.md). Podstawowe podejście jest użyć widoku rekordu do wyświetlania i prawdopodobnie aktualizacji rekordów jednym zestawie rekordów. Ponadto warto również za pomocą innych zestawów rekordów, zgodnie z opisem w [widoków rekordów: wypełnianie pola listy z drugiego zestawu wierszy](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)   
 [Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)