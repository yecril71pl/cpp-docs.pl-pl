---
title: 'Wyjątki: używanie makr MFC i wyjątków języka C++'
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
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371588"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Wyjątki: używanie makr MFC i wyjątków języka C++

W tym artykule omówiono zagadnienia dotyczące pisania kodu, który używa zarówno makr obsługi wyjątków MFC i słów kluczowych obsługi wyjątków języka C++.

W tym artykule omówiono następujące tematy:

- [Mieszanie słów kluczowych i makr wyjątków](#_core_mixing_exception_keywords_and_macros)

- [Wypróbuj bloki wewnątrz bloków zaczepowych](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mieszanie słów kluczowych i makr wyjątków

W tym samym programie można mieszać makra wyjątków MFC i słowa kluczowe wyjątków C++. Ale nie można mieszać makr MFC z słowami kluczowymi wyjątków C++ w tym samym bloku, ponieważ makra automatycznie usuwają obiekty wyjątków, gdy wychodzą poza zakres, podczas gdy kod przy użyciu słów kluczowych obsługi wyjątków nie. Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Główną różnicą między makrami a słowami kluczowymi jest to, że makra "automatycznie" usuwają przechwycony wyjątek, gdy wyjątek wykracza poza zakres. Kod przy użyciu słów kluczowych nie; wyjątki przechwycone w bloku połowowym muszą zostać jawnie usunięte. Mieszanie makr i słowa kluczowe wyjątku C++ może spowodować przecieki pamięci, gdy obiekt wyjątku nie zostanie usunięty, lub uszkodzenie sterty, gdy wyjątek zostanie usunięty dwukrotnie.

Poniższy kod, na przykład unieważnia wskaźnik wyjątku:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Ten problem `e` występuje, ponieważ jest usuwany, gdy wykonanie przechodzi z "wewnętrzny" **CATCH** bloku. Za pomocą **makra THROW_LAST** zamiast **throw** instrukcji spowoduje "zewnętrzne" **CATCH** bloku, aby otrzymać prawidłowy wskaźnik:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Wypróbuj bloki wewnątrz bloków catch

Nie można ponownie zgłosić bieżący wyjątek z wewnątrz **try** bloku, który znajduje się wewnątrz **catch** bloku. Poniższy przykład jest nieprawidłowy:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [Wyjątki: Badanie zawartości wyjątku](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
