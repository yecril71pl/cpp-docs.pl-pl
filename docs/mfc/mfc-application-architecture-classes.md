---
title: Klasy związane z architekturą aplikacji MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32a842d69e227633f8fbd2291a47296d384a75c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438629"
---
# <a name="mfc-application-architecture-classes"></a>Klasy związane z architekturą aplikacji MFC

Klasy w tej kategorii przyczyniają się do architektury aplikacji framework. Dostarczają funkcje wspólne dla większości aplikacji. Należy wypełnić platformę, by dodać funkcje specyficzne dla aplikacji. Zazwyczaj można to zrobić przez wyprowadzanie nowe klasy z klas architektury, a następnie dodając nowych członków lub zastępowanie istniejących funkcji Członkowskich.

[Kreatorzy aplikacji](../mfc/reference/mfc-application-wizard.md) wygenerować kilka typów aplikacji, z którego korzysta struktury aplikacji na różne sposoby. SDI (interfejsu pojedynczego dokumentu) i aplikacje MDI (mechanizm interfejsu wielu dokumentów) wykorzystać część struktury o nazwie architektury dokument/widok. Inne typy aplikacji, takich jak oparta na oknach dialogowych aplikacji, aplikacje oparte na formularzach i bibliotek DLL, użyj tylko niektórych funkcji architektury dokument/widok.

Aplikacje dokumentu/widoku zawiera co najmniej jeden zestaw dokumentów, widoków i okien ramowych. Obiekt szablonu dokumentu kojarzy klasy dla każdego zestawu dokument/widok/ramki.

Mimo że nie masz opartych na architekturze dokument/widok w Twojej aplikacji MFC, istnieje kilka zalet w ten sposób. MFC OLE kontenera i serwera obsługi opiera się na architektury dokumentu/widoku, ponieważ obsługa drukowania i podglądu wydruku.

Wszystkie aplikacje MFC mają co najmniej dwa obiekty: obiekt aplikacji pochodzące z [CWinApp](../mfc/reference/cwinapp-class.md), a jakieś obiekt okna głównego, pochodną (często pośrednio) [CWnd](../mfc/reference/cwnd-class.md). (W większości przypadków okno główne jest tworzony na podstawie [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), lub [CDialog](../mfc/reference/cdialog-class.md), które są uzyskiwane z `CWnd`.)

Aplikacje, które używają architektury dokument/widok zawierający dodatkowe obiekty. Obiekty główne są:

- Obiekt aplikacji pochodzi od klasy [CWinApp](../mfc/reference/cwinapp-class.md), jak wspomniano wcześniej.

- Co najmniej jednego dokumentu obiektu klasy pochodnej klasy [CDocument](../mfc/reference/cdocument-class.md). Obiekty klasy dokumentu są odpowiedzialne za wewnętrznej reprezentacji danych manipulować w widoku. Może być skojarzony z plikiem danych.

- Wyświetl obiekty pochodną klasy [CView](../mfc/reference/cview-class.md). Każdy widok jest oknem które jest dołączone do dokumentu i skojarzony z oknem ramki. Widoki wyświetlanie i manipulowanie danymi zawarte w obiekcie klasy dokumentu.

Aplikacje dokumentu/widoku również zawierać okien ramowych (pochodną [CFrameWnd](../mfc/reference/cframewnd-class.md)) i zarządzania dokumentami szablonów (pochodną [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

