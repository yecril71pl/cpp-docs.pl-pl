---
title: /Zc:inline (usuwanie nieużywanej sekcji COMDAT)
ms.date: 09/05/2019
f1_keywords:
- /Zc:inline
- VC.Project.VCCLCompilerTool.RemoveUnreferencedCodeData
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
- /Zc:inline
ms.assetid: a4c94224-1d73-4bea-a9d5-4fa73dc924df
ms.openlocfilehash: 290252262254521c024d7b0d6355472199d1f55d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218965"
---
# <a name="zcinline-remove-unreferenced-comdat"></a>/Zc:inline (usuwanie nieużywanej sekcji COMDAT)

Usuwa nieużywane dane lub funkcje, które są COMDAT lub mają tylko połączenie wewnętrzne. W obszarze **/Zc: inline**kompilator określa, że jednostki translacji z danymi wbudowanymi lub funkcjami muszą również zawierać ich definicje.

## <a name="syntax"></a>Składnia

> **/Zc: inline**[ **-** ]

## <a name="remarks"></a>Uwagi

Gdy jest określony **/Zc: inline** , kompilator nie emituje informacji o symbolach dla nieużywanych funkcji COMDAT lub danych. Lub, w przypadku danych lub funkcji, które mają tylko wewnętrzny związek. Ta optymalizacja upraszcza część pracy konsolidatora w kompilacjach wydania lub w przypadku określenia opcji [/OPT: ref](opt-optimizations.md) konsolidatora. Optymalizacja kompilatora może znacznie zmniejszyć rozmiar pliku. obj i zwiększyć szybkość konsolidatora. Opcja kompilatora nie jest włączona w przypadku wyłączenia optymalizacji ([/od](od-disable-debug.md)). Lub, po określeniu [/GL (Optymalizacja całego programu)](gl-whole-program-optimization.md).

Domyślnie ta opcja jest wyłączona (**/Zc: inline-**) w kompilacjach w wierszu polecenia. Opcja [/permissive-](permissive-standards-conformance.md) nie włącza **/Zc: inline**. W projektach programu MSBuild opcja jest ustawiana za pomocą **Właściwości konfiguracji**  >  **Język C/C++**  >  **Language**  >  Usuń kod, którego nie można**odwołać i Właściwość danych** , która domyślnie ma wartość **tak** .

Jeśli określono **/Zc: inline** , kompilator wymusza wymóg języka c++ 11, że wszystkie zadeklarowane funkcje **`inline`** muszą mieć definicję dostępną w tej samej jednostce translacji, jeśli są używane. Gdy ta opcja nie jest określona, kompilator firmy Microsoft zezwala na niezgodny kod, który wywołuje funkcje zadeklarowane, **`inline`** nawet jeśli żadna definicja nie jest widoczna. Aby uzyskać więcej informacji, zobacz Standard C++ 11, w sekcji 3,2 i ppkt 7.1.2. Ta opcja kompilatora została wprowadzona w Visual Studio 2013 Update 2.

Aby użyć opcji **/Zc: inline** , zaktualizuj kod niezgodny.

Ten przykład pokazuje, jak niezgodne użycie deklaracji funkcji wbudowanej bez definicji nadal kompiluje i łączy, gdy zostanie użyta Domyślna **/Zc: line-** Option:

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

int main() {
   Example example;
   example.inline_call(); // normal call when definition unavailable
}
```

Gdy **/Zc: inline** jest włączona, ten sam kod powoduje wystąpienie błędu [LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md) , ponieważ kompilator nie emituje nieliniowej treści kodu dla `Example::inline_call` przykładu. obj. Powoduje to, że wywołanie nieliniowe w `main` celu odwołuje się do niezdefiniowanego symbolu zewnętrznego.

Aby rozwiązać ten problem, można usunąć **`inline`** słowo kluczowe z deklaracji `Example::inline_call` , przenieść definicję `Example::inline_call` do pliku nagłówkowego lub przenieść implementację `Example` do Main. cpp. Następny przykład przenosi definicję do pliku nagłówkowego, gdzie jest widoczny dla każdego obiektu wywołującego, który zawiera nagłówek.

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

int main() {
   Example2 example2;
   example2.inline_call(); // normal call when definition unavailable
}
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja języka**C/C++**  >  **Language** .

1. Zmodyfikuj właściwość **Usuń kod i dane bez odwołań** , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
