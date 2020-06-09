---
title: Klasy debugowania i wyjątków
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 6c7d1fc20556993c3c6690122786d7a767d895ad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625935"
---
# <a name="debugging-and-exception-classes"></a>Klasy debugowania i wyjątków

Te klasy zapewniają obsługę debugowania alokacji pamięci dynamicznej i przekazywania informacji o wyjątku z funkcji, w której wyjątek jest zgłaszany do funkcji, w której jest przechwytywany.

Używaj klas [CDumpContext](reference/cdumpcontext-class.md) i [CMemoryState](reference/cmemorystate-structure.md) podczas programowania, aby pomóc w debugowaniu, zgodnie z opisem w [debugowaniu aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques). Użyj [CRuntimeClass](reference/cruntimeclass-structure.md) , aby określić klasę dowolnego obiektu w czasie wykonywania, zgodnie z opisem w artykule [Uzyskiwanie dostępu do informacji o klasie czasu wykonywania](accessing-run-time-class-information.md). Struktura używa programu `CRuntimeClass` do dynamicznego tworzenia obiektów dla określonej klasy.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
