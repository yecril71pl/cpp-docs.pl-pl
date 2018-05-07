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
ms.openlocfilehash: 3678d95ff0748c1854e509d898dfa89778c9a5f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-chotkeyctrl"></a>Korzystanie z CHotKeyCtrl
Formantu klawisza dostępu, reprezentowany przez klasę [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), jest wyświetlany tekst reprezentację kombinacji klawiszy użytkownik wpisze, np. CTRL + SHIFT + Q okno. Ta funkcja obsługuje również reprezentacji wewnętrznej tego klucza w postaci wirtualnego kodu klucza i zestaw flag, które reprezentują stan shift. Formantu klawisza dostępu nie ustawia faktycznie klawisza dostępu, które zależy od programu. (Listę standardowych wirtualnego kodów klucza, zobacz Winuser.h).  
  
 Użyj formantu klawisza dostępu, aby pobrać dane wejściowe użytkownika, dla których klawisza dostępu do skojarzenia z okna lub wątku. Formanty klawisza dostępu są często używane w oknach dialogowych, takich jak może być wyświetlany, gdy użytkownikowi przypisać klawisz skrótu. Jest odpowiedzialność programu do pobierania wartości opisujące klawisza dostępu z formantu klawisza dostępu i wywoływanie odpowiednie funkcje do skojarzenia z okna lub wątek klawisza dostępu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Używanie kontrolki klawisza dostępu](../mfc/using-a-hot-key-control.md)  
  
-   [Ustawianie klawisza dostępu](../mfc/setting-a-hot-key.md)  
  
-   [Globalne klawisze dostępu](../mfc/global-hot-keys.md)  
  
-   [Klawisze dostępu właściwe dla wątków](../mfc/thread-specific-hot-keys.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki](../mfc/controls-mfc.md)

