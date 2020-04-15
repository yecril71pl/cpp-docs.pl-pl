---
title: 'CWinApp: klasa aplikacji'
ms.date: 11/04/2016
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
ms.openlocfilehash: 007a4e53fd9b3eae612947cd76ee352776572d4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373524"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: klasa aplikacji

Główna klasa aplikacji w MFC hermetyzuje inicjowania, uruchamiania i zakończenia aplikacji dla systemu operacyjnego Windows. Aplikacja zbudowana na platformie musi mieć jeden i tylko jeden obiekt klasy pochodzące z [CWinApp](../mfc/reference/cwinapp-class.md). Ten obiekt jest konstruowany przed utworzeniem okien.

`CWinApp`pochodzi z `CWinThread`, który reprezentuje główny wątek wykonywania dla aplikacji, który może mieć jeden lub więcej wątków. W ostatnich wersjach MFC `InitInstance`, `ExitInstance` `OnIdle` **Uruchom**, i funkcje członkowskie są rzeczywiście w klasie `CWinThread`. Te funkcje są omawiane `CWinApp` w tym miejscu tak, jakby były członkami zamiast, ponieważ dyskusja dotyczy roli obiektu jako obiektu aplikacji, a nie jako wątek podstawowy.

> [!NOTE]
> Klasa aplikacji stanowi podstawowy wątek wykonywania aplikacji. Za pomocą funkcji interfejsu API Win32, można również utworzyć pomocnicze wątki wykonywania. Te wątki można użyć biblioteki MFC. Aby uzyskać więcej informacji, zobacz [Wielowątkowe](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Jak każdy program dla systemu operacyjnego Windows, aplikacja ramowa `WinMain` ma funkcję. W aplikacji ramowej nie piszesz `WinMain`jednak . Jest dostarczany przez bibliotekę klas i jest wywoływana podczas uruchamiania aplikacji. `WinMain`wykonuje standardowe usługi, takie jak rejestrowanie klas okien. Następnie wywołuje funkcje członkowskie obiektu aplikacji, aby zainicjować i uruchomić aplikację. (Można dostosować, `WinMain` zastępując funkcje `CWinApp` członkowskie, `WinMain` które wywołuje.)

Aby zainicjować aplikację, `WinMain` wywołuje funkcje `InitApplication` `InitInstance` obiektu aplikacji i elementu członkowskiego. Aby uruchomić pętlę komunikatów `WinMain` aplikacji, wywołuje funkcję **uruchom** element członkowski. Po zakończeniu `WinMain` wywołuje funkcję `ExitInstance` elementu członkowskiego obiektu aplikacji.

> [!NOTE]
> Nazwy wyświetlane **pogrubioną czcionką** w tej dokumentacji wskazują elementy dostarczone przez bibliotekę klas Microsoft Foundation i visual C++. Nazwy wyświetlane `monospaced` w typie wskazują elementy, które tworzysz lub zastępujesz.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CWinApp i kreator aplikacji MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)
