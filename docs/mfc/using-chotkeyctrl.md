---
title: Korzystanie z CHotKeyCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CHotKeyCtrl
dev_langs:
- C++
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd966b74590d0e7641f2f789b5c45f901a3cf8c8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421508"
---
# <a name="using-chotkeyctrl"></a>Korzystanie z CHotKeyCtrl

Formantu klawisza dostępu, reprezentowane przez klasę [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), jest oknem które wyświetla tekstowa reprezentacja kombinacji klawiszy użytkownik wpisuje w nim, takie jak CTRL + SHIFT + Q. Udostępnia ona również wewnętrznej reprezentacji tego klucza w postaci wirtualnego klucza kodu i zestaw flagi pokazujące stan shift. Formantu klawisza dostępu nie ustawia faktycznie klawisza dostępu — tą operacją zależy od programu. (Aby uzyskać listę standardowa wirtualnej kody klawiszy, zobacz Winuser.h).

Użyj formantu klawisza dostępu, aby pobrać dane wejściowe użytkownika, dla których klawisza dostępu do skojarzenia z okna lub wątku. Formanty klawisza dostępu są często używane w oknach dialogowych, takich jak może wyświetlić podczas pytania użytkownika, aby przypisać klawisz dostępu. Odpowiada programu do pobierania wartości opisujące klawisza dostępu z formantu klawisza dostępu oraz wywołanie odpowiednie funkcje, aby skojarzyć klawisza dostępu z okna lub wątku.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Używanie kontrolki klawisza dostępu](../mfc/using-a-hot-key-control.md)

- [Ustawianie klawisza dostępu](../mfc/setting-a-hot-key.md)

- [Globalne klawisze dostępu](../mfc/global-hot-keys.md)

- [Klawisze dostępu właściwe dla wątków](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)

