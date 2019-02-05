---
title: Formanty rozmiaru
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.combo
helpviewer_keywords:
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 14ccba02-7171-463a-a121-7018cf1e2e5a
ms.openlocfilehash: a6381dcf1aeb9f73ac3b656229d9332df2a6a519
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742716"
---
# <a name="sizing-controls"></a>Formanty rozmiaru

Zmień rozmiar kontrolki za pomocą uchwytów zmiany rozmiaru. Po umieszczeniu wskaźnika na uchwyt zmiany rozmiaru, zmienia kształt, aby wskazać kierunki, w których kontrolki można zmienić rozmiar. Uchwyty zmiany rozmiaru Active są wypełnione; Jeśli uchwyt zmiany rozmiaru jest pusty, formant nie można zmienić rozmiaru na tej osi.

Możesz również zmienić rozmiar formantu przez przyciągania formant do prowadnic i marginesów lub przenosząc jeden przypięty kontroli i przewodnik od innego.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-size-an-individual-control"></a>Rozmiar poszczególnych kontrolek

1. Zaznacz formant.

1. Przeciągnij uchwyty zmiany rozmiaru, aby zmienić rozmiar formantu:

   - Uchwyty zmiany rozmiaru u góry i strony Zmień rozmiar poziomej lub pionowej.

   - Uchwyty zmiany rozmiaru w rogach Zmień rozmiar zarówno w poziomie, jak i w pionie.

   > [!TIP]
   > Możesz zmienić rozmiar formantu jednostki jednego okna dialogowego (DLU) w danym momencie, przytrzymując **Shift** kluczy i korzystać z funkcji **Strzałka w prawo** i **strzałkę w dół** kluczy.

## <a name="to-automatically-size-a-control-to-fit-the-text-within-it"></a>Aby automatycznie rozmiar formantu do tekstu w nim

Wybierz **rozmiar do zawartości** z **Format** menu.

\- lub —

Kliknij prawym przyciskiem myszy formant, a następnie wybierz **rozmiar do zawartości** z menu skrótów.

## <a name="to-make-controls-the-same-width-height-or-size"></a>Aby wprowadzić kontroluje tej samej szerokości, wysokości lub rozmiar

Można zmienić rozmiar grupy formantów, w zależności od rozmiaru formantu dominującego.

1. [Zaznacz formanty](../windows/selecting-multiple-controls.md) chcesz zmienić.

   Wcześniej w tej serii jest dominującym kontrolka. Końcowe rozmiaru formantów w grupie zależy od rozmiaru formantu dominującego. Aby uzyskać więcej informacji dotyczących zaznaczania formantu dominującego zobacz [Określanie formantu dominującego](../windows/specifying-the-dominant-control.md).

1. Z **Format** menu, wybierz **Wyrównaj rozmiar**, a następnie wybierz jedno z następujących poleceń:

   - **Oba**

   - **Wysokość**

   - **Szerokość**

## <a name="to-set-the-size-of-the-combo-box-and-its-drop-down-list"></a>Aby ustawić rozmiar kombi pola i jego listy rozwijanej

Po dodaniu do okna dialogowego, można rozmiar pola kombi. Można również określić rozmiar pola listy rozwijanej. Aby uzyskać więcej informacji, zobacz [dodanie wartości do kontrolki pola kombi](../windows/adding-values-to-a-combo-box-control.md).

### <a name="to-size-a-combo-box"></a>Rozmiar pola kombi

1. Zaznacz formant pola kombi w oknie dialogowym.

   Początkowo tylko uchwyty zmiany rozmiaru lewej i prawej są aktywne.

1. Ustaw szerokość pola kombi za pomocą uchwytów zmiany rozmiaru.

Można również ustawić pionowy rozmiar część rozwijana pola kombi.

### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Aby ustawić rozmiar kombi pole listy rozwijanej

1. Wybierz przycisk ze strzałką listy rozwijanej z prawej strony pola kombi.

   ![Strzałka na pola kombi w projekcie MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   Zarys zmian kontroli do wyświetlenia rozmiaru pola kombi z listy rozwijanej obszarem rozszerzony.

1. Użyj dolnej uchwyt zmiany rozmiaru, aby zmienić początkowy rozmiar obszaru listy rozwijanej.

   ![Pole kombi&#45;rozmiaru pola w projekcie MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

1. Wybierz strzałkę ponownie, aby zamknąć część listy rozwijanej pola kombi.

## <a name="to-set-the-width-of-a-horizontal-scroll-bar-and-make-it-appear"></a>Ustawianie szerokości poziomego paska przewijania i są wyświetlane

Po dodaniu pola listy z poziomy pasek przewijania w oknie dialogowym przy użyciu klas MFC pasek przewijania nie będzie automatycznie wyświetlane w aplikacji.

Ustaw maksymalną szerokość elementu najszerszego, wywołując [CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent) w kodzie.

   Bez ustawienia tej wartości pasek przewijania nie będzie wyświetlane, nawet jeśli elementy w polu listy są większe niż okno.
> [!NOTE]
> Poziomy pasek przewijania wymaga MFC.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
