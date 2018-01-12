---
title: "Przetwarzanie pętli bezczynności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: baabba60ffaf886b7a34acfbff5b923a4495fa1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="idle-loop-processing"></a>Przetwarzanie pętli bezczynności
Wiele aplikacji przetwarzania długich "w"tle. Zagadnienia dotyczące wydajności dyktowania czasami przy użyciu wielowątkowość dla tych działań. Wątków obejmują programowanie dodatkowe obciążenie, więc nie są zalecane do prostych zadań, takich jak pracy czas bezczynności, który wykonuje MFC w [OnIdle](../mfc/reference/cwinthread-class.md#onidle) funkcji. Ten artykuł skupia się na przetwarzanie w stanie bezczynności. Aby uzyskać więcej informacji o wielowątkowości, zobacz [wielowątkowość tematy](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Niektóre rodzaje przetwarzania w tle są odpowiednio wykonywane podczas interwałów, które użytkownik nie jest w przeciwnym razie interakcji z aplikacją. W aplikacji utworzonych dla systemu operacyjnego Microsoft Windows aplikacja może wykonywać przetwarzania czas bezczynności, Podziel proces długotrwały na małe fragmenty wiele. Po przetworzeniu każdego fragmentu aplikacji daje Kontrola wykonywania do systemu Windows przy użyciu [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) pętli.  
  
 W tym artykule opisano dwa sposoby przetwarzania w aplikacji w stanie bezczynności:  
  
-   Przy użyciu **PeekMessage** w pętli komunikatów głównego MFC.  
  
-   Osadzanie innego **PeekMessage** pętli w innym miejscu w aplikacji.  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage w pętli komunikatów MFC  
 W aplikacji opracowanych za pomocą MFC, głównego komunikat pętli w `CWinThread` klasa zawiera pętli komunikatów, który wywołuje [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) interfejsu API systemu Win32. Pętla wywołania `OnIdle` funkcji członkowskiej klasy `CWinThread` między wiadomości. Aplikacja może przetwarzać komunikatów w tym okresie bezczynności przez zastąpienie `OnIdle` funkcji.  
  
> [!NOTE]
>  **Uruchom**, `OnIdle`, i niektórych innych funkcji elementów członkowskich są członkami klasy `CWinThread` zamiast klasy `CWinApp`. `CWinApp`jest pochodną `CWinThread`.  
  
 Aby uzyskać więcej informacji o wydajności przetwarzanie w stanie bezczynności, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w *odwołania MFC*.  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage w innym miejscu w aplikacji  
 Inna metoda wykonywania bezczynności przetwarzania w aplikacji polega na osadzanie pętli komunikatów w jednym z funkcji. Pętla wiadomości jest bardzo podobny do pętli komunikatów głównego MFC, znalezione w [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Oznacza to, że w pętli w aplikacji opracowanych za pomocą MFC musi wykonywać wiele funkcji pętli komunikatów głównego. Poniższy fragment kodu przedstawia pisanie pętli komunikatów, który jest zgodny z MFC:  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]  
  
 Ten kod osadzone w przypadku funkcji pętli tak długo, jak jest przetwarzanie w stanie bezczynności zrobić. W tym pętli wielokrotnie wywołuje zagnieżdżonych pętli **PeekMessage**. Tak długo, jak tego wywołania zwraca wartość niezerową, wywołuje pętli `CWinThread::PumpMessage` przeprowadzić translacji normalnego komunikatu i wysyłania. Mimo że `PumpMessage` jest nieudokumentowanej, można sprawdzić jego kod źródłowy w pliku ThrdCore.Cpp w katalogu \atlmfc\src\mfc instalację programu Visual C++.  
  
 Raz zakończenia pętli wewnętrznej zewnętrzne pętli wykonuje przetwarzanie w stanie bezczynności z co najmniej jednego wywołania `OnIdle`. Pierwsze wywołanie służy do celów MFC. Możesz wprowadzić dodatkowe wywołania `OnIdle` do pracy tła.  
  
 Aby uzyskać więcej informacji o wydajności przetwarzanie w stanie bezczynności, zobacz [OnIdle](../mfc/reference/cwinthread-class.md#onidle) w odwołaniu biblioteki MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)

