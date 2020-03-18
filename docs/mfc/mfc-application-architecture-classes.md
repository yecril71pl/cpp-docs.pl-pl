---
title: Klasy związane z architekturą aplikacji MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 1e09447623b32e9b10063af5bc91ac9589f45e44
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447721"
---
# <a name="mfc-application-architecture-classes"></a>Klasy związane z architekturą aplikacji MFC

Klasy w tej kategorii współtworzą architekturę aplikacji platformy. Dostarczają one funkcje wspólne dla większości aplikacji. Aby dodać funkcje specyficzne dla aplikacji, należy wypełnić strukturę. Zazwyczaj należy to zrobić, wprowadzając nowe klasy z klas architektury, a następnie dodając nowe składowe lub zastępując istniejące funkcje składowe.

[Kreatory aplikacji](../mfc/reference/mfc-application-wizard.md) generują kilka typów aplikacji, z których wszystkie używają struktury aplikacji w różny sposób. Aplikacje SDI (interfejs pojedynczego dokumentu) i MDI (wiele dokumentów interfejsu dokumentu) wykorzystują w pełni użycie części platformy nazywanej architekturą dokumentu/widoku. Inne typy aplikacji, takie jak aplikacje oparte na oknach dialogowych, aplikacje oparte na formularzach i biblioteki DLL, wykorzystują tylko niektóre funkcje architektury dokumentu/widoku.

Aplikacje dokumentu/widoku zawierają jeden lub więcej zestawów dokumentów, widoków i okien ramowych. Obiekt szablonu dokumentu kojarzy klasy dla każdego dokumentu/widoku/zestawu ramek.

Chociaż nie ma potrzeby używania architektury dokumentu/widoku w aplikacji MFC, istnieje wiele zalet, aby to zrobić. Obsługa kontenera i serwera OLE MFC jest oparta na architekturze dokumentów/widoków, co jest obsługiwane w przypadku drukowania i podglądu wydruku.

Wszystkie aplikacje MFC mają co najmniej dwa obiekty: obiekt aplikacji pochodzący z [CWinApp](../mfc/reference/cwinapp-class.md)oraz kilka rodzajów obiektów głównego okna, pochodnych (często pośrednio) z [CWnd](../mfc/reference/cwnd-class.md). (Najczęściej okno główne pochodzi od [obiektu CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)lub [CDialog](../mfc/reference/cdialog-class.md), z których wszystkie pochodzą z `CWnd`).

Aplikacje korzystające z architektury dokumentu/widoku zawierają dodatkowe obiekty. Obiekty główne to:

- Obiekt aplikacji pochodzący z klasy [CWinApp](../mfc/reference/cwinapp-class.md), jak wspomniano wcześniej.

- Co najmniej jeden obiekt klasy dokumentu pochodzący z klasy [CDocument](../mfc/reference/cdocument-class.md). Obiekty klasy dokumentu są odpowiedzialne za wewnętrzną reprezentację danych manipulowaną w widoku. Mogą być skojarzone z plikiem danych.

- Co najmniej jeden obiekt widoku pochodzący z klasy [CView](../mfc/reference/cview-class.md). Każdy widok to okno dołączone do dokumentu i powiązane z oknem ramki. W widokach są wyświetlane dane zawarte w obiekcie klasy dokumentu i manipulowanie nimi.

Aplikacje dokumentu/widoku zawierają również okna ramowe (pochodzące z [obiektu CFrameWnd](../mfc/reference/cframewnd-class.md)) i szablony dokumentów (pochodzące z [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
