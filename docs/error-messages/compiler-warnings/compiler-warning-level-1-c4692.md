---
title: "Kompilatora (poziom 1) ostrzeżenie C4692 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4692
dev_langs: C++
helpviewer_keywords: C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8088c1434ab33899f60b08c0817464f9ddb9c82e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4692"></a>Kompilator C4692 ostrzegawcze (poziom 1)
'funkcja': podpis z nieprywatnego elementu członkowskiego zawiera typ macierzysty 'native_type' zestawu prywatnego  
  
 Typ, który nie jest widoczna poza zestaw zawiera funkcji członkowskiej, którego sygnatura zawiera typ macierzysty, która nie jest widoczna poza zestaw. W związku z tym funkcja członkowska nie powinna być wywoływana, jeśli jej typ zawierający jest utworzone poza zestaw.  
  
 Aby uzyskać więcej informacji, zobacz [wpisz widoczność](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).  
  
 To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4692.  
  
```  
// C4692.cpp  
// compile with: /W1 /c /clr  
#pragma warning(default:4692)  
class Private_Native_Class {};  
public class Public_Native_Class {};  
public ref class Public_Ref_Class {  
public:  
   void Test(Private_Native_Class *) {}   // C4692  
   void Test2(Public_Native_Class *) {}   // OK  
};  
```