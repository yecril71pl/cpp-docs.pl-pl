---
title: Wymiana danych w oknie dialogowym
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 338630aef358d9490461179288d5c45a2d3b821c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302320"
---
# <a name="dialog-data-exchange"></a>Wymiana danych w oknie dialogowym

Użycie mechanizmu DDX ustawisz wartości początkowe w oknie dialogowym Zmienne Członkowskie obiektu, zwykle w swojej `OnInitDialog` obsługi lub konstruktora okna dialogowego. Natychmiast przed wyświetleniem okna dialogowego, mechanizm DDX struktury przesyła wartości zmiennych składowych kontrolek w oknie dialogowym, w którym są wyświetlane podczas samego pojawi się okno dialogowe w odpowiedzi na `DoModal` lub `Create`. Domyślna implementacja klasy `OnInitDialog` w `CDialog` wywołania `UpdateData` funkcji składowej klasy typu `CWnd` zainicjować formantów w oknie dialogowym.

Ten sam mechanizm przesyła wartości z kontrolek do zmiennych składowych po kliknięciu przycisku OK (lub po każdym wywołaniu `UpdateData` funkcja elementu członkowskiego z argumentem **TRUE**). Mechanizm walidacji danych okna dialogowego sprawdza wszystkie elementy danych, dla których określono reguły poprawności.

Na poniższym rysunku przedstawiono wymiana danych okna dialogowego.

![Wymiana danych okno dialogowe](../mfc/media/vc379d1.gif "wymiany danych okno dialogowe") <br/>
Wymiana danych w oknie dialogowym

`UpdateData` działa w obu kierunkach, określony przez **BOOL** parametr przekazywany do niego. Przeprowadzenie programu exchange, `UpdateData` konfiguruje `CDataExchange` wywołań i obiekt klasy okna dialogowego zastąpieniu obiektu `CDialog`firmy `DoDataExchange` funkcja elementu członkowskiego. `DoDataExchange` przyjmuje argument typu `CDataExchange`. `CDataExchange` Obiekt przekazany do `UpdateData` reprezentuje kontekst programu exchange, definiowanie takie informacje jak kierunek programu exchange.

Po użytkownik (lub Kreatora kodów) zastąpić `DoDataExchange`, określ wywołanie jednej funkcji DDX na element członkowski danych (kontrola). Każda funkcja DDX wie, jak do wymiany danych w obu kierunkach, na podstawie kontekstu dostarczonych przez `CDataExchange` argument przekazany do usługi `DoDataExchange` przez `UpdateData`.

Biblioteka MFC zawiera wiele funkcji DDX dla różnych rodzajów wymiany. W poniższym przykładzie przedstawiono `DoDataExchange` zastąpienia, w której dwa DDX funkcje i jedna funkcja DDV noszą nazwę:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` i `DDV_` wiersze to mapowanie danych. Funkcje DDX i DDV przykładowych pokazano są odpowiednio kontrolkę pola wyboru i formant pola edycji.

Jeśli użytkownik anuluje modalne okno dialogowe, `OnCancel` funkcja elementu członkowskiego kończy się okno dialogowe i `DoModal` zwraca wartość **IDCANCEL**. W takiej sytuacji żadne dane nie są wymieniane między okna dialogowego i obiektu okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Walidacja danych okna dialogowego](../mfc/dialog-data-validation.md)
