---
title: Grupowanie przycisków radiowych w oknie dialogowym (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.grouping
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
ms.openlocfilehash: 1776823a7385499e5a01a04134fe31f42700e14b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665949"
---
# <a name="grouping-radio-buttons-on-a-dialog-box-c"></a>Grupowanie przycisków radiowych w oknie dialogowym (C++)

Po dodaniu przycisków radiowych w oknie dialogowym je traktować jako grupa, ustawiając **grupy** właściwość **właściwości** okna dla pierwszego przycisku w grupie. Pojawi się w polu Identyfikator kontrolki, dla tego przycisku radiowego [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), co pozwala dodać zmienną członkowską, grupy przycisków radiowych.

Może mieć więcej niż jedna grupa przycisków radiowych w oknie dialogowym, a każda grupa powinny zostać dodane, korzystając z następującej procedury.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Aby dodać grupę przycisków radiowych w oknie dialogowym

1. Zaznacz formant przycisku radiowego w [okno przybornika](/visualstudio/ide/reference/toolbox) i kliknij lokalizację, w którym chcesz umieścić kontrolkę w oknie dialogowym.

2. Powtórz krok 1, aby dodać dowolną liczbę przyciski radiowe, ile potrzebujesz. Upewnij się, że przyciski radiowe w grupie są kolejne w kolejności tabulacji (Aby uzyskać więcej informacji, zobacz [zmiana kolejności formanty karty](../windows/changing-the-tab-order-of-controls.md)).

3. W [okno właściwości](/visualstudio/ide/reference/properties-window)ustaw **grupy** właściwość *pierwszy* przycisku radiowego w kolejności tabulacji na **True**.

   Zmiana **grupy** właściwości **True** dodaje WS_GROUP styl do przycisku wpis obiektu okna dialogowego skryptu zasobu i gwarantuje, że użytkownik może wybrać tylko jeden przycisk radiowy jednocześnie przycisku grupy (po kliknięciu przycisku radiowego co inne osoby w grupie zostaną wyczyszczone).

   > [!NOTE]
   > Tylko pierwszy przycisk radiowy w grupie powinny mieć **grupy** właściwością **True**. Jeśli masz dodatkowe formanty, które nie są częścią grupy przycisk, ustaw **grupy** właściwość pierwszy formant *jest spoza grupy* do **True** także. Pierwszy formant spoza grupy można szybko określić, naciskając klawisz **Ctrl**+**D** Aby wyświetlić kolejność tabulacji.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Aby dodać zmiennej składowej w grupie przycisków radiowych

1. Kliknij prawym przyciskiem myszy pierwszą kontrolkę przycisku radiowego w kolejności tabulacji (formant dominujący i z **grupy** właściwość ustawioną na wartość True).

2. Wybierz **Dodaj zmienną** z menu skrótów.

3. W [Kreator dodawania zmiennej składowej](../ide/add-member-variable-wizard.md), wybierz opcję **zmienna sterująca** pole wyboru, a następnie wybierz **wartość** przycisku radiowego.

4. W **nazwa zmiennej** wpisz nazwę dla nowej zmiennej elementu członkowskiego.

5. W **typ zmiennej** pola listy, wybierz opcję **int** lub typ `int`.

6. Teraz można edytować swój kod, aby określić, który przycisk radiowy powinien zostaną wyświetlone jako zaznaczone. Na przykład `m_radioBox1 = 0;` wybiera pierwszy przycisk radiowy w grupie.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Rozmieszczenie kontrolek w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[Kontrolki w oknach dialogowych](../windows/controls-in-dialog-boxes.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)