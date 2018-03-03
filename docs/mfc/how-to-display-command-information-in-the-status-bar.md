---
title: "Porady: wyświetlanie informacji o poleceniu na pasku stanu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da836f48592d97b3526c568eb9d9a830428f53a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Porady: wyświetlanie informacji o poleceniu na pasku stanu
Po uruchomieniu Kreatora aplikacji, aby utworzyć szkielet aplikacji może obsługiwać paska narzędzi i paska stanu. Tylko jedną opcję w Kreatorze aplikacji obsługuje zarówno. Pasek stanu jest obecny, aplikacja automatycznie zapewnia przydatne opinii jako użytkownik przesunie wskaźnik nad elementami menu. Aplikacja automatycznie wyświetla ciąg monitu w pasku stanu, gdy element menu zostanie wyróżniona. Na przykład, gdy użytkownik przesunie wskaźnik nad **Wytnij** na **Edytuj** menu na pasku stanu może być wyświetlany w obszarze wiadomości w pasku stanu "Wycina zaznaczenie i umieszcza je w Schowku". Monit ułatwia użytkownikom zrozumienie przeznaczenia elementu menu. Ta metoda działa również po kliknięciu przycisku paska narzędzi.  
  
 Definiując monitu ciągów dla elementów menu, które dodajesz do programu, można dodać do tej pomocy paska stanu. Aby to zrobić, podaj ciągi Monituj podczas edytowania właściwości elementu menu w edytorze menu. Ciągów, które należy zdefiniować są przechowywane w pliku zasobów aplikacji. mają one takich samych identyfikatorów jako poleceń, których one wyjaśnienia.  
  
 Domyślnie, Kreator aplikacji dodaje `AFX_IDS_IDLEMESSAGE`, identyfikator standardowe komunikat "Gotowe", która jest wyświetlana, gdy program oczekuje na nowe komunikaty. Jeśli określono opcję Context-Sensitive pomoc w Kreatorze aplikacji, wiadomości jest zmieniana na "Aby uzyskać pomoc, naciśnij klawisz F1".  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

