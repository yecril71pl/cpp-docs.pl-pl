---
title: "Kompilatora (poziom 3) ostrzeżenie C4191 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4191
dev_langs:
- C++
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4a40f5a05b4efc030cd545f2ffd27325fca86294
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4191"></a>Kompilator C4191 ostrzegawcze (poziom 3)
"operator na operację": niebezpieczna konwersja z "typ wyrażenia" na wymagany typ  
  
 Kilka operacji dotyczących wskaźników funkcji są uważane za niebezpieczne:  
  
-   Typy funkcji z innego konwencji wywoływania.  
  
-   Typy funkcji z różnymi zwracać Konwencji.  
  
-   Argument lub zwracane typy o różnych rozmiarach, typu kategorii lub klasyfikacji.  
  
-   Różną długość listy argumentów (na `__cdecl`tylko na rzutowanie z listy dłużej na krótszą listy, nawet jeśli krótszą jest VARARG).  
  
-   Wskaźnik do danych (inne niż **void\***) aliasem względem wskaźnika do funkcji.  
  
-   Inne różnica typu, która będzie uzyskanie błąd lub ostrzeżenie na `reinterpret_cast`.  
  
 Wywołanie tej funkcji za pośrednictwem wynikowego wskaźnika może spowodować awarię programu.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4191:  
  
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