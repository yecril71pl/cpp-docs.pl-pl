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
ms.openlocfilehash: c12953ab0b9922788747246a97115188b2f686ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616821"
---
# <a name="dialog-data-exchange"></a>Wymiana danych w oknie dialogowym

W przypadku korzystania z mechanizmu DDX należy ustawić początkowe wartości zmiennych składowych obiektu okna dialogowego, zazwyczaj w programie `OnInitDialog` obsługi lub w konstruktorze okien dialogowych. Bezpośrednio przed wyświetleniem okna dialogowego mechanizm DDX struktury przenosi wartości zmiennych Członkowskich do kontrolek w oknie dialogowym, gdzie są wyświetlane, gdy samo okno dialogowe pojawia się w odpowiedzi na `DoModal` lub `Create` . Domyślna implementacja `OnInitDialog` w programie `CDialog` wywołuje `UpdateData` funkcję elementu członkowskiego klasy w `CWnd` celu zainicjowania kontrolek w oknie dialogowym.

Ten sam mechanizm przenosi wartości z formantów do zmiennych składowych, gdy użytkownik kliknie przycisk OK (lub po każdym wywołaniu `UpdateData` funkcji składowej z argumentem **true**). Mechanizm walidacji danych okna dialogowego sprawdza poprawność wszystkich elementów danych, dla których określono reguły walidacji.

Na poniższej ilustracji przedstawiono wymianę danych okna dialogowego.

![Wymiana danych okna dialogowego](../mfc/media/vc379d1.gif "Wymiana danych okna dialogowego") <br/>
Wymiana danych w oknie dialogowym

`UpdateData`działa w obu kierunkach, jak określono w parametrze **bool** przekazanym do niego. Aby przeprowadzić wymianę, skonfiguruje `UpdateData` `CDataExchange` obiekt i wywołuje przesłonięcie `CDialog` `DoDataExchange` funkcji składowej klasy okna dialogowego. `DoDataExchange`przyjmuje argument typu `CDataExchange` . `CDataExchange`Obiekt przeszedł do `UpdateData` reprezentuje kontekst wymiany, definiując takie informacje jako kierunek wymiany.

Podczas przesłonięcia (lub Kreatora kodu) `DoDataExchange` można określić wywołanie jednej funkcji DDX na element członkowski danych (kontrolka). Każda funkcja DDX wie, jak wymieniać dane w obu kierunkach na podstawie kontekstu dostarczonego przez `CDataExchange` argument przekazany do `DoDataExchange` użytkownika `UpdateData` .

MFC udostępnia wiele funkcji DDX dla różnych rodzajów wymiany. W poniższym przykładzie przedstawiono `DoDataExchange` przesłonięcie, w którym są wywoływane dwie funkcje DDX i jedna funkcja DDV:

[!code-cpp[NVC_MFCControlLadenDialog#49](codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_`Wiersze i `DDV_` to Mapa danych. Wyświetlane przykładowe funkcje DDX i DDV są przeznaczone dla kontrolki pole wyboru i kontrolka pole edycji.

Jeśli użytkownik anuluje modalne okno dialogowe, `OnCancel` funkcja członkowska zakończy działanie okna dialogowego i `DoModal` zwróci wartość **IDCANCEL**. W takim przypadku żadne dane nie są wymieniane między oknem dialogowym a obiektem okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Wymiana i walidacja danych w oknie dialogowym](dialog-data-exchange-and-validation.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)<br/>
[Walidacja danych okna dialogowego](dialog-data-validation.md)
