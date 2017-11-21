---
title: TypeOf operatorem T::TypeID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 90c75b67dc6496f51d335f83a49242b7f7ae0b29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="typeof-goes-to-ttypeid"></a>Operator typeof został zastąpiony operatorem T::typeid
`typeof` Operator używany w rozszerzeń zarządzanych dla języka C++ ma zostać supplanted przez `typeid` — słowo kluczowe w programie Visual C++.  
  
 W zarządzanych rozszerzeń `__typeof()` operator zwraca skojarzonego `Type*` obiektu po upływie nazwę typu zarządzanego. Na przykład:  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 W nowej składni `__typeof` został zastąpiony w innej formie `typeid` zwracającą `Type^` gdy został określony parametr typu zarządzanego.  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne zmiany w języku (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [TypeID](../windows/typeid-cpp-component-extensions.md)