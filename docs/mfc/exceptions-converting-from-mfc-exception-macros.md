---
title: 'Wyjątki: Konwertowanie z makr wyjątków MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394510"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Wyjątki: Konwertowanie z makr wyjątków MFC

Jest to zaawansowane tematu.

W tym artykule opisano sposób konwertowania istniejący kod napisany w języku makr MFC — **SPRÓBUJ**, **CATCH**, **THROW**i tak dalej — aby używać obsługę wyjątków C++ słowa kluczowe **spróbuj**, **catch**, i **throw**. Tematy obejmują:

- [Zalety konwersji](#_core_advantages_of_converting)

- [Konwersja kodu za pomocą makra wyjątków należy używać wyjątków języka C++](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> Korzyści wynikające z konwersji

Prawdopodobnie nie trzeba przekonwertować istniejącego kodu, ale należy pamiętać różnic między implementacjami makra w MFC w wersji 3.0 i implementacje we wcześniejszych wersjach. Te różnice i kolejne zmiany w zachowaniu kodu, które zostały omówione w [wyjątków: Zmiany w makrach wyjątków w wersji 3.0 lub nowszej](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Główne zalety konwertowanie są następujące:

- Kod, który używa słów kluczowych obsługi wyjątków języka C++ kompiluje, aby nieco mniejsze. Plik EXE lub. BIBLIOTEKI DLL.

- C++ Słów kluczowych obsługi wyjątków są bardziej wszechstronna: One może obsługiwać wyjątki dowolnego typu danych, który można skopiować (**int**, **float**, **char**i tak dalej), podczas gdy makra obsługi wyjątków tylko klasy `CException` klasy i pochodzić od niego.

Główna różnica między makra i słów kluczowych jest, że kod przy użyciu makra "automatycznie" spowoduje usunięcie przechwycony wyjątek gdy wyjątek wykracza poza zakres. Kod za pomocą słów kluczowych nie jest, więc należy je jawnie usunąć przechwycony wyjątek. Aby uzyskać więcej informacji, zobacz artykuł [wyjątków: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Inna różnica polega na składni. Składnia służąca do makr i słów kluczowych różni się w trzech względami:

1. Argumenty i deklaracji wyjątku:

   A **CATCH** wywołanie makra ma następującą składnię:

   **CATCH (** *exception_class*, *exception_object_pointer_name* **)**

   Zwróć uwagę, przecinka między nazwę klasy i nazwy wskaźnika obiektu.

   W deklaracji wyjątku **catch** — słowo kluczowe używa następującej składni:

   **CATCH (** *exception_type* *exception_name* **)**

   Tej instrukcji deklaracji wyjątku wskazuje typ wyjątku catch block uchwyty.

2. Ogranicznik bloki catch:

   Za pomocą makra **CATCH** — makro (z jej argumentów) rozpoczyna się pierwszego bloku catch; **AND_CATCH** — makro rozpoczyna się bloki catch kolejnych i **END_CATCH** — makro kończy sekwencji bloki catch.

   Za pomocą słów kluczowych **catch** — słowo kluczowe (z jego deklaracji wyjątku) rozpoczyna się każdy blok catch. Nie ma odpowiednika do **END_CATCH** — makro; catch block kończy się jego zamykającego nawiasu klamrowego.

3. Wyrażenie throw:

   Użyj makra **THROW_LAST** można ponownie wygenerować bieżący wyjątek. **Throw** — słowo kluczowe z żadnego argumentu ma taki sam skutek.

##  <a name="_core_doing_the_conversion"></a> Wykonywania konwersji

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Aby przekonwertować kodu za pomocą makr, aby używać słów kluczowych obsługi wyjątków języka C++

1. Znajdź wszystkie wystąpienia makr MFC **SPRÓBUJ**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**, i **THROW_LAST**.

2. Zamień lub Usuń wszystkie wystąpienia następujące makra:

   **SPRÓBUJ** (zastąp go wartością **spróbuj**)

   **CATCH** (zastąp go wartością **catch**)

   **AND_CATCH** (zastąp go wartością **catch**)

   **END_CATCH** (usuń jego)

   **THROW** (zastąp go wartością **throw**)

   **THROW_LAST** (zastąp go wartością **throw**)

3. Argumenty — makro, dzięki czemu tworzą one deklaracje prawidłowy wyjątek.

   Na przykład zmienić

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   na

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Zmodyfikuj kod w blokach catch, tak, aby usuwa obiektów wyjątków zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz artykuł [wyjątków: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Oto przykład kodu obsługi wyjątków, przy użyciu makr wyjątków MFC. Należy pamiętać, że ponieważ kod w poniższym przykładzie użyto makr, wyjątek `e` zostanie automatycznie usunięte:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Kod w następnym przykładzie używa słowa kluczowe wyjątków języka C++, więc wyjątek muszą zostać jawnie usunięte:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątków: Używanie makr MFC i wyjątków C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)<br/>
