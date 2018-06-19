---
title: Serwery dokumentów aktywnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc207541bda3084db6bc8ab3896f46761587169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340167"
---
# <a name="active-document-servers"></a>Serwery dokumentów aktywnych
Serwery dokumentów aktywnych, takich jak Word, Excel lub PowerPoint dokumenty hosta z aplikacjami innych typów o nazwie aktywne dokumenty. W odróżnieniu od OLE osadzonych obiektów (które są po prostu wyświetlane na stronie innego dokumentu), dokumenty aktywne Podaj pełną interfejsu i pełną funkcjonalność natywnych aplikacji serwera, z której zostały utworzone. Użytkownicy mogą tworzyć dokumenty przy użyciu pełnych możliwości ich ulubionych aplikacji (jeśli są włączone dokumentów aktywnych), jeszcze można traktować Projekt wynikowy jako pojedynczej jednostki.  
  
 Dokumenty aktywne może mieć więcej niż jedną stronę i są zawsze aktywny w miejscu. Dokumenty aktywne kontrolować część interfejsu użytkownika, scalanie menu za ich pomocą **pliku** i **pomocy** menu kontenera. One zajmują cały obszar edycji kontenera i kontrolować widoki i układ strony drukarki (marginesy, stopek itd.).  
  
 MFC implementuje serwery dokumentów aktywnych z interfejsów dokument/widok, mapy wysyłania polecenia drukowania, zarządzania menu i zarządzania rejestru. Szczególne wymagania dotyczące programowania, omówiono w [dokumenty aktywne](../mfc/active-documents.md).  
  
 MFC obsługuje dokumenty aktywne z [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) klasa pochodzi od [CCmdTarget](../mfc/reference/ccmdtarget-class.md), i [CDocObjectServerItem](../mfc/reference/cdocobjectserveritem-class.md), pochodną [ COleServerItem](../mfc/reference/coleserveritem-class.md). Kontenery dokumentów aktywnych z obsługuje MFC [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md) klasa pochodzi od [COleClientItem](../mfc/reference/coleclientitem-class.md).  
  
 `CDocObjectServer` mapuje interfejsy aktywnego dokumentu i inicjuje i aktywuje aktywnego dokumentu. MFC także makra do obsługi routingu poleceń w dokumenty aktywne. Aby użyć dokumenty aktywne w aplikacji, należy umieścić w pliku StdAfx.h AfxDocOb.h.  
  
 Regularne serwera MFC przechwytuje własną `COleServerItem`-klasy. Kreator aplikacji MFC w przypadku wybrania generuje tej klasy można **mini serwer** lub **pełny serwer** pola wyboru spowoduje obsługi dokumentów złożonych serwera aplikacji. Można również wybrać **serwer dokumentów aktywnych** pole wyboru, Kreator aplikacji MFC generuje klasę pochodzącą od `CDocObjectServerItem` zamiast tego.  
  
 `COleDocObjectItem` Klasa umożliwia kontener OLE w taki sposób, aby stać się kontenera dokumentów aktywnych. Kreator aplikacji MFC umożliwia utworzenie kontenera dokumentów aktywnych wybierając **kontenera dokumentów aktywnych** wyboru na stronie Obsługa dokumentów złożonych, Kreator aplikacji MFC. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji kontenera dokumentów aktywnych](../mfc/creating-an-active-document-container-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

