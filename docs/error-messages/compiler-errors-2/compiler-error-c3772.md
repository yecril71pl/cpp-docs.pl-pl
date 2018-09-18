---
title: Błąd kompilatora C3772 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db40c71001e34cc24c19410006cd39f658718c14
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048763"
---
# <a name="compiler-error-c3772"></a>Błąd kompilatora C3772

"name": Nieprawidłowa deklaracja szablonu zaprzyjaźnionego

Nie może deklarować elementu przyjaznego specjalizacja szablonu klasy. Nie można zadeklarować jawna lub częściowa specjalizacja szablonu klasy i w tej samej instrukcji deklarować elementu przyjaznego, że specjalizacji. *Nazwa* symbolu zastępczego identyfikuje Nieprawidłowa deklaracja.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

- Nie deklaruj znajomego specjalizacja szablonu klasy.

- Jeśli jest to odpowiedni dla aplikacji, deklarować elementu przyjaznego szablonu klasy lub deklarować elementu przyjaznego określonego specjalizacji jawne lub częściowe.

## <a name="example"></a>Przykład

Poniższy przykład kodu nie powiedzie się, ponieważ deklaruje znajomego częściowej specjalizacji szablonu klasy.

```cpp
// c3772.cpp
// compile with: /c

// A class template.
    template<class T> class A {};

// A partial specialization of the class template.
    template<class T> class A<T*> {};

// An explicit specialization.
    template<> class A<char>;

class X {
// Invalid declaration of a friend of a partial specialization.
    template<class T> friend class A<T*>; // C3772

// Instead, if it is appropriate for your application, declare a
// friend of the class template. Consequently, all specializations
// of the class template are friends:
//    template<class T> friend class A;
// Or declare a friend of a particular partial specialization:
//    friend class A<int*>;
// Or declare a friend of a particular explicit specialization:
//    friend class A<char>;
};
```

## <a name="see-also"></a>Zobacz też

[Szablony](../../cpp/templates-cpp.md)<br/>
[Specjalizacja szablonu](../../cpp/template-specialization-cpp.md)
