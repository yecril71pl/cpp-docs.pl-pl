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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303823"
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
