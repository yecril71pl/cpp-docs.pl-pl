---
title: "C3370 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3370
dev_langs: C++
helpviewer_keywords: C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b1a6a450c0c3faca9088b01e1016df5f4e5a4045
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3370"></a>C3370 błąd kompilatora
"Nazwa idl_module": idl_module jeszcze nie zdefiniowany  
  
 Przed użyciem [idl_module](../../windows/idl-module.md) do określenia punktu wejścia w bibliotece DLL, musisz najpierw użyć `idl_module` do określenia nazwy biblioteki DLL.  
  
 Poniższy przykład generuje C3370:  
  
```  
// C3370.cpp  
[module(name=MyLibrary)];  
// uncomment the following line to resolve the error  
// [idl_module(name="name1", dllname=x.dll)];  
[idl_module(name="name1"), entry(100)] // C3370  
int f1();  
  
int main()  
{  
}  
```