---
title: Pobieranie danych z obiektu okna dialogowego | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b8f39673701ca61b6423e7247f52c0de5a846b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="retrieving-data-from-the-dialog-object"></a>Pobieranie danych z obiektu okna dialogowego
Platformę zapewnia prosty sposób zainicjować wartości formantów w oknie dialogowym oraz do pobierania wartości z kontroli. Więcej pracochłonne ręczne podejściem jest wywołaniem funkcji, takich jak `SetDlgItemText` i `GetDlgItemText` funkcji elementów członkowskich klasy `CWnd`, które mają zastosowanie do sterowania systemu windows. Z tych funkcji, należy każdy kontrola dostępu indywidualnie do ustawić lub pobrać jej wartość wywoływanie funkcji, takich jak `SetWindowText` i `GetWindowText`. Podejście framework automatyzuje zarówno inicjowania i pobierania.  
  
 Wymiana danych okna dialogowego (DDX) umożliwia łatwiejsze wymiany danych między formantów w oknie dialogowym pole i element członkowski zmiennych w obiektu okna dialogowego. To z programem exchange działa w obu kierunkach. Zainicjować formantów w oknie dialogowym można ustawić wartości elementów członkowskich danych w obiekcie okna dialogowego i ramach zostaną przeniesione wartości do kontrolki, zanim zostanie wyświetlone okno dialogowe. Następnie możesz w dowolnym momencie zaktualizować elementy członkowskie danych okna dialogowego z danych wprowadzonych przez użytkownika. W tym momencie można użyć danych, odwołując się do zmiennych Członkowskich danych.  
  
 Można także porządkować dla wartości formantów okna dialogowego zostanie automatycznie wykonana Walidacja z Walidacja danych okna dialogowego (DDV).  
  
 DDX i DDV omówiono bardziej szczegółowo w [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md).  
  
 Dla modalne okno dialogowe, można pobrać żadnych danych, które użytkownik wprowadził, kiedy `DoModal` zwraca **IDOK** , ale przed okna dialogowego obiekt zostanie zniszczony. Pola z niemodalnego okna dialogowego można pobrać dane z obiektu okna dialogowego w dowolnym momencie przez wywołanie metody `UpdateData` z argumentem **TRUE** , a następnie uzyskiwanie dostępu do zmiennych Członkowskich klasy okna dialogowego. Ten temat jest omówiona bardziej szczegółowo w [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

