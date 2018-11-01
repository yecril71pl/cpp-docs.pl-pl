---
title: Tworzenie etykietki narzędzia dla przycisku kontrolki Toolbar (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
ms.openlocfilehash: 9179dfcc47f69b9f5db131467f0216da6363085c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558014"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>Tworzenie etykietki narzędzia dla przycisku kontrolki Toolbar (C++)

### <a name="to-create-a-tool-tip"></a>Aby utworzyć etykietki narzędzia

1. Wybierz przycisk paska narzędzi.

2. W [okno właściwości](/visualstudio/ide/reference/properties-window)w **monitu** właściwość pola, Dodaj opis przycisku na pasek stanu; po wiadomości, dodać `\n` i nazwa Porada narzędzia.

Typowym przykładem etykietki narzędzia jest **drukowania** znajdujący się w **WordPad**:

1. Otwórz **WordPad**.

2. Umieść wskaźnik myszy nad **drukowania** przycisku paska narzędzi.

3. Należy zauważyć, że wyraz `Print` teraz zmiennoprzecinkowych pod wskaźnika myszy.

4. Spójrz na pasku stanu (u dołu **WordPad** okna)-Zwróć uwagę, że teraz zawiera tekst `Prints the active document`.

`Print` w **kroku 3** nazywa się "narzędzia poradę," i `Prints the active document` z **kroku 4** "Opis przycisk na pasku stanu."

Jeśli chcesz, aby ten efekt przy użyciu **narzędzi** edytorze ustaw **monitu** właściwość `Prints the active document\nPrint`.

> [!NOTE]
> Możesz edytować tekst monitu przy użyciu [okno właściwości](/visualstudio/ide/reference/properties-window).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

ATL i MFC

## <a name="see-also"></a>Zobacz też

[Tworzenie, przenoszenie i edytowanie przycisków paska narzędzi](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[Edytor paska narzędzi](../windows/toolbar-editor.md)