---
title: Klasy Windows Sockets
ms.date: 11/04/2016
f1_keywords:
- vc.classes.net
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 4abdd8f8fbfc115b5014ffd0b3a37df357852b16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371805"
---
# <a name="windows-sockets-classes"></a>Klasy Windows Sockets

Windows Sockets umożliwiają sieci niezależne od protokołu do komunikowania się między dwoma komputerami. Gniazda te mogą być synchroniczne (program czeka, aż odbywa się komunikacja) lub asynchroniczną (program będzie nadal działać podczas komunikacji dzieje się).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Hermetyzuje interfejsu API Windows Sockets w w otoce alokowania elastycznego.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Wyższy poziom abstrakcji pochodną `CAsyncSocket`. Działa ona synchronicznie.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Udostępnia `CFile` interfejs do gniazda Windows.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
