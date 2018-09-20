---
title: Używanie formantu wspólnego jako okna podrzędnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 73ddb010aeb8190c063d2691806e3ebd89d0f744
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417972"
---
# <a name="using-a-common-control-as-a-child-window"></a>Używanie formantu wspólnego jako okna podrzędnego

Dowolny wspólnych formantów Windows może służyć jako okna podrzędnego inne okna. Poniższa procedura opisuje sposób dynamicznie tworzenie wspólne kontrolki, a następnie pracować z nią.

### <a name="to-use-a-common-control-as-a-child-window"></a>Aby użyć formantu wspólnego jako okna podrzędnego

1. Zdefiniuj kontrolki w powiązanych klas lub program obsługi.

1. Użyj formantu zastępowania metody [CWnd::Create](../mfc/reference/cwnd-class.md#create) metodę, aby utworzyć formant Windows.

1. Po utworzeniu kontrolki (jako wczesne jako `OnCreate` obsługi Jeśli podklasą kontrolki), można manipulować kontroli przy użyciu jego elementów członkowskich. Zobacz opisy poszczególnych formantów na [formantów](../mfc/controls-mfc.md) szczegółowe informacje na temat metody.

1. Po zakończeniu za pomocą kontrolki, użyj [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) do zniszczenia kontrolki.

## <a name="see-also"></a>Zobacz też

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

