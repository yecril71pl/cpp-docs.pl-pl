---
title: Inicjowanie okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42526eea184cb4f28d5214fe0c56281ac6da9d6c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426110"
---
# <a name="initializing-the-dialog-box"></a>Inicjowanie okna dialogowego

Po okna dialogowego pole i wszystkich jego formantów są tworzone, ale tuż przed okna dialogowego pole (dowolnego typu) są wyświetlane na ekranie, obiektu okna dialogowego firmy [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcja członkowska jest wywoływana. Dla modalnego okna dialogowego, ten problem wystąpi podczas `DoModal` wywołania. Aby uzyskać niemodalnego okna dialogowego `OnInitDialog` jest wywoływana, gdy `Create` jest wywoływana. Zazwyczaj zastąpienie `OnInitDialog` zainicjować okno dialogowe formanty, takie jak ustawianie początkowy tekst pola edycji. Należy wywołać `OnInitDialog` funkcji składowej klasy bazowej `CDialog`, z Twojej `OnInitDialog` zastąpienia.

Jeśli chcesz ustawić kolor tła okno dialogowe (i w przypadku wszystkich innych oknach dialogowych w aplikacji), zobacz [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

