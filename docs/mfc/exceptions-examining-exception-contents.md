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
ms.openlocfilehash: 7500db2a29f9d4ccef37b9265f5f2968c2d07993
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217951"
---
# <a name="exceptions-examining-exception-contents"></a>Wyjątki: badanie zawartości wyjątku

Chociaż **`catch`** argument bloku może być niemal dowolnego typu danych, funkcje MFC zgłaszają wyjątki typów pochodnych od klasy `CException` . Aby przechwytywać wyjątek zgłoszony przez funkcję MFC, należy napisać **`catch`** blok, którego argument jest wskaźnikiem do `CException` obiektu (lub obiektu pochodnego `CException` , takiego jak `CMemoryException` ). W zależności od dokładnego typu wyjątku można przeanalizować elementy członkowskie danych obiektu wyjątku, aby zebrać informacje o konkretnej przyczynie wyjątku.

Na przykład `CFileException` Typ ma `m_cause` element członkowski danych, który zawiera typ wyliczeniowy, który określa przyczynę wyjątku pliku. Niektóre przykłady możliwych zwracanych wartości to `CFileException::fileNotFound` i `CFileException::readOnly` .

Poniższy przykład pokazuje, jak przeanalizować zawartość `CFileException` . Inne typy wyjątków można badać podobnie.

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](exceptions-freeing-objects-in-exceptions.md) i [wyjątkach: Przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](exception-handling-in-mfc.md)
