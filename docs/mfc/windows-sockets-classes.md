---
title: Klasy Windows Sockets
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 18537c0de09185c8cd219e3d17ef8bb297e1d711
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433608"
---
# <a name="windows-sockets-classes"></a>Klasy Windows Sockets

Windows Sockets umożliwiają sieci niezależne od protokołu do komunikowania się między dwoma komputerami. Gniazda te mogą być synchroniczne (program czeka, aż odbywa się komunikacja) lub asynchroniczną (program będzie nadal działać podczas komunikacji dzieje się).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Hermetyzuje interfejsu API Windows Sockets w w otoce alokowania elastycznego.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Wyższy poziom abstrakcji pochodną `CAsyncSocket`. Działa ona synchronicznie.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Udostępnia `CFile` interfejs do gniazda Windows.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

