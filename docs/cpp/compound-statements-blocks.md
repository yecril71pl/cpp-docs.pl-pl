---
title: Instrukcje złożone (bloki)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337346"
---
# <a name="compound-statements-blocks"></a>Instrukcje złożone (bloki)

Instrukcja złożona składa się z instrukcji zero lub więcej ujętych w nawiasach klamrowych (**{ }**). Instrukcja złożona może być używana wszędzie tam, gdzie oczekuje się instrukcji. Instrukcje złożone są powszechnie nazywane "bloki."

## <a name="syntax"></a>Składnia

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Uwagi

W poniższym przykładzie użyto instrukcji złożonej jako części *instrukcji* **if** (zobacz [Instrukcja if, aby](../cpp/if-else-statement-cpp.md) uzyskać szczegółowe informacje na temat składni):

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> Ponieważ deklaracja jest instrukcją, deklaracja może być jedną z instrukcji na *liście instrukcji*. W rezultacie nazwy zadeklarowane wewnątrz instrukcji złożonej, ale nie jawnie zadeklarowane jako statyczne, mają zakres lokalny i (dla obiektów) okres istnienia. Zobacz [Zakres](../cpp/scope-visual-cpp.md) szczegółowe informacje na temat traktowania nazw z zakresem lokalnym.

## <a name="see-also"></a>Zobacz też

[Omówienie instrukcji języka C++](../cpp/overview-of-cpp-statements.md)
