---
title: Testowanie aplikacji internetowych
ms.date: 11/04/2016
helpviewer_keywords:
- Web applications [MFC], testing
- debugging Web applications [MFC], testing applications
- testing [MFC], Internet applications
- debugging [MFC], Web applications
- Internet debugging and testing
ms.assetid: ac4c74e3-d4ad-4e19-8f6c-e270de067f01
ms.openlocfilehash: e582fd006a49e672fb21c86b054b8d35f489698f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290946"
---
# <a name="testing-internet-applications"></a>Testowanie aplikacji internetowych

Istnieją pewne unikatowe wyzwania testowania w Internecie, szczególnie w przypadku aplikacji uruchomionych na serwerze sieci Web. Wstępne testowanie będzie prawdopodobnie odbywać się przy użyciu pojedynczego użytkownika klienta nawiązującego połączenie z serwera testowego. To być przydatne podczas debugowania kodu.

Należy również przetestować w rzeczywistych warunkach: za pomocą wielu klientów połączonych za pośrednictwem szybkich połączeń, a także o małej szybkości linii szeregowych, w tym połączeń modemu. Może być trudne do symulowania rzeczywistych warunków, ale warto bez obaw wydatków czasu projektowania możliwych scenariuszy i ich wykonania. Jeśli to możliwe również można użyć narzędzi, czy pojemność i testowania obciążeniowego. Niektóre klasy błędów, takie jak błędy czasu są trudne do znalezienia i do odtworzenia.

Jednym z wyzwań programowania Internet jest jego widoczność. Wiele dostępów do swojej witryny może spowalniać działanie serwera. Chcesz, aby serwer do upadaj łagodnie. Chcesz uniemożliwić wszystko, co może stanowić destrukcyjne na komputerze użytkownika, jeśli aplikacja nie powiedzie się (np. uszkodzenie danych podczas zapisywania w rejestrze lub podczas zapisywania plików cookie na komputerze klienckim).

## <a name="see-also"></a>Zobacz także

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)
