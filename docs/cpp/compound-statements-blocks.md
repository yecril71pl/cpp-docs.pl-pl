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
ms.openlocfilehash: 6aef2a0b5716ab501fabe80f0dda15080abe3ff5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154867"
---
# <a name="compound-statements-blocks"></a>Instrukcje złożone (bloki)

Instrukcja złożona składa się z zero lub więcej instrukcji ujęta w nawiasy klamrowe (**{}**). Instrukcja złożona może służyć wszędzie tam, gdzie Oczekiwano instrukcji. Instrukcje złożone są często nazywane "blokuje".

## <a name="syntax"></a>Składnia

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Uwagi

W poniższym przykładzie użyto instrukcji złożonej jako *instrukcji* wchodzi w skład **Jeśli** — instrukcja (zobacz [if — instrukcja](../cpp/if-else-statement-cpp.md) szczegółowe informacje na temat składni):

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
>  Ponieważ deklaracja znajduje się zdanie, deklaracja może być jednym z instrukcji w *listy instrukcji*. W rezultacie nazwy zadeklarowane wewnątrz instrukcji złożonej, ale nie zostały jawnie zadeklarowane jako statyczne, mają zakres lokalny i (dla obiektów) okres istnienia. Zobacz [zakres](../cpp/scope-visual-cpp.md) szczegółowe informacje na temat przetwarzania nazw z zakresem lokalnym.

## <a name="see-also"></a>Zobacz także

[Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)