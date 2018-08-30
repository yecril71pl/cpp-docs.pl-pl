---
title: Kompilator ostrzeżenie (poziom 3) C4686 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4686
dev_langs:
- C++
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32a44cd929eb7629ef317ce9847950b613bde52c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202083"
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