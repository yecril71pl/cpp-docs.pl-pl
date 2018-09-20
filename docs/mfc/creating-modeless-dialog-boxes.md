---
title: Tworzenie Niemodalnych okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77b80f66f2956e71b90e4d939a0fb74aef28edb1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407039"
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych

Niemodalne okno dialogowe trzeba podać publicznego konstruktora w klasy okien dialogowych. Aby utworzyć niemodalne okno dialogowe, wywołania konstruktora publicznego, a następnie wywołać obiektu okna dialogowego [Utwórz](../mfc/reference/cdialog-class.md#create) funkcja elementu członkowskiego, które można załadować zasobu okna dialogowego. Możesz wywołać **Utwórz** podczas lub po wywołaniu konstruktora. Jeśli zasobu okna dialogowego właściwości **WS_VISIBLE**, natychmiast pojawi się okno dialogowe. Jeśli nie, należy wywołać jej [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

