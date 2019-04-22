---
title: Błąd kompilatora C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 248431afb25aa4b9480818f76388f6ad56d8e006
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777929"
---
# <a name="compiler-error-c3821"></a>Błąd kompilatora C3821

'Funkcja': typ zarządzany lub funkcja nie można używać w funkcji niezarządzanej

Funkcji w zestawie wbudowanym lub [setjmp](../../c-runtime-library/reference/setjmp.md) nie może zawierać typy wartości ani klas zarządzanych. Aby naprawić ten błąd, należy usunąć zestaw wbudowany i `setjmp` lub Usuń obiekty zarządzane.

C3821 może również wystąpić, Jeśli spróbujesz użyć automatycznego przechowywania w funkcji vararg.  Aby uzyskać więcej informacji, zobacz [zmiennej listy argumentów (...) (C++Sposób niezamierzony) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) i [ C++ stosu semantyki dla typów odwołań](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3821.

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3821.

```
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
