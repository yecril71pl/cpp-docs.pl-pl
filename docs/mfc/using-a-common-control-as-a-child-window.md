---
title: Używanie formantu wspólnego jako okna podrzędnego
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 827690f273852dee8f9461aa9af51f1cf7f4ce6e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180573"
---
# <a name="using-a-common-control-as-a-child-window"></a>Używanie formantu wspólnego jako okna podrzędnego

Dowolny wspólnych formantów Windows może służyć jako okna podrzędnego inne okna. Poniższa procedura opisuje sposób dynamicznie tworzenie wspólne kontrolki, a następnie pracować z nią.

### <a name="to-use-a-common-control-as-a-child-window"></a>Aby użyć formantu wspólnego jako okna podrzędnego

1. Zdefiniuj kontrolki w powiązanych klas lub program obsługi.

1. Użyj formantu zastępowania metody [CWnd::Create](../mfc/reference/cwnd-class.md#create) metodę, aby utworzyć formant Windows.

1. Po utworzeniu kontrolki (jako wczesne jako `OnCreate` obsługi Jeśli podklasą kontrolki), można manipulować kontroli przy użyciu jego elementów członkowskich. Zobacz opisy poszczególnych formantów na [formantów](../mfc/controls-mfc.md) szczegółowe informacje na temat metody.

1. Po zakończeniu za pomocą kontrolki, użyj [CWnd::DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow) do zniszczenia kontrolki.

## <a name="see-also"></a>Zobacz także

[Tworzenie i używanie kontrolek](../mfc/making-and-using-controls.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
