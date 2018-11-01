---
title: Routing poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: add047984f5a32e505e8a739922daa137b5e671d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541703"
---
# <a name="command-routing"></a>Routing poleceń

Twoja odpowiedzialność w pracy z poleceniami jest ograniczona do nawiązywania połączeń mapy komunikatów między poleceniami i ich funkcje obsługi zadań, które okno właściwości. Należy również napisać większość programy obsługi poleceń.

Windows są zwykle wysyłane do głównej ramki okna, ale komunikaty polecenia są następnie kierowane do innych obiektów. Struktura kieruje polecenia za pośrednictwem standardowych sekwencji obiekty docelowe poleceń, z których jeden jest powinny mieć obsługi polecenia. Każdy obiekt w elemencie docelowym polecenia sprawdza jego mapy wiadomości, aby zobaczyć, jeśli może obsługiwać komunikatu przychodzącego.

Różnych klas w elemencie docelowym polecenia Sprawdź, czy mapy własnych wiadomości o różnych porach. Zazwyczaj klasa kieruje polecenia do niektórych innych obiektów, aby dać im pierwszej szansy w wierszu polecenia. Jeśli żadna z tych obiektów obsługuje polecenie, oryginalnej klasy sprawdza jego własnej mapy wiadomości. Następnie jeśli go nie może dostarczyć sam program obsługi, jego może kierować polecenia do jeszcze więcej obiekty docelowe poleceń. Tabela [trasy poleceń standardowych](#_core_standard_command_route) poniżej pokazano, jak każdą z klas struktury tej sekwencji. Ogólne kolejność, w której element docelowy polecenia kieruje polecenia to:

1. Do jego podrzędny aktualnie aktywnego obiektu elemencie docelowym polecenia.

1. Do samego siebie.

1. Do innych celów polecenia.

W jaki sposób kosztownych jest ten mechanizm routingu w porównaniu do programu obsługi sposób działania w odpowiedzi na polecenie, koszt marszruty jest niska. Mieć na uwadze, w ramach generuje polecenia, tylko wtedy, gdy użytkownik wchodzi w interakcję z obiektem interfejsu użytkownika.

### <a name="_core_standard_command_route"></a> Standardowe polecenia trasy

|Gdy obiekt tego typu otrzymuje polecenie. . .|Daje ona samej i innych obiektów w elemencie docelowym polecenia możliwość obsługi polecenia w podanej kolejności:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Okno ramki MDI (`CMDIFrameWnd`)|1.  Aktywne `CMDIChildWnd`<br />2.  To okno ramek<br />3.  Aplikacja (`CWinApp` obiektu)|
|Okna ramki dokumentu (`CFrameWnd`, `CMDIChildWnd`)|1.  Widok aktywny<br />2.  To okno ramek<br />3.  Aplikacja (`CWinApp` obiektu)|
|Widok|1.  Ten widok<br />2.  Dokument dołączony do tego widoku|
|dokument|1.  Ten dokument<br />2.  Szablon dokumentu, dołączony do dokumentu|
|Okno dialogowe|1.  To okno dialogowe<br />2.  Okno, który jest właścicielem okno dialogowe<br />3.  Aplikacja (`CWinApp` obiektu)|

W przypadku, gdy ponumerowanych wpisów w drugiej kolumnie tabeli powyżej wspomnieć o inne obiekty, takie jak dokument, zobacz odpowiadający mu element w pierwszej kolumnie. Na przykład podczas odczytywania w drugiej kolumnie, widok przekazuje polecenia do swoich dokumentów, zobacz wpis "Dokument" w pierwszej kolumnie, aby wykonać dalsze routingu.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

