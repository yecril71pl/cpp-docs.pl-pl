---
title: 'Instrukcje: Tworzenie okna dialogowego (C++)'
ms.date: 02/15/2019
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
ms.openlocfilehash: 0d5e4836933f1ce32f28c7fd03c81be5b7d09fd9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222085"
---
# <a name="how-to-create-a-dialog-box-c"></a>Instrukcje: Tworzenie okna dialogowego (C++)

Położenie i rozmiar okna dialogowego języka C++ oraz lokalizacja i rozmiar kontrolek w niej są mierzone w jednostkach okna dialogowego. Wartości poszczególnych kontrolek i okna dialogowego pojawiają się w prawym dolnym rogu paska stanu programu Visual Studio po ich wybraniu.

> [!NOTE]
> Jeśli projekt nie zawiera jeszcze pliku. RC, zobacz [Tworzenie nowego pliku skryptu zasobu](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Instrukcje

**Edytor okien dialogowych** umożliwia:

### <a name="to-create-a-new-dialog-box"></a>Aby utworzyć nowe okno dialogowe

1. W [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources)kliknij prawym przyciskiem myszy plik *. RC* , a następnie wybierz pozycję **Dodaj zasób**.

1. W oknie dialogowym **Dodawanie zasobu** wybierz pozycję **okno dialogowe** na liście **Typ zasobu** , a następnie wybierz pozycję **Nowy**.

   Jeśli **+** obok typu zasobu **okna dialogowego** pojawia się znak plus (), oznacza to, że szablony okna dialogowego są dostępne. Wybierz znak plus, aby rozwinąć listę szablonów, wybierz szablon i wybierz pozycję **Nowy**.

   Nowe okno dialogowe zostanie otwarte w **edytorze okien dialogowych**.

Możesz również otworzyć istniejące okna dialogowe w edytorze okien dialogowych do edycji.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Aby utworzyć okno dialogowe, którego użytkownik nie może zamknąć

Można utworzyć okno dialogowe środowiska uruchomieniowego, którego użytkownik nie może zamknąć. Ten rodzaj okna dialogowego jest przydatny w przypadku logowań oraz dla blokad aplikacji lub dokumentów.

1. W okienku **Właściwości** okna dialogowego Ustaw właściwość **menu system** **`false`** .

   To ustawienie powoduje wyłączenie menu systemowego okna dialogowego i przycisku **Zamknij** .

1. W formularzu okna dialogowego usuń przyciski **Anuluj** i **OK** .

   W czasie wykonywania użytkownik nie może zamknąć modalnego okna dialogowego, które ma te cechy.

Aby włączyć testowanie tego rodzaju okna dialogowego, funkcja okna dialogowego test wykrywa, kiedy naciśnięto **klawisz ESC** . **ESC** jest również znany jako klucz wirtualny VK_ESCAPE. Niezależnie od tego, jak okno dialogowe ma zachowywać się w czasie wykonywania, można zakończyć tryb testowy, naciskając klawisz **ESC**.

> [!NOTE]
> W przypadku aplikacji MFC, aby utworzyć okno dialogowe, którego użytkownicy nie mogą zakończyć, należy zastąpić zachowanie domyślne `OnOK` i, `OnCancel` ponieważ nawet jeśli usuniesz skojarzone przyciski, okno dialogowe będzie nadal można odrzucić, naciskając klawisz **Enter** lub **ESC**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Aby określić lokalizację i rozmiar okna dialogowego

W [oknie właściwości](/visualstudio/ide/reference/properties-window) można ustawić właściwości, aby określić miejsce wyświetlania okna dialogowego na ekranie.

- Właściwość **centrum** logicznego.

   Jeśli ustawisz wartość na **true**, okno dialogowe będzie zawsze wyświetlane na środku ekranu. W przypadku ustawienia dla tej właściwości **wartości false**, można ustawić właściwości **XPos** i **YPos** .

- Właściwości **XPos** i **YPos** , które są używane do jawnego definiowania, gdzie zostanie wyświetlone okno dialogowe.

   Te właściwości położenia są wartościami przesunięcia w lewym górnym rogu obszaru wyświetlania, który jest zdefiniowany jako `{X=0, Y=0}` .

- Właściwość **dopasowania bezwzględnego** , która wpływa na pozycję.

   Jeśli **wartość jest równa true**, współrzędne są względem ekranu. W przypadku **wartości false**współrzędne są względne w stosunku do okna właściciela okna dialogowego.

### <a name="to-test-a-dialog-box"></a>Aby przetestować okno dialogowe

Podczas projektowania okna dialogowego można symulować i testować jego zachowanie w czasie wykonywania bez kompilowania programu. W tym trybie można:

- Wpisz tekst, wybierz z list pól kombi, Włącz lub wyłącz opcje, a następnie wybierz polecenie polecenia.

- Przetestuj kolejność tabulacji.

- Przetestuj grupowanie kontrolek, takich jak przyciski radiowe i pola wyboru.

- Przetestuj skróty klawiaturowe dla kontrolek w oknie dialogowym.

> [!NOTE]
> Połączenia z kodem okna dialogowego za pomocą kreatorów nie są uwzględniane w symulacji.

Po przetestowaniu okna dialogowego zwykle jest ono wyświetlane w lokalizacji względem okna głównego programu. Jeśli ustawisz właściwość **bezwzględną Wyrównaj** okno dialogowe na **wartość true**, okno dialogowe jest wyświetlane w pozycji względem lewego górnego rogu ekranu.

1. Gdy **Edytor okien dialogowych** jest aktywnym oknem, przejdź do **Format**  >  **okna dialogowego**formatowanie menu.

1. Aby zakończyć symulację, naciśnij klawisz **ESC** lub wybierz przycisk **Zamknij** w oknie dialogowym, które chcesz przetestować.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Instrukcje: Zarządzanie kontrolkami okna dialogowego](../windows/controls-in-dialog-boxes.md)<br/>
