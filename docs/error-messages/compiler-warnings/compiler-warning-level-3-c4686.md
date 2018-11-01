---
title: Kompilator ostrzeżenie (poziom 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 5e23e6aa69fe8a59e3dfd22af7e33780c223cdd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584525"
---
# <a name="compiler-warning-level-3-c4686"></a>Kompilator ostrzeżenie (poziom 3) C4686

> "*typu zdefiniowanego przez użytkownika*': możliwe zmiany w zachowaniu, zmiana UDT zwracają konwencji wywoływania

## <a name="remarks"></a>Uwagi

Specjalizacja szablonu klasy nie jest zdefiniowany, zanim został on użyty w zwracanym typem. Wszystkie elementy, które tworzy wystąpienie klasy rozwiąże C4686; deklarowanie wystąpienia lub uzyskiwania dostępu do członka (C\<int >:: niczego) są również opcje.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

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