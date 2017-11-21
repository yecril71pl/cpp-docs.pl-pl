---
title: "Za pomocą formantu klawisza dostępu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 016243de093ced7483506068e6e6478c024b07d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-hot-key-control"></a>Używanie formantu klawisza dostępu
Typowy sposób formantu klawisza dostępu jest zgodny ze wzorcem poniżej:  
  
-   Formant nie zostanie utworzony. Jeśli formant jest określona w szablonie — okno dialogowe, tworzenie odbywa się automatycznie po utworzeniu okna dialogowego. (Powinien mieć [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) element członkowski w klasy okien dialogowych umożliwiająca formantu klawisza dostępu.) Alternatywnie można użyć [Utwórz](../mfc/reference/chotkeyctrl-class.md#create) funkcji członkowskiej można utworzyć formantu jako okna podrzędnego każdego okna.  
  
-   Jeśli chcesz ustawić wartość domyślną dla formantu, wywołaj [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) funkcję elementu członkowskiego. Jeśli chcesz zabronić używania określonych stanach shift, wywołanie [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). W przypadku kontrolek w oknie dialogowym jest odpowiedni moment, aby to zrobić, w oknie dialogowym [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkcji.  
  
-   Użytkownik wchodzi w interakcję z formantem naciskając kombinację klawiszy dostępu, po aktywowaniu formantu klawisza dostępu. Użytkownik następnie aplikacja wskazuje, że to zadanie jest zakończone, być może przez kliknięcie przycisku w oknie dialogowym.  
  
-   Gdy program jest powiadamiany o to, że użytkownik wybrał klawisza dostępu, należy używać funkcji członkowskiej [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) pobrać wirtualnego wartości klucza i shift stanu formantu klawisza dostępu.  
  
-   Jeśli znasz już klucza co wybrany przez użytkownika, można ustawić klawisza dostępu przy użyciu jednej z metod opisanych w [Ustawianie klawisza dostępu](../mfc/setting-a-hot-key.md).  
  
-   W przypadku formantu klawisza dostępu w oknie dialogowym go i `CHotKeyCtrl` obiektu zostaną automatycznie usunięte. Jeśli nie, musisz upewnij się, że oba formantu i `CHotKeyCtrl` obiektu prawidłowo zostaną zniszczone.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

