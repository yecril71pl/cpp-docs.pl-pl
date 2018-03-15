---
title: "/ Zc: inline (usuwanie nieużywanej sekcji COMDAT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a9c62ea6557ba6ba575fc71a34f39d24f41f76fd
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (usuwanie nieużywanej sekcji COMDAT)

Usuwa funkcje nieużywane lub dane, które są Comdat lub mieć tylko powiązania wewnętrznego. Gdy **/Zc: inline** określono kompilatora wymaga jednostek tłumaczenia, korzystających z wbudowanym danych lub funkcji śródwierszowych musi także obejmować definicje danych lub funkcji.

## <a name="syntax"></a>Składnia

> **/Zc:inline**[**-**]

## <a name="remarks"></a>Uwagi

Gdy **/Zc: inline** określono kompilator nie Emituj informacje o symbolach dla nieużywanej sekcji COMDAT funkcji lub danych lub funkcji lub dane, które mają tylko powiązanie wewnętrzne. Tego rodzaju optymalizacji upraszcza niektóre pracy wykonanej przez konsolidator w kompilacjach wydania lub gdy opcja konsolidatora [/OPT:REF](../../build/reference/opt-optimizations.md) jest określona. Gdy kompilator wykonuje tego rodzaju optymalizacji, można znacznie zmniejszyć rozmiar pliku .obj i poprawy szybkości konsolidatora. Ta opcja kompilatora nie jest włączona, gdy optymalizacje są wyłączone ([/Od](../../build/reference/od-disable-debug.md)) lub gdy [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md) jest określona.

Domyślnie ta opcja jest wyłączona (**/Zc:inline-**). [/ Ograniczająca-](permissive-standards-conformance.md) nie obsługuje opcji **/Zc: inline**.

Jeśli **/Zc: inline** określono kompilator wymusza C ++ 11 konieczność zgłoszonego przez wszystkie funkcje `inline` muszą być dostępne w tej samej jednostce tłumaczenia definicji, jeśli są one używane. Jeśli nie określono opcji, kompilator Microsoft umożliwia zgodność z systemem innym niż kod, który wywołuje funkcje zadeklarowany `inline` nawet, jeśli definicja nie jest widoczne. Aby uzyskać więcej informacji zobacz C ++ 11 standard, w wersji 3.2 i sekcji 7.1.2. Ta opcja kompilatora została wprowadzona w programie Visual Studio 2013 Update 2.

Aby użyć **/Zc: inline** opcję Kod niezgodnych aktualizacji.

W tym przykładzie pokazano sposób użycia niezgodnych deklaracji funkcji wbudowanej bez definicji nadal kompiluje i łączy, gdy domyślny **/Zc:inline-** jest używana opcja:

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

Gdy **/Zc: inline** jest włączona, taki sam kod przyczyny [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) błąd, ponieważ kompilator nie Emituj treść kodu z systemem innym niż wbudowane `Example::inline_call` w example.obj. Powoduje to wywołanie z systemem innym niż wbudowane `main` do odwołania Niezdefiniowany symbol zewnętrzny.

Aby rozwiązać ten problem, można usunąć `inline` — słowo kluczowe z deklaracji `Example::inline_call`, Przenieś definicji `Example::inline_call` w nagłówku pliku, lub Przenieś wykonania `Example` do main.cpp. Kolejnym przykładzie przenosi definicji do pliku nagłówka, gdzie jest widoczny dla każdego obiektu wywołującego, który zawiera nagłówek.

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

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **języka** strony właściwości.

1. Modyfikowanie **Usuń nieużywane kod i dane** właściwości, a następnie wybierz pozycję **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
