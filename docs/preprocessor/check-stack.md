---
title: check_stack
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.check_stack
- check_stack_CPP
helpviewer_keywords:
- check_stack pragma
- pragmas, check_stack
- pragmas, check_stack usage table
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
ms.openlocfilehash: 93ded20bde98cc4e7b0fc15fd8332195d38f2543
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451990"
---
# <a name="checkstack"></a>check_stack
Instruuje kompilator, aby wyłączyć sondy stosu, jeśli `off` (lub `-`) jest określony, lub Włącz sondy stosu, jeśli `on` (lub `+`) jest określony.

## <a name="syntax"></a>Składnia

```
#pragma check_stack([ {on | off}] )
#pragma check_stack{+ | -}
```

## <a name="remarks"></a>Uwagi

Jeśli żaden argument nie zostanie podany, sondy stosu są traktowane zgodnie z domyślną. Ta dyrektywa pragma uwzględniona na pierwszej funkcji zdefiniowanych po pragmy jest widoczny. Sondy stosu należą ani makr, ani nie ma funkcji, które są wbudowane wygenerowany.

Jeśli nie udzielisz argument **check_stack** pragma, sprawdzeniem stosu powraca do zachowanie określone w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [odwołanie do kompilatora](../build/reference/compiler-options.md). Interakcja `#pragma check_stack` i [/GS](../build/reference/gs-control-stack-checking-calls.md) opcji podsumowanych w poniższej tabeli.

### <a name="using-the-checkstack-pragma"></a>Za pomocą check_stack Pragma

|Składnia|Skompilowany przy użyciu<br /><br /> Opcja/GS?|Akcja|
|------------|------------------------------------|------------|
|`#pragma check_stack( )` lub<br /><br /> `#pragma check_stack`|Tak|Wyłącza sprawdzanie stosu dla funkcji, które należy wykonać|
|`#pragma check_stack( )` lub<br /><br /> `#pragma check_stack`|Nie|Włącza sprawdzanie stosu dla funkcji, które należy wykonać|
|`#pragma check_stack(on)`<br /><br /> lub `#pragma check_stack +`|Tak lub nie|Włącza sprawdzanie stosu dla funkcji, które należy wykonać|
|`#pragma check_stack(off)`<br /><br /> lub `#pragma check_stack -`|Tak lub nie|Wyłącza sprawdzanie stosu dla funkcji, które należy wykonać|

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)