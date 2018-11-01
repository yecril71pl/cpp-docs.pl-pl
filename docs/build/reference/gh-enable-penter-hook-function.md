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
ms.openlocfilehash: 8b013d3d6506c1436a1f7f2245461980c0493b5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452315"
---
# <a name="gh-enable-penter-hook-function"></a>/Gh (Włącz funkcję _penter Hook)

Powoduje, że wywołanie `_penter` funkcji na początku każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

```
/Gh
```

## <a name="remarks"></a>Uwagi

`_penter` Funkcja nie jest częścią wszystkie biblioteki i jest maksymalnie musisz podać definicję `_penter`.

Jeśli nie chcesz jawnie wywołać `_penter`, nie należy podać prototypu. Funkcja musi znajdować się tak, jakby miał poniższy prototyp i musi wypychania zawartości wszystkich rejestrów przy uruchamianiu i pop zawartości bez zmian przy zamykaniu:

```
void __declspec(naked) __cdecl _penter( void );
```

Ta deklaracja nie jest dostępne dla projektów 64-bitowych.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy kod, gdy skompilowano z opcją **/Gh**, pokazuje, jak `_penter` jest wywoływana dwa razy; raz podczas wprowadzania funkcji `main` i raz podczas wprowadzania funkcji `x`.

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

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)