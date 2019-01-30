---
title: Zaznaczanie kontrolek
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.author: Michael.Blome
ms.topic: tutorial
ms.service: cpp
author: mikeblome
ms.openlocfilehash: 008c99ae4b2cba5ff8f8b9ab069bb1b8085b7524
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293640"
---
# <a name="selecting-controls"></a>Zaznaczanie kontrolek

Zaznacz formanty do rozmiaru, wyrównanie, przenieść, skopiować, lub je usunąć, a następnie ukończ operację, którą chcesz. W większości przypadków należy wybrać więcej niż jeden formant na korzystanie z narzędzia określania rozmiaru i wyrównanie [paska narzędzi edytora okien dialogowych](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Po wybraniu formantu, ma przyciemnione obramowanie wokół niej z niezawodnej (aktywny) lub pusty (nieaktywny) "uchwytów," małe kwadraty, są wyświetlane w krawędź zaznaczenia. Po wybraniu wielu formantów formantu dominującego ma uchwyty zmiany rozmiaru stałych i wszystkich innych wybranych kontrolek mają uchwyty zmiany rozmiaru pusty.

Podczas zmiany rozmiaru lub wyrównywanie formantów wielu **okna dialogowego** Edytor używa "formantu dominującego" Aby określić, jak rozmiar lub wyrównane do innych kontrolek. Domyślnie formant dominujący jest pierwszy formant wybrane.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-controls"></a>Aby wybrać wiele formantów

1. W [okno przybornika](/visualstudio/ide/reference/toolbox), wybierz opcję **wskaźnik** narzędzia.

1. Przeciągnij wskaźnik, aby narysować pole zaznaczenia wokół formanty, które chcesz zaznaczyć w oknie dialogowym.

   Po zwolnieniu przycisku myszy kontroluje wszystkie wewnątrz i przecinające się są zaznaczone pola wyboru.

   \- lub —

   Naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

   \- lub —

   Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz kontrolki, czy chcesz uwzględnić w zaznaczeniu.

## <a name="to-remove-a-control-from-a-group-of-selected-controls-or-to-add-a-control-to-a-group-of-selected-controls"></a>Aby usunąć formant z grupą wybranych kontrolek lub dodać kontrolkę z grupą wybranych kontrolek

1. Z grupą wybrano kontrolki, naciśnij i przytrzymaj **Shift** klucza, a następnie wybierz kontrolkę, która do usuwania lub Dodaj do istniejącego zaznaczenia.

   > [!NOTE]
   > Przytrzymanie **Ctrl** klucza i wybierając polecenie Kontrolki wyboru spowoduje, że, które kontrolują formantu dominującego w ramach tego zaznaczenia.

## <a name="to-specify-the-dominant-control"></a>Aby określić formant dominujący

1. Naciśnij i przytrzymaj **Ctrl** klucza i kliknij formant, którego chcesz użyć do wywierania wpływu na rozmiar lub lokalizację innych formantów *pierwszy*.

> [!NOTE]
> Uchwyty zmiany rozmiaru formantu dominującego są stałe, podczas gdy uchwyty kontrolek podrzędnych są puste. Dalsze zmiany rozmiaru lub wyrównanie opiera się na formant dominujący.

## <a name="to-change-the-dominant-control"></a>Aby zmienić kontrolki dominującej

1. Wyczyść bieżący wybór, klikając poza wszystkie obecnie wybrane formanty.

1. Powtórz poprzedniej procedury, wybierając najpierw innej kontrolki.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)