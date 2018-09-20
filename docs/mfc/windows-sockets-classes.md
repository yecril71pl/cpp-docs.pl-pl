---
title: Windows Sockets klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.net
dev_langs:
- C++
helpviewer_keywords:
- sockets classes [MFC]
- Windows Sockets [MFC], classes
ms.assetid: 58b9ab8d-9e44-4db3-8265-e04e713d2e9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 893fa525b04376cde0e96f280c95e6bfd1243946
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439981"
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

