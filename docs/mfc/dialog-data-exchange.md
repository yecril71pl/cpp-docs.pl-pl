---
title: Wymiana danych okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35f280228d523c7401e2a90ca395a79a9c87cd51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-data-exchange"></a>Wymiana danych w oknie dialogowym
Używany mechanizm DDX, należy ustawić wartości początkowe okna dialogowego zmienne Członkowskie obiektu, zwykle w Twojej `OnInitDialog` obsługi lub konstruktora okna dialogowego. Natychmiast przed wyświetleniem okna dialogowego, w ramach mechanizmu DDX przesyła wartości zmiennych Członkowskich do formantów w oknie dialogowym, gdzie są wyświetlane po sam wyświetli się okno dialogowe w odpowiedzi na `DoModal` lub **Utwórz** . Domyślna implementacja `OnInitDialog` w `CDialog` wywołania `UpdateData` funkcji członkowskiej klasy `CWnd` zainicjować formantów w oknie dialogowym.  
  
 Ten sam mechanizm transferu wartości z kontrolki do zmiennych Członkowskich po kliknięciu przycisku OK (lub przy każdym wywołaniu `UpdateData` funkcji członkowskiej z argumentem **TRUE**). Mechanizm Walidacja danych okna dialogowego sprawdza poprawność elementów danych, dla których określono reguły sprawdzania poprawności.  
  
 Na poniższym rysunku przedstawiono wymiana danych okna dialogowego.  
  
 ![Wymiana danych okna dialogowego pole](../mfc/media/vc379d1.gif "vc379d1")  
Wymiana danych w oknie dialogowym  
  
 `UpdateData`działa w obu kierunkach, określony przez **BOOL** parametr przekazany do niego. Przeprowadzenie programu exchange `UpdateData` konfiguruje `CDataExchange` obiektu i wywołania klasy okien dialogowych zastąpienie `CDialog`w `DoDataExchange` funkcję elementu członkowskiego. `DoDataExchange`przyjmuje argument typu `CDataExchange`. `CDataExchange` Obiekt przekazywany do `UpdateData` reprezentuje kontekst programu exchange, określenie tych informacji jako kierunek programu exchange.  
  
 Jeśli zastąpienie użytkownik (lub Kreatora kodu) `DoDataExchange`, określić wywołanie jednej funkcji DDX dla każdego elementu członkowskiego danych (kontrola). Każda funkcja DDX potrafi wymiany danych w obu kierunkach na podstawie kontekstu dostarczonych przez `CDataExchange` argumentu przekazanego do Twojej `DoDataExchange` przez `UpdateData`.  
  
 MFC udostępnia wiele funkcji DDX dla różnych rodzajów wymiany. W poniższym przykładzie przedstawiono `DoDataExchange` zastąpienia, w których dwie DDX są nazywane funkcji i funkcji DDV:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]  
  
 `DDX_` i `DDV_` wiersze są mapowania danych. Funkcje DDX i DDV przykładowych pokazano są odpowiednio dla formantu pole wyboru i kontrolkę pola edycji.  
  
 Jeśli użytkownik anuluje modalne okno dialogowe, `OnCancel` funkcji członkowskiej kończy się okno dialogowe i `DoModal` zwraca wartość **IDCANCEL**. W takim przypadku nie są wymieniane dane między okno dialogowe i obiektu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Dane okna dialogowego wymiana i Walidacja](../mfc/dialog-data-exchange-and-validation.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)   
 [Walidacja danych okna dialogowego](../mfc/dialog-data-validation.md)

