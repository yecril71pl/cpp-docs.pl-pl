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
ms.openlocfilehash: 8518e21a9fa6bcf5ac640cff25b17c5028046b06
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447022"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: klasa aplikacji

Główna Klasa aplikacji w MFC hermetyzuje inicjalizację, uruchomienie i zakończenie działania aplikacji dla systemu operacyjnego Windows. Aplikacja skompilowana na platformie musi mieć jeden i tylko jeden obiekt klasy pochodzącej od [CWinApp](../mfc/reference/cwinapp-class.md). Ten obiekt jest konstruowany przed utworzeniem systemu Windows.

`CWinApp` pochodzi od `CWinThread`, który reprezentuje główny wątek wykonywania aplikacji, który może mieć jeden lub więcej wątków. W ostatnich wersjach MFC funkcje elementów członkowskich `InitInstance`, **Run**, `ExitInstance`i `OnIdle` są faktycznie w klasie `CWinThread`. Te funkcje zostały omówione tutaj, tak jakby były `CWinApp` członkami, ponieważ dyskusja dotyczy roli obiektu jako obiektu aplikacji, a nie jako wątku podstawowego.

> [!NOTE]
>  Klasa aplikacji stanowi podstawowy wątek wykonywania aplikacji. Korzystając z funkcji Win32 API, można również utworzyć pomocnicze wątki wykonywania. Te wątki mogą korzystać z biblioteki MFC. Aby uzyskać więcej informacji, zobacz [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Podobnie jak w przypadku każdego programu dla systemu operacyjnego Windows, aplikacja platformy ma funkcję `WinMain`. W aplikacji platformy nie można jednak pisać `WinMain`. Jest on dostarczany przez bibliotekę klas i jest wywoływany podczas uruchamiania aplikacji. `WinMain` wykonuje standardowe usługi, takie jak rejestrowanie klas okien. Następnie wywołuje funkcje członkowskie obiektu aplikacji w celu zainicjowania i uruchomienia aplikacji. (Można dostosować `WinMain`, zastępując `CWinApp` funkcje członkowskie, które `WinMain` wywołania.)

Aby zainicjować aplikację, `WinMain` wywołuje `InitApplication` i `InitInstance` funkcji członkowskich obiektu aplikacji. Aby uruchomić pętlę komunikatów aplikacji, `WinMain` wywołuje funkcję **uruchamiania** elementu członkowskiego. Po zakończeniu `WinMain` wywołuje funkcję członkowską `ExitInstance` obiektu aplikacji.

> [!NOTE]
>  Nazwy wyświetlane **pogrubione** w tej dokumentacji wskazują elementy dostarczone przez Biblioteka MFC i wizualizację C++. Nazwy wyświetlane w typie `monospaced` wskazują elementy, które tworzysz lub przesłonisz.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CWinApp i kreator aplikacji MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Funkcje składowe CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)
