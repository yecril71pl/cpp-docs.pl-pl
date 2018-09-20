---
title: Ilustracja routingu poleceń | Dokumentacja firmy Microsoft
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
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46449a90223bdb5e7774d4be5710014ff2c6ccae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406077"
---
# <a name="command-routing-illustration"></a>Ilustracja routingu poleceń

Aby zilustrować, należy wziąć pod uwagę komunikatem polecenia Wyczyść wszystko elementu menu, w menu Edycja aplikacji MDI. Załóżmy, że funkcja obsługi dla tego polecenia stanie się być funkcją składową klasy dokumentu aplikacji. Poniżej przedstawiono, jak polecenie osiągnie jej obsługi po użytkownik wybierze element menu:

1. W oknie głównym ramki odbiera komunikat polecenia najpierw.

1. Główne okno ramek MDI daje aktualnie aktywne okno podrzędne MDI możliwość obsługi polecenia.

1. Standardowy routing oknem ramki podrzędnego MDI zapewnia jej widok szansę w wierszu polecenia przed sprawdzeniem jego własnej mapy wiadomości.

1. Widok najpierw sprawdza jego własnej mapy wiadomości i następnie znajdowanie żadna procedura obsługi kieruje polecenia do jego skojarzonego dokumentu.

1. Dokument sprawdza jego mapy wiadomości i wyszukuje program obsługi. Ten dokument funkcja członkowska jest wywoływana i zatrzymuje routingu.

Jeśli dokument nie ma program obsługi, go polecenie będzie następnie kierować do jego szablonu dokumentu. A następnie polecenie zwróci się do widoku, a następnie w oknie ramki. Na koniec okno ramowe będzie sprawdź jego mapie komunikatów. Jeśli sprawdzanie również nie powiodło się, polecenia będą kierowane do główne okno ramek MDI, a następnie do obiektu aplikacji — ultimate docelowego nieobsługiwanych poleceń.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

