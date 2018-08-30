---
title: C4191 (poziom 3) ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4191
dev_langs:
- C++
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3b0198971064bec114e4665a499e070ddb61501
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197501"
---
# <a name="compiler-warning-level-3-c4191"></a>C4191 (poziom 3) ostrzeżenia kompilatora
' operator/operacja': niebezpieczna konwersja z 'typ wyrażenia' na 'typ wymagany'  
  
 Kilka operacji obejmujących wskaźniki funkcji są uważane za niebezpieczne:  
  
-   Typy funkcji przy użyciu różnych konwencji wywoływania.  
  
-   Typy funkcji przy użyciu różnych konwencji zwracania.  
  
-   Argument lub zwracane typy o różnych rozmiarach, typ kategorii lub klasyfikacji.  
  
-   Różne długości listy argumentów (na `__cdecl`tylko na rzutowanie z dłuższą listę do krótszej listy, nawet jeśli krótszy jest VARARG).  
  
-   Wskaźnik do danych (inne niż **void**<strong>\*</strong>) aliasem względem wskaźnika do funkcji.  
  
-   Inne różnica typu, które byłyby błąd lub ostrzeżenie na `reinterpret_cast`.  
  
 Wywołanie tej funkcji za pośrednictwem wynikowego wskaźnika może spowodować awarię programu.  
  
 To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład spowoduje wygenerowanie C4191:  
  
```  
// C4191.cpp  
// compile with: /W3 /clr  
#pragma warning(default: 4191)  
  
void __clrcall f1() { }  
void __cdecl   f2() { }  
  
typedef void (__clrcall * fnptr1)();  
typedef void (__cdecl   * fnptr2)();  
  
int main() {  
   fnptr1 fp1 = static_cast<fnptr1>(&f1);  
   fnptr2 fp2 = (fnptr2) &f2;  
  
   fnptr1 fp3 = (fnptr1) &f2;   // C4191  
   fnptr2 fp4 = (fnptr2) &f1;   // C4191  
};  
```