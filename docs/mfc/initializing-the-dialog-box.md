---
title: Inicjowanie okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 14cdf94bef79f254b4aaa2c1c0dfba6c88b7498b
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685623"
---
# <a name="initializing-the-dialog-box"></a>Inicjowanie okna dialogowego

Po utworzeniu okna dialogowego i wszystkich jego kontrolek, ale tuż przed oknem dialogowym (dowolnego typu) pojawia się na ekranie, wywoływana jest funkcja członkowska [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) obiektu okna dialogowego. W przypadku modalnego okna dialogowego dzieje się to w trakcie wywołania `DoModal`. Dla niemodalnego okna dialogowego, `OnInitDialog` jest wywoływana, gdy zostanie wywołana `Create`. Zwykle zastąpisz `OnInitDialog`, aby zainicjować kontrolki okna dialogowego, takie jak ustawienie początkowego tekstu pola edycji. Należy wywołać funkcję członkowską `OnInitDialog` klasy podstawowej, `CDialog`, z przesłonięcia `OnInitDialog`.

Jeśli chcesz ustawić kolor tła okna dialogowego (i wszystkie inne okna dialogowe w aplikacji), zobacz [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
