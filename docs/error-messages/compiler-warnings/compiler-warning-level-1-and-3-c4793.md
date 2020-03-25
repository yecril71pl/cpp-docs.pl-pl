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
ms.openlocfilehash: de6f514d8e3ad8e7715c9cd13a695e3398fffc8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164810"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Ostrzeżenie kompilatora (poziom 1 i 3) C4793

> "*Function*": funkcja została skompilowana jako kod natywny: "*Przyczyna*"

## <a name="remarks"></a>Uwagi

Kompilator nie może kompilować *funkcji* do kodu zarządzanego, mimo że określono opcję kompilatora [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Zamiast tego kompilator emituje ostrzeżenie C4793 i wyjaśniający komunikat kontynuacji, a następnie kompiluje *funkcję* w kodzie natywnym. Komunikat kontynuacji zawiera tekst *przyczyny* wyjaśniający, dlaczego nie można skompilować *funkcji* do `MSIL`.

Jest to ostrzeżenie poziomu 1 w przypadku określenia opcji **/CLR: Pure** kompilatora.  **/CLR: Pure** kompilator Option jest przestarzały w programie visual Studio 2015 i nieobsługiwany w programie visual Studio 2017.

W poniższej tabeli wymieniono wszystkie możliwe komunikaty kontynuacji.

|Komunikat dotyczący przyczyny|Uwagi|
|--------------------|-------------|
|Wyrównane typy danych nie są obsługiwane w kodzie zarządzanym|Środowisko CLR musi być w stanie alokować dane zgodnie z wymaganiami, co może nie być możliwe, jeśli dane są wyrównane z deklaracjami, takimi jak [__m128](../../cpp/m128.md) lub [align](../../cpp/align-cpp.md).|
|Funkcje używające "__ImageBase" nie są obsługiwane w kodzie zarządzanym|`__ImageBase` jest specjalnym symbolem konsolidatora, który jest zazwyczaj używany tylko przez kod natywny niskiego poziomu do załadowania biblioteki DLL.|
|element VarArgs nie jest obsługiwany przez opcję kompilatora "/CLR"|Funkcje natywne nie mogą wywoływać funkcji zarządzanych, które mają [listę zmiennych argumentów](../../cpp/functions-with-variable-argument-lists-cpp.md) (VarArgs), ponieważ funkcje mają różne wymagania układu stosu. Jeśli jednak określisz opcję **/CLR: Pure** kompilatora, listy zmiennych argumentów są obsługiwane, ponieważ zestaw może zawierać tylko funkcje zarządzane. Aby uzyskać więcej informacji, zobacz [czysty i możliwy doC++zweryfikowania kod (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|64-bitowe środowisko CLR nie obsługuje danych zadeklarowanych za pomocą modyfikatora __ptr32|Wskaźnik musi mieć taki sam rozmiar jak natywny wskaźnik na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|32-bitowe środowisko CLR nie obsługuje danych zadeklarowanych za pomocą modyfikatora __ptr64|Wskaźnik musi mieć taki sam rozmiar jak natywny wskaźnik na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32 \__ptr64](../../cpp/ptr32-ptr64.md).|
|Co najmniej jeden z elementów wewnętrznych nie jest obsługiwany w kodzie zarządzanym|Nazwa wewnętrzna nie jest dostępna w chwili, gdy komunikat jest emitowany. Jednak wewnętrznie, które powoduje, że ten komunikat zazwyczaj reprezentuje instrukcję komputera niskiego poziomu.|
|Wbudowany zestaw natywny ("__asm") nie jest obsługiwany w kodzie zarządzanym|[Wbudowany kod asemblera](../../assembler/inline/asm.md) może zawierać dowolny kod natywny, którego nie można zarządzać.|
|Thunk funkcji wirtualnych innej niż __clrcall muszą być skompilowane jako natywne|Funkcja wirtualna[nie__clrcall](../../cpp/clrcall.md) thunk musi używać niezarządzanego adresu.|
|Funkcja używająca elementu "_setjmp" musi być skompilowana jako natywna|Środowisko CLR musi być w stanie kontrolować wykonywanie programu. Jednak funkcja [setjmp](../../cpp/using-setjmp-longjmp.md) pomija regularne wykonywanie programów przez zapisanie i przywrócenie informacji niskiego poziomu, takich jak rejestry i stan wykonania.|

## <a name="example"></a>Przykład

Poniższy przykład generuje C4793.

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

Poniższy przykład generuje C4793.

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
