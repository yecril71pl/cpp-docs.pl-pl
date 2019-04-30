---
title: 'Wyjątki: Używanie makr MFC i wyjątków języka C++'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406018"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Wyjątki: Używanie makr MFC i wyjątków języka C++

W tym artykule omówiono zagadnienia dotyczące pisania kodu, który używa zarówno makra obsługi wyjątków MFC i słów kluczowych obsługi wyjątków języka C++.

W tym artykule omówiono następujące tematy:

- [Mieszanie słowa kluczowe wyjątków i makra](#_core_mixing_exception_keywords_and_macros)

- [Bloki try wewnątrz bloki catch](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> Mieszanie słowa kluczowe wyjątków i makra

Można łączyć z makr wyjątków MFC a słowa kluczowe wyjątków języka C++, w tym samym programie. Ale nie można mieszać makr MFC z słowa kluczowe wyjątków języka C++, w tym samym bloku, ponieważ makra obiektów wyjątków automatycznie usuwać gdy wykraczają poza zakres, natomiast nie ma kodu za pomocą słów kluczowych obsługi wyjątków. Aby uzyskać więcej informacji, zobacz artykuł [wyjątków: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Główna różnica między makra i słów kluczowych jest, że makra "automatycznie" Usuń zgłoszony wyjątek, gdy wyjątek wykracza poza zakres. Kod przy użyciu słów kluczowych nie; wyjątki przechwytywane w bloku catch muszą zostać jawnie usunięte. Mieszania makr i słowa kluczowe wyjątków języka C++ może spowodować przecieki pamięci, gdy nieusunięty obiekt wyjątku lub uszkodzenie sterty, gdy wyjątek został usunięty dwa razy.

Poniższy kod, na przykład unieważnia wskaźnika wyjątek:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Ten problem występuje, ponieważ `e` jest usuwany podczas wykonywania przekazuje poza "wewnętrzny" **CATCH** bloku. Za pomocą **THROW_LAST** makr zamiast **THROW** spowoduje, że instrukcja "zewnętrzny" **CATCH** bloku, aby uzyskać prawidłowy wskaźnik:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> Bloki wewnątrz bloków Catch try

Nie można ponownie wygenerować bieżący wyjątek z poziomu **spróbuj** blok, który znajduje się wewnątrz **CATCH** bloku. Poniższy przykład jest nieprawidłowy:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątków: Badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
