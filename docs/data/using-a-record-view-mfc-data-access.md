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
ms.openlocfilehash: 4107b5e19020843fa50495153841ebcba64301ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077688"
---
# <a name="using-a-record-view--mfc-data-access"></a>Używanie widoku rekordu (dostęp do danych MFC)

W tym temacie wyjaśniono, jak często może dostosować domyślny kod dla widoków rekordów, które kreator zapisuje dla Ciebie. Zazwyczaj chcesz ograniczyć wybór rekordów za pomocą [filtru](../data/odbc/recordset-filtering-records-odbc.md) lub [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), być może [sortowania](../data/odbc/recordset-sorting-records-odbc.md) rekordów, dostosowywanie instrukcji SQL.  
  
Za pomocą `CRecordView` jest bardzo podobne, używając [CFormView](../mfc/reference/cformview-class.md). Podstawowe podejście ma wyświetlać i być może aktualizować rekordy jednym zestawie rekordów przy użyciu widoku rekordu. Poza tym, możesz chcieć użyć innych zestawów rekordów także zgodnie z opisem w [widoków rekordów: wypełnianie pola listy z drugiego zestawu rekordów](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
## <a name="see-also"></a>Zobacz też  

[Widoki rekordów (dostęp do danych MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista sterowników ODBC](../data/odbc/odbc-driver-list.md)