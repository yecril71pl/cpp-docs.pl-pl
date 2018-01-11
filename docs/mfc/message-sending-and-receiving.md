---
title: "Wysyłanie i odbieranie komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c587e3b84ae7afd7869a5c1405d8ddc4ab417b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="message-sending-and-receiving"></a>Wysyłanie i odbieranie komunikatów
Należy wziąć pod uwagę wysyłania część procesu i sposób odpowiadania przez platformę.  
  
 Większość komunikaty w wyniku interakcji z programem. Polecenia są generowane przez kliknięcie myszą w elementach menu lub przycisków paska narzędzi lub naciśnięcia klawiszy skrótów. Użytkownik generuje również komunikaty systemu Windows, na przykład przeniesienie lub zmiana rozmiaru okna. Inne komunikaty systemu Windows są wysyłane w przypadku wystąpienia zdarzenia, takie jak uruchamianie programu lub zakończenie, jak windows Pobierz lub utratę fokus i tak dalej. Komunikaty powiadomień dotyczących formantu są generowane przez kliknięcie myszą lub innych interakcji użytkowników z formantem, takich jak formantu przycisku lub pola listy w oknie dialogowym.  
  
 **Uruchom** funkcji członkowskiej klasy `CWinApp` pobiera wiadomości i wysyła je do odpowiednich okna. Większość komunikaty poleceń są wysyłane do okna ramki głównej aplikacji. `WindowProc` Wstępnie zdefiniowane przez pobiera biblioteki klasy wiadomości i kieruje je w różny sposób, w zależności od kategorii odebranego komunikatu.  
  
 Teraz Rozważmy odbierania część procesu.  
  
 Początkowa odbiorcy wiadomości musi być obiektem okna. Komunikaty systemu Windows są zazwyczaj obsługiwane bezpośrednio przez ten obiekt okna. Komunikaty poleceń, zwykle pochodzących z aplikacji główne okno ramowe, Pobierz kierowane do opisanego w łańcuchu docelowym polecenia [Routing poleceń](../mfc/command-routing.md).  
  
 Każdy obiekt odbiór wiadomości lub poleceń ma własną wiadomości mapowania tej pary wiadomości lub polecenia o nazwie jego obsługi.  
  
 Gdy obiekt docelowy polecenia odbiera wiadomości lub polecenia, wyszukuje jego mapy komunikatów pod kątem dopasowania. W przypadku odnalezienia obsługi wiadomości, wywołuje program obsługi. Aby uzyskać więcej informacji o sposobie są przeszukiwane mapy komunikatów, zobacz [jak Framework wyszukiwania mapy wiadomości](../mfc/how-the-framework-searches-message-maps.md). Odwołuje się ponownie na figurę [polecenia w strukturze](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

