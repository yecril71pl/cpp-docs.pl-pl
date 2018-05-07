---
title: Routing poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecb836f8fee1efab7f5f925c6ec3ce0f470d666b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing"></a>Routing poleceń
Twoje odpowiedzialność w pracy z poleceń jest ograniczona do tworzenia mapy komunikatów połączeń między polecenia i ich funkcje programu obsługi, zadań, które okno właściwości. Należy również napisać większości programy obsługi poleceń.  
  
 Komunikaty systemu Windows są zwykle wysyłane do głównego okna ramowego, ale komunikaty poleceń są następnie kierowane do innych obiektów. Platformę kieruje polecenia przy użyciu standardowych sekwencji obiekty docelowe poleceń, z których jeden powinien mieć obsługi dla polecenia. Każdy obiekt docelowy polecenia sprawdza jego mapy wiadomości, aby zobaczyć, czy może obsłużyć komunikat przychodzący.  
  
 Różnych klas docelowym polecenia Sprawdź, czy mapy własnych wiadomości w różnym czasie. Zazwyczaj klasa kieruje polecenia do innych obiektów na umożliwieniu im pierwszy w wierszu polecenia. Jeśli żaden z tych obiektów obsługuje polecenie, oryginalnej klasy sprawdza własną mapy komunikatów. Następnie jeśli nie można go przekazać sam program obsługi, go może kierować polecenia do jeszcze więcej obiekty docelowe poleceń. Tabela [trasy standardowego polecenia](#_core_standard_command_route) poniżej pokazano, jak klas struktury tej sekwencji. Ogólne kolejność, w którym element docelowy polecenia kieruje polecenie jest:  
  
1.  Do obiektu docelowego polecenia obecnie aktywny.  
  
2.  Do samego siebie.  
  
3.  Do innych celów polecenia.  
  
 Jak kosztowne jest ten mechanizm routingu w porównaniu do obsługi sieci jest w odpowiedzi na polecenie, koszt marszruty jest niska. Przy tym pamiętać, że platformę generuje polecenia tylko wtedy, gdy użytkownik użyje obiektu interfejsu użytkownika.  
  
### <a name="_core_standard_command_route"></a> Standardowe polecenia trasy  
  
|Gdy obiekt tego typu odebrało polecenie. . .|Udostępnia samej i innych obiektów w elemencie docelowym polecenia możliwość obsługi polecenia w podanej kolejności:|  
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|  
|Okna ramowe MDI (`CMDIFrameWnd`)|1.  Aktywne `CMDIChildWnd`<br />2.  To okno ramowe<br />3.  Aplikacji (`CWinApp` obiektu)|  
|Okna ramowe dokumentów (`CFrameWnd`, `CMDIChildWnd`)|1.  Aktywny widok<br />2.  To okno ramowe<br />3.  Aplikacji (`CWinApp` obiektu)|  
|Widok|1.  Ten widok<br />2.  Dokument dołączony do tego widoku|  
|dokument|1.  Ten dokument<br />2.  Szablon dokumentu dołączony do dokumentu|  
|Okno dialogowe|1.  To okno dialogowe<br />2.  Okno, który jest właścicielem okno dialogowe<br />3.  Aplikacji (`CWinApp` obiektu)|  
  
 W przypadku, gdy numerowane wpisów w drugiej kolumnie powyższej tabeli zawierać inne obiekty, takie jak dokument, zobacz odpowiadający mu element w pierwszej kolumnie. Na przykład podczas czytania w drugiej kolumnie czy widok przekazuje polecenia do swoich dokumentów, zobacz wpis "Dokumentu" w pierwszej kolumnie, które należy wykonać dodatkowe routingu.  
  
## <a name="see-also"></a>Zobacz też  
 [Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

