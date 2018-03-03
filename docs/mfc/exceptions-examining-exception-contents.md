---
title: "Wyjątki: Badanie zawartości wyjątku | Dokumentacja firmy Microsoft"
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
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 953dd61247f7d14ad04d5d5f85529c89f3aaad9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-examining-exception-contents"></a>Wyjątki: badanie zawartości wyjątku
Mimo że **catch** bloku argument może być prawie każdego typu danych, funkcje MFC zgłaszają wyjątki typów pochodnych klasy `CException`. Aby przechwycić wyjątek zgłoszony przez funkcję MFC, następnie należy napisać **catch** blok, którego argument jest wskaźnik do `CException` obiektu (lub typ pochodzący od obiektu `CException`, takich jak `CMemoryException`). W zależności od dokładnej typ wyjątku można zbadać elementów członkowskich danych obiektu wyjątku Aby zebrać informacje dotyczące określonego powodu wyjątku.  
  
 Na przykład `CFileException` typ ma `m_cause` elementu danych, która zawiera typ wyliczany określający przyczyną wyjątku pliku. Przykłady możliwych zwracać wartości są **CFileException::fileNotFound** i **CFileException::readOnly**.  
  
 Poniższy przykład przedstawia sposób sprawdź zawartość `CFileException`. Innego typu wyjątku może sprawdzić w podobny sposób.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [wyjątki: zwalnianie obiektów w wyjątkach](../mfc/exceptions-freeing-objects-in-exceptions.md) i [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

