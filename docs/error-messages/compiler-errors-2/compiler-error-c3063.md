---
title: Błąd kompilatora C3063
ms.date: 11/04/2016
f1_keywords:
- C3063
helpviewer_keywords:
- C3063
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
ms.openlocfilehash: 9e53d9fe273a392695212df6dbeb679822a39068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404224"
---
# <a name="compiler-error-c3063"></a>Błąd kompilatora C3063

operator 'operator': wszystkie operandy muszą posiadać ten sam typ wyliczeniowy

Korzystając z operatorów na modułach wyliczających, oba operandy musi być typem wyliczenia. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie oraz stosowanie wyliczeń w C++sposób niezamierzony](../../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3063 i pokazuje, jak go naprawić:

```
// C3063.cpp
// compile with: /clr
enum class E { a, b } e, mask;
int main() {
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)

   if ( ( e & mask ) != E() )   // OK
      ;
}
```