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
ms.openlocfilehash: 1f8f8f7e40b1c873c4428542c628d02e250f14b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626339"
---
# <a name="initializing-the-dialog-box"></a>Inicjowanie okna dialogowego

Po utworzeniu okna dialogowego i wszystkich jego kontrolek, ale tuż przed oknem dialogowym (dowolnego typu) pojawia się na ekranie, wywoływana jest funkcja członkowska [OnInitDialog](reference/cdialog-class.md#oninitdialog) obiektu okna dialogowego. W przypadku modalnego okna dialogowego dzieje się to w trakcie `DoModal` wywołania. Dla niemodalnego okna dialogowego `OnInitDialog` jest wywoływana, gdy `Create` jest wywoływana. Zwykle przesłonisz `OnInitDialog` , aby zainicjować kontrolki okna dialogowego, takie jak ustawienie początkowego tekstu pola edycji. Należy wywołać `OnInitDialog` funkcję członkowską klasy podstawowej, `CDialog` z `OnInitDialog` przesłonięcia.

Jeśli chcesz ustawić kolor tła okna dialogowego (i wszystkie inne okna dialogowe w aplikacji), zobacz [Ustawianie koloru tła okna dialogowego](setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
