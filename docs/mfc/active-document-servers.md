---
title: Serwery dokumentów aktywnych
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619142"
---
# <a name="active-document-servers"></a>Serwery dokumentów aktywnych

Serwery dokumentów aktywnych, takie jak Word, Excel lub dokumenty hosta programu PowerPoint dla innych typów aplikacji o nazwie Active Documents. W przeciwieństwie do obiektów OLE Embedded (które są po prostu wyświetlane na stronie innego dokumentu), aktywne dokumenty zapewniają pełny interfejs i kompletną funkcjonalność aplikacji serwera, która je tworzy. Użytkownicy mogą tworzyć dokumenty przy użyciu pełnych możliwości ich ulubionych aplikacji (jeśli są włączone, jeśli są aktywnymi dokumentami), ale mogą traktować projekt wynikający z jednej jednostki.

Aktywne dokumenty mogą mieć więcej niż jedną stronę i są zawsze aktywne. Formanty Active Documents — część interfejsu użytkownika, scalanie ich menu z menu **plik** i **Pomoc** kontenera. Zajmują cały obszar edycji kontenera i kontrolują widoki i układ strony drukarki (marginesy, stopki itp.).

MFC implementuje serwery dokumentów aktywnych przy użyciu interfejsów dokumentów/widoków, map wysyłania poleceń, drukowania, zarządzania menu i zarządzania rejestrem. Szczególne wymagania programistyczne omówiono w [dokumentach aktywnych](active-documents.md).

MFC obsługuje aktywne dokumenty z klasą [CDocObjectServer](reference/cdocobjectserver-class.md) , pochodną od [CCmdTarget](reference/ccmdtarget-class.md)i [CDocObjectServerItem](reference/cdocobjectserveritem-class.md), uzyskaną z [COleServerItem](reference/coleserveritem-class.md). MFC obsługuje kontenery dokumentów aktywnych z klasą [metody COleDocObjectItem](reference/coledocobjectitem-class.md) , pochodzących od [COleClientItem](reference/coleclientitem-class.md).

`CDocObjectServer`mapuje aktywne interfejsy dokumentów i inicjuje i aktywuje aktywny dokument. MFC udostępnia również makra do obsługi routingu poleceń w aktywnych dokumentach. Aby korzystać z dokumentów aktywnych w aplikacji, Dołącz AfxDocOb. h do pliku StdAfx. h.

Zwykły serwer MFC przechwytuje własną `COleServerItem` klasę pochodną. Kreator aplikacji MFC generuje tę klasę dla Ciebie, jeśli zaznaczysz pole wyboru **mini-Server** lub **Full-Server** , aby umożliwić obsługę dokumentu złożonego serwera aplikacji. Jeśli zaznaczysz również pole wyboru **serwer aktywnego dokumentu** , Kreator aplikacji MFC generuje klasę pochodną `CDocObjectServerItem` zamiast.

`COleDocObjectItem`Klasa umożliwia kontenerowi OLE przestają się kontenerem aktywnego dokumentu. Za pomocą Kreatora aplikacji MFC można utworzyć kontener aktywnego dokumentu, zaznaczając pole wyboru **kontener aktywnego dokumentu** na stronie Obsługa dokumentu złożonego w Kreatorze aplikacji MFC. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji kontenera dokumentów aktywnych](creating-an-active-document-container-application.md).

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](active-document-containment.md)
