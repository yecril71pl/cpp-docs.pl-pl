---
title: C2384 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce139166e2378a26a91bc66db134ec6098aedbdc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33194934"
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