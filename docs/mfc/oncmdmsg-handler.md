---
title: Program obsługi OnCmdMsg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnCmdMsg
dev_langs:
- C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6691e4935d46b32bc8f433823888bb7f53a36890
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398836"
---
# <a name="oncmdmsg-handler"></a>Program obsługi OnCmdMsg

Aby umożliwić routing poleceń, wywołuje każdym obiekcie docelowym polecenia `OnCmdMsg` funkcji składowej typu dalej elemencie docelowym polecenia w sekwencji. Polecenie jest przeznaczony dla użycia `OnCmdMsg` do określenia, czy ich obsługi polecenia i przekazać go do innego elemencie docelowym polecenia, jeśli nie można go obsłużyć.

Każda klasa w elemencie docelowym polecenia mogą zastępować `OnCmdMsg` funkcja elementu członkowskiego. Zastąpienia umożliwiają każdego polecenia trasy klasy do określonego celu dalej. Okno ramowe na przykład zawsze kieruje polecenia do jego bieżące okno podrzędne lub widok, jak pokazano w tabeli [trasy poleceń standardowych](../mfc/command-routing.md).

Wartość domyślna `CCmdTarget` implementacji `OnCmdMsg` używa mapę komunikatów w elemencie docelowym polecenia klasy do wyszukiwania dla funkcji programu obsługi dla każdego komunikatu polecenia odbierze — w taki sam sposób, że standardowe komunikaty są przeszukiwane. Jeśli znajdzie dopasowanie, wywołuje metodę programu obsługi. Wyszukiwanie w mapie komunikatów zostało wyjaśnione w [jak Framework wyszukuje mapy komunikatów](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje programy obsługi](../mfc/how-the-framework-calls-a-handler.md)

