---
title: Projektowanie okno dialogowe (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742690"
---
# <a name="designing-a-dialog-box-c"></a>Projektowanie okno dialogowe (C++)

Lokalizacja i rozmiar okno dialogowe z C++ i położenie i rozmiar formantów, to są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po ich wybraniu stanu programu Visual Studio.

Podczas projektowania okna dialogowego, można symulować i testować jej zachowania w czasie wykonywania bez kompilacji programu. W tym trybie możesz wykonywać następujące czynności:

- Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybierz polecenia.

- Przetestuj kolejność tabulacji.

- Przetestuj zgrupowania formantów, takich jak pola wyboru i przyciski opcji.

- Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.

   > [!NOTE]
   > Połączenia do kodu pola dialogowego przy użyciu kreatorów nie są objęte symulacją.

Podczas testowania okna dialogowego, zwykle wyświetla się ono w lokalizacji, która jest określana względem okna głównego programu. Jeśli ustawiono okno dialogowe **bezwzględnie Wyrównaj** właściwości **True**, okno dialogowe jest wyświetlane w położeniu względem lewego górnego rogu ekranu.

Aby uzyskać informacje dotyczące sposobu dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index).

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Aby określić lokalizację i rozmiar okna dialogowego

Istnieją trzy właściwości, które można ustawić w [okno właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostanie wyświetlone okno dialogowe na ekranie. **Centrum** właściwość jest atrybut typu wartość logiczna; Jeśli równa wartości **True**, okno dialogowe pojawia się zawsze w środku ekranu. Jeśli ustawisz na **False**, możesz ustawić **Pozycja_x** i **Pozycja_y** właściwości umożliwia jawne zdefiniowanie w przypadku, gdy na ekranie, zostanie wyświetlone okno dialogowe. Właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako `{X=0, Y=0}`. Pozycja również opiera się na **bezwzględnie Wyrównaj** właściwości: Jeżeli **True**, współrzędne są podawane względem ekranu; Jeśli **False**, współrzędne są podawane względem okna dialogowego Okno właściciela.

## <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe

1. Gdy **okna dialogowego** edytora jest aktywnym oknem, na pasku menu, wybierz polecenie **Format** > **Test dialogowy**.

1. Aby zakończyć symulację, naciśnij klawisz **Esc**, lub po prostu wybierz **Zamknij** przycisku w oknie dialogowym, które testujesz.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Pokazywanie i ukrywanie paska narzędzi Edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)