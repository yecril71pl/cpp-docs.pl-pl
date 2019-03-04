---
title: Klasy debugowania i wyjątków
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 328d7a38c544b56f83ea3e8b1136b1122c4dfa14
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271414"
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków

Te klasy zapewniają obsługę dynamicznej alokacji pamięci debugowania i do przekazywania informacji wyjątku przez funkcję, gdzie wyjątek jest zgłaszany do funkcji, gdzie zostanie przechwycony.

Używanie klas [CDumpContext](../mfc/reference/cdumpcontext-class.md) i [CMemoryState](../mfc/reference/cmemorystate-structure.md) podczas programowania, która pomaga w debugowaniu, zgodnie z opisem w [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) można określić klasę dowolnego obiektu w czasie wykonywania, zgodnie z opisem w artykule [uzyskiwania dostępu do środowiska wykonawczego informacji o klasie](../mfc/accessing-run-time-class-information.md). Środowisko wykorzystuje `CRuntimeClass` dynamicznie utworzyć obiekty określonej klasy.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
