---
title: Wyrównywanie formantów
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
ms.assetid: a4f49a73-4a17-44b3-8568-aa35f646b5cf
ms.openlocfilehash: abfae0f0146fa736a6427eb1180805717ce8a78e
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484984"
---
# <a name="align-controls"></a>Wyrównywanie formantów

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

Poniższe procedury pokazują, jak wyrównać formanty:

## <a name="to-align-groups-of-controls"></a>Dopasowanie grup formantów

1. [Zaznacz formanty](../windows/selecting-multiple-controls.md) pożądane dopasowanie. Pamiętaj o wybraniu formantu, który ma być formantu dominującego najpierw lub ustaw go jako formant dominujący przed przystąpieniem do wykonywania wyrównanie lub zmiany rozmiaru polecenia.

   Ostateczne stanowisko grupy formantów, zależy od położenie formantu dominującego. Aby uzyskać więcej informacji dotyczących zaznaczania formantu dominującego zobacz [Określanie formantu dominującego](../windows/specifying-the-dominant-control.md).

1. Z **Format** menu, wybierz **Wyrównaj**, a następnie wybierz jedną z następujących wyrównanie:

   - `Lefts`: wyrównuje wybranych kontrolek wzdłuż ich po lewej stronie.

   - `Centers`: wyrównuje wybranych kontrolek w poziomie wzdłuż ich punkty Centrum.

   - `Rights`: wyrównuje wybranych kontrolek wzdłuż jego prawej stronie.

   - `Tops`: wyrównuje wybranych kontrolek wzdłuż górnej krawędzi.

   - `Middles`: wyrównuje wybranych kontrolek w pionie wzdłuż punktom środkowej.

   - `Bottoms`: wyrównuje wybranych kontrolek wzdłuż dolnej krawędzi.

## <a name="to-even-the-spacing-between-controls"></a>Nawet odstępów między formantami

**Okna dialogowego** Edytor umożliwia utworzenie formanty równomiernie między peryferyjnych wybrano kontrolki.

1. Wybierz kontrolki, które chcesz zmienić.

1. Z **Format** menu, wybierz **Rozmieść równomiernie**, a następnie wybierz jedną z następujących wyrównanie odstępy:

   - `Across`: miejsce formantów równomiernie między najdalej z lewej strony i wybraną kontrolkę po prawej stronie.

   - `Down`: miejsce formantów równomiernie między najwyższego poziomu i znajdujących się najniżej wybraną kontrolkę.

## <a name="to-center-controls-in-a-dialog-box"></a>Aby wyśrodkować formantów w oknie dialogowym

1. Wybierz formantów, które chcesz zmienić.

1. Z **Format** menu, wybierz **Centrum w oknie dialogowym**, a następnie wybierz jedną z następujących procedur:

   - `Vertical`: Centrum kontrolki w pionie w oknie dialogowym.

   - `Horizontal`: Centrum kontrolki w poziomie w oknie dialogowym.

## <a name="to-arrange-push-buttons-along-the-right-or-bottom-of-a-dialog-box"></a>Aby rozmieścić przyciski poleceń po prawej stronie lub u dołu okna dialogowego

1. Wybierz jeden lub więcej przycisków.

1. Z **Format** menu, wybierz **Rozmieść przyciski**, a następnie wybierz jedną z następujących procedur:

   - `Right`: wyrównuje przycisków wzdłuż prawej krawędzi okna dialogowego.

   - `Bottom`: wyrównuje przycisków wzdłuż dolnej krawędzi okna dialogowego.

       Wybranie kontrolki niż przycisku polecenia, nie ma wpływu na jego położenie.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)