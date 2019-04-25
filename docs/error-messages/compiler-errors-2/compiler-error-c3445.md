---
title: Błąd kompilatora C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328656"
---
# <a name="compiler-error-c3445"></a>Błąd kompilatora C3445

> Kopiuj list-initialization elementu "*typu*" nie może używać konstruktora jawnego

Zgodnie z ISO C ++ 17 standardowy kompilator jest wymagany do należy wziąć pod uwagę jawny Konstruktor przypadku rozpoznawania przeciążenia w liście Inicjalizacja kopiowania, ale musi zgłosić błąd, jeśli niejawnej tego przeciążenia.

Począwszy od programu Visual Studio 2017, kompilator znajdzie błędy związane z tworzenia obiektu za pomocą listy inicjalizatora, które nie zostały odnalezione przez program Visual Studio 2015. Te błędy mogą prowadzić do awarii lub niezdefiniowane zachowanie w czasie wykonywania.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Aby poprawić ten błąd, należy zamiast tego użyj inicjalizacji bezpośredniej:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
