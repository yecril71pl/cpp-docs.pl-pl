---
title: Testowanie aplikacji internetowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 518fbe754b676798c6d2acc2a3e26ea1d3e3d4ac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444168"
---
# <a name="testing-internet-applications"></a>Testowanie aplikacji internetowych

Istnieją pewne unikatowe wyzwania testowania w Internecie, szczególnie w przypadku aplikacji uruchomionych na serwerze sieci Web. Wstępne testowanie będzie prawdopodobnie odbywać się przy użyciu pojedynczego użytkownika klienta nawiązującego połączenie z serwera testowego. To być przydatne podczas debugowania kodu.

Należy również przetestować w rzeczywistych warunkach: za pomocą wielu klientów połączonych za pośrednictwem szybkich połączeń, a także o małej szybkości linii szeregowych, w tym połączeń modemu. Może być trudne do symulowania rzeczywistych warunków, ale warto bez obaw wydatków czasu projektowania możliwych scenariuszy i ich wykonania. Jeśli to możliwe również można użyć narzędzi, czy pojemność i testowania obciążeniowego. Niektóre klasy błędów, takie jak błędy czasu są trudne do znalezienia i do odtworzenia.

Jednym z wyzwań programowania Internet jest jego widoczność. Wiele dostępów do swojej witryny może spowalniać działanie serwera. Chcesz, aby serwer do upadaj łagodnie. Chcesz uniemożliwić wszystko, co może stanowić destrukcyjne na komputerze użytkownika, jeśli aplikacja nie powiedzie się (np. uszkodzenie danych podczas zapisywania w rejestrze lub podczas zapisywania plików cookie na komputerze klienckim).

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

