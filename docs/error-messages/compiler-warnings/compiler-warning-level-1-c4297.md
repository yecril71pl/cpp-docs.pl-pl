---
title: Kompilatora (poziom 1) ostrzeżenie C4297 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9253ae709109927e69940d5023b542dfb543c6de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4297"></a>Kompilator C4297 ostrzegawcze (poziom 1)
"Funkcja": funkcja nie zakłada się, że zgłosić wyjątek, ale nie  
  
 (Być może niejawną) zawiera deklarację funkcji `noexcept` specyfikator, pustą `throw` specyfikator wyjątek lub [__declspec(nothrow)](../../cpp/nothrow-cpp.md) atrybutu, jak i definicja zawiera jeden lub więcej [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) instrukcje. Aby rozwiązać C4297, nie należy próbować zgłaszanie wyjątków w funkcjach, które są zadeklarowane `__declspec(nothrow)`, `noexcept(true)` lub `throw()`. Można również usunąć `noexcept`, `throw()`, lub `__declspec(nothrow)` specyfikacji.  
  
 Domyślnie kompilator generuje niejawne `noexcept(true)` specyfikatory destruktory zdefiniowane przez użytkownika i funkcje program wycofujący przydzielenia generowane przez kompilator specjalnych funkcji Członkowskich. To jest zgodny z normą ISO standardem C ++ 11. Aby uniknąć generowania specyfikatory niejawny modyfikator noexcept i przywrócić kompilatora niestandardowym zachowania programu Visual Studio 2013, użyj **/Zc:implicitNoexcept-** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [/Zc: implicitnoexcept (niejawne specyfikatory wyjątków)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).  
  
 Aby uzyskać więcej informacji na specyfikacje wyjątków, zobacz [specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md). Zobacz też [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) informacji na temat sposobu modyfikowania zachowania obsługi w czasie kompilacji wyjątków.  
  
 To ostrzeżenie zostanie również wygenerowany dla __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) funkcje oznaczone jako zewnętrzne "C", nawet jeśli są funkcje języka C++.  
  
 Poniższy przykład generuje C4297:  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```