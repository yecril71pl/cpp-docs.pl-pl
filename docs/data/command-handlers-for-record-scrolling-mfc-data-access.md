---
title: "Polecenie Programy obsługi dla rekordu przewijania (MFC Data Access) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d3164cfd8a7d78191f2076637b51d96bb45f2293
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Programy obsługi poleceń dla rekordu przewijanie (dostęp do danych MFC)
[CRecordView](../mfc/reference/crecordview-class.md) klasa udostępnia domyślne polecenie obsługi dla standardowych następujących poleceń:  
  
-   **ID_RECORD_MOVE_FIRST**  
  
-   **ID_RECORD_MOVE_LAST**  
  
-   **ID_RECORD_MOVE_NEXT**  
  
-   **ID_RECORD_MOVE_PREV**  
  
 `OnMove` Funkcji członkowskiej zawiera domyślne polecenie obsługi wszystkie cztery poleceń, które przemieszczać się między rekordami. Te polecenia są wydawane, RFX (lub DFX) ładuje nowego rekordu do zestawu rekordów pól i DDX przenosi wartości do formantów rekordem formularza. Aby uzyskać informacje o RFX, zobacz [wymiany pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Należy użyć tych identyfikatory poleceń standardowych dla obiektów interfejsu użytkownika skojarzonego z poleceń standardowych rekordów nawigacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)