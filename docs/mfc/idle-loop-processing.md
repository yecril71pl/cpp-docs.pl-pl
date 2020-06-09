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
ms.openlocfilehash: 74ca89d91cf4e60b09a063551b526f177caed161
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624517"
---
# <a name="idle-loop-processing"></a>Przetwarzanie pętli bezczynności

Wiele aplikacji wykonuje długotrwałe przetwarzanie "w tle". Czasami zagadnienia dotyczące wydajności wymuszają używanie wielowątkowości dla takich zadań. Wątki obejmują dodatkowe nakłady programistyczne, więc nie są zalecane w przypadku prostych zadań, takich jak praca w czasie bezczynności, którą MFC wykonuje w funkcji [OnIdle](reference/cwinthread-class.md#onidle) . Ten artykuł koncentruje się na przetwarzaniu bezczynności. Aby uzyskać więcej informacji na temat wielowątkowości, zobacz [temat wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Niektóre rodzaje przetwarzania w tle są odpowiednio wykonywane podczas interwałów, w których użytkownik nie współdziała z aplikacją. W aplikacji opracowanej dla systemu operacyjnego Microsoft Windows aplikacja może przetwarzać czas bezczynności, dzieląc długotrwały proces na wiele małych fragmentów. Po przetworzeniu każdego fragmentu aplikacja uzyskuje Sterowanie wykonywaniem do systemu Windows przy użyciu pętli [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) .

W tym artykule objaśniono dwa sposoby bezczynnościowego przetwarzania w aplikacji:

- Używanie **PeekMessage** w pętli głównej komunikatu MFC.

- Osadzenie innej pętli **PeekMessage** w innym miejscu w aplikacji.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage w pętli komunikatów MFC

W aplikacji opracowanej przy użyciu MFC, główna pętla komunikatów w `CWinThread` klasie zawiera pętlę komunikatów, która wywołuje Win32 API [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) . Ta pętla również wywołuje `OnIdle` funkcję członkowską `CWinThread` między komunikatami. Aplikacja może przetwarzać komunikaty w tym czasie bezczynności, zastępując `OnIdle` funkcję.

> [!NOTE]
> `Run`, `OnIdle` , i niektóre inne funkcje członkowskie są teraz członkami klasy, a `CWinThread` nie z klasą `CWinApp` . `CWinApp`pochodzi od `CWinThread` .

Aby uzyskać więcej informacji na temat wykonywania bezczynnego przetwarzania, zobacz [OnIdle](reference/cwinthread-class.md#onidle) w *dokumentacji MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage w innym miejscu aplikacji

Inna metoda wykonywania przetwarzania bezczynnego w aplikacji polega na osadzeniu pętli komunikatów w jednej z funkcji. Ta pętla komunikatów jest bardzo podobna do głównej pętli komunikatów MFC, którą można znaleźć w [CWinThread:: Run](reference/cwinthread-class.md#run). Oznacza to, że pętla w aplikacji opracowanej przy użyciu MFC musi wykonywać wiele z tych samych funkcji co główna pętla komunikatów. Poniższy fragment kodu ilustruje zapisywanie pętli komunikatów, która jest zgodna z MFC:

[!code-cpp[NVC_MFCDocView#8](codesnippet/cpp/idle-loop-processing_1.cpp)]

Ten kod, osadzony w funkcji, pętle pod warunkiem, że przetwarzanie jest bezczynne. W tej pętli zagnieżdżona pętla cyklicznie wywołuje `PeekMessage` . Tak długo, jak to wywołanie zwraca wartość różną od zera, wywołuje pętlę, `CWinThread::PumpMessage` Aby wykonać normalne tłumaczenie i wysyłanie komunikatów. Chociaż `PumpMessage` jest nieudokumentowany, można przeanalizować swój kod źródłowy w pliku ThrdCore. cpp w katalogu \atlmfc\src\mfc instalacji Visual C++.

Gdy wewnętrzna pętla zostanie zakończona, pętla zewnętrzna wykonuje przetwarzanie bezczynne z co najmniej jednym wywołaniem do `OnIdle` . Pierwsze wywołanie jest przeznaczone dla celów MFC. Możesz wykonać dodatkowe wywołania, aby `OnIdle` wykonać własne działania w tle.

Aby uzyskać więcej informacji o wykonywaniu bezczynności, zobacz [OnIdle](reference/cwinthread-class.md#onidle) w dokumentacji biblioteki MFC.

## <a name="see-also"></a>Zobacz też

[Tematy ogólne dotyczące MFC](general-mfc-topics.md)
