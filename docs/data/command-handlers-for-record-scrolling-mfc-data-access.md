---
title: Programy obsługi poleceń do rekordu przewijania (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 66944221910dbd23d78a78fc951030efbee86bd0
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038522"
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

## <a name="see-also"></a>Zobacz także

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)