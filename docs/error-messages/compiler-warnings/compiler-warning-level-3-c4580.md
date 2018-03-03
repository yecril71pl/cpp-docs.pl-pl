---
title: "Kompilatora (poziom 3) ostrzeżenie C4580 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed0391a1a31b4ab64efa01fc15622831de890489
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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