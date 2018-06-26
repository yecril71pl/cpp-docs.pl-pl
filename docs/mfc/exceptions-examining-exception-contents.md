---
title: 'Wyjątki: Badanie zawartości wyjątku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c7453b92ce14fbbcd20ea0f9a8bd8a7a2b5b6d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932237"
---
# <a name="exceptions-examining-exception-contents"></a>Wyjątki: badanie zawartości wyjątku
Mimo że **catch** bloku argument może być prawie każdego typu danych, funkcje MFC zgłaszają wyjątki typów pochodnych klasy `CException`. Aby przechwycić wyjątek zgłoszony przez funkcję MFC, następnie należy napisać **catch** blok, którego argument jest wskaźnik do `CException` obiektu (lub typ pochodzący od obiektu `CException`, takich jak `CMemoryException`). W zależności od dokładnej typ wyjątku można zbadać elementów członkowskich danych obiektu wyjątku Aby zebrać informacje dotyczące określonego powodu wyjątku.  
  
 Na przykład `CFileException` typ ma `m_cause` elementu danych, która zawiera typ wyliczany określający przyczyną wyjątku pliku. Przykłady możliwych zwracać wartości są `CFileException::fileNotFound` i `CFileException::readOnly`.  
  
 Poniższy przykład przedstawia sposób sprawdź zawartość `CFileException`. Innego typu wyjątku może sprawdzić w podobny sposób.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md) i [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

