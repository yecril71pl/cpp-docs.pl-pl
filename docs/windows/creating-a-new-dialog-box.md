---
title: 'Instrukcje: Tworzenie okna dialogowego (C++)'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 28ed6c8be262e0446b828cfa3e6e9fe2ba53672a
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344208"
---
# <a name="how-to-create-a-dialog-box-c"></a>Instrukcje: Tworzenie okna dialogowego (C++)

Lokalizacja i rozmiar okno dialogowe z C++ i położenie i rozmiar formantów, to są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po ich wybraniu stanu programu Visual Studio.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Instrukcje

**Edytor okien dialogowych** umożliwia:

### <a name="to-create-a-new-dialog-box"></a>Aby utworzyć nowe okno dialogowe

1. W [widok zasobów](how-to-create-a-resource-script-file.md#create-resources), kliknij prawym przyciskiem myszy użytkownika *.rc* plik i wybierz **Dodaj zasób**.

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **okna dialogowego** w **typ zasobu** , a następnie wybierz **New**.

   Jeśli znak plus ( **+** ) pojawia się obok **okna dialogowego** typ zasobu, oznacza to dostępnych szablonów okno dialogowe. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

   Zostanie otwarte nowe okno dialogowe w **Edytor okien dialogowych**.

Możesz również otworzyć istniejącego okna dialogowe w edytorze okno dialogowe do edycji.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Aby utworzyć okno dialogowe, które użytkownik nie może zamknąć

Można utworzyć użytkownika nie może zamknąć okno dialogowe z środowiska uruchomieniowego. Tego rodzaju okno dialogowe jest użyteczny ze względu na potrzeby logowania oraz dla aplikacji lub blokady dokumentu.

1. W **właściwości** okienku okna dialogowego, ustaw **Menu systemowe** właściwości **false**.

   To ustawienie wyłącza menu systemu okna dialogowego i **Zamknij** przycisku.

1. W formularzu okno dialogowe Usuń **anulować** i **OK** przycisków.

   W czasie wykonywania użytkownik nie może zamknąć okno modalne okno dialogowe, które ma te cechy.

Umożliwia testowanie tego rodzaju okno dialogowe funkcji okno dialogowe testowej wykrywa, gdy **Esc** naciśnięciu. **ESC** jest również nazywany vk_escape — klawisz wirtualnego. Niezależnie od tego, jak okno dialogowe umożliwia zachowanie w czasie wykonywania, możesz zakończyć tryb testowy, naciskając klawisz **Esc**.

> [!NOTE]
> Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zamknąć, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy usuniesz skojarzone przyciski, nadal można odrzucić okno dialogowe, naciskając klawisz  **Wprowadź** lub **Esc**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Aby określić lokalizację i rozmiar okna dialogowego

Ma właściwości można ustawić w [okno właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostanie wyświetlone okno dialogowe na ekranie.

- Wartość logiczna **Centrum** właściwości.

   Jeśli wartość jest ustawiona na **True**, okno dialogowe pojawia się zawsze w środku ekranu. Jeśli ta właściwość jest ustawiona na **False**, możesz ustawić **Pozycja_x** i **Pozycja_y** właściwości.

- **Pozycja_x** i **Pozycja_y** właściwości, które są używane do definiowania jawnie, w przypadku, gdy na ekranie pojawi się okno dialogowe.

   Te właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako `{X=0, Y=0}`.

- **Bezwzględnie Wyrównaj** właściwość, która ma wpływ na położenie.

   Jeśli **True**, współrzędne są podawane względem ekranu. Jeśli **False**, współrzędne są podawane względem okna dialogowego od właściciela tego okna.

### <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe

Podczas projektowania okna dialogowego, można symulować i testować jej zachowania w czasie wykonywania bez kompilacji programu. W tym trybie możesz wykonywać następujące czynności:

- Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybierz polecenia.

- Przetestuj kolejność tabulacji.

- Przetestuj zgrupowania formantów, takich jak pola wyboru i przyciski opcji.

- Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.

> [!NOTE]
> Połączenia do kodu pola dialogowego przy użyciu kreatorów nie są objęte symulacją.

Podczas testowania okna dialogowego, zwykle wyświetla się ono w lokalizacji, która jest określana względem okna głównego programu. Jeśli ustawiono okno dialogowe **bezwzględnie Wyrównaj** właściwości **True**, okno dialogowe jest wyświetlane w położeniu względem lewego górnego rogu ekranu.

1. Gdy **Edytor okien dialogowych** jest aktywnym oknem, przejdź do menu **Format** > **Test dialogowy**.

1. Aby zakończyć symulację, naciśnij klawisz **Esc** lub wybierz **Zamknij** przycisku w oknie dialogowym, które testujesz.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Instrukcje: Zarządzanie formantów okna dialogowego](../windows/controls-in-dialog-boxes.md)<br/>