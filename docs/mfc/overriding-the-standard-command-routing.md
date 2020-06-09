---
title: Zastępowanie standardowego routingu poleceń
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 680b185f8d68a834862bc0fe14bf6e7984effd65
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617725"
---
# <a name="overriding-the-standard-command-routing"></a>Zastępowanie standardowego routingu poleceń

W rzadkich przypadkach, gdy konieczne jest zaimplementowanie niektórych różnic w standardowym routingu struktury, można go zastąpić. Pomysłem jest zmiana routingu w jednej lub większej liczbie klas przez zastąpienie `OnCmdMsg` tych klas. Zrób tak:

- W klasie, która przerywa kolejność do przekazania do niedomyślnego obiektu.

- W nowym obiekcie niedomyślnym lub w elemencie docelowym polecenia może być w nim przekazywać polecenia do.

Jeśli wstawisz nowy obiekt do routingu, jego Klasa musi być klasą docelową polecenia. W zastępujące wersje programu `OnCmdMsg` Pamiętaj, aby wywoływać zastępowaną wersję. Zobacz [OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg) funkcja członkowska klasy `CCmdTarget` w *Kompendium MFC* i wersje w takich klasach jak `CView` i w podanym `CDocument` kodzie źródłowym dla przykładów.

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje program obsługi](how-the-framework-calls-a-handler.md)
