---
title: "Funkcje śródwierszowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5adadc990bed67abe739a4d73b2973b26ca207
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="inline-functions"></a>Funkcje śródwierszowe

**Dotyczące firmy Microsoft**

`__inline` — Słowo kluczowe informuje kompilator, aby zastąpić kod w definicji funkcji dla każdego wystąpienia wywołania funkcji. Jednak podstawienia występuje tylko według uznania kompilatora. Na przykład kompilator nie niewyrównane funkcję Jeśli wykonywana jest jego adresu lub jest zbyt duży, aby wbudowanego.

Dla funkcji wziąć pod uwagę jako potencjalny ze śródwierszowaniem, należy użyć definicji stylu nowych funkcji.

Ten formularz umożliwia określenie wbudowanej funkcji:

> **__inline** *typu*<sub>opt</sub> *definicji funkcji*

Korzystanie z funkcji śródwierszowych generuje kod szybszy i czasami może wygenerować kod mniejsze niż generuje wywołania funkcji równoważne z następujących powodów:

- Zaoszczędzić czas wymagany do wykonania wywołania funkcji.

- W tekście małych funkcji, być może trzy wiersze lub mniej, utworzyć mniejsza ilość kodu niż wywołania funkcji równoważne, ponieważ kompilator nie generuje kod obsługi argumentów i wartości zwracanej.

- Wbudowane funkcje generowane podlegają optymalizacji kodu nie jest dostępny do normalnej pracy, ponieważ kompilator nie przeprowadza interprocedural optymalizacji.

Funkcje przy użyciu `__inline` nie należy mylić z wbudowanego kodu asemblera. Zobacz [asemblera wbudowanego](../c-language/inline-assembler-c.md) Aby uzyskać więcej informacji.

**KOŃCOWY określonych firmy Microsoft**  

## <a name="see-also"></a>Zobacz też

[w tekście, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

