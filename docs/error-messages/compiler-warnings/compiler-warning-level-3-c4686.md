---
title: Ostrzeżenie kompilatora (poziom 3) C4686
description: Ostrzeżenie kompilatora Microsoft C++ C4686.
ms.date: 08/29/2020
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 6886ae7f413de630457b53e85b5cd75c4542ee19
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194500"
---
# <a name="compiler-warning-level-3-c4686"></a>Ostrzeżenie kompilatora (poziom 3) C4686

> "*Typ zdefiniowany przez użytkownika*": możliwa zmiana w zachowaniu, zmiana w Konwencji WYWOŁYWANIA powrotu UDT

## <a name="remarks"></a>Uwagi

Specjalizacja szablonu klasy nie została zdefiniowana przed użyciem w zwracanym typie. Wszystko, co tworzy wystąpienie klasy, rozwiązuje C4686; Deklarowanie wystąpienia lub uzyskiwanie dostępu do elementu członkowskiego (na przykład `C<int>::some_member` ) jest również opcje.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Zamiast tego spróbuj wykonać następujące czynności:

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```
