---
title: 'Porady: Definiowanie statycznego konstruktora interfejsu (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d2df4610cdc0e7b7bcf579c6280cbc00961409f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Porady: definiowanie statycznego konstruktora interfejsu (C++/CLI)
Interfejs może mieć statycznego konstruktora, który może służyć do zainicjowania statyczne elementy członkowskie danych.  Konstruktor statyczny zostanie wywołana najwyżej jeden raz i będzie wywoływana przed po raz pierwszy uzyskać dostępu do członka statycznego interfejsu.  
  
## <a name="example"></a>Przykład  
  
```  
// mcppv2_interface_class2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct MyInterface {  
   static int i;  
   static void Test() {  
      Console::WriteLine(i);  
   }  
  
   static MyInterface() {   
      Console::WriteLine("in MyInterface static constructor");  
      i = 99;  
   }  
};  
  
ref class MyClass : public MyInterface {};  
  
int main() {  
   MyInterface::Test();  
   MyClass::MyInterface::Test();  
  
   MyInterface ^ mi = gcnew MyClass;  
   mi->Test();  
}  
```  
  
```Output  
in MyInterface static constructor  
99  
99  
99  
```  
  
## <a name="see-also"></a>Zobacz też  
 [klasy interfejsu](../windows/interface-class-cpp-component-extensions.md)