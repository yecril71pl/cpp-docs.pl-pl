---
title: Routing poleceń
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: 8d1e1e59c56439c01655a1416df645ccc6922411
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907621"
---
# <a name="command-routing"></a>Routing poleceń

Odpowiedzialność za pracę z poleceniami jest ograniczona do tworzenia połączeń mapy komunikatów między poleceniami i ich funkcjami obsługi, zadanie, dla którego jest używany [Kreator klas MFC](reference/mfc-class-wizard.md). Należy również napisać kod dla programów obsługi poleceń.

Komunikaty systemu Windows są zwykle wysyłane do głównego okna ramki, ale komunikaty poleceń są następnie kierowane do innych obiektów. Struktura kieruje polecenia przez standardową sekwencję obiektów docelowych poleceń, z których jedna powinna mieć procedurę obsługi dla polecenia. Każdy obiekt docelowy polecenia sprawdza mapę komunikatów, aby sprawdzić, czy może obsłużyć komunikat przychodzący.

Różne klasy docelowe poleceń sprawdzają własne mapy komunikatów w różnych godzinach. Zazwyczaj Klasa kieruje polecenie do określonych obiektów, aby dać im pierwszą szansę na polecenie. Jeśli żaden z tych obiektów nie obsługuje polecenia, oryginalna Klasa sprawdza swoją własną mapę komunikatów. Następnie, jeśli nie może dostarczyć samego programu obsługi, może on skierować polecenie do jeszcze więcej obiektów docelowych poleceń. W poniższej [tabeli](#_core_standard_command_route) poniżej pokazano, jak każda z klas ma strukturę tej sekwencji. Ogólna kolejność, w której obiekt docelowy polecenia kieruje polecenie:

1. Do aktualnie aktywnego obiektu podrzędnego polecenia — obiekt docelowy.

1. Do samego siebie.

1. Z innymi obiektami docelowymi polecenia.

Jak drogie jest ten mechanizm routingu w porównaniu do tego, co program obsługi w odpowiedzi na polecenie, koszt routingu jest niski. Należy pamiętać, że struktura generuje polecenia tylko wtedy, gdy użytkownik współdziała z obiektem interfejsu użytkownika.

### <a name="_core_standard_command_route"></a>Standardowa trasa polecenia

|Gdy obiekt tego typu otrzymuje polecenie. . .|Nadaje sobie i innym obiektom docelowym polecenia możliwość obsługi polecenia w następującej kolejności:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Okno ramek MDI (`CMDIFrameWnd`)|1.  Wyprzedzeni`CMDIChildWnd`<br />2.  To okno ramowe<br />3.  Aplikacja (`CWinApp` obiekt)|
|Okno ramki dokumentu (`CFrameWnd`, `CMDIChildWnd`)|1.  Widok aktywny<br />2.  To okno ramowe<br />3.  Aplikacja (`CWinApp` obiekt)|
|Widok|1.  Ten widok<br />2.  Dokument dołączony do widoku|
|dokument|1.  Ten dokument<br />2.  Szablon dokumentu dołączony do dokumentu|
|Okno dialogowe|1.  To okno dialogowe<br />2.  Okno, które jest właścicielem okna dialogowego<br />3.  Aplikacja (`CWinApp` obiekt)|

Gdzie numerowane wpisy w drugiej kolumnie powyższej tabeli wskazują inne obiekty, takie jak dokument, zobacz odpowiadające im elementy w pierwszej kolumnie. Na przykład podczas odczytywania w drugiej kolumnie, w której widok przekazuje polecenie do dokumentu, zobacz wpis "Document" w pierwszej kolumnie, aby dalej postępować zgodnie z routingiem.

## <a name="see-also"></a>Zobacz także

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)
