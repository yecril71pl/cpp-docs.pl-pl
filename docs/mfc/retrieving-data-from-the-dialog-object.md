---
title: Pobieranie danych z obiektu okna dialogowego
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 903d76a1e672d05a3c093e528f7153562df8e3e5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685572"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Pobieranie danych z obiektu okna dialogowego

Struktura zapewnia łatwy sposób inicjowania wartości kontrolek w oknie dialogowym i pobierania wartości z kontrolek. Bardziej pracochłonne ręczne podejście polega na wywołaniu funkcji, takich jak `SetDlgItemText` i `GetDlgItemText` funkcji członkowskich klasy `CWnd`, które mają zastosowanie do okien kontroli. Korzystając z tych funkcji, uzyskujesz dostęp do każdej kontrolki indywidualnie, aby ustawić lub pobrać jej wartość, wywołując funkcje, takie jak `SetWindowText` i `GetWindowText`. Podejście struktury automatyzuje zarówno inicjowanie, jak i pobieranie.

Wymiana danych w oknie dialogowym (DDX) umożliwia łatwiejsze wymianę danych między kontrolkami w oknie dialogowym a zmiennymi składowymi w obiekcie okna dialogowego. Ta wymiana działa w obu kierunkach. Aby zainicjować kontrolki w oknie dialogowym, można ustawić wartości elementów członkowskich danych w obiekcie okna dialogowego, a struktura przetransferuje wartości do kontrolek przed wyświetleniem okna dialogowego. Następnie można w dowolnym momencie zaktualizować elementy członkowskie danych okna dialogowego o dane wprowadzone przez użytkownika. W tym momencie można użyć danych, odwołując się do zmiennych składowych danych.

Można także rozmieścić wartości kontrolek okna dialogowego, aby automatycznie sprawdzać poprawność przy użyciu walidacji danych okna dialogowego (DDV).

DDX i DDV zostały omówione bardziej szczegółowo w [oknie dialogowym wymiana danych i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

W przypadku modalnego okna dialogowego można pobrać wszystkie dane wprowadzone przez użytkownika, gdy `DoModal` zwraca IDOK, ale przed zniszczeniem obiektu okna dialogowego. W przypadku niemodalnego okna dialogowego można pobrać dane z obiektu okna dialogowego w dowolnym momencie, wywołując `UpdateData` z argumentem **true** , a następnie uzyskując dostęp do zmiennych składowych klasy okna dialogowego. Ten temat został szczegółowo omówiony w [oknie dialogowym wymiana danych i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
