---
title: Testowanie kontrolki ATL DHTML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, testing
- testing controls
- DHTML controls
- DHTML controls, testing
ms.assetid: 0e4b4358-80ce-4505-8b06-ef4f30b1d1f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea2301a85411cea8d5ffd6121f4fb4f45d3196eb
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860852"
---
# <a name="testing-the-atl-dhtml-control"></a>Testowanie kontrolki ATL DHTML

Po utworzeniu projektu może kompilowania i testowania kontroli próbki. Zanim to zrobisz, użyj **Widok klas** i **Eksploratora rozwiązań** zbadanie projektu. Elementy projektu są opisane bardziej szczegółowo w [identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md).

## <a name="to-build-and-test-the-atl-dhtml-control"></a>Aby skompilować i przetestować kontrolki ATL DHTML

1. Skompiluj projekt. Z **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

1. Po ukończeniu kompilacji, otwórz **kontener testu**. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do **kontener testu**.

1. W **kontener testu**, z **Edytuj** menu, kliknij przycisk **Wstaw nową kontrolkę**.

1. W **Wstawianie formantu** okna dialogowego Wybierz formant z listy rozwijanej. Należy pamiętać, że jego nazwa jest oparta na krótką nazwę, wskazana w Kreatorze formantu ATL. Kliknij przycisk **OK**.

1. Sprawdź kontrolki. Należy pamiętać, że ma paska przewijania. Zmień rozmiar formantu, aby uaktywnić paska przewijania za pomocą uchwytów sterujących.

1. Przetestuj przyciski formantu. Zmienia kolor tła na kolor wskazywany przez przycisk.

1. Zamknij **kontener testu**.

Następnie spróbuj [modyfikowanie kontrolki DHTML](../atl/modifying-the-atl-dhtml-control.md).

## <a name="see-also"></a>Zobacz też

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)
