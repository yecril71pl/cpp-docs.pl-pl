---
title: "Kompilatora (poziom 3) ostrzeżenie C4792 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4792
dev_langs: C++
helpviewer_keywords: C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9ad10bfc9939a8646f55f33bb7c6e4a5314a3424
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4792"></a>Kompilator C4792 ostrzegawcze (poziom 3)
Funkcja "function" zadeklarowana za pomocą sysimport i odwoływać się z kodu natywnego; Importowanie biblioteki wymagane do połączenia  
  
 Funkcji macierzystej, które zostały zaimportowane do programu z DllImport została wywołana z niezarządzanej funkcji. W związku z tym należy połączyć biblioteki importowanej biblioteki dll.  
  
 To ostrzeżenie nie można rozpoznać w kodzie lub zmieniając go skompilować. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma, aby wyłączyć to ostrzeżenie.  
  
 Poniższy przykład generuje C4792:  
  
```  
// C4792.cpp  
// compile with: /clr /W3  
// C4792 expected  
using namespace System::Runtime::InteropServices;  
[DllImport("msvcrt")]  
extern "C" int __cdecl puts(const char *);  
int main() {}  
  
// Uncomment the following line to resolve.  
// #pragma warning(disable : 4792)  
#pragma unmanaged  
void func(void){  
   puts("test");  
}  
```