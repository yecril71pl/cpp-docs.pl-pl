---
title: __raise | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs: C++
helpviewer_keywords: __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a59485af5532276a125b020213e2ce01212511d9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="raise"></a>__raise
Zwrócono szczególną uwagę na miejsce wywołania zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Z kodu zarządzanego zdarzenia można tylko wygenerowany z należące do klasy, w którym jest zdefiniowana. Zobacz [zdarzeń](../windows/event-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 Słowo kluczowe `__raise` powoduje błąd wysyłanego, jeśli wywołujesz niepowiązane zdarzeń.  
  
> [!NOTE]
>  Szablonu klasy lub struktury nie mogą zawierać zdarzenia.  
  
## <a name="example"></a>Przykład  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Obsługa zdarzeń](../cpp/event-handling.md)   
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)