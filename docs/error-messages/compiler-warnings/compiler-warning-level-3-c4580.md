---
title: Kompilatora (poziom 3) ostrzeżenie C4580 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 89ad08af77b62cd0992e9415e2df8b31233e4e0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4580"></a>Kompilator C4580 ostrzegawcze (poziom 3)
[attribute] jest przestarzały; Zamiast tego określ System::Attribute lub Platform::Metadata jako klasa podstawowa  
  
[[atrybutu](../../windows/attribute.md)] nie jest już preferowanych składnia Tworzenie atrybutów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika atrybuty](../../windows/user-defined-attributes-cpp-component-extensions.md). Dla kodu CLR pochodzi atrybutów z `System::Attribute`. Kod środowiska uruchomieniowego systemu Windows, pochodzi atrybutów z `Platform::Metadata`.  
  
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