---
title: Aktywacja (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: ba3c705227e6ca189527d29d4f3ae0f21c71eb72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493512"
---
# <a name="activation-c"></a>Aktywacja (C++)

W tym artykule opisano rolę aktywacji w wizualne edytowanie elementów OLE. Po użytkownik ma osadzony element OLE w dokumencie kontenera, może być konieczne można użyć. Aby to zrobić, użytkownik kliknie dwukrotnie elementu, który aktywuje tego elementu. Edytuje najczęściej działania w celu aktywacji. Wiele bieżących elementów OLE, gdy aktywowany do edycji, spowodować menu i pasków zadań w bieżącym oknie ramki, aby zmienić odzwierciedlają poglądy należące do aplikacji serwera, który utworzył element. To zachowanie, znane jako aktywacji w miejscu, umożliwia użytkownikowi edytowanie dowolnego elementu osadzonego wewnątrz złożonego dokumentu bez opuszczania okno dokumentu kontenera.

Jest również możliwe edytowanie elementy osadzone OLE w osobnym oknie. Dzieje się tak, jeśli aplikacja kontenera lub serwer nie obsługuje aktywacji w miejscu. W tym przypadku, gdy użytkownik kliknie dwukrotnie element osadzony, aplikacja serwera jest uruchamiana w oddzielnym oknie i osadzonego elementu jest wyświetlany jako swój własny dokument. Użytkownik edytuje element w tym oknie. Po zakończeniu edycji użytkownik zamknie aplikację serwera i zwraca do aplikacji kontenera.

Jako alternatywę, użytkownik może wybrać "Otwórz do edycji" za pomocą  **\<obiektu > Otwórz** polecenie **Edytuj** menu. Spowoduje to otwarcie obiekt w osobnym oknie.

> [!NOTE]
>  Edytowanie elementów osadzonych w osobnym oknie była standardowe zachowanie w wersji 1, OLE i niektóre aplikacje OLE może obsługiwać tylko ten styl edycji.

Aktywacja w miejscu promuje zorientowany podejście do tworzenia dokumentów. Użytkownik może traktować złożonego dokumentu jako pojedynczą jednostkę, pracujemy nad tym, bez przełączania się między aplikacjami. Jednak Aktywacja w miejscu jest używana tylko w przypadku elementów osadzonych, nie dla połączonych elementów: musi być edytowany w osobnym oknie. Jest to spowodowane połączony element rzeczywiście jest przechowywana w innym miejscu. Edytowanie połączony element odbywa się w kontekście rzeczywistych danych, oznacza to, gdzie dane są przechowywane. Edytowanie połączony element w osobnym oknie przypomina o tym użytkownika, którego dane należą do innego dokumentu.

MFC nie obsługuje zagnieżdżonych aktywacji w miejscu. Jeśli tworzysz aplikację kontenera/serwera i że kontenera/serwera jest osadzony w innym kontenerze i aktywowany w miejscu jej nie w miejscu należy aktywować obiekty osadzone wewnątrz niego.

Co się dzieje z osadzonego elementu, gdy użytkownik kliknie dwukrotnie zależy od zleceń zdefiniowanych dla elementu. Aby uzyskać informacje, zobacz [Aktywacja: zlecenia](../mfc/activation-verbs.md).

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Kontenery](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)

