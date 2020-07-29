---
title: Ostrzeżenie kompilatora (poziom 1) C4530
description: Przewodnik referencyjny dotyczący ostrzeżenia kompilatora języka Microsoft C++ C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: fe0a2b4c8eb881327f3e59d66e7e6941f0a2cad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230665"
---
# <a name="compiler-warning-level-1-c4530"></a>Ostrzeżenie kompilatora (poziom 1) C4530

> Użyto programu obsługi wyjątków języka C++, ale nie włączono semantyki operacji unwind. Określ/EHsc

Kod używa obsługi wyjątków języka C++, ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nie został uwzględniony w opcjach kompilatora.

## <a name="remarks"></a>Uwagi

Kompilator wymaga **`/EHsc`** opcji kompilowania kodu c++, który następuje po standardzie c++ dla obsługi wyjątków. Standardowa *semantyka* odwinięcia C++ określa, że obiekty i ramki stosu zbudowane między miejscem, w którym jest generowany wyjątek, a które zostały przechwycone, muszą zostać zniszczone i odzyskane zasoby. Ten proces jest nazywany *rozwinięcia stosu*.

**`/EHsc`** Opcja nakazuje kompilatorowi generowanie kodu, który wywołuje destruktory na automatycznym obiekcie magazynu, gdy wyjątek przechodzi przez zawierającą ramkę stosu. *Automatyczne obiekty magazynu* są obiektami przydzielonymi na stosie, takimi jak zmienne lokalne. Jest on nazywany automatycznym magazynem, ponieważ jest przypisywany automatycznie, gdy funkcje są wywoływane i udostępniane automatycznie po powrocie. *Ramka stosu* jest danymi umieszczonymi na stosie, gdy wywoływana jest funkcja, wraz z jej automatycznym magazynem.

Gdy wyjątek jest zgłaszany, może przechodzić przez kilka ramek stosu przed przechwyconą. Te ramki stosu muszą być rozwiązane, gdy wyjątek przechodzi przez nich w odwrotnej kolejności wywoływania. Aby odzyskiwać swoje zasoby, należy zniszczyć automatyczne obiekty magazynu w każdej klatce stosu. Jest to ten sam proces niszczenia i odzyskiwania, który odbywa się automatycznie, gdy funkcja zwraca normalne.

Gdy ta **`/EHsc`** opcja nie jest włączona, automatyczne obiekty magazynu w ramkach stosu między funkcją zgłaszania a funkcją, w której został przechwycony wyjątek nie są niszczone. Tylko automatyczne obiekty magazynu utworzone w **`try`** **`catch`** bloku lub zostaną zniszczone, co może prowadzić do znacznego wycieku zasobów i innych nieoczekiwanych zachowań.

Jeśli w pliku wykonywalnym mogą zostać zgłoszone wyjątki, można bezpiecznie zignorować to ostrzeżenie. Jakiś kod może wymagać innych opcji obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Skompiluj próbkę, **`/EHsc`** Aby rozwiązać ten problem.
