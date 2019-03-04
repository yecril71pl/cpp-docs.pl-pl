---
title: Przetwarzanie pętli bezczynności
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 0d0e3fcba9ce447ec359958fc5ed59c6d596dd7a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287144"
---
# <a name="idle-loop-processing"></a>Przetwarzanie pętli bezczynności

Wiele aplikacji przetwarzania długich "w tle." Czasami zagadnienia związane z wydajnością dyktowania, za pomocą wielowątkowości dla tych prac. Wątki obejmują rozwoju dodatkowe obciążenie, więc nie są zalecane dla prostych zadań, takich jak praca czas bezczynności (%), który wykonuje MFC, w [OnIdle](../mfc/reference/cwinthread-class.md#onidle) funkcji. Ten artykuł koncentruje się na przetwarzanie w stanie bezczynności. Aby uzyskać więcej informacji o wielowątkowości, zobacz [tematy o wielowątkowości](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Niektóre rodzaje przetwarzania w tle odpowiednio są wykonywane podczas interwałów, które użytkownik nie jest w przeciwnym razie interakcji z aplikacją. W aplikacji dla systemu operacyjnego Microsoft Windows aplikacja może wykonywać przetwarzanie w czasie bezczynności (%), dzieląc długotrwałym procesem na wiele małych fragmentów. Po przetworzeniu każdego fragmentu, aplikacja przekazuje sterowanie wykonywania za pomocą Windows [PeekMessage](/windows/desktop/api/winuser/nf-winuser-peekmessagea) pętli.

W tym artykule opisano bezczynności przetwarzania w aplikacji na dwa sposoby:

- Za pomocą **PeekMessage** w MFC główna pętla wiadomości.

- Osadzanie innego **PeekMessage** pętli, gdzie indziej w aplikacji.

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage w pętli komunikatów MFC

W aplikacji opracowanych przez MFC, głównym komunikat pętli w `CWinThread` klasa zawiera pętlę komunikatów, który wywołuje [PeekMessage](/windows/desktop/api/winuser/nf-winuser-peekmessagea) interfejsu API systemu Win32. Pętla wywołania `OnIdle` funkcji składowej typu `CWinThread` między komunikatami. Aplikacja może przetwarzać komunikatów w tym okresie bezczynności przez zastąpienie `OnIdle` funkcji.

> [!NOTE]
>  `Run`, `OnIdle`, i niektórych innych funkcji Członkowskich są teraz elementów członkowskich klasy `CWinThread` , a nie klasy `CWinApp`. `CWinApp` jest tworzony na podstawie `CWinThread`.

Aby uzyskać więcej informacji na temat wykonywania przetwarzanie w stanie bezczynności, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w *odwołanie MFC*.

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage w innych miejscach w aplikacji

Inna metoda do wykonywania w stanie bezczynności, przetwarzanie w aplikacji polega na tym, osadzanie pętlę komunikatów w jednym z funkcji. Ta pętla komunikatów jest bardzo podobny do MFC główna pętla wiadomości, w [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Oznacza to pętlę w aplikacji utworzonych za pomocą MFC, należy wykonać wiele tych samych funkcji jako główna pętla wiadomości. Poniższy fragment kodu przedstawia pisanie pętli komunikatów, która jest zgodna z MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Ten kod, który jest osadzony w przypadku funkcji w pętli tak długo, jak jest przetwarzanie w stanie bezczynności celu. W tym pętli, zagnieżdżonej pętli wielokrotnie wywołuje `PeekMessage`. Tak długo, jak to wywołanie zwraca wartość różną od zera, pętli wywołuje `CWinThread::PumpMessage` do wykonywania tłumaczeń normalny komunikat dotyczący i wysyłki. Mimo że `PumpMessage` jest nieudokumentowane, można zbadać jego kod źródłowy w pliku ThrdCore.Cpp w katalogu \atlmfc\src\mfc instalację programu Visual C++.

Po zakończeniu wewnętrzną pętlę zewnętrzna pętla wykonuje przetwarzanie w stanie bezczynności za pomocą jednego lub wielu wywołań do `OnIdle`. Pierwsze wywołanie jest na potrzeby biblioteki MFC. Można wprowadzić dodatkowych połączeń do `OnIdle` do pracy tła.

Aby uzyskać więcej informacji na temat wykonywania przetwarzanie w stanie bezczynności, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w odwołanie do biblioteki MFC.

## <a name="see-also"></a>Zobacz także

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
