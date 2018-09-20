---
title: Modalne i Niemodalne okna dialogowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e355c3bcef9edb68e49903dafbf4719fe0aa925
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417530"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modalne i niemodalne okna dialogowe

Można użyć klasy [CDialog](../mfc/reference/cdialog-class.md) Zarządzanie dwa rodzaje okien dialogowych:

- *Modalne okna dialogowe*, która wymaga od użytkownika odpowiada przed kontynuowaniem program

- *Niemodalne okna dialogowe*, które pozostają na ekranie i są dostępne do użycia w dowolnym momencie, ale zezwala na inne działania użytkownika

Edytowanie zasobów oraz procedury tworzenia szablonu okna dialogowego są takie same dla modalne i Niemodalne okna dialogowe.

Tworzenie okna dialogowego programu wymaga wykonania następujących czynności:

1. Użyj [Edytor okien dialogowych](../windows/dialog-editor.md) projektować okno dialogowe i utworzyć jej zasobów szablonu okna dialogowego.

1. Tworzenie klasy okien dialogowych.

1. Połącz [kontrolki zasobu okna dialogowego do obsługi komunikatów](../windows/adding-event-handlers-for-dialog-box-controls.md) klasy okna dialogowego.

1. Dodaj elementy członkowskie danych skojarzonych z formantów w oknie dialogowym oraz określić [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md) i [walidacji danych okna dialogowego](../mfc/dialog-data-validation.md) formantów.

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

