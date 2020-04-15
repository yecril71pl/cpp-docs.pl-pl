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
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354167"
---
# <a name="activation-c"></a>Aktywacja (C++)

W tym artykule wyjaśniono rolę aktywacji w edycji wizualnej elementów OLE. Po użytkownik osadza element OLE w dokumencie kontenera, może być konieczne użycie. W tym celu użytkownik kliknie dwukrotnie element, który aktywuje ten element. Najczęstszą aktywnością aktywacji jest edycja. Wiele bieżących elementów OLE, po aktywacji do edycji, spowodować menu i paski narzędzi w bieżącym oknie ramki, aby zmienić, aby odzwierciedlić te należące do aplikacji serwera, który utworzył element. To zachowanie, znane jako aktywacja w miejscu, umożliwia użytkownikowi edytowanie dowolnego elementu osadzonego w dokumencie złożonym bez opuszczania okna dokumentu kontenera.

Możliwe jest również edytowanie osadzonych elementów OLE w osobnym oknie. Stanie się tak, jeśli kontener lub aplikacja serwera nie obsługuje aktywacji w miejscu. W takim przypadku, gdy użytkownik dwukrotnie kliknie element osadzony, aplikacja serwera jest uruchamiana w osobnym oknie, a element osadzony jest wyświetlany jako własny dokument. Użytkownik edytuje element w tym oknie. Po zakończeniu edycji użytkownik zamyka aplikację serwera i powraca do aplikacji kontenera.

Alternatywnie użytkownik może wybrać "otwórz edycję" ** \<** za pomocą obiektu> polecenie Otwórz w menu **Edycja.** Spowoduje to otwarcie obiektu w osobnym oknie.

> [!NOTE]
> Edytowanie elementów osadzonych w osobnym oknie było zachowaniem standardowym w wersji 1 ole, a niektóre aplikacje OLE mogą obsługiwać tylko ten styl edycji.

Aktywacja w miejscu promuje podejście zorientowane na dokument do tworzenia dokumentów. Użytkownik może traktować dokument złożony jako pojedynczą jednostkę, pracując nad nim bez przełączania między aplikacjami. Jednak aktywacja w miejscu jest używana tylko dla elementów osadzonych, a nie dla elementów połączonych: muszą być edytowane w osobnym oknie. Dzieje się tak, ponieważ połączony element jest faktycznie przechowywany w innym miejscu. Edycja połączonego elementu odbywa się w rzeczywistym kontekście danych, czyli gdzie dane są przechowywane. Edytowanie połączonego elementu w osobnym oknie przypomina użytkownikowi, że dane należą do innego dokumentu.

MFC nie obsługuje zagnieżdżonej aktywacji w miejscu. Jeśli tworzysz aplikację kontenera/serwera, a ten kontener/serwer jest osadzony w innym kontenerze i jest aktywowany w miejscu, nie może w miejscu aktywować obiektów osadzonych w nim.

Co się stanie z elementem osadzonym, gdy użytkownik kliknie dwukrotnie, zależy od zleceń zdefiniowanych dla elementu. Aby uzyskać więcej informacji, zobacz [Aktywacja: Czasowniki](../mfc/activation-verbs.md).

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Containers](../mfc/containers.md)<br/>
[Serwery](../mfc/servers.md)
