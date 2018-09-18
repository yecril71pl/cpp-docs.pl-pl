---
title: Kompilator ostrzeżenie (poziom 3) C4580 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a9d25a77b6936a3b5b741a1da927c6beb24cbb1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072228"
---
# <a name="compiler-warning-level-3-c4580"></a>Kompilator ostrzeżenie (poziom 3) C4580

[attribute] jest przestarzały; zamiast niego Określ System::Attribute lub Platform::Metadata jako klasę bazową

[[atrybut](../../windows/attribute.md)] nie jest już preferowana składnia do tworzenia atrybuty zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [atrybuty zdefiniowane przez użytkownika](../../windows/user-defined-attributes-cpp-component-extensions.md). Dla kodu CLR pochodzić atrybuty z `System::Attribute`. Dla kodu środowiska uruchomieniowego Windows pochodzić atrybuty z `Platform::Metadata`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3454 i pokazuje, jak go naprawić.

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