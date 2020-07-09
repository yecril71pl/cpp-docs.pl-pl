---
title: /Gh (Włącz funkcję _penter Hook)
description: Opisuje opcję kompilatora/GH w celu wywołania podanej funkcji _penter.
ms.date: 07/06/2020
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 96597d964e6a341aa25f4d52d34974949eb7b096
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058584"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (Włącz funkcję _penter Hook)

Powoduje wywołanie `_penter` funkcji na początku każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

> **`/Gh`**

## <a name="remarks"></a>Uwagi

`_penter`Funkcja nie jest częścią żadnej biblioteki. Istnieje możliwość podania definicji `_penter` .

Jeśli nie planujesz jawnie wywołania `_penter` , nie musisz podawać prototypu. Funkcja musi wypchnąć zawartość wszystkich rejestrów we wpisie i wyskakującą niezmieniona zawartość przy zamykaniu. Musi wyglądać tak, jakby miał następujący prototyp:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Ta deklaracja nie jest dostępna dla projektów 64-bitowych.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę właściwości **Konfiguracja**  >  wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy kod, podczas kompilowania z **/GH**, pokazuje, jak `_penter` jest wywoływana dwukrotnie; raz podczas wprowadzania funkcji `main` i raz podczas wprowadzania funkcji `x` . Przykład składa się z dwóch plików źródłowych, które są kompilowane osobno.

```cpp
// local_penter.cpp
// compile with: cl /EHsc /c local_penter.cpp
// processor: x86
#include <stdio.h>

extern "C" void __declspec(naked) __cdecl _penter( void ) {
   _asm {
      push eax
      push ebx
      push ecx
      push edx
      push ebp
      push edi
      push esi
    }

   printf_s("\nIn a function!");

   _asm {
      pop esi
      pop edi
      pop ebp
      pop edx
      pop ecx
      pop ebx
      pop eax
      ret
    }
}
```

```cpp
// Gh_compiler_option.cpp
// compile with: cl /EHsc /Gh Gh_compiler_option.cpp local_penter.obj
// processor: x86
#include <stdio.h>

void x() {}

int main() {
   x();
}
```

W przypadku uruchomienia, `_penter` funkcja lokalna jest wywoływana przy wpisie do `main` i `x` :

```Output

In a function!
In a function!
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[`/GH`(Włącz funkcję Hook _pexit)](gh-enable-pexit-hook-function.md)
