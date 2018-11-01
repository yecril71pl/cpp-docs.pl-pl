---
title: 'Wyjątki: badanie zawartości wyjątku'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 4355a575f29741d0c7b9f1e12e40ca9d977219b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630077"
---
# <a name="exceptions-examining-exception-contents"></a>Wyjątki: badanie zawartości wyjątku

Mimo że **catch** bloku argument może być prawie każdego typu danych, zgłaszają wyjątki typów pochodnych typu klasy, funkcje MFC `CException`. Aby przechwycić wyjątek zgłoszony przez funkcję MFC, następnie należy napisać **catch** bloku, w której argument jest wskaźnikiem do `CException` obiektu (lub obiekt pochodzący od `CException`, takich jak `CMemoryException`). W zależności od dokładnego typu wyjątku, można sprawdzić składowych danych obiekt wyjątku, aby zebrać informacje na temat przyczyny określonego wyjątku.

Na przykład `CFileException` typ ma `m_cause` składową danych, która zawiera typ wyliczany określający przyczynę wyjątku plików. Przykłady możliwych wartości zwracane są `CFileException::fileNotFound` i `CFileException::readOnly`.

Poniższy przykład pokazuje, jak sprawdzić zawartość `CFileException`. Podobnie można sprawdzić innych typów wyjątków.

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md) i [wyjątki: wyjątki połowowe i usuwanie](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

