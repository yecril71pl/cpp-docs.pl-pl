---
title: Testowanie zmodyfikowanej kontrolki ATL DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: f0fec3e2430fd5956e3cc48cd64532efee30926d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501676"
---
# <a name="testing-the-modified-atl-dhtml-control"></a>Testowanie zmodyfikowanej kontrolki ATL DHTML

Wypróbuj nowe kontrolki, aby zobaczyć, jak działa teraz.

## <a name="to-build-and-test-the-modified-control"></a>Tworzenie i testowanie zmodyfikowanej kontrolki

1. Skompiluj ponownie projekt, a następnie otwórz go w **kontener testu**. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do **kontener testu**.

   Zmień rozmiar kontrolki aby pokazać wszystkie przyciski, którą dodałeś.

1. Sprawdź dwa przyciski, które wstawione przez zmianę kodu HTML. Każdy przycisk ma etykietę, został zidentyfikowany w [modyfikowanie kontrolki DHTML ATL](../atl/modifying-the-atl-dhtml-control.md): **Odśwież** i **HelloHTML**.

1. Przetestuj dwa nowe przyciski, aby zobaczyć, jak działają.

Teraz przetestować metody, które nie są częścią interfejsu użytkownika.

1. Zaznacz formant, więc obramowania została aktywowana.

1. Na **kontroli** menu, kliknij przycisk **wywołania metody**.

Metody na liście etykietą **nazwę metody** to metody, które można wywołać kontenera: `MethodInvoked` i `GoToURL`. Wszystkie inne metody są kontrolowane przez interfejs użytkownika.

1. Wybierz metodę do wywołania, a następnie kliknij przycisk `Invoke` Aby wyświetlić okno komunikatu metody lub przejdź do www.microsoft.com.

1. W **wywołania metody** okno dialogowe, kliknij przycisk **Zamknij**.

Aby dowiedzieć się więcej na temat różnych elementów i plików, które tworzą kontrolki ATL DHTML, zobacz [identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Zobacz też

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)
