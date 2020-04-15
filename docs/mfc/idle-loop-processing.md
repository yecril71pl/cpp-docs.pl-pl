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
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376011"
---
# <a name="idle-loop-processing"></a>Przetwarzanie pętli bezczynności

Wiele aplikacji wykonuje długotrwałe przetwarzanie "w tle". Czasami zagadnienia dotyczące wydajności dyktują użycie wielowątkowej pracy dla takiej pracy. Wątki obejmują dodatkowe obciążenie rozwoju, więc nie są one zalecane dla prostych zadań, takich jak praca w czasie bezczynności, który MFC wykonuje w [OnIdle](../mfc/reference/cwinthread-class.md#onidle) funkcji. W tym artykule koncentruje się na bezczynności przetwarzania. Aby uzyskać więcej informacji na temat wielowątkowych, zobacz [Tematy wielowątkowe](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Niektóre rodzaje przetwarzania w tle są odpowiednio wykonywane w odstępach czasu, że użytkownik nie jest w inny sposób interakcji z aplikacją. W aplikacji opracowanej dla systemu operacyjnego Microsoft Windows aplikacja może wykonywać przetwarzanie w czasie bezczynnym, dzieląc długi proces na wiele małych fragmentów. Po przetworzeniu każdego fragmentu aplikacja daje kontrolę wykonania systemu Windows przy użyciu pętli [PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew)

W tym artykule wyjaśniono dwa sposoby bezczynnego przetwarzania w aplikacji:

- Za pomocą **PeekMessage** w głównej pętli komunikatów MFC.

- Osadzanie innej pętli **PeekMessage** w innym miejscu w aplikacji.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>Wgląd w pętlę komunikatów MFC

W aplikacji opracowanej za pomocą MFC `CWinThread` głównej pętli komunikatów w klasie zawiera pętlę komunikatów, która wywołuje interfejs API [Win32 PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew) Ta pętla `OnIdle` wywołuje również `CWinThread` funkcję elementu członkowskiego między wiadomościami. Aplikacja może przetwarzać wiadomości w tym czasie bezczynność, zastępując `OnIdle` funkcję.

> [!NOTE]
> `Run`, `OnIdle`a niektóre inne funkcje członkowskie `CWinThread` są teraz `CWinApp`członkami klasy, a nie klasy . `CWinApp`pochodzi z `CWinThread`.

Aby uzyskać więcej informacji na temat wykonywania bezczynnego przetwarzania, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w *odwołaniu MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>Zaglądaj w inne miejsce w twojej aplikacji

Inną metodą wykonywania bezczynnego przetwarzania w aplikacji polega osadzanie pętli komunikatów w jednej z funkcji. Ta pętla komunikatów jest bardzo podobna do głównej pętli komunikatów MFC, znalezionej w [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Oznacza to, że taka pętla w aplikacji opracowanej za pomocą MFC musi wykonywać wiele takich samych funkcji, jak główna pętla wiadomości. Poniższy fragment kodu demonstruje pisanie pętli komunikatów, która jest zgodna z MFC:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Ten kod, osadzone w funkcji, pętli tak długo, jak istnieje bezczynne przetwarzania do zrobienia. W tej pętli zagnieżdżona pętla wielokrotnie wywołuje `PeekMessage`. Tak długo, jak to wywołanie zwraca wartość `CWinThread::PumpMessage` niezerową, wywołania pętli do wykonywania normalnego tłumaczenia wiadomości i wysyłania. Mimo `PumpMessage` że jest nieudokumentowany, można sprawdzić jego kod źródłowy w pliku ThrdCore.Cpp w katalogu \atlmfc\src\mfc instalacji programu Visual C++.

Po zakończeniu pętli wewnętrznej zewnętrzna pętla wykonuje bezczynne przetwarzanie `OnIdle`za pomocą jednego lub więcej wywołań . Pierwsze wezwanie jest dla celów MFC. Możesz wykonywać dodatkowe `OnIdle` połączenia, aby wykonać własną pracę w tle.

Aby uzyskać więcej informacji na temat wykonywania bezczynnego przetwarzania, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w odwołaniu do biblioteki MFC.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)
