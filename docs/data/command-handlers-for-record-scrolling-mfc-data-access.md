---
title: Programy obsługi poleceń do przewijania rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 14ef845c3029f1d9a30d257f91c1b33017b6ec8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336942"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Programy obsługi poleceń do przewijania rekordów (dostęp do danych MFC)

[Klasa CRecordView](../mfc/reference/crecordview-class.md) zapewnia domyślną obsługę poleceń dla następujących poleceń standardowych:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Funkcja `OnMove` elementu członkowskiego zapewnia domyślną obsługę poleceń dla wszystkich czterech poleceń, które są przesuwają się z rekordu do rekordu. W miarę wydawania tych poleceń rfx (lub DFX) ładuje nowy rekord do pól walec rekordów, a DDX przenosi wartości do formantów formularza rekordu. Aby uzyskać informacje o RFX, zobacz [Wymiana pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
> Pamiętaj, aby używać tych standardowych identyfikatorów poleceń dla wszystkich obiektów interfejsu użytkownika skojarzonych ze standardowymi poleceniami nawigacji rekordów.

## <a name="see-also"></a>Zobacz też

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
