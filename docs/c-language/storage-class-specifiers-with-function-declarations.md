---
title: Specyfikatory klasy magazynowania z deklaracjami funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8816ac8917281ed19dfc1afe9e12d302a3423f74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111410"
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

## <a name="see-also"></a>Zobacz też

[Klasy magazynu w języku C](../c-language/c-storage-classes.md)