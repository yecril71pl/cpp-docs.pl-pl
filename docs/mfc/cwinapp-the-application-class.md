---
title: 'CWinApp: Klasa aplikacji'
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: d9f0d4f5ba6b6b070b23ce98ecda8c7accf44934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241565"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: Klasa aplikacji

Główna klasa aplikacji w MFC hermetyzuje Inicjalizacja, uruchamianie i kończenie działania aplikacji dla systemu operacyjnego Windows. Aplikacja oparta na strukturze musi mieć jeden i tylko jeden obiekt klasę pochodną [CWinApp](../mfc/reference/cwinapp-class.md). Ten obiekt jest konstruowany przed utworzeniem systemu windows.

`CWinApp` jest tworzony na podstawie `CWinThread`, która reprezentuje główny wątek wykonywania dla aplikacji, które mogą mieć jeden lub więcej wątków. W nowszych wersjach MFC `InitInstance`, **Uruchom**, `ExitInstance`, i `OnIdle` elementów członkowskich są faktycznie klasy `CWinThread`. Te funkcje zostały omówione w tym miejscu, tak, jakby były one `CWinApp` członków zamiast tego, ponieważ Dyskusja dotyczy roli obiektu jako obiektu aplikacji, a nie jako wątek główny.

> [!NOTE]
>  Klasa aplikacji stanowi podstawowy wątek wykonywania aplikacji. Korzystając z funkcji Win32 API, można również utworzyć pomocnicze wątki wykonywania. Te wątki, można użyć biblioteki MFC. Aby uzyskać więcej informacji, zobacz [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Podobnie jak dowolnego programu dla systemu operacyjnego Windows ma aplikacji framework `WinMain` funkcji. W ramach aplikacji, jednak nie napiszesz `WinMain`. On dostarczony przez bibliotekę klas i jest wywoływana podczas uruchamiania aplikacji. `WinMain` przeprowadza standardowe usługi, takie jak rejestrowanie klas okien. Następnie wywołuje element członkowski funkcji obiektu aplikacji do zainicjowania i uruchomienia aplikacji. (Możesz dostosować `WinMain` przez zastąpienie `CWinApp` funkcje Członkowskie `WinMain` wywołań.)

Aby zainicjować aplikację, `WinMain` wywołuje obiekt aplikacji `InitApplication` i `InitInstance` funkcji elementów członkowskich. Aby uruchomić pętli komunikatów dla aplikacji, `WinMain` wywołania **Uruchom** funkcja elementu członkowskiego. Po zakończeniu `WinMain` wywołuje obiekt aplikacji `ExitInstance` funkcja elementu członkowskiego.

> [!NOTE]
>  Nazw wyświetlanych w **bold** w tej dokumentacji wskazują elementów dostarczanych przez bibliotekę Microsoft Foundation Class i Visual C++. Nazw wyświetlanych w `monospaced` typu wskazać elementy, które można utworzyć ani zastąpić.

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CWinApp i kreator aplikacji MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)
