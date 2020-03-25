---
title: Ostrzeżenie kompilatora (poziom 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185454"
---
# <a name="compiler-warning-level-3-c4686"></a>Ostrzeżenie kompilatora (poziom 3) C4686

> "*Typ zdefiniowany przez użytkownika*": możliwa zmiana w zachowaniu, zmiana w Konwencji WYWOŁYWANIA powrotu UDT

## <a name="remarks"></a>Uwagi

Specjalizacja szablonu klasy nie została zdefiniowana przed użyciem w zwracanym typie. Wszystko, co spowoduje wystąpienie klasy, rozwiązuje C4686; Deklarowanie wystąpienia lub uzyskiwanie dostępu do elementu członkowskiego (C\<int >:: cokolwiek) jest również opcjami.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

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
