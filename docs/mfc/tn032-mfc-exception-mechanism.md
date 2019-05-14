---
title: 'TN032: Mechanizm wyjątków MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 5b419fdcc4f20579b1a809dd8a5cf6a93f4fe835
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611413"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: Mechanizm wyjątków MFC

Poprzednie wersje programu Visual C++ nie obsługuje standardowe mechanizmie wyjątków C++ i MFC podane makra **TRY/CATCH/THROW** , użyto zamiast tego. Ta wersja programu Visual C++ w pełni obsługuje wyjątki C++. Ta uwaga objętych usługą, niektóre szczegóły implementacji zaawansowanej poprzedniego makra w tym sposobu automatycznego oczyszczania stosu na podstawie obiektów. Ponieważ wyjątki C++ obsługuje odwijanie domyślnie stosu, ta uwaga techniczna nie jest już konieczne.

Zapoznaj się [wyjątków: Używanie makr MFC i wyjątków C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) Aby uzyskać więcej informacji na temat różnic między makr MFC i nowych słów kluczowych języka C++.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
