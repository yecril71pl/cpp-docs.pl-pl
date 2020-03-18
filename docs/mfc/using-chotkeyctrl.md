---
title: Korzystanie z CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: e2002d96a1eba913e260fa92281f730355a83ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447242"
---
# <a name="using-chotkeyctrl"></a>Korzystanie z CHotKeyCtrl

Kontrolka klawisza gorąca, reprezentowana przez klasę [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), to okno, w którym jest wyświetlana tekstowa reprezentacja kombinacji klawiszy, na przykład Ctrl + Shift + Q. Utrzymuje również wewnętrzną reprezentację tego klucza w postaci kodu klucza wirtualnego i zestawu flag, które reprezentują stan przesunięcia. Kontrolka klawisza dostępu nie ustawia w rzeczywistości klawisza dostępu do programu. (Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser. h.)

Użyj formantu klawisza dostępu, aby uzyskać dane wejściowe użytkownika, dla którego klucz dostępu ma zostać skojarzony z oknem lub wątkiem. Kontrolki klawisza dostępu są często używane w oknach dialogowych, na przykład podczas monitowania użytkownika o przypisanie klawisza skrótu. Jest on odpowiedzialny za pobieranie wartości opisujących klawisz gorąca z kontrolki klawisza gorąca i wywołanie odpowiednich funkcji w celu skojarzenia klawisza gorąca z oknem lub wątkiem.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Używanie kontrolki klawisza dostępu](../mfc/using-a-hot-key-control.md)

- [Ustawianie klawisza dostępu](../mfc/setting-a-hot-key.md)

- [Globalne klawisze dostępu](../mfc/global-hot-keys.md)

- [Klawisze dostępu właściwe dla wątków](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)
