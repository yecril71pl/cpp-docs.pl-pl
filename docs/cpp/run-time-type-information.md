---
title: Informacje typu Run-Time | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9ce0094bce1f8e7590cef0cbe3bfe85f35158d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056064"
---
# <a name="run-time-type-information"></a>Informacje o typie uzyskiwanym w czasie rzeczywistym

Informacje typu Run-time (RTTI) to mechanizm, który pozwala, aby typ obiektu był ustalony podczas wykonywania programu. RTTI został dodany do języka C++, ponieważ wielu dostawców bibliotek klas zostały Implementowanie tę funkcję samodzielnie. Przyczyną niezgodności między bibliotekami. W związku z tym, stała się oczywista, obsługa informacje typu run-time wymaganego na poziomie języka.

Dla jasności tej dyskusji RTTI jest prawie całkowicie ograniczony do wskaźników. Jednak kwestie omówione mają zastosowanie również do odwołań.

Istnieją trzy główne elementy języka C++ do informacje typu run-time:

- [Dynamic_cast](../cpp/dynamic-cast-operator.md) operatora.

   Używany na potrzeby konwersji typów polimorficznych.

- [Typeid](../cpp/typeid-operator.md) operatora.

   Umożliwia identyfikowanie dokładnego typu obiektu.

- [Type_info](../cpp/type-info-class.md) klasy.

   Używane do przechowywania informacji o typie zwrócony przez **typeid** operatora.

## <a name="see-also"></a>Zobacz także

[Rzutowanie](../cpp/casting.md)