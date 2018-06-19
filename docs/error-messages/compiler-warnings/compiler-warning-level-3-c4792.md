---
title: Kompilatora (poziom 3) ostrzeżenie C4792 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a4b0867305c56fc551e55680b6ed48bdb701cc09
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292103"
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