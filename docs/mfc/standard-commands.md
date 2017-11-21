---
title: Polecenia standardowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 93471fa28adf2c094b953b70daaf9c81d05047f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="standard-commands"></a>Polecenia standardowe
Platformę definiuje wiele poleceń standardowych komunikatów. Identyfikatory dla tych poleceń zwykle mieć postać:  
  
 **ID_** *źródła*_*elementu*  
  
 gdzie *źródła* jest zwykle nazwy menu i *elementu* elementu menu. Na przykład identyfikator polecenia dla nowego polecenia menu Plik jest `ID_FILE_NEW`. Identyfikatory poleceń standardowych są wyświetlone czcionką pogrubioną w dokumentacji. Identyfikatory zdefiniowane przez programistę zostały pokazane czcionki, która różni się od otaczającego tekstu.  
  
 Oto niektóre z najważniejszych poleceń obsługiwane listę:  
  
 *Polecenia Menu Plik*  
 Nowe otwarte, Zamknij, Zapisz, Zapisz jako, ustawienia strony Ustawienia wydruku, drukowania, Podgląd wydruku, wyjścia i ostatnio używanych plików.  
  
 *Polecenia Menu Edycja*  
 Usuń zaznaczenie, usuń zaznaczenie wszystkich, kopiowanie, wycinanie, znajdowanie, Wklej, powtórz, Zamień, wybierz wszystkie cofania i ponawiania.  
  
 *Widok poleceń Menu*  
 Pasek narzędzi i paska stanu.  
  
 *Polecenia Menu okna*  
 Nowe, rozmieszczanie, Kaskadowo sąsiadująco w poziomie, sąsiadująco w pionie i podziału.  
  
 *Polecenia Menu Pomoc*  
 Indeks, korzystanie z pomocy i o.  
  
 *Polecenia OLE (Menu Edycja)*  
 Wstaw nowy obiekt, Edytuj łącza, Wklej łącze, Wklej specjalne i *typename* obiektu (zlecenie polecenia).  
  
 Framework zapewnia różne poziomy wsparcia dla tych poleceń. Niektóre polecenia są obsługiwane tylko jako identyfikatory poleceń zdefiniowanych, inne są obsługiwane z implementacjami dokładnego. Na przykład platformę implementuje polecenia Otwórz menu Plik przez utworzenie nowego obiektu dokumentu, wyświetlanie otwarte okno dialogowe Otwieranie i odczytywania pliku. Z kolei, musisz zaimplementować poleceń menu Edycja użytkownika, od poleceń, takich jak **id_edit_copy —** zależą od rodzaju dane są kopiowane.  
  
 Więcej informacji na temat polecenia obsługiwane i poziomu implementacji, pod warunkiem, zobacz [22 Uwaga techniczna](../mfc/tn022-standard-commands-implementation.md). Polecenia standardowe są zdefiniowane w pliku AFXRES. H.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)

