---
title: 'Wyjątki: Konwertowanie z makr wyjątków MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a386de558730e12bb8cf40da250c1d04dd4ff37a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931121"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Wyjątki: konwertowanie z makr wyjątków MFC
Jest to zaawansowane tematu.  
  
 W tym artykule opisano sposób konwertowania istniejący kod napisany za pomocą makr MFC — **SPRÓBUJ**, **CATCH**, **THROW**i tak dalej — do użycia, obsługa wyjątków języka C++ słowa kluczowe **spróbuj**, **catch**, i **throw**. Tematy obejmują:  
  
-   [Zalety konwersji](#_core_advantages_of_converting)  
  
-   [Konwertowanie kodu z makr wyjątków do użycia wyjątków języka C++](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> Zalety konwersji  
 Prawdopodobnie nie należy przekonwertować istniejący kod, ale należy zwrócić uwagę różnice między implementacje makra w wersji 3.0 MFC i implementacje we wcześniejszych wersjach. Te różnice i kolejne zmiany w zachowaniu kodu zostały omówione w [wyjątki: zmiany w makrach wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
 Główne zalety konwertowanie są następujące:  
  
-   Kompiluje kod, który używa słowa kluczowe języka C++ obsługi wyjątków do nieco mniejsze. Wywołanie pliku EXE lub. BIBLIOTEKI DLL.  
  
-   Słowa kluczowe języka C++ obsługi wyjątków są bardziej elastyczne: ich obsługi wyjątków każdego typu danych, które mogą zostać skopiowane (**int**, **float**, **char**i tak dalej), podczas gdy makra obsługi wyjątków tylko klasy `CException` i klas pochodnych.  
  
 Główna różnica między makra i słowa kluczowe jest, że kod przy użyciu makra "automatycznie" Usuwa zgłoszony wyjątek, gdy wyjątek wykracza poza zakres. Kodu za pomocą słowa kluczowe nie jest dostępne, dlatego należy jawnie usunąć zgłoszony wyjątek. Aby uzyskać więcej informacji, zobacz artykuł [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Inna różnica polega na składni. Składnia makra i słów kluczowych różni się w trzech aspektach:  
  
1.  Argumenty i deklaracje wyjątku:  
  
     A **CATCH** wywołanie makra ma następującą składnię:  
  
     **CATCH (** *exception_class*, *exception_object_pointer_name* **)**  
  
     Zwróć uwagę, przecinka między nazwę klasy i nazwę obiektu wskaźnika.  
  
     W deklaracji wyjątku **catch** — słowo kluczowe używa następującej składni:  
  
     **CATCH (** *exception_type* *exception_name ***)**  
  
     Ta instrukcja deklaracji wyjątku wskazuje typ wyjątku catch zablokować uchwytów.  
  
2.  Ogranicznik bloki catch:  
  
     Makra **CATCH** makra (z jego argumentów) rozpoczyna się pierwszego bloku catch; **and_catch —** makro rozpoczyna się bloki catch kolejnych i **end_catch —** — makro kończy sekwencji bloków catch.  
  
     Słów kluczowych **catch** — słowo kluczowe (z jego deklaracji wyjątku) rozpoczyna każdy blok catch. Nie ma odpowiednika do **end_catch —** makro; zablokować kończy się jego zamykający nawias klamrowy catch.  
  
3.  Wyrażenie throw:  
  
     Użyj makra **throw_last —** ponowne wygenerowanie bieżącego wyjątku. **Throw** — słowo kluczowe z nie argumentów ma ten sam efekt.  
  
##  <a name="_core_doing_the_conversion"></a> Podczas konwersji  
  
#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Aby przekonwertować kod przy użyciu makra, aby użyć słów kluczowych języka C++, obsługa wyjątków  
  
1.  Znajdź wszystkie wystąpienia makr MFC **SPRÓBUJ**, **CATCH**, **and_catch —**, **end_catch —**, **THROW**, i **throw_last —**.  
  
2.  Zamień lub Usuń wszystkie wystąpienia następujące makra:  
  
     **SPRÓBUJ** (go zastąpić **spróbuj**)  
  
     **CATCH** (go zastąpić **catch**)  
  
     **And_catch —** (go zastąpić **catch**)  
  
     **End_catch —** (usunąć jego)  
  
     **THROW** (go zastąpić **throw**)  
  
     **Throw_last —** (go zastąpić **throw**)  
  
3.  Argumenty makra, dzięki czemu tworzą one deklaracje prawidłowy wyjątek.  
  
     Na przykład zmienić  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     na  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  Zmodyfikuj kod w blokach catch, tak, aby usuwa obiekty wyjątków w razie potrzeby. Aby uzyskać więcej informacji, zobacz artykuł [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Oto przykładowy kod obsługi wyjątków za pomocą makr wyjątków MFC. Należy pamiętać, że ponieważ kod w poniższym przykładzie użyto makra wyjątek `e` zostanie automatycznie usunięty:  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 Kod w następnym przykładzie używa wyjątek słowa kluczowe języka C++, więc wyjątek muszą zostać jawnie usunięte:  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [wyjątkami: za pomocą makr MFC i wyjątków języka C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

