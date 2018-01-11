---
title: "Kompilatora (poziom 1) ostrzeżenie C4165 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4165
dev_langs: C++
helpviewer_keywords: C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e31f0e0440b0c31197ded21464edc9d686c4864e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4165"></a>Kompilator C4165 ostrzegawcze (poziom 1)
"HRESULT" jest konwertowany na "bool"; Czy na pewno jest to, co chcesz zrobić?  
  
Gdy użycie HRESULT w [Jeśli](../../cpp/if-else-statement-cpp.md) instrukcji, HRESULT zostanie przekonwertowany na [bool](../../cpp/bool-cpp.md) , chyba że jawnie testu dla zmiennej jako wyniku HRESULT. To ostrzeżenie jest domyślnie wyłączone.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C4165  
  
```cpp  
// C4165.cpp  
// compile with: /W1  
#include <windows.h>  
#pragma warning(1:4165)  
  
extern HRESULT hr;  
int main() {  
   if (hr) {  
   // try either of the following ...  
   // if (FAILED(hr)) { // C4165 expected  
   // if (hr != S_OK) {  
   }  
}  
```