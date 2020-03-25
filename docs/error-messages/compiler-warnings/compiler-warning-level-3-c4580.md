---
title: Ostrzeżenie kompilatora (poziom 3) C4580
ms.date: 11/04/2016
f1_keywords:
- C4580
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
ms.openlocfilehash: 28d8534dad5fc1b234c180b879ad0645f05cfd65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198617"
---
# <a name="compiler-warning-level-3-c4580"></a>Ostrzeżenie kompilatora (poziom 3) C4580

[Attribute] jest przestarzały; Zamiast tego należy określić system:: Attribute lub platform:: Metadata jako klasę bazową

[[Attribute](../../windows/attributes/attribute.md)] nie jest już preferowaną składnią dla tworzenia atrybutów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../extensions/user-defined-attributes-cpp-component-extensions.md). Dla kodu CLR atrybuty pochodne z `System::Attribute`. W przypadku kodu środowisko wykonawcze systemu Windows atrybuty pochodne z `Platform::Metadata`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3454 i pokazuje, jak rozwiązać ten problem.

```cpp
// C4580.cpp
// compile with: /W3 /c /clr
[attribute]   // C4580
public ref class Attr {
public:
   int m_t;
};

public ref class Attr2 : System::Attribute {
public:
   int m_t;
};
```
