---
title: "C2384 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2384
dev_langs: C++
helpviewer_keywords: C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d87769a2e02e6214e474dab2b74859e85a6880b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2384"></a>C2384 błąd kompilatora
"członek": nie można zastosować __declspec(thread) do elementu członkowskiego z zarządzanego lub klasy WinRT  
  
 [Wątku](../../cpp/thread.md) `__declspec` modyfikatora nie można używać na element członkowski zarządzanego lub klasy środowiska wykonawczego systemu Windows.  
  
 Wątek statycznego magazynu lokalnego w kodzie zarządzanym jest możliwe tylko dla statycznie ładowanych bibliotek DLL — plik DLL, który musi być statycznie załadowany podczas uruchamiania procesu. Środowisko wykonawcze systemu Windows nie obsługuje lokalny magazyn wątków.  
  
 Następujący wiersz generuje C2384 i pokazuje, jak go naprawić w języku C + +/ CLI kodu:  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```