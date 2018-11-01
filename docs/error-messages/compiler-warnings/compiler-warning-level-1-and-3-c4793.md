---
title: Ostrzeżenie kompilatora (poziom 1 i 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: e7ca3b10e09b0d6818fbc7f5607ebc9c95c7f15c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623252"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Ostrzeżenie kompilatora (poziom 1 i 3) C4793

> "*funkcja*": funkcja jest kompilowana jako kod natywny: "*Przyczyna*"

## <a name="remarks"></a>Uwagi

Kompilator nie może skompilować *funkcja* wywołanie kodu zarządzanego, nawet jeśli [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) określono opcję kompilatora. Zamiast tego kompilator emituje ostrzeżenie C4793 i komunikat wyjaśniający kontynuacji, a następnie kompiluje *funkcja* kod natywny. Komunikat kontynuacji zawiera *Przyczyna* tekst, który wyjaśnia, dlaczego *funkcja* nie może zostać skompilowana do `MSIL`.

To ostrzeżenie poziomu 1 po określeniu **/CLR: pure** — opcja kompilatora.  **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Poniższa tabela zawiera listę wszystkich możliwych kontynuacji wiadomości.

|Przyczyna wiadomości|Uwagi|
|--------------------|-------------|
|Wyrównane typy danych nie są obsługiwane w kodzie zarządzanym|Środowisko CLR musi być w stanie przydzielić danych zgodnie z potrzebami, która może nie być możliwe w przypadku danych jest powiązana z deklaracji, takich jak [__m128](../../cpp/m128.md) lub [wyrównać](../../cpp/align-cpp.md).|
|Funkcje, które używają "__ImageBase" nie są obsługiwane w kodzie zarządzanym|`__ImageBase` jest symbol specjalny konsolidatora, który zazwyczaj jest używana tylko przez kod macierzysty niskiego poziomu można załadować biblioteki DLL.|
|varargs nie są obsługiwane przez "/ clr" — opcja kompilatora|Funkcje natywne nie można wywołać funkcji zarządzanych, które mają [listy zmiennych argumentów](../../cpp/functions-with-variable-argument-lists-cpp.md) (VARARG), ponieważ funkcje mają inny stos wymagania związane z układem. Jednak w przypadku określenia **/CLR: pure** — opcja kompilatora, zmiennym argumentem list są obsługiwane, ponieważ zestaw może zawierać tylko funkcje zarządzane. Aby uzyskać więcej informacji, zobacz [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|64-bitowe środowisko CLR nie obsługuje danych zadeklarowany za pomocą modyfikatora __ptr32|Wskaźnik musi być taki sam rozmiar jak wskaźnik natywny na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|32-bitowe środowisko CLR nie obsługuje danych zadeklarowany za pomocą modyfikatora __ptr64|Wskaźnik musi być taki sam rozmiar jak wskaźnik natywny na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|
|Funkcje wewnętrzne co najmniej jeden nie jest obsługiwana w kodzie zarządzanym|Nazwa wewnętrznego nie jest dostępna w czasie, który jest emitowane wiadomości. Jednak wewnętrznie, powoduje, że ten komunikat zazwyczaj reprezentuje instrukcji niskiego poziomu maszyny.|
|Wbudowany natywny zestaw (__asm) nie jest obsługiwana w kodzie zarządzanym|[Wbudowany kod asemblera](../../assembler/inline/asm.md) może zawierać dowolne kodu natywnego, które nie mogą być zarządzane.|
|Wywołanie funkcji wirtualnej __clrcall nie muszą być kompilowane jako natywne|Innej niż[__clrcall](../../cpp/clrcall.md) thunk funkcji wirtualnej musi używać adresu niezarządzanych.|
|Funkcji za pomocą "_setjmp powoduje" muszą być kompilowane jako natywne|Środowisko CLR musi mieć możliwość kontrolowania wykonywania programu. Jednak [setjmp](../../cpp/using-setjmp-longjmp.md) funkcja pomija wykonywania regularnych programu, zapisywanie i przywracanie informacji niskiego poziomu, takie jak rejestrów i stan wykonywania.|

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4793.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

Poniższy przykład spowoduje wygenerowanie C4793.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```