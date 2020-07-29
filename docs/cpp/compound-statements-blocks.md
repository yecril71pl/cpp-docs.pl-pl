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
ms.openlocfilehash: a06a3d9ce887150ba3333e8e9e874ab337f8b4df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221812"
---
# <a name="compound-statements-blocks"></a>Instrukcje złożone (bloki)

Złożona instrukcja składa się z zero lub więcej instrukcji ujętych w nawiasy klamrowe (**{}**). Złożonej instrukcji można użyć wszędzie tam, gdzie jest oczekiwana instrukcja. Złożone instrukcje są zwykle nazywane "blokami".

## <a name="syntax"></a>Składnia

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Uwagi

W poniższym przykładzie użyto złożonej instrukcji jako części *instrukcji* **`if`** instrukcji (patrz [instrukcja IF](../cpp/if-else-statement-cpp.md) w celu uzyskania szczegółowych informacji o składni):

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
> Ponieważ deklaracja jest instrukcją, deklaracja może być jedną z instrukcji na *liście instrukcji*. W związku z tym nazwy zadeklarowane wewnątrz instrukcji złożonej, ale nie są jawnie zadeklarowane jako static, mają zakres lokalny i (dla obiektów) okres istnienia. Zobacz [zakres](../cpp/scope-visual-cpp.md) , aby uzyskać szczegółowe informacje na temat traktowania nazw z zakresem lokalnym.

## <a name="see-also"></a>Zobacz także

[Omówienie instrukcji języka C++](../cpp/overview-of-cpp-statements.md)
