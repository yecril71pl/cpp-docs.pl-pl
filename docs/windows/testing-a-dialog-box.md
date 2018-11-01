---
title: Testowanie okna dialogowego (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 101a2b556b2593953bfa6482f96d5b1aadc38d1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625075"
---
# <a name="testing-a-dialog-box-c"></a>Testowanie okna dialogowego (C++)

Podczas projektowania okna dialogowego, można symulować i testować jej zachowania w czasie wykonywania bez kompilacji programu. W tym trybie możesz wykonywać następujące czynności:

- Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybierz polecenia.

- Przetestuj kolejność tabulacji.

- Przetestuj zgrupowania formantów, takich jak pola wyboru i przyciski opcji.

- Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.

   > [!NOTE]
   > Połączenia do kodu pola dialogowego przy użyciu kreatorów nie są objęte symulacją.

Podczas testowania okna dialogowego, zwykle wyświetla się ono w lokalizacji, która jest określana względem okna głównego programu. Jeśli ustawiono okno dialogowe **bezwzględnie Wyrównaj** właściwości **True**, okno dialogowe jest wyświetlane w położeniu względem lewego górnego rogu ekranu.

### <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe

1. Gdy **okna dialogowego** edytora jest aktywnym oknem, na pasku menu, wybierz polecenie **Format** > **Test dialogowy**.

2. Aby zakończyć symulację, naciśnij klawisz **Esc**, lub po prostu wybierz **Zamknij** przycisku w oknie dialogowym, które testujesz.

Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)