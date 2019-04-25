---
title: Polecenia standardowe
ms.date: 11/04/2016
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
ms.openlocfilehash: 987023322e38584d10901c1ab1fe20ac46926bd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307162"
---
# <a name="standard-commands"></a>Polecenia standardowe

Struktura definiuje wiele poleceń standardowych komunikatów. Identyfikatory poleceń zazwyczaj formę:

**ID_** *źródła*_*elementu*

gdzie *źródła* jest zazwyczaj nazwy menu i *elementu* element menu. Na przykład identyfikator polecenia dla polecenia Nowy w menu Plik jest id_file_new —. Identyfikatory poleceń standardowych są wyświetlane pogrubioną czcionką w dokumentacji. Identyfikatory zdefiniowane przez programistę są wyświetlane w czcionkę, która różni się od otaczającego tekstu.

Oto niektóre z najważniejszych polecenia obsługiwane listę:

*Polecenia Menu Plik*<br/>
Nowe otwarte, zamknij Zapisz Zapisz jako, ustawienia strony, ustawienia wydruku, drukowania, Podgląd wydruku, zakończenia i ostatnio używanych plików.

*Polecenia Menu Edycja*<br/>
Wyczyść, usuń zaznaczenie wszystkich, kopiowanie, wycinanie, wyszukiwanie, wklejania, powtórz, Zastąp, zaznacz wszystko Cofnij i wykonaj ponownie.

*Polecenia menu widoku*<br/>
Pasek narzędzi i pasek stanu.

*Polecenia menu okna*<br/>
Nowe, rozmieszczanie, zastosować kaskadowo, sąsiadująco w poziomie, sąsiadująco w pionie i dzielenie.

*Polecenia menu pomocy*<br/>
Indeks, korzystanie z pomocy i o.

*Polecenia OLE (w Menu Edycja)*<br/>
Wstaw nowy obiekt, Edytuj łącza, Wklej łącze, Wklej specjalne i *typename* obiektu (zlecenie polecenia).

Struktura zapewnia różne poziomy wsparcia dla tych poleceń. Niektóre polecenia są obsługiwane tylko jako identyfikatory poleceń zdefiniowane, podczas gdy inne są obsługiwane w przypadku implementacji dokładnego. Na przykład platformę implementuje polecenia Otwórz menu Plik, tworząc nowy obiekt dokumentu, wyświetlanie otwarte okno dialogowe i otwierania i odczytywania pliku. Z kolei należy zaimplementować poleceń menu Edycja samodzielnie, ponieważ zależą od charakteru danych poleceń, takich jak id_edit_copy — kopiowanie.

Aby dowiedzieć się więcej o polecenia obsługiwane i stopień wdrożenia, pod warunkiem, zobacz [techniczne 22 Uwaga](../mfc/tn022-standard-commands-implementation.md). Polecenia standardowe są zdefiniowane w pliku AFXRES. H.

## <a name="see-also"></a>Zobacz także

[Obiekty interfejsu użytkownika i identyfikatory poleceń](../mfc/user-interface-objects-and-command-ids.md)
