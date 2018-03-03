---
title: "Klasy debugowania i wyjątków | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 622e6d04a567668ebfd2c737c5cdde1c2ea09b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków
Te klasy obsługi debugowania dynamicznej alokacji pamięci oraz do przekazywania informacji wyjątek z funkcji, w którym wyjątku funkcji gdzie zostanie przechwycony.  
  
 Użyj klasy [CDumpContext](../mfc/reference/cdumpcontext-class.md) i [CMemoryState](../mfc/reference/cmemorystate-structure.md) podczas tworzenia, aby umożliwić debugowanie, zgodnie z opisem w [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) można określić klasę wszystkich obiektów w czasie wykonywania, zgodnie z opisem w artykule [podczas uzyskiwania dostępu do środowiska wykonawczego informacje o klasie](../mfc/accessing-run-time-class-information.md). Używa w ramach `CRuntimeClass` można dynamicznie utworzyć obiekty określonej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

