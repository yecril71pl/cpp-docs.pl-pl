---
title: /Gh (Włącz funkcję _penter Hook)
ms.date: 11/04/2016
f1_keywords:
- _penter
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _penter function
- -Gh compiler option [C++]
ms.assetid: 1510a082-8a0e-486e-a309-6add814b494f
ms.openlocfilehash: 87815b5f0e0450b84acbe3c35b7ef4f31216ec72
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749294"
---
# <a name="gh-enable-_penter-hook-function"></a>/Gh (Włącz funkcję _penter Hook)

Powoduje wywołanie `_penter` funkcji na początku każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

```
/Gh
```

## <a name="remarks"></a>Uwagi

Funkcja `_penter` nie jest częścią żadnej biblioteki i to do `_penter`Ciebie należy podanie definicji .

Jeśli nie planujesz `_penter`jawnie wywołać, nie trzeba podać prototypu. Funkcja musi wyglądać tak, jakby miała następujący prototyp i musi wypchnąć zawartość wszystkich rejestrów przy wejściu i pop niezmienionej zawartości na wyjściu:

```cpp
void __declspec(naked) __cdecl _penter( void );
```

Ta deklaracja nie jest dostępna dla projektów 64-bitowych.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Wiersz polecenia.**

1. Wpisz opcję kompilatora w polu **Opcje dodatkowe.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy kod, po skompilowaniu `_penter` z **/Gh**, pokazuje, jak jest wywoływana dwa razy; raz podczas wprowadzania funkcji `main` i `x`raz podczas wprowadzania funkcji .

```cpp
// Gh_compiler_option.cpp
// compile with: /Gh
// processor: x86
#include <stdio.h>
void x() {}

int main() {
   x();
}

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

```Output
In a function!
In a function!
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
