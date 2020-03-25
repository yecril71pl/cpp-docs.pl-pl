---
title: Instrukcje iteracji (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
ms.openlocfilehash: e8f064fd19e69de2819673f48a7f14e26d60b87e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178262"
---
# <a name="iteration-statements-c"></a>Instrukcje iteracji (C++)

Instrukcje iteracji powodują, że instrukcje (lub złożone instrukcje), które mają być wykonywane zero lub więcej razy, podlegają pewnym kryteriom zakończenia pętli. Kiedy te instrukcje są instrukcjami złożonymi, są wykonywane w kolejności, z wyjątkiem przypadków, gdy napotkana jest instrukcja [Break](../cpp/break-statement-cpp.md) lub [Continue](../cpp/continue-statement-cpp.md) .

C++zawiera cztery instrukcje iteracji — [while](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [dla](../cpp/for-statement-cpp.md)i z [zakresu dla](../cpp/range-based-for-statement-cpp.md). Każda z tych iteracji wykonuje iteracje do momentu, gdy jego wyrażenie zakończenia zwróci wartość zero (false) lub do momentu zakończenia pętli z instrukcją **Break** . Poniższa tabela zawiera podsumowanie tych instrukcji i ich działań; Każdy z nich został szczegółowo omówiony w poniższych sekcjach.

### <a name="iteration-statements"></a>Instrukcje iteracji

|Wyciąg|Oceniane na|Inicjowanie|Pełny|
|---------------|------------------|--------------------|---------------|
|**while**|Góra pętli|Nie|Nie|
|**do**|Dolna pętla|Nie|Nie|
|**for**|Góra pętli|Yes|Yes|
|**oparte na zakresie dla**|Góra pętli|Yes|Yes|

Część instrukcji instrukcji iteracji nie może być deklaracją. Jednak może to być złożonej instrukcji zawierającej deklarację.

## <a name="see-also"></a>Zobacz też

[Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)
