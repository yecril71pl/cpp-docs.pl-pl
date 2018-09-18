---
title: Polecenie Programy obsługi dla rekordu przewijania (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b51a6e9c9cf9516ed86066f712a17fea69c3cb50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112242"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Programy obsługi poleceń do rekordu przewijania (dostęp do danych MFC)

[CRecordView](../mfc/reference/crecordview-class.md) klasa udostępnia domyślną obsługi poleceń dla następujących poleceń standardowych:  
  
- ID_RECORD_MOVE_FIRST  
  
- ID_RECORD_MOVE_LAST  
  
- ID_RECORD_MOVE_NEXT  
  
- ID_RECORD_MOVE_PREV  
  
`OnMove` Funkcja elementu członkowskiego zawiera domyślne obsługi poleceń dla wszystkich czterech poleceń, które przemieszczać się między rekordami. Te polecenia są wydawane, RFX (lub DFX) ładuje nowy rekord do pola zestawu rekordów i DDX przenosi wartości do kontrolki formularza rekordów. Aby uzyskać informacje na temat RFX, zobacz [wymiany pól rekordu (RFX)](../data/odbc/record-field-exchange-rfx.md).  
  
> [!NOTE]
>  Należy użyć tych identyfikatory poleceń standardowych dla obiektów interfejsu użytkownika skojarzony z poleceń standardowych nawigacji rekordów.  
  
## <a name="see-also"></a>Zobacz też  

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)