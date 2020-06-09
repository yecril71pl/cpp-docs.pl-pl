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
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619182"
---
# <a name="activation-c"></a>Aktywacja (C++)

W tym artykule wyjaśniono rolę aktywacji podczas edycji wizualizacji elementów OLE. Gdy użytkownik osadzony element OLE w dokumencie kontenera, może być konieczne jego użycie. W tym celu użytkownik kliknie dwukrotnie element, który aktywuje ten element. Jest to Najczęstsze działanie na potrzeby aktywacji. Wiele bieżących elementów OLE, gdy są aktywowane do edycji, powoduje, że menu i paski narzędzi w oknie bieżące klatki zmieniają się w celu odzwierciedlenia tych należących do aplikacji serwerowej, która utworzyła element. Takie zachowanie, znane jako aktywacja w miejscu, umożliwia użytkownikowi edytowanie wszystkich elementów osadzonych w dokumencie złożonym bez opuszczania okna dokumentu kontenera.

Istnieje również możliwość edytowania osadzonych elementów OLE w osobnym oknie. Dzieje się tak, jeśli aplikacja kontenera lub serwera nie obsługuje aktywacji w miejscu. W takim przypadku, gdy użytkownik kliknie dwukrotnie element osadzony, aplikacja serwera zostanie uruchomiona w osobnym oknie, a element osadzony zostanie wyświetlony jako własny dokument. Użytkownik edytuje element w tym oknie. Po zakończeniu edycji użytkownik zamyka aplikację serwera i wraca do aplikacji kontenera.

Alternatywnie użytkownik może wybrać opcję "Otwórz edycję" przy użyciu polecenia ** \<object> Otwórz** w menu **Edycja** . Spowoduje to otwarcie obiektu w osobnym oknie.

> [!NOTE]
> Edytowanie osadzonych elementów w osobnym oknie było zachowaniem standardowym w wersji 1 OLE, a niektóre aplikacje OLE mogą obsługiwać tylko ten styl edycji.

Aktywacja w miejscu promuje podejście skoncentrowane na dokumentach do tworzenia dokumentów. Użytkownik może traktować złożone dokumenty jako pojedynczą jednostkę, pracując nad nią bez przełączania się między aplikacjami. Jednak aktywacja w miejscu jest używana tylko dla elementów osadzonych, a nie dla elementów połączonych: muszą one być edytowane w osobnym oknie. Wynika to z faktu, że połączony element jest faktycznie przechowywany w innym miejscu. Edytowanie połączonego elementu odbywa się w bieżącym kontekście danych, czyli w przypadku przechowywania danych. Edytowanie połączonego elementu w osobnym oknie przypomina użytkownika, że dane należą do innego dokumentu.

MFC nie obsługuje aktywacji zagnieżdżonej w miejscu. W przypadku kompilowania aplikacji kontenera/serwera, gdy kontener/serwer jest osadzony w innym kontenerze i aktywowanym w miejscu, nie można aktywować obiektów w miejscu.

Co się stanie z elementem osadzonym po dwukrotnym kliknięciu go przez użytkownika, zależy od czasowników zdefiniowanych dla tego elementu. Aby uzyskać więcej informacji, zobacz [Aktywacja: czasowniki](activation-verbs.md).

## <a name="see-also"></a>Zobacz też

[OLE](ole-in-mfc.md)<br/>
[Containers](containers.md)<br/>
[Serwery](servers.md)
