---
title: Kategorie komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d0e4710c74c12bf62cd19df6a053aea9ac35eaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348452"
---
# <a name="message-categories"></a>Kategorie komunikatów
Jakiego rodzaju wiadomości podczas pisania obsług dla istnieją trzy główne kategorie:  
  
1.  komunikaty systemu Windows  
  
     Obejmuje to przede wszystkim tych wiadomości, począwszy od **WM_** prefiksu, z wyjątkiem **WM_COMMAND**. Komunikaty systemu Windows są obsługiwane przez system windows i widoków. Komunikaty te są często mają parametry, które są używane w wyborze sposobu obsługi wiadomości.  
  
2.  Powiadomień dotyczących formantu karty  
  
     Obejmuje to **WM_COMMAND** komunikatów powiadomień od formantów i innych okien podrzędnych do ich nadrzędnej systemu windows. Na przykład formantu edycyjnego wysyła nadrzędnego **WM_COMMAND** komunikat zawierający **EN_CHANGE** kod powiadomień dotyczących formantu, gdy użytkownik trwało akcji, który może zmienić tekst w formancie edycyjnym. Okna obsługi wiadomości odpowiada na komunikat powiadomienia w odpowiedni sposób, takie jak pobieranie tekstu w formancie.  
  
     Platformę kieruje komunikaty powiadomień dotyczących formantu, jak inny **WM_** wiadomości. Jedynym wyjątkiem jest jednak **BN_CLICKED** komunikatów powiadomień dotyczących formantu wysyłane przez przyciski, gdy użytkownik kliknie je. Ten komunikat jest specjalnym jako komunikat polecenia i kierowania podobnie jak inne polecenia.  
  
3.  Komunikaty poleceń  
  
     Obejmuje to **WM_COMMAND** komunikatów powiadomień z obiektów interfejsu użytkownika: menu, przycisków paska narzędzi i klawiszy skrótów. Platformę przetwarza polecenia inaczej niż inne komunikaty i mogą być obsługiwane za więcej typów obiektów, zgodnie z objaśnieniem w [obiekty docelowe poleceń](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Komunikaty systemu Windows i komunikaty powiadomień dotyczących formantu  
 Komunikaty w kategorii 1 i 2 — komunikaty systemu Windows i powiadomień dotyczących formantów — są obsługiwane przez system windows: obiekty klas pochodnych od klasy `CWnd`. Obejmuje to `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, i własnych klas pochodnych tych klas podstawowych. Hermetyzuj takie obiekty `HWND`, dojścia do okna systemu Windows.  
  
##  <a name="_core_command_messages"></a> Komunikaty poleceń  
 Komunikaty w kategorii 3 — poleceń — są obsługiwane przez różnych obiektów: dokumentów, szablony dokumentów i obiekt aplikacji oprócz okien i widoków. Jeśli polecenie ma bezpośredni wpływ niektórych określonego obiektu, warto mieć obiektu obsługi polecenia. Na przykład polecenie Otwórz w menu Plik jest logicznie skojarzony z aplikacją: określony dokument po otrzymaniu polecenie otwarcia aplikacji. Dlatego Obsługa polecenia Otwórz jest funkcją członkowską klasy aplikacji. Aby uzyskać więcej informacji na temat poleceń i jak są kierowane do obiektów, zobacz [jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

