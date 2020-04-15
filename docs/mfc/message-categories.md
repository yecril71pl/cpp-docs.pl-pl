---
title: Kategorie komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364751"
---
# <a name="message-categories"></a>Kategorie komunikatów

Jakie rodzaje wiadomości piszesz programy obsługi dla Istnieją trzy główne kategorie:

1. komunikaty systemu Windows

   Obejmuje to przede wszystkim te komunikaty, począwszy od prefiksu **WM_,** z wyjątkiem WM_COMMAND. Komunikaty systemu Windows są obsługiwane przez okna i widoki. Te komunikaty często mają parametry, które są używane do określania sposobu obsługi wiadomości.

1. Powiadomienia kontrolne

   Obejmuje to WM_COMMAND komunikatów powiadomień z formantów i innych okien podrzędnych do ich okien nadrzędnych. Na przykład formant edycji wysyła jego nadrzędnej WM_COMMAND komunikat zawierający EN_CHANGE kodu kontroli powiadomień, gdy użytkownik podjął akcję, która może zmienić tekst w formancie edycji. Program obsługi okna dla wiadomości odpowiada na komunikat powiadomienia w odpowiedni sposób, takich jak pobieranie tekstu w formancie.

   Framework trasy kontroli powiadomień wiadomości, takich jak inne **wiadomości WM_.** Wyjątkiem jest jednak komunikat BN_CLICKED powiadomienia formantu wysyłane przez przyciski, gdy użytkownik kliknie je. Ta wiadomość jest traktowana specjalnie jako komunikat polecenia i kierowana jak inne polecenia.

1. Komunikaty poleceń

   Obejmuje to WM_COMMAND komunikatów powiadomień z obiektów interfejsu użytkownika: menu, przycisków paska narzędzi i klawiszy akceleratora. Struktura przetwarza polecenia inaczej niż inne wiadomości i mogą być obsługiwane przez więcej rodzajów obiektów, jak wyjaśniono w [celach docelowych polecenia](../mfc/command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Wiadomości systemu Windows i komunikaty z powiadomieniami o kontroli

Wiadomości w kategoriach 1 i 2 — Wiadomości systemu Windows i powiadomienia sterujące `CWnd`— są obsługiwane przez okna: obiekty klas pochodzących z klasy . Obejmuje `CFrameWnd`to `CMDIFrameWnd` `CMDIChildWnd`, `CView` `CDialog`, , i własne klasy pochodzące z tych klas podstawowych. Takie obiekty hermetyzują `HWND`dojście do okna systemu Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Komunikaty poleceń

Wiadomości w kategorii 3 — polecenia — mogą być obsługiwane przez szerszą gamę obiektów: dokumenty, szablony dokumentów i sam obiekt aplikacji oprócz okien i widoków. Gdy polecenie bezpośrednio wpływa na niektóre określonego obiektu, ma sens, aby ten obiekt obsługiwać polecenia. Na przykład polecenie Otwórz w menu Plik jest logicznie skojarzone z aplikacją: aplikacja otwiera określony dokument po otrzymaniu polecenia. Tak więc program obsługi dla Open polecenia jest funkcją elementu członkowskiego klasy aplikacji. Aby uzyskać więcej informacji o poleceniach i sposobie ich kierowania do obiektów, zobacz [Jak framework wywołuje program obsługi](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](../mfc/messages-and-commands-in-the-framework.md)
