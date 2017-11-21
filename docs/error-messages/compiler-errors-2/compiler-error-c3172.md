---
title: "C3172 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3172
dev_langs: C++
helpviewer_keywords: C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f6bc65ad1f62139e7131e7bb4fbd07a59cb9dd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3172"></a>C3172 błąd kompilatora
"nazwa_modułu": nie można określić innych atrybutów idl_module w projekcie  
  
 [idl_module](../../windows/idl-module.md) atrybutów o tej samej nazwie ale o innej `dllname` lub `version` parametry zostały znalezione w dwóch plików w kompilacji. Tylko jeden unikatowy `idl_module` atrybut może być określona dla kompilacji.  
  
 Identyczne `idl_module` atrybuty można określić więcej niż jednego pliku kodu źródłowego.  
  
 Na przykład jeśli następujące `idl_module` znaleziono atrybuty:  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 a następnie  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 Kompilator może wygenerować C3172 (Uwaga: wartości różnych wersji).