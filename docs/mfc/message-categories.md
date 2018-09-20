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
ms.openlocfilehash: 3b1b8da6f6c1b94432d9cd4c91d88f6d844fbb27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433052"
---
# <a name="message-categories"></a>Kategorie komunikatów

Jakie rodzaje komunikatów podczas pisania procedur obsługi dla istnieją trzy główne kategorie:

1. komunikaty systemu Windows

     Obejmuje to przede wszystkim te komunikaty, począwszy od **WM_** prefiksu, z wyjątkiem WM_COMMAND. Komunikaty Windows są obsługiwane przez system windows i widoków. Te komunikaty są często mają parametry, które są używane w wyborze sposobu obsługi wiadomości.

1. Powiadomień dotyczących formantu karty

     Obejmuje to wm_command — komunikaty powiadomień od formantów i innych okien podrzędnych do ich nadrzędnej systemu windows. Na przykład formant edycji wysyła jego element nadrzędny komunikatów WM_COMMAND, zawierającego kod powiadamianie kontrolki EN_CHANGE, gdy użytkownik ma podjąć akcję, która może być zmieniony tekst w kontrolce edycji. Okna obsługi dla wiadomości odpowiada na komunikat powiadomienia w odpowiedni sposób, takie jak pobieranie tekstu w formancie.

     Struktura kieruje komunikaty powiadamianie kontrolki, takie jak inne **WM_** wiadomości. Jedynym wyjątkiem jest jednak komunikatu powiadomienia kontroli BN_CLICKED, które są wysyłane przez przyciski, gdy użytkownik kliknie je. Ten komunikat jest traktowany specjalnie jako komunikat polecenia i kierowane podobnie jak inne polecenia.

1. Komunikaty poleceń

     Obejmuje to wm_command — komunikaty powiadomień z obiektów interfejsu użytkownika: menu, przyciski paska narzędzi i klawiszy skrótów. Struktura przetwarza polecenia inaczej niż inne komunikaty i może zostać obsłużony przez więcej różnych obiektów, jak wyjaśniono w [obiekty docelowe poleceń](../mfc/command-targets.md).

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows komunikatów i powiadamianie kontrolki komunikatów

Komunikaty w kategorii 1 i 2 — Windows wiadomości i powiadomień dotyczących formantu karty — są obsługiwane przez system windows: obiektów klasy pochodnej klasy `CWnd`. Obejmuje to `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, i własnych klas pochodnych tych klas bazowych. Takie obiekty hermetyzują `HWND`, uchwytem do okna Windows.

##  <a name="_core_command_messages"></a> Komunikaty poleceń

Komunikaty w kategorii 3 — polecenia — może obsługiwać szerszą gamy obiektów: dokumenty, szablony dokumentów i obiekt aplikacji oprócz okien i widoków. Gdy polecenie bezpośrednio wpływa na niektórych określonego obiektu, dobrym pomysłem będzie mieć ten obiekt obsługi polecenia. Na przykład polecenie Otwórz menu Plik jest logicznie skojarzone z aplikacją: aplikacja zostanie otwarta określonego dokumentu po odebraniu polecenia. Obsługa polecenia Otwórz więc funkcji składowej klasy aplikacji. Aby uzyskać więcej informacji o poleceniach oraz jak są kierowane do obiektów, zobacz [jak struktura wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)

