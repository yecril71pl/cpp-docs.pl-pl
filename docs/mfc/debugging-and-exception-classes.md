---
title: Klasy debugowania i wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9adf6a585771336de9fb33abbebdd6bab97383ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków
Te klasy obsługi debugowania dynamicznej alokacji pamięci oraz do przekazywania informacji wyjątek z funkcji, w którym wyjątku funkcji gdzie zostanie przechwycony.  
  
 Użyj klasy [CDumpContext](../mfc/reference/cdumpcontext-class.md) i [CMemoryState](../mfc/reference/cmemorystate-structure.md) podczas tworzenia, aby umożliwić debugowanie, zgodnie z opisem w [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) można określić klasę wszystkich obiektów w czasie wykonywania, zgodnie z opisem w artykule [podczas uzyskiwania dostępu do środowiska wykonawczego informacje o klasie](../mfc/accessing-run-time-class-information.md). Używa w ramach `CRuntimeClass` można dynamicznie utworzyć obiekty określonej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

