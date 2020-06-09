---
title: Program obsługi OnCmdMsg
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 5114fe53a5bac345eb6a55fb6c371f7bc1f698ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624026"
---
# <a name="oncmdmsg-handler"></a>Program obsługi OnCmdMsg

Aby wykonać routing poleceń, każdy element docelowy polecenia wywołuje `OnCmdMsg` funkcję elementu członkowskiego następnego polecenia docelowego w sekwencji. Elementy docelowe polecenia używane `OnCmdMsg` do określenia, czy mogą obsługiwać polecenie i kierować je do innego obiektu docelowego polecenia, jeśli nie mogą go obsłużyć.

Każda Klasa Target polecenia może przesłonić `OnCmdMsg` funkcję członkowską. Zastąpienia umożliwiają każdej klasie kierowanie poleceń do określonego następnego celu. Okno ramek, na przykład, zawsze kieruje polecenia do jego bieżącego okna podrzędnego lub widoku, jak pokazano w [standardowym marszrucie polecenia](command-routing.md)tabeli.

Domyślna `CCmdTarget` Implementacja programu `OnCmdMsg` używa mapy komunikatów klasy Target polecenia, aby wyszukać funkcję procedury obsługi dla każdego komunikatu polecenia, który odbiera, w taki sam sposób, w jaki przeszukiwane są standardowe komunikaty. Jeśli znajdzie dopasowanie, wywoła procedurę obsługi. Wyszukiwanie w mapie komunikatów zostało wyjaśnione w [sposób, w jaki struktura przeszukuje mapy komunikatów](how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Zobacz też

[Jak struktura wywołuje program obsługi](how-the-framework-calls-a-handler.md)
