---
title: Trwa pobieranie danych z obiektu okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3055468c04bba7c9cb999d0a642c0819524ff7e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391413"
---
# <a name="retrieving-data-from-the-dialog-object"></a>Pobieranie danych z obiektu okna dialogowego

Struktura zapewnia łatwy sposób można zainicjować wartości formantów w oknie dialogowym i pobierać wartości z kontrolek. Więcej pracochłonne ręczne podejście jest wywołaniem funkcji, takich jak `SetDlgItemText` i `GetDlgItemText` funkcji elementów członkowskich klasy `CWnd`, które mają zastosowanie do sterowania systemu windows. Za pomocą tych funkcji można kontrola dostępu do każdego pojedynczo, aby ustawić lub pobrać jej wartość wywołaniem funkcji, takich jak `SetWindowText` i `GetWindowText`. Podejście struktury automatyzuje proces inicjowania i pobierania.

Wymiana danych okna dialogowego (DDX) pozwala łatwiej wymianę danych między formantów okna dialogowego pole i elementów członkowskich zmiennych w obiektu okna dialogowego. Ten program exchange działa w obu kierunkach. Aby zainicjować kontrolki w oknie dialogowym, można ustawić wartości elementów członkowskich danych w obiekcie okna dialogowego, a struktura będzie przesyłać wartości do formantów, zanim zostanie wyświetlone okno dialogowe. Następnie możesz w dowolnym momencie zaktualizować elementy członkowskie danych okna dialogowego przy użyciu danych wprowadzonych przez użytkownika. W tym momencie można użyć danych, odwołując się do zmiennych element członkowski danych.

Można także porządkować dla wartości formantów okna dialogowego, aby zostać uwierzytelnionym automatycznie za pomocą Walidacja danych okna dialogowego (DDV).

DDX i DDV omówiona bardziej szczegółowo w [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

Dla modalnego okna dialogowego, można pobrać żadnych danych, które użytkownik wprowadził, kiedy `DoModal` zwraca IDOK, ale przed okna dialogowego niszczony jest obiekt. Dla niemodalnego okna dialogowego, można pobrać dane z obiektu okna dialogowego w dowolnym momencie przez wywołanie metody `UpdateData` z argumentem **TRUE** ich i uzyskującym zmienne składowe klasy okna dialogowego. Ten temat jest omówiona bardziej szczegółowo w [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

