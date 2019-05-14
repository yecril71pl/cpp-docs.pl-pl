---
title: Kompilator ostrzeżenie (poziom 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611833"
---
# <a name="compiler-warning-level-1-c4743"></a>Kompilator ostrzeżenie (poziom 1) C4743

"*typu*"ma inny rozmiar "*plik1*"i"*plik2*": *numer* i *numer* bajtów

Zewnętrznej zmiennej lub odwołuje się do zdefiniowanych w dwóch plikach ma różne typy w tych plikach, a kompilator ustali, że rozmiar zmiennej w *plik1* różni się od rozmiar zmiennej w *plik2*.

## <a name="remarks"></a>Uwagi

Istnieje ważny przypadek, gdy to ostrzeżenie może być emitowana dla C++. W przypadku takich samych typach o tej samej nazwie w dwóch różnych plikach, jeśli te deklaracje zawierać funkcji wirtualnych, a deklaracji nie są takie same, kompilator może emitować ostrzeżenie C4744 dla tabel funkcję wirtualną. To ostrzeżenie występuje, ponieważ istnieją dwie tabele o różnych funkcji wirtualnej dla tego samego typu i konsolidatora należy wybrać jeden z nich, aby dołączyć do pliku wykonywalnego.  Istnieje możliwość, że może spowodować w swoim programie, wywołanie funkcji wirtualnej problem.

Aby rozwiązać to ostrzeżenie, użyj jednej definicji typu albo używać różnych nazw typów lub zmienne.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4743. Aby skompilować go, umieść oba pliki w tym samym folderze, a następnie uruchom  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
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

```cpp
// C4743b.cpp
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
