---
title: Informacje o typie uzyskiwanym w czasie rzeczywistym
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: 195274d7bcef0ff4d82383a8ec828ca9267573b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178941"
---
# <a name="run-time-type-information"></a>Informacje o typie uzyskiwanym w czasie rzeczywistym

Informacje o typie czasu wykonywania (RTTI) to mechanizm, który umożliwia określenie typu obiektu podczas wykonywania programu. RTTI został dodany do języka C++ , ponieważ wielu dostawców bibliotek klas jednocześnie implementuje te funkcje. Spowodowało to niezgodności między bibliotekami. W rezultacie stało się oczywiste, że obsługa informacji o typie czasu wykonywania była konieczna na poziomie języka.

W celu zapewnienia przejrzystości ta dyskusja dotycząca RTTI jest niemal całkowicie ograniczona do wskaźników. Omawiane koncepcje dotyczą jednak również odwołań.

Istnieją trzy główne C++ elementy języka do informacji o typie w czasie wykonywania:

- Operator [dynamic_cast](../cpp/dynamic-cast-operator.md) .

   Używane do konwersji typów polimorficznych.

- Operator [typeid](../cpp/typeid-operator.md) .

   Służy do identyfikowania dokładnego typu obiektu.

- Klasa [type_info](../cpp/type-info-class.md) .

   Używane do przechowywania informacji o typie zwracanych przez operator **typeid** .

## <a name="see-also"></a>Zobacz też

[Rzutowanie](../cpp/casting.md)
