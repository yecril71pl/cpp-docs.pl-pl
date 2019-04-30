---
title: Serwery dokumentów aktywnych
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 7050b810bb5e1f0c240222cd9b8c4922ced4238a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394978"
---
# <a name="active-document-servers"></a>Serwery dokumentów aktywnych

Serwery dokumentów aktywnych, takich jak Word, Excel lub PowerPoint hosta dokumenty w innych typów aplikacji o nazwie dokumenty aktywne. W odróżnieniu od OLE obiekty osadzone (które są po prostu wyświetlane na stronie innego dokumentu), Active dokumenty zawierają pełny interfejs i Pełna macierzystą funkcjonalność aplikacji serwera, z której zostały utworzone. Użytkownicy mogą tworzyć dokumenty przy użyciu pełnych możliwości ich ulubionych aplikacji (jeśli są one aktywnego dokumentu, włączone), jeszcze traktować Projekt wynikowy jako pojedynczy element.

Dokumenty aktywne może mieć więcej niż jedną stronę i są zawsze aktywny w miejscu. Dokumenty aktywne kontrolować część interfejsu użytkownika, scalanie menu za pomocą **pliku** i **pomocy** menu kontenera. One zajmują cały obszar edycji kontenera i kontrolowanie widoków i układ strony drukarki (marginesy, stopki i tak dalej).

MFC implementuje serwery dokumentów aktywnych przy użyciu interfejsów dokument/widok, mapy wysyłania poleceń, drukowanie, zarządzania menu i zarządzanie rejestrem. Konkretne wymagania programowania są omówione w [dokumenty aktywne](../mfc/active-documents.md).

Biblioteka MFC obsługuje dokumenty aktywne za pomocą [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) klasy pochodzące z [CCmdTarget](../mfc/reference/ccmdtarget-class.md), i [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), pochodzącej z [ COleServerItem](../mfc/reference/coleserveritem-class.md). Biblioteka MFC obsługuje kontenery dokumentów aktywnych z [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) klasy pochodzące z [COleClientItem](../mfc/reference/coleclientitem-class.md).

`CDocObjectServer` mapuje interfejsy aktywnego dokumentu i inicjuje i aktywuje aktywnego dokumentu. Biblioteka MFC zawiera również makra, aby obsługiwać routing poleceń w dokumenty aktywne. Aby użyć dokumenty aktywne w aplikacji, należy dołączyć AfxDocOb.h w pliku StdAfx.h.

Regularne serwerze MFC przechwytuje własną `COleServerItem`-klasy pochodnej. Kreator aplikacji MFC generuje tę klasę dla Ciebie, jeśli zostanie wybrana **miniserwera** lub **pełny serwer** pole wyboru, aby zapewnić serwer aplikacji Obsługa dokumentów złożonych. Można również wybrać **serwera aktywnego dokumentu** pole wyboru, Kreator aplikacji MFC generuje klasę pochodną `CDocObjectServerItem` zamiast tego.

`COleDocObjectItem` Klasa umożliwia kontener OLE w taki sposób, aby stać się kontener aktywnego dokumentu. Kreator aplikacji MFC można użyć, aby utworzyć kontener aktywnego dokumentu, wybierając **kontener dokumentów aktywnych** pole wyboru na stronie Obsługa dokumentów złożonych, Kreator aplikacji MFC. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji kontenera dokumentów aktywnych](../mfc/creating-an-active-document-container-application.md).

## <a name="see-also"></a>Zobacz także

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)
