---
title: Tworzenie okna dialogowego (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: a3b8143d3a70906f910a445816a188913a593e5d
ms.sourcegitcommit: eb2b34a24e6edafb727e87b138499fa8945f981e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56264819"
---
# <a name="creating-a-dialog-box-c"></a>Tworzenie okna dialogowego (C++)

Lokalizacja i rozmiar okno dialogowe z C++ i położenie i rozmiar formantów, to są mierzone w jednostkach okna dialogowego. Wartości dla poszczególnych formantów i w oknie dialogowym są wyświetlane w prawej dolnej części paska po ich wybraniu stanu programu Visual Studio.

Podczas projektowania okna dialogowego, można symulować i testować jej zachowania w czasie wykonywania bez kompilacji programu. W tym trybie możesz wykonywać następujące czynności:

- Wpisz tekst, wybierz z listy pola kombi, włączanie lub wyłączanie opcji i wybierz polecenia.

- Przetestuj kolejność tabulacji.

- Przetestuj zgrupowania formantów, takich jak pola wyboru i przyciski opcji.

- Przetestuj skróty klawiaturowe dla formantów w oknie dialogowym.

   > [!NOTE]
   > Połączenia do kodu pola dialogowego przy użyciu kreatorów nie są objęte symulacją.

Podczas testowania okna dialogowego, zwykle wyświetla się ono w lokalizacji, która jest określana względem okna głównego programu. Jeśli ustawiono okno dialogowe **bezwzględnie Wyrównaj** właściwości **True**, okno dialogowe jest wyświetlane w położeniu względem lewego górnego rogu ekranu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>Aby utworzyć nowe okno dialogowe

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc, a następnie wybierz **Dodaj zasób** z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. W **Dodaj zasób** okno dialogowe, wybierz opcję **okna dialogowego** w **typ zasobu** , a następnie wybierz **New**.

   Jeśli znak plus (**+**) pojawia się obok **okna dialogowego** typ zasobu, oznacza to dostępnych szablonów okno dialogowe. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon, a następnie wybierz **New**.

   Zostanie otwarte nowe okno dialogowe w **okna dialogowego** edytora.

   Możesz również [otwarcie istniejącego okna dialogowe w edytorze okno dialogowe edycji](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Aby utworzyć okno dialogowe, które użytkownik nie może zamknąć

Można utworzyć użytkownika nie może zamknąć okno dialogowe z środowiska uruchomieniowego. Tego rodzaju okno dialogowe jest użyteczny ze względu na potrzeby logowania oraz dla aplikacji lub blokady dokumentu.

1. W **właściwości** okienku okna dialogowego, ustaw **Menu systemowe** właściwości **false**.

   To ustawienie wyłącza menu systemu okna dialogowego i **Zamknij** przycisku.

1. W formularzu okno dialogowe Usuń **anulować** i **OK** przycisków.

   W czasie wykonywania użytkownik nie może zamknąć okno modalne okno dialogowe, które ma te cechy.

Umożliwia testowanie tego rodzaju okno dialogowe funkcji okno dialogowe testowej wykrywa, gdy **Esc** naciśnięciu. (**Esc** jest również nazywany vk_escape — klawisz wirtualnego.) Niezależnie od tego, jak okno dialogowe umożliwia zachowanie w czasie wykonywania, możesz zakończyć tryb testowy, naciskając klawisz **Esc**.

> [!NOTE]
> Dla aplikacji MFC, aby utworzyć okno dialogowe, którego nie można zamknąć, należy zastąpić domyślne zachowanie `OnOK` i `OnCancel` ponieważ nawet wtedy, gdy usuniesz skojarzone przyciski, nadal można odrzucić okno dialogowe, naciskając klawisz  **Wprowadź** lub **Esc**.

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Aby określić lokalizację i rozmiar okna dialogowego

Istnieją trzy właściwości, które można ustawić w [okno właściwości](/visualstudio/ide/reference/properties-window) do określenia, gdzie zostanie wyświetlone okno dialogowe na ekranie. **Centrum** właściwość jest atrybut typu wartość logiczna; Jeśli równa wartości **True**, okno dialogowe pojawia się zawsze w środku ekranu. Jeśli ustawisz na **False**, możesz ustawić **Pozycja_x** i **Pozycja_y** właściwości umożliwia jawne zdefiniowanie w przypadku, gdy na ekranie, zostanie wyświetlone okno dialogowe. Właściwości pozycji są wartości przesunięcia z lewym górnym rogu obszaru wyświetlania, która jest zdefiniowana jako `{X=0, Y=0}`. Pozycja również opiera się na **bezwzględnie Wyrównaj** właściwości: Jeżeli **True**, współrzędne są podawane względem ekranu; Jeśli **False**, współrzędne są podawane względem okna dialogowego Okno właściciela.

## <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe

1. Gdy **okna dialogowego** edytora jest aktywnym oknem, na pasku menu, wybierz polecenie **Format** > **Test dialogowy**.

1. Aby zakończyć symulację, naciśnij klawisz **Esc**, lub po prostu wybierz **Zamknij** przycisku w oknie dialogowym, które testujesz.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Instrukcje: tworzenie zasobu](../windows/how-to-create-a-resource.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>