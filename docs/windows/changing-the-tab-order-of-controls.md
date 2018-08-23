---
title: Zmiana kolejności kart formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5f846244956687b73b6fc7272fe0c4d7d00d0e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596344"
---
# <a name="changing-the-tab-order-of-controls"></a>Zmiana kolejności kart formantów

Kolejność tabulacji tkwi w kolejności, w którym **kartę** klucz przenosi fokus wprowadzania z jednego formantu do drugiego w oknie dialogowym. Zwykle kolejność tabulacji rozpoczynające się od lewej do prawej i od góry do dołu w oknie dialogowym. Każda kontrolka ma **Tabstop** właściwość, która określa, czy formant uzyskuje fokus wprowadzania.

### <a name="to-set-input-focus-for-a-control"></a>Aby ustawić fokus wprowadzania kontrolki

1. W [okno właściwości](/visualstudio/ide/reference/properties-window), wybierz opcję **True** lub **False** w **Tabstop** właściwości.

Nawet formantów, które nie mają **Tabstop** właściwością **True** muszą być częścią kolejności tabulacji. Może to być istotne, na przykład, gdy użytkownik [Definiowanie kluczy dostępu (Mnemonik)](../windows/defining-mnemonics-access-keys.md) dla formantów, które nie mają podpisy. Statyczny tekst, który zawiera klucz dostępu dla kontrolki powiązane musi bezpośrednio poprzedzać pokrewnej kontrolki w kolejności tabulacji.

> [!NOTE]
> Jeśli Twoje okno dialogowe zawiera nakładające się formanty, zmiana kolejności kart może zmienić sposób wyświetlania kontrolki. Formanty, które później w kolejności tabulacji są zawsze wyświetlane na górze nakładające się formanty, które je poprzedzają w kolejności tabulacji.

### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Aby wyświetlić bieżące kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

1. Na **Format** menu, kliknij przycisk **kolejność tabulacji**.

\- lub —

- Naciśnij klawisz **Ctrl**+**D**.

### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Aby zmienić kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym

1. Na **Format** menu, kliknij przycisk **kolejność tabulacji**.

   Liczba w lewym górnym rogu każdej kontrolki zawiera jej miejscu w kolejności tabulacji w bieżącym.

2. Ustawianie kolejności tabulacji, klikając pozycję każdej kontrolki w kolejności ma **kartę** klucza do wykonania.

3. Naciśnij klawisz **Enter** aby zakończyć działanie **kolejność tabulacji** trybu.

   > [!TIP]
   > Po wprowadzeniu **kolejność tabulacji** tryb, możesz nacisnąć przycisk **Esc** lub **Enter** wyłączyć możliwość zmiany kolejności tabulacji.

### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Aby zmienić kolejność tabulacji dla co najmniej dwóch formantów

1. Z **Format** menu, wybierz **kolejność tabulacji**.

2. Określ, gdzie rozpoczyna się zmiany w kolejności. Aby to zrobić, przytrzymaj wciśnięty **Ctrl** klucza i ma miejsce kliknięcie kontrolki przed subskrypcję, w którym zmiany kolejności do rozpoczęcia.

   Na przykład, jeśli chcesz zmienić kolejność formantów `7` za pośrednictwem `9`, naciśnij i przytrzymaj **Ctrl**, następnie wybierz kontrolkę `6` pierwszy.

   > [!NOTE]
   > Aby ustawić numer określonej kontrolki `1` (pierwszy w kolejności tabulacji), kliknij dwukrotnie formant.

3. Wersja **Ctrl** klucza, a następnie kliknij formanty w kolejności, ma **kartę** klawisz, aby wykonać kroki od tego momentu.

4. Naciśnij klawisz **Enter** aby zakończyć działanie **kolejność tabulacji** trybu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)  
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)  
[Kontrolki](../mfc/controls-mfc.md)