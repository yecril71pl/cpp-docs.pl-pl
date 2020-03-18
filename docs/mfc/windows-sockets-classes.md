---
title: Klasy Windows Sockets
ms.date: 11/04/2016
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
ms.openlocfilehash: 3f1b7b2b6674b4a5f8c8f7bff6c5fa239715f459
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445982"
---
# <a name="windows-sockets-classes"></a>Klasy Windows Sockets

Windows Sockets zapewniają niezależny od protokołu sieciowego sposób komunikacji między dwoma komputerami. Te gniazda można synchronicznie (program czeka na zakończenie komunikacji) lub asynchronicznie (program kontynuuje działanie w trakcie komunikacji).

[CAsyncSocket](../mfc/reference/casyncsocket-class.md)<br/>
Hermetyzuje interfejs API Windows Sockets w elastycznej otoki.

[CSocket](../mfc/reference/csocket-class.md)<br/>
Streszczenie wyższego poziomu pochodzące z `CAsyncSocket`. Działa synchronicznie.

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Udostępnia interfejs `CFile` do gniazda systemu Windows.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
