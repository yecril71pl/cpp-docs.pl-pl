---
title: OnIdle — funkcja członkowska | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b334a4561af40b69bc367ab5b1129afa8fb29ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377301"
---
# <a name="onidle-member-function"></a>OnIdle — Funkcja członkowska

Podczas przetwarzania żadnych komunikatów Windows struktura wywołuje [CWinApp](../mfc/reference/cwinapp-class.md) funkcja elementu członkowskiego [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (opisanej w odwołanie do biblioteki MFC).

Zastąp `OnIdle` do wykonywania zadań w tle. Domyślna wersja aktualizuje stan obiektów interfejsu użytkownika, takich jak przyciski paska narzędzi i wykonuje oczyszczania obiekty tymczasowe, utworzone przez platformę w trakcie jego działania. Na poniższym rysunku przedstawiono, jak pętli komunikatów wywołuje `OnIdle` gdy nie ma żadnych komunikatów w kolejce.

![Przetwarzanie pętli komunikatów](../mfc/media/vc387c1.gif "vc387c1") pętli komunikatów

Aby uzyskać więcej informacji na temat działania w pętli bezczynności, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md).

## <a name="see-also"></a>Zobacz też

[CWinApp: klasa aplikacji](../mfc/cwinapp-the-application-class.md)
