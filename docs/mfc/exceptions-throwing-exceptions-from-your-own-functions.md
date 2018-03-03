---
title: "Wyjątki: Zgłaszanie wyjątków z własnych funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15aeb1af7f41cf2df8be3f69657ec6870c55ab34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Wyjątki: zgłaszanie wyjątków z własnych funkcji
Istnieje możliwość użycia model obsługi wyjątków MFC wyłącznie do przechwytuje wyjątków zgłaszanych przez funkcje MFC lub innych bibliotek. Oprócz przechwytywanie wyjątków zgłaszanych przez kod biblioteki, może zgłosić wyjątki z własnego kodu podczas pisania funkcje, które mogą wystąpić wyjątkowe warunki.  
  
 Gdy jest zgłaszany wyjątek, wykonywanie bieżącej funkcji został zatrzymany, a następnie przechodzi bezpośrednio do **catch** bloku ramki najbardziej wewnętrzny wyjątek. Mechanizm wyjątków pomija ścieżki normalne zakończenia w funkcji. W związku z tym należy pewno chcesz usunąć te bloki pamięci, które zostaną usunięte w normalnym zakończenia.  
  
#### <a name="to-throw-an-exception"></a>Aby zgłosić wyjątek  
  
1.  Użyj jednej z funkcji pomocnika MFC, takich jak `AfxThrowMemoryException`. Te funkcje throw obiekt przydzielony wstępnie wyjątek odpowiedniego typu.  
  
     W poniższym przykładzie funkcja próbuje przydzielić dwa bloki pamięci i zgłasza wyjątek, jeśli albo alokacja nie powiedzie się:  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     Jeśli pierwsza alokacja nie powiedzie się, możesz po prostu zgłosić wyjątek pamięci. Jeśli pierwsza alokacja zakończy się pomyślnie, ale drugi zakończy się niepowodzeniem, należy zwolnić pierwszego bloku alokacji przed zgłoszeniem wyjątku. W przypadku obu alokacji, można kontynuować normalnie i zwolnij bloki podczas zamykania funkcji.  
  
     - lub -  
  
2.  Umożliwia wskazanie Warunek problem wyjątek zdefiniowane przez użytkownika. Element dowolnego typu, a nawet całą grupę, można zgłosić jako wyjątku.  
  
     W poniższym przykładzie próbuje odtwarzanie dźwięku za pośrednictwem urządzenie typu wave i zgłasza wyjątek, jeśli występuje błąd.  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  MFC domyślna obsługa wyjątków ma zastosowanie tylko do wskaźników do `CException` obiektów (i obiekty `CException`-klas pochodnych). W powyższym przykładzie pomija mechanizm wyjątków MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

