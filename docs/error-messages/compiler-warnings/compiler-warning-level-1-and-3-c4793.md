---
title: Kompilator ostrzegawcze (poziom 1 i 3) C4793 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4793
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56b60a028f3fa1a847d4242c0768f8082d6a686e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Ostrzeżenie kompilatora (poziom 1 i 3) C4793
"Funkcja": funkcja jest skompilowany, ponieważ kod natywny: "Przyczyna"  
  
 Kompilator nie można skompilować *funkcja* kodu zarządzanego, nawet jeśli [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) określono opcję kompilatora. Zamiast tego kompilator emituje ostrzeżenie C4793 i komunikat wyjaśniające kontynuacji, a następnie kompiluje *funkcja* kodu natywnego. Zawiera komunikat kontynuacji *Przyczyna* tekst, który zawiera informacje o przyczynie *funkcja* nie można skompilować do `MSIL`.  
  
 Jest to ostrzeżenia poziomu 1 po określeniu `/clr:pure` — opcja kompilatora.  **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015.  
  
 W poniższej tabeli wymieniono wszystkie komunikaty o ewentualnej kontynuacji.  
  
|Przyczyna wiadomości|Uwagi|  
|--------------------|-------------|  
|Wyrównane typy danych nie są obsługiwane w kodzie zarządzanym|Środowisko CLR musi mieć możliwość przydzielić danych zgodnie z potrzebami, który może nie być możliwe, jeśli dane jest wyrównywana z deklaracji, takich jak [__m128](../../cpp/m128.md) lub [Dopasuj](../../cpp/align-cpp.md).|  
|Funkcje, które używają "__ImageBase" nie są obsługiwane w kodzie zarządzanym|`__ImageBase` to symbol konsolidatora specjalne, który zazwyczaj jest używany tylko przez kod natywny niskiego poziomu można załadować biblioteki DLL.|  
|varargs nie są obsługiwane przez "/ clr" — opcja kompilatora|Funkcje natywne nie można wywołać zarządzanych funkcje, które mają [listy zmiennych argumentów](../../cpp/functions-with-variable-argument-lists-cpp.md) (VARARG) ponieważ funkcje mają wymagania układ różnych stosu. Jednak jeśli określisz `/clr:pure` — opcja kompilatora, zmiennych argumentów listy są obsługiwane, ponieważ zestaw może zawierać tylko funkcje zarządzania. Aby uzyskać więcej informacji, zobacz [czystej i weryfikowalny kod (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|  
|64-bitowym CLR nie obsługuje danych zadeklarowana z modyfikatorem __ptr32|Wskaźnik musi być taki sam rozmiar jak wskaźnik natywny na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|  
|32-bitowym CLR nie obsługuje danych zadeklarowana z modyfikatorem __ptr64|Wskaźnik musi być taki sam rozmiar jak wskaźnik natywny na bieżącej platformie. Aby uzyskać więcej informacji, zobacz [__ptr32, \__ptr64](../../cpp/ptr32-ptr64.md).|  
|Funkcje wewnętrzne co najmniej jeden nie jest obsługiwana w zarządzanym kodzie|Wewnętrzna nazwa nie jest dostępny w czasie, które są emitowane wiadomości. Jednak wewnętrznie powodujący zazwyczaj ten komunikat reprezentuje instrukcji maszyny niskiego poziomu.|  
|Wbudowany natywny zestaw (__asm) nie jest obsługiwane w kodzie zarządzanym|[Kod zestawu wbudowanego](../../assembler/inline/asm.md) może zawierać dowolne kodu natywnego, które nie mogą być zarządzane.|  
|Konwersja funkcji wirtualnej z systemem innym niż __clrcall musi być kompilowane jako natywne|Niż[__clrcall](../../cpp/clrcall.md) thunk funkcji wirtualnej muszą używać adresu niezarządzane.|  
|Funkcji za pomocą "_setjmp" musi być kompilowane jako natywne|Środowisko CLR musi mieć możliwość kontrolowania wykonywania programu. Jednak [setjmp](../../cpp/using-setjmp-longjmp.md) funkcja pomija program regularnego wykonywania przez zapisywanie i przywracanie informacji niskiego poziomu, takich jak rejestrów i stanu wykonywania.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4793.  
  
```  
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
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4793.  
  
```  
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