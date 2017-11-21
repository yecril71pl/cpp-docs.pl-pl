---
title: "Konsumowanie typów ogólnych (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: generics [C++], consuming from .NET languages
ms.assetid: e6330ef5-e907-432e-b527-7a22f5899639
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e1abb5cdebca8c19aeeb4ec00fbc46b3120170d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="consuming-generics-ccli"></a>Konsumowanie typów ogólnych (C++/CLI)
Typy ogólne w jednym języku .NET mogą być używane w innych językach .NET. W przeciwieństwie do szablonów ogólnego w skompilowanym zestawie nadal pozostaje ogólnego. W związku z tym jedną może utworzyć wystąpienia typu ogólnego w innym zestawie i nawet w innym języku niż zestaw, w którym zdefiniowano typ ogólny.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Ten przykład przedstawia klasy ogólnej zdefiniowany w języku C#.  
  
### <a name="code"></a>Kod  
  
```  
// consuming_generics_from_other_NET_languages.cs  
// compile with: /target:library  
// a C# program  
public class CircularList<ItemType> {  
   class ListNode    {  
      public ItemType m_item;  
      public ListNode next;  
      public ListNode(ItemType item) {  
         m_item = item;  
      }  
   }  
  
   ListNode first, last;  
  
   public CircularList() {}  
  
   public void Add(ItemType item) {  
      ListNode newnode = new ListNode(item);  
      if (first == null) {  
         first = last = newnode;  
         first.next = newnode;  
         last.next = first;  
      }  
      else {  
         newnode.next = first;  
         first = newnode;  
         last.next = first;  
      }   
   }  
  
   public void Remove(ItemType item) {  
      ListNode iter = first;  
      if (first.m_item.Equals( item )) {  
         first =   
         last.next = first.next;  
      }  
      for ( ; iter != last ; iter = iter.next )  
         if (iter.next.m_item.Equals( item )) {  
              if (iter.next == last)  
                  last = iter;  
              iter.next = iter.next.next;  
              return;  
          }  
   }  
  
   public void PrintAll() {  
      ListNode iter = first;  
      do {  
         System.Console.WriteLine( iter.m_item );  
         iter = iter.next;  
      } while (iter != last);  
   }  
}  
```  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W tym przykładzie korzysta z zestawu utworzone w języku C#.  
  
### <a name="code"></a>Kod  
  
```  
// consuming_generics_from_other_NET_languages_2.cpp  
// compile with: /clr  
#using <consuming_generics_from_other_NET_languages.dll>  
using namespace System;  
class NativeClass {};  
ref class MgdClass {};  
  
int main() {  
   CircularList<int>^ circ1 = gcnew CircularList<int>();  
   CircularList<MgdClass^>^ circ2 = gcnew CircularList<MgdClass^>();  
  
   for (int i = 0 ; i < 100 ; i += 10)  
      circ1->Add(i);  
   circ1->Remove(50);  
   circ1->PrintAll();  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
90  
80  
70  
60  
40  
30  
20  
10  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)