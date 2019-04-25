---
title: Testowanie zmodyfikowanej kontrolki ATL DHTML
ms.date: 11/06/2018
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls, testing
ms.assetid: 42316118-9433-410f-9d8a-0efcc1eff824
ms.openlocfilehash: 55cdaba64ccb95ee5695c082a5e146b1e7dc2cf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196577"
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

1. Na **kontroli** menu, wybierz **wywołania metody**.

   Metody na liście etykietą **nazwę metody** to metody, które można wywołać kontenera: `MethodInvoked` i `GoToURL`. Wszystkie inne metody są kontrolowane przez interfejs użytkownika.

1. Wybierz metodę do wywołania, a następnie wybierz pozycję **Invoke** Aby wyświetlić okno komunikatu metody lub przejdź do `www.microsoft.com`.

1. W **wywołania metody** okna dialogowego wybierz **Zamknij**.

Aby dowiedzieć się więcej na temat różnych elementów i plików, które tworzą kontrolki ATL DHTML, zobacz [identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="see-also"></a>Zobacz także

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)
