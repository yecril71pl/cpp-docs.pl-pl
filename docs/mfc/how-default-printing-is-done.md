---
title: Jak jest wykonywane Drukowanie domyślne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f3616ba3fac4d5ed8ccca6b71d6fc04a2d5c106
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399902"
---
# <a name="how-default-printing-is-done"></a>Jak jest wykonywane drukowanie domyślne

W tym artykule opisano domyślne proces drukowania w Windows pod kątem programu MFC framework.

W aplikacjach MFC widok klasy posiada funkcję członkowską, o nazwie `OnDraw` zawierający kod rysowania. `OnDraw` pobiera wskaźnik do [CDC](../mfc/reference/cdc-class.md) obiektu jako parametr. Czy `CDC` obiekt reprezentuje kontekst urządzenia do odbierania obraz produkowane przez `OnDraw`. Po odebraniu okna wyświetlania dokumentu [WM_PAINT](/windows/desktop/gdi/wm-paint) komunikatu struktura wywołuje `OnDraw` i przekazuje je kontekst urządzenia dla ekranu ( [CPaintDC](../mfc/reference/cpaintdc-class.md) obiektu można określić). W związku z tym `OnDraw`danych wyjściowych zbliża się do ekranu.

W programowaniu dla Windows wysyłający dane wyjściowe do drukarki jest bardzo podobny do wysyłania danych wyjściowych na ekranie. Jest to spowodowane Windows graficzny interfejs urządzenia (GDI) jest zależne od sprzętu. Te same funkcje GDI można użyć do wyświetlania na ekranie lub drukowania, po prostu, używając kontekstu odpowiednie urządzenie. Jeśli `CDC` obiekt `OnDraw` odbiera reprezentuje drukarki, `OnDraw`danych wyjściowych zbliża się do drukarki.

W tej sekcji wyjaśniono, jak aplikacje MFC mogą wykonywać proste drukowanie bez konieczności dodatkowego wysiłku niewiele większego. Szablon dba wyświetlania okna dialogowego drukowania i tworzenie kontekstu urządzenia dla drukarki. Gdy użytkownik wybierze polecenie Drukuj w menu Plik, widok przekazuje kontekst urządzenia `OnDraw`, który rysuje na drukarce dokumentu.

Istnieją jednak pewne istotne różnice między drukowania i wyświetlanie na ekranie. Podczas drukowania, należy podzielić dokument na różnych stron i wyświetl je pojedynczo, zamiast wyświetlania dowolną część jest widoczna w oknie. Jako następstwem musisz wiedzieć o rozmiar papieru (czy jest rozmiar letter, rozmiar prawnych lub kopertę). Można wydrukować w różnych orientacji, takie jak tryb pozioma lub pionowa. Bibliotekę Microsoft Foundation Class nie można przewidzieć, jak aplikacja poradzi sobie te problemy, dzięki czemu zapewnia protokół można dodać te funkcje.

Czy protokół został opisany w artykule [dokumentów szablonie wielostronicowym](../mfc/multipage-documents.md).

## <a name="see-also"></a>Zobacz też

[Drukowanie](../mfc/printing.md)

