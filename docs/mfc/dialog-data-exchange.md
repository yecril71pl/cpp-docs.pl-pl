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
ms.openlocfilehash: 9a0199577ea46520c2eadc308812de8a1ce4b514
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "71685804"
---
# <a name="dialog-data-exchange"></a>Wymiana danych w oknie dialogowym

W przypadku korzystania z mechanizmu DDX należy ustawić początkowe wartości zmiennych składowych obiektu okna dialogowego, zazwyczaj w obsłudze `OnInitDialog` lub w konstruktorze okna dialogowego. Bezpośrednio przed wyświetleniem okna dialogowego mechanizm DDX struktury przenosi wartości zmiennych Członkowskich do kontrolek w oknie dialogowym, gdzie są wyświetlane, gdy samo okno dialogowe pojawia się w odpowiedzi na `DoModal` lub `Create`. Domyślna implementacja `OnInitDialog` w `CDialog` wywołuje funkcję elementu członkowskiego `UpdateData` klasy `CWnd` w celu zainicjowania kontrolek w oknie dialogowym.

Ten sam mechanizm przenosi wartości z formantów do zmiennych składowych, gdy użytkownik kliknie przycisk OK (lub po każdym wywołaniu funkcji składowej `UpdateData` z argumentem **true**). Mechanizm walidacji danych okna dialogowego sprawdza poprawność wszystkich elementów danych, dla których określono reguły walidacji.

Na poniższej ilustracji przedstawiono wymianę danych okna dialogowego.

![Wymiana danych okna dialogowego](../mfc/media/vc379d1.gif "Wymiana danych okna dialogowego") <br/>
Wymiana danych w oknie dialogowym

`UpdateData` działa w obu kierunkach, jak określono w parametrze **bool** przekazanym do niego. Aby przeprowadzić wymianę, `UpdateData` konfiguruje obiekt `CDataExchange` i wywołuje przesłonięcie klasy okna dialogowego `DoDataExchange` funkcji członkowskiej `CDialog`. `DoDataExchange` przyjmuje argument typu `CDataExchange`. Obiekt `CDataExchange` przeszedł do `UpdateData` reprezentuje kontekst wymiany, definiując takie informacje jako kierunek wymiany.

Gdy użytkownik (lub Kreator kodu) przesłoni `DoDataExchange`, należy określić wywołanie jednej funkcji DDX na element członkowski danych (kontrolka). Każda funkcja DDX wie, jak wymieniać dane w obu kierunkach na podstawie kontekstu dostarczonego przez argument `CDataExchange` przekazany do `DoDataExchange` przez `UpdateData`.

MFC udostępnia wiele funkcji DDX dla różnych rodzajów wymiany. W poniższym przykładzie pokazano przesłonięcie `DoDataExchange`, w którym są wywoływane dwie funkcje DDX i jedna funkcja DDV:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

@No__t_0 i `DDV_` wierszy są mapą danych. Wyświetlane przykładowe funkcje DDX i DDV są przeznaczone dla kontrolki pole wyboru i kontrolka pole edycji.

Jeśli użytkownik anuluje modalne okno dialogowe, funkcja elementu członkowskiego `OnCancel` kończy działanie okna dialogowego i `DoModal` zwróci wartość **IDCANCEL**. W takim przypadku żadne dane nie są wymieniane między oknem dialogowym a obiektem okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Wymiana i walidacja danych w oknie dialogowym](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Walidacja danych okna dialogowego](../mfc/dialog-data-validation.md)
