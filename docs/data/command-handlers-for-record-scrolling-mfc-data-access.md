---
title: Programy obsługi poleceń do przewijania rekordów (dostęp do danych MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213450"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Programy obsługi poleceń do przewijania rekordów (dostęp do danych MFC)

Klasa [formularzy CRecordView](../mfc/reference/crecordview-class.md) udostępnia domyślną obsługę poleceń dla następujących standardowych poleceń:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Funkcja członkowska `OnMove` udostępnia domyślną obsługę poleceń dla wszystkich czterech poleceń, które przechodzą z rekordu do rekordu. Po wydaniu tych poleceń RFX (lub DFX) ładuje nowy rekord do pól zestawu rekordów i DDX przenosi wartości do kontrolek formularza rekordu. Aby uzyskać informacje na temat RFX, zobacz temat [Rejestrowanie pól rekordów (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Należy pamiętać, aby użyć tych standardowych identyfikatorów poleceń dla wszystkich obiektów interfejsu użytkownika skojarzonych z poleceniami nawigacji rekordu standardowego.

## <a name="see-also"></a>Zobacz też

[Obsługa nawigacji w widoku rekordu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
