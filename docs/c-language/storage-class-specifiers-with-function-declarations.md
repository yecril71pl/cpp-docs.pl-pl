---
title: Specyfikatory klasy magazynowania z deklaracjami funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157886"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specyfikatory klasy magazynowania z deklaracjami funkcji

Można użyć dowolnego **statyczne** lub `extern` — Specyfikator klasy magazynowania w deklaracjach funkcji. Funkcje zawsze mają globalne okresy istnienia.

**Microsoft Specific**

Deklaracje funkcji na poziomie wewnętrznym ma takie samo znaczenie jak deklaracje funkcji na poziomie zewnętrznym. Oznacza to, czy funkcja jest widoczna w punkcie deklaracji w pozostałej części jednostki translacji, nawet, jeśli zostanie ona zadeklarowana w zakresie lokalnym.

**END specyficzny dla Microsoft**

Reguły widoczności dla funkcji różnią się nieco od reguły dotyczące zmiennych, w następujący sposób:

- Funkcja zadeklarowana jako **statyczne** jest widoczna tylko w pliku źródłowym, w którym jest zdefiniowany. Można wywołać funkcji w tym samym pliku źródłowym **statyczne** funkcji, ale działa w innych plikach źródłowych nie można uzyskać do niego dostęp bezpośrednio przez nazwę. Można zadeklarować innego **statyczne** funkcji o tej samej nazwie w pliku źródłowym różnych bez powodowania konfliktów.

- Funkcje zadeklarowane jako `extern` są widoczne w całym wszystkich plików źródłowych w programie (o ile później ponownie zadeklarować funkcję jako **statyczne**). Można wywołać żadnej funkcji `extern` funkcji.

- Deklaracje funkcji, które pominąć specyfikator klasy magazynu są `extern` domyślnie.

**Microsoft Specific**

Firma Microsoft zezwala ponowna definicja `extern` identyfikator **statyczne**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Klasy magazynu w języku C](../c-language/c-storage-classes.md)
