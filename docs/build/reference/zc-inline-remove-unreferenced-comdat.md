---
title: /Zc:inline (usuwanie nieużywanej sekcji COMDAT)
ms.date: 03/01/2018
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 6855773c6ec807a7488fa5604ddee7fd43983135
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441239"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (usuwanie nieużywanej sekcji COMDAT)

Usuwa nieużywane funkcje lub dane, które są Comdat lub mieć tylko powiązanie wewnętrzne. Gdy **/Zc: inline** jest określony, kompilator wymaga jednostki translacji, korzystające z danych wbudowane lub funkcji śródwierszowych należy również uwzględnić definicje danych lub funkcji.

## <a name="syntax"></a>Składnia

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Uwagi

Gdy **/Zc: inline** jest określony, kompilator nie emituje informacje o symbolach dla nieużywanej sekcji COMDAT funkcji lub danych lub funkcji lub dane, które mają tylko powiązanie wewnętrzne. Tego rodzaju optymalizacji upraszcza część pracy wykonanej przez konsolidator w kompilacjach wydania lub opcji konsolidatora [/OPT: REF](../../build/reference/opt-optimizations.md) jest określony. Gdy kompilator wykonuje tego rodzaju optymalizacji, można znacznie zmniejszyć rozmiar pliku .obj i zwiększyć szybkość konsolidatora. Nie włączono tę opcję kompilatora, gdy są wyłączone optymalizacje ([/Od](../../build/reference/od-disable-debug.md)) lub gdy [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md) jest określony.

Domyślnie ta opcja jest wyłączona (**/Zc:inline-**). [/ Permissive-](permissive-standards-conformance.md) opcji nie włącza **/Zc: inline**.

Jeśli **/Zc: inline** jest określony, kompilator wymusza C ++ 11 wymogu, że wszystkie funkcje zadeklarowane `inline` muszą być dostępne w tej samej jednostce translacji definicji, jeśli są one używane. Gdy opcja nie jest określona, kompilator Microsoft umożliwia kod bez zgodności, który wywołuje funkcje zadeklarowane `inline` nawet, jeśli definicja nie jest widoczna. Aby uzyskać więcej informacji zobacz standard C ++ 11, w sekcji 7.1.2 i sekcji 3.2. Tę opcję kompilatora została wprowadzona w Visual Studio 2013 Update 2.

Aby użyć **/Zc: inline** opcji kodu braku zgodności aktualizacji.

Ten przykład przedstawia sposób niezgodny z użytkowania wbudowaną deklarację funkcji bez definicji nadal kompiluje i łączy, gdy domyślny **/Zc:inline-** jest używana opcja:

```cpp
// example.h
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#pragma once

class Example {
public:
   inline void inline_call(); // declared but not defined inline
   void normal_call();
   Example() {};
};
```

```cpp
// example.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include <stdio.h>
#include "example.h"

void Example::inline_call() {
   printf("inline_call was called.\n");
}

void Example::normal_call() {
   printf("normal_call was called.\n");
   inline_call(); // with /Zc:inline-, inline_call forced into .obj file
}
```

```cpp
// zcinline.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline.cpp example.cpp
#include "example.h"

void main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Gdy **/Zc: inline** jest włączona, taki sam kod przyczyny [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) błąd, ponieważ kompilator nie emituje treść-śródwierszowych kodu `Example::inline_call` w example.obj. Powoduje to, że-śródwierszowych wywołania w `main` można odwoływać się do niezdefiniowanego symbolu zewnętrznego.

Aby rozwiązać ten problem, można usunąć `inline` słowo kluczowe z deklaracji `Example::inline_call`, Przenieś definicji `Example::inline_call` w nagłówku pliku lub przenieść wykonania `Example` do main.cpp. Następny przykład przenosi definicji do pliku nagłówka, w których jest ona widoczna na dowolny obiekt wywołujący, który zawiera nagłówek.

```cpp
// example2.h
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#pragma once
#include <stdio.h>

class Example2 {
public:
   inline void inline_call() {
      printf("inline_call was called.\n");
   }
   void normal_call();
   Example2() {};
};
```

```cpp
// example2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void Example2::normal_call() {
   printf("normal_call was called.\n");
   inline_call();
}
```

```cpp
// zcinline2.cpp
// Compile by using: cl /W4 /EHsc /O2 zcinline2.cpp example2.cpp
#include "example2.h"

void main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** stronę właściwości.

1. Modyfikowanie **Usuń nieużywany kod i dane** właściwości, a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
