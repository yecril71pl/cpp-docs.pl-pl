---
title: Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621452"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku

Inne funkcje elementów członkowskich uchwytu widoku i interpretują wszystkie dane wejściowe użytkownika. Zwykle definiujesz funkcje członkowskie obsługi komunikatów w klasie widoku do przetworzenia:

- [Komunikaty](messages.md) systemu Windows generowane przez akcje myszy i klawiatury.

- [Polecenia](user-interface-objects-and-command-ids.md) z menu, przyciski paska narzędzi i klawisze skrótów.

Te funkcje członkowskie programu obsługi komunikatów interpretują następujące działania jako dane wejściowe, wybrane lub edytowane, w tym przeniesienie danych do i ze schowka:

- Ruchy myszy i kliknięcia, przeciąganie i podwójne kliknięcie

- Naciśnięć klawiszy

- Polecenia menu

Które komunikaty systemu Windows, które są obsługiwane przez widok, zależy od potrzeb aplikacji.

[Tematy obsługi komunikatów i mapowania](message-handling-and-mapping.md) wyjaśniają sposób przypisywania elementów menu i innych obiektów interfejsu użytkownika do poleceń oraz sposób powiązania poleceń z funkcjami obsługi. [Tematy obsługi komunikatów i mapowania](message-handling-and-mapping.md) wyjaśniają także, jak MFC kieruje polecenia i wysyła standardowe komunikaty systemu Windows do obiektów, które zawierają procedury obsługi.

Na przykład aplikacja może wymagać zaimplementowania bezpośredniego rysowania myszy w widoku. Przykład Bazgroły pokazuje, jak obsłużyć odpowiednio WM_LBUTTONDOWN, WM_MOUSEMOVE i WM_LBUTTONUP wiadomości, aby rozpocząć, kontynuować i zakończyć rysowanie segmentu linii. Z drugiej strony czasami trzeba interpretować myszą w widoku jako zaznaczenie. `OnLButtonDown`Funkcja obsługi widoku decyduje o tym, czy użytkownik był rysowany lub wybierany. W przypadku wybrania program obsługi zdecyduje, czy kliknięcie znajdował się w granicach niektórych obiektów w widoku, a jeśli tak, Zmień wartość wyświetlaną, aby pokazać obiekt jako wybrany.

Widok może również obsługiwać niektóre polecenia menu, takie jak te z menu Edycja, aby wyciąć, skopiować, wkleić lub usunąć wybrane dane przy użyciu Schowka. Taka procedura obsługi wywoła niektóre elementy członkowskie powiązane z schowkiem klasy `CWnd` w celu przeniesienia wybranego elementu danych do lub ze schowka.

## <a name="see-also"></a>Zobacz też

[Używanie widoków](using-views.md)
