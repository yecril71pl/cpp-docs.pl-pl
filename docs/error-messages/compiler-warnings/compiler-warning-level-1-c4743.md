---
title: Kompilator ostrzeżenie (poziom 1) C4743
ms.date: 11/04/2016
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: d17fd65f1108aab6e3ce97ec75c0ffb899c06cda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152011"
---
# <a name="compiler-warning-level-1-c4743"></a>Kompilator ostrzeżenie (poziom 1) C4743

"*typu*"ma inny rozmiar "*plik1*"i"*plik2*": *numer* i *numer* bajtów

Zewnętrznej zmiennej lub odwołuje się do zdefiniowanych w dwóch plikach ma różne typy w tych plikach, a kompilator ustali, że rozmiar zmiennej w *plik1* różni się od rozmiar zmiennej w *plik2*.

Istnieje ważna przypadek, gdy to ostrzeżenie może być emitowana dla języka C++. W przypadku takich samych typach o tej samej nazwie w dwóch różnych plikach, jeśli te deklaracje zawierać funkcji wirtualnych, a deklaracji nie są takie same, kompilator może emitować ostrzeżenie C4744 dla tabel funkcję wirtualną. To ostrzeżenie występuje, ponieważ istnieją dwie tabele różnych wielkości funkcję wirtualną dla tego samego typu i konsolidatora należy wybrać jeden z nich, aby dołączyć do pliku wykonywalnego.  Istnieje możliwość, że może to spowodować wywołanie funkcji wirtualnej niewłaściwy program.

Aby rozwiązać to ostrzeżenie, użyj jednej definicji typu albo używać różnych nazw typów lub zmienne.

## <a name="example"></a>Przykład

W tym przykładzie zawiera jedną definicję tego typu.

```
// C4743a.cpp
// compile with: /c
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4743.

```
// C4743b.cpp
// compile with: C4743a.cpp /W1 /GL /O2
// C4743 expected
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```