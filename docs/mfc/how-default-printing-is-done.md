---
title: "Jak jest wykonywane Drukowanie domyślne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5001026f1e5fe9e1fed86a49b0565b09ddd6b555
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-default-printing-is-done"></a>Jak jest wykonywane drukowanie domyślne
W tym artykule opisano domyślny proces drukowania w systemie Windows w ramach MFC.  
  
 W aplikacjach MFC, klasa widoku zawiera funkcję elementu członkowskiego o nazwie `OnDraw` zawierający kod rysowania. `OnDraw`pobiera wskaźnik do [CDC](../mfc/reference/cdc-class.md) obiektu jako parametr. Czy `CDC` obiekt reprezentuje kontekst urządzenia do odbierania obrazu utworzonego przez `OnDraw`. Kiedy okno dokumentu otrzyma [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) komunikatu, wywołuje framework `OnDraw` i przekazuje ją na ekranie kontekstu urządzenia ( [cpaintdc —](../mfc/reference/cpaintdc-class.md) obiektu na konkretnym). W związku z tym `OnDraw`wyjściowy przejść do ekranu.  
  
 W programowaniu dla systemu Windows, wysyłanie dane wyjściowe do drukarki jest bardzo podobny do wysyłania danych wyjściowych do ekranu. Jest to spowodowane Windows graficzny interfejs urządzenia (GDI) jest zależne od sprzętu. Możesz użyć tej samej funkcji GDI ekranu lub drukowania po prostu przy użyciu kontekstu odpowiedniego urządzenia. Jeśli `CDC` obiekt, który `OnDraw` odbiera reprezentuje drukarki, `OnDraw`wyjściowy zbliża się do drukarki.  
  
 W tej sekcji wyjaśniono, jak aplikacje MFC mogą wykonywać proste drukowanie bez konieczności wprowadzania dodatkowych działań ze strony użytkownika. Platformę zapewnia obsługę wyświetlania okna dialogowego drukowania i tworzenie kontekstu urządzenia dla drukarki. Gdy użytkownik wybierze polecenie Drukuj z menu Plik, widok przekazuje kontekst urządzenia `OnDraw`, który pobiera dokument na drukarce.  
  
 Istnieją jednak niektóre istotne różnice między i ekranu. Podczas drukowania, należy podzielić dokument na różnych stronach i wyświetlić je pojedynczo, zamiast wyświetlania dowolnej części jest widoczna w oknie. Jako następstwem trzeba znać rozmiar papieru (czy jest letter, rozmiar prawnych lub koperty). Można drukować w różnych położeniach, takim jak tryb pozioma lub pionowa. Microsoft Foundation Class Library nie można przewidzieć sposób obsługi przez aplikację te problemy, dzięki czemu oferuje protokołu dodanie tych funkcji.  
  
 Że protokół jest opisane w artykule [dokumenty szablonie wielostronicowym](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie](../mfc/printing.md)

