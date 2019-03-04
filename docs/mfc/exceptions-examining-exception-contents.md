---
title: 'Wyjątki: Badanie zawartości wyjątku'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: f6f9bca6f6b7ca9d104cb492c760ab89f7163afd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259389"
---
# <a name="exceptions-examining-exception-contents"></a>Wyjątki: Badanie zawartości wyjątku

Mimo że **catch** bloku argument może być prawie każdego typu danych, zgłaszają wyjątki typów pochodnych typu klasy, funkcje MFC `CException`. Aby przechwycić wyjątek zgłoszony przez funkcję MFC, następnie należy napisać **catch** bloku, w której argument jest wskaźnikiem do `CException` obiektu (lub obiekt pochodzący od `CException`, takich jak `CMemoryException`). W zależności od dokładnego typu wyjątku, można sprawdzić składowych danych obiekt wyjątku, aby zebrać informacje na temat przyczyny określonego wyjątku.

Na przykład `CFileException` typ ma `m_cause` składową danych, która zawiera typ wyliczany określający przyczynę wyjątku plików. Przykłady możliwych wartości zwracane są `CFileException::fileNotFound` i `CFileException::readOnly`.

Poniższy przykład pokazuje, jak sprawdzić zawartość `CFileException`. Podobnie można sprawdzić innych typów wyjątków.

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątków: Zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md) i [wyjątków: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)
