---
title: "C3208 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3208
dev_langs: C++
helpviewer_keywords: C3208
ms.assetid: 6d060bfe-52cf-4599-8f70-bdeb5a670df3
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5078264a615aa3dd998e2e71f366e8062054e6d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3208"></a>C3208 błąd kompilatora
"Funkcja": lista parametrów szablonu dla szablonu klasy "class" jest niezgodny z listy parametrów szablonu dla szablonu parametru szablonu "parameter"  
  
 Parametr szablonu szablonu nie ma taką samą liczbę parametrów szablonu jako klasa dostarczonego szablonu.  
  
 Poniższy przykład generuje C3208:  
  
```  
// C3208.cpp  
template <template <class T> class TT >  
int f();  
  
template <class T1, class T2>  
struct S;  
  
template <class T1>  
struct R;  
  
int i = f<S>();   // C3208  
// try the following line instead  
// int i = f<R>();  
```