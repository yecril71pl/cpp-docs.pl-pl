---
title: Ostrzeżenie kompilatora (poziom 1) C4530
description: Przewodnik po kompilatorze Microsoft C++ ostrzeżenie C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369784"
---
# <a name="compiler-warning-level-1-c4530"></a>Ostrzeżenie kompilatora (poziom 1) C4530

> Używany program obsługi wyjątków języka C++, ale nie są włączone semantyka unwind. Określ /EHsc

Kod używa obsługi wyjątków języka C++, ale [/EHsc](../../build/reference/eh-exception-handling-model.md) nie został uwzględniony w opcjach kompilatora.

## <a name="remarks"></a>Uwagi

Kompilator wymaga **`/EHsc`** opcji do tworzenia kodu C++, który następuje standard C++ dla obsługi wyjątków. *Semantyka odwijania* standardu C++ określa, że obiekty i ramki stosu skonstruowane między miejscem, w którym jest generowany wyjątek i miejscem jego przełowienia, muszą zostać zniszczone, a ich zasoby odzyskane. Ten proces jest znany jako *odwijanie stosu*.

Opcja **`/EHsc`** nakazuje kompilatorowi do generowania kodu, który wywołuje destruktory na obiektach magazynu automatycznego, gdy wyjątek przechodzi przez ramkę stosu zawierającego. *Obiekty magazynu automatycznego* są obiektami przydzielonymi na stosie, takimi jak zmienne lokalne. Nazywa się to magazynem automatycznym, ponieważ jest przydzielany automatycznie, gdy funkcje są wywoływane, i zwalniany automatycznie po ich powrocie. *Ramka stosu* to dane umieszczone na stosie, gdy wywoływana jest funkcja, wraz z jej automatycznym przechowywaniem.

Gdy wyjątek, może podróżować przez kilka ramek stosu, zanim zostanie przechwycony. Te ramki stosu muszą zostać rozwiń, ponieważ wyjątek przechodzi przez nie w odwrotnej kolejności wywoływania. Obiekty magazynu automatycznego w każdej ramce stosu muszą zostać zniszczone, aby odzyskać swoje zasoby w sposób czysty. Jest to ten sam proces niszczenia i odzyskiwania, który odbywa się automatycznie, gdy funkcja zwraca się normalnie.

Gdy **`/EHsc`** opcja nie jest włączona, automatyczne obiekty magazynu w ramkach stosu między funkcją zgłaszania a funkcją, w której zostanie przechwycony wyjątek, nie zostaną zniszczone. Tylko automatyczne obiekty magazynu utworzone w bloku **try** lub **catch** zostają zniszczone, co może prowadzić do znacznych przecieków zasobów i innych nieoczekiwanych zachowań.

Jeśli w pliku wykonywalnym nie można wrzucać żadnych wyjątków, można bezpiecznie zignorować to ostrzeżenie. Niektóre kody mogą wymagać innych opcji obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Przykład

Następujący przykład generuje C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Skompiluj **`/EHsc`** przykład z, aby rozwiązać ostrzeżenie.
