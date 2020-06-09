---
title: Klasy związane z architekturą aplikacji MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 455a49a4f93f2fb2590447071edca76a32cbc5dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618020"
---
# <a name="mfc-application-architecture-classes"></a>Klasy związane z architekturą aplikacji MFC

Klasy w tej kategorii współtworzą architekturę aplikacji platformy. Dostarczają one funkcje wspólne dla większości aplikacji. Aby dodać funkcje specyficzne dla aplikacji, należy wypełnić strukturę. Zazwyczaj należy to zrobić, wprowadzając nowe klasy z klas architektury, a następnie dodając nowe składowe lub zastępując istniejące funkcje składowe.

[Kreatory aplikacji](reference/mfc-application-wizard.md) generują kilka typów aplikacji, z których wszystkie używają struktury aplikacji w różny sposób. Aplikacje SDI (interfejs pojedynczego dokumentu) i MDI (wiele dokumentów interfejsu dokumentu) wykorzystują w pełni użycie części platformy nazywanej architekturą dokumentu/widoku. Inne typy aplikacji, takie jak aplikacje oparte na oknach dialogowych, aplikacje oparte na formularzach i biblioteki DLL, wykorzystują tylko niektóre funkcje architektury dokumentu/widoku.

Aplikacje dokumentu/widoku zawierają jeden lub więcej zestawów dokumentów, widoków i okien ramowych. Obiekt szablonu dokumentu kojarzy klasy dla każdego dokumentu/widoku/zestawu ramek.

Chociaż nie ma potrzeby używania architektury dokumentu/widoku w aplikacji MFC, istnieje wiele zalet, aby to zrobić. Obsługa kontenera i serwera OLE MFC jest oparta na architekturze dokumentów/widoków, co jest obsługiwane w przypadku drukowania i podglądu wydruku.

Wszystkie aplikacje MFC mają co najmniej dwa obiekty: obiekt aplikacji pochodzący z [CWinApp](reference/cwinapp-class.md)oraz kilka rodzajów obiektów głównego okna, pochodnych (często pośrednio) z [CWnd](reference/cwnd-class.md). (Najczęściej okno główne pochodzi od [obiektu CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)lub [CDialog](reference/cdialog-class.md), które pochodzą z `CWnd` .)

Aplikacje korzystające z architektury dokumentu/widoku zawierają dodatkowe obiekty. Obiekty główne to:

- Obiekt aplikacji pochodzący z klasy [CWinApp](reference/cwinapp-class.md), jak wspomniano wcześniej.

- Co najmniej jeden obiekt klasy dokumentu pochodzący z klasy [CDocument](reference/cdocument-class.md). Obiekty klasy dokumentu są odpowiedzialne za wewnętrzną reprezentację danych manipulowaną w widoku. Mogą być skojarzone z plikiem danych.

- Co najmniej jeden obiekt widoku pochodzący z klasy [CView](reference/cview-class.md). Każdy widok to okno dołączone do dokumentu i powiązane z oknem ramki. W widokach są wyświetlane dane zawarte w obiekcie klasy dokumentu i manipulowanie nimi.

Aplikacje dokumentu/widoku zawierają również okna ramowe (pochodzące z [obiektu CFrameWnd](reference/cframewnd-class.md)) i szablony dokumentów (pochodzące z [CDocTemplate](reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
