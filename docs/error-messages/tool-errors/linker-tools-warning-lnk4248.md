---
title: Ostrzeżenie LNK4248 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: db9432c505b7348c9bef5ed34aac1cb4edecb17b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461233"
---
# <a name="linker-tools-warning-lnk4248"></a>Ostrzeżenie LNK4248 narzędzi konsolidatora

Nierozpoznany token typeref (token) dla 'type'; Obraz może nie działać.

Typ nie ma definicji metadanych MSIL.

LNK4248 może wystąpić, gdy jest tylko do przodu deklaracji typu w moduł MSIL (skompilowany przy użyciu **/CLR**), gdzie typ odwołuje się moduł MSIL, a moduł MSIL jest połączony z modułu macierzystego, który zawiera definicję dla Typ.

W takiej sytuacji konsolidator zapewni definicji typu natywnego w metadanych MSIL, a to zapewnienia poprawnego zachowania.

Jednak jeśli deklaracji typu do przodu jest typem CLR, następnie definicji typu natywnego konsolidator posiada może nie być poprawna

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Należy podać definicję typu w moduł MSIL.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK4248. Zdefiniuj A struktury do rozwiązania.

```
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>Przykład

Poniższy przykład zawiera do przodu definicji typu.

```
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie LNK4248.

```
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```