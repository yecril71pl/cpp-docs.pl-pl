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
ms.openlocfilehash: 3875a6931b4380f0531e4c1786de6dddfccb76ca
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625465"
---
# <a name="message-categories"></a>Kategorie komunikatów

Jakiego rodzaju komunikaty są przeznaczone do obsługi zapisu, istnieją trzy główne kategorie:

1. komunikaty systemu Windows

   Obejmuje to przede wszystkim te komunikaty zaczynające się od prefiksu **WM_** , z wyjątkiem WM_COMMAND. Komunikaty systemu Windows są obsługiwane przez system Windows i widoki. Te komunikaty często mają parametry, które są używane w celu określenia sposobu obsługi wiadomości.

1. Powiadomienia sterujące

   Obejmuje to WM_COMMAND komunikatów powiadomień z formantów i innych okien podrzędnych do ich okien nadrzędnych. Na przykład kontrolka edycji wysyła swój nadrzędny komunikat WM_COMMAND zawierający kod powiadomienia EN_CHANGE Control, gdy użytkownik podjął akcję, która może mieć zmieniony tekst w kontrolce edycji. Program obsługi komunikatu reaguje na komunikat powiadomienia w inny sposób, na przykład pobierając tekst w kontrolce.

   Struktura kieruje komunikaty powiadomień sterowania, jak inne wiadomości **WM_** . Jedynym wyjątkiem jest to, że jest to komunikat BN_CLICKED Control — powiadomienie wysyłane przez przyciski po kliknięciu przez użytkownika. Ten komunikat jest traktowany specjalnie jako komunikat polecenia i kierowany jak inne polecenia.

1. Komunikaty poleceń

   Obejmuje to WM_COMMAND komunikatów powiadomień z obiektów interfejsu użytkownika: menu, przyciski paska narzędzi i klawisze skrótów. Struktura przetwarza polecenia inaczej niż inne komunikaty i może być obsługiwana przez więcej rodzajów obiektów, jak wyjaśniono w [obiektach docelowych poleceń](command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Komunikaty systemu Windows i kontrolki — komunikaty powiadomień

Komunikaty w kategoriach 1 i 2 — komunikaty systemu Windows i powiadomienia dotyczące kontroli — są obsługiwane przez system Windows: obiekty klas pochodnych od klasy `CWnd` . Obejmuje to,,,, `CFrameWnd` `CMDIFrameWnd` `CMDIChildWnd` `CView` `CDialog` i własne klasy pochodne od tych klas podstawowych. Takie obiekty hermetyzują `HWND` uchwyt do okna systemu Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Komunikaty poleceń

Komunikaty w kategorii 3 — polecenia — mogą być obsługiwane przez szersze wiele obiektów: dokumenty, szablony dokumentów i sam obiekt aplikacji oprócz systemu Windows i widoków. Gdy polecenie bezpośrednio wpływa na określony obiekt, warto mieć ten obiekt, aby obsłużyć polecenie. Na przykład polecenie Otwórz w menu plik jest logicznie skojarzone z aplikacją: aplikacja otwiera określony dokument po odebraniu polecenia. Dlatego program obsługi polecenia Otwórz jest funkcją członkowską klasy aplikacji. Aby uzyskać więcej informacji o poleceniach i sposobie ich kierowania do obiektów, zobacz [jak struktura wywołuje program obsługi](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Zobacz też

[Komunikaty i polecenia w strukturze](messages-and-commands-in-the-framework.md)
