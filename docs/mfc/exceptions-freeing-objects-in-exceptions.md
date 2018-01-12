---
title: "Wyjątki: Zwalnianie obiektów w wyjątkach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Wyjątki: zwalnianie obiektów w wyjątkach
W tym artykule opisano konieczność i metody zwalnianie obiektów w przypadku wystąpienia wyjątku. Tematy obejmują:  
  
-   [Obsługa wyjątków w lokalnie](#_core_handling_the_exception_locally)  
  
-   [Wyrzucanie wyjątków po niszczenie obiektów](#_core_throwing_exceptions_after_destroying_objects)  
  
 Wyjątki zgłaszane przez platformę, lub z przepływu normalnego program przerwania aplikacji. W związku z tym jest bardzo ważne, aby śledzić Zamknij obiektów, dzięki czemu można poprawnie usunąć z nich w przypadku jest zwracany wyjątek.  
  
 Istnieją dwie podstawowe metody w tym celu.  
  
-   Obsługa wyjątków lokalnie za pomocą **spróbuj** i **catch** słowa kluczowe, a następnie zniszcz wszystkie obiekty z jednej instrukcji.  
  
-   Destroy dowolnego obiektu w **catch** blok przed zgłoszeniem wyjątku poza blokiem dla dalszego obsługi.  
  
 Poniżej przedstawiono te dwie metody jako rozwiązania do poniższego przykładu problemy:  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 Jak podano powyżej, `myPerson` nie zostaną usunięte, jeśli wyjątek jest zgłaszany przez `SomeFunc`. Wykonanie przechodzi bezpośrednio do następnego obsługi Wyjątek zewnętrzny, pomijanie zakończenia normalnej funkcji i kod, który usuwa obiekt. Wskaźnik do obiektu wykracza poza zakres, gdy wyjątek pozostawia funkcji i pamięci zajmowanego przez obiekt nigdy nie będzie można odzyskać, tak długo, jak działa program. To jest przeciek pamięci; można wykryć za pomocą narzędzia Diagnostyka pamięci.  
  
##  <a name="_core_handling_the_exception_locally"></a>Obsługa wyjątków w lokalnie  
 **Bloku try/catch** modelu zapewnia obrony metodę programowania unikanie przecieki pamięci i zapewnienie, że obiekty zostały zniszczone w wystąpieniu wyjątku. Przykład pokazany w tym artykule można na przykład ulegną w następujący sposób:  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 W tym przykładzie nowe Ustawia program obsługi wyjątku catch wyjątku i jego obsługa lokalnie. Następnie zazwyczaj kończy działanie funkcji i niszczy obiektu. Ważnym aspektem w tym przykładzie jest, że kontekstu do catch wyjątku jest nawiązywane z **bloku try/catch** bloków. Bez ramki lokalnego wyjątek funkcja nigdy nie wiedział, czy wyjątek ma zostać zgłoszony i byłyby nie można zakończyć normalnie i zniszcz obiektu.  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>Wyrzucanie wyjątków po niszczenie obiektów  
 Innym sposobem obsługi wyjątków jest przekazać je dalej zewnętrznego kontekstu obsługi wyjątków. W Twojej **catch** bloku, można wykonać niektóre Oczyszczanie lokalnie przydzielone obiekty i następnie zgłosić wyjątek potrzeby dalszego przetwarzania.  
  
 Funkcja przerzucane może lub nie może być konieczne cofnięcie przydziału stosu obiektów. Jeśli funkcja zawsze zwalnia obiektu heap przed zwróceniem w przypadku normalnych, następnie funkcja powinny również deallocate obiektu heap przed zgłoszeniem wyjątku. Z drugiej strony Jeśli funkcja nie zwykle cofnąć obiekt przed zwróceniem w przypadku normalnych, następnie należy zdecydować, na podstawie przypadku — czy ich alokację obiektu heap.  
  
 W poniższym przykładzie pokazano, jak lokalnie przydzielone obiekty można wyczyścić:  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 Mechanizm wyjątków automatycznie cofa alokację ramki obiektów; Skrót destruktor obiektu ramki.  
  
 Jeśli wywołanie funkcji, które można zgłaszają wyjątki, możesz użyć **bloku try/catch** bloków, aby upewnić się, przechwytują wyjątki i mieć możliwość zniszczyć wszystkie obiekty, które zostały utworzone. W szczególności należy pamiętać, że wiele funkcji MFC mogą zgłaszają wyjątki.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

