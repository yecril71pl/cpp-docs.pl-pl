---
title: "C2026 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2026
dev_langs: C++
helpviewer_keywords: C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: acee7db1513dd3e999a90218ea674930c2a13f1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2026"></a>C2026 błąd kompilatora
ciąg zbyt długi, obcięto końcowe znaki  
  
 Ciąg był dłuższy niż limit 16380 znaki jednobajtowe.  
  
 Przed sąsiadujących ze sobą ciągów jest połączony ciąg nie może być dłuższa niż 16380 znaki jednobajtowe.  
  
 Ciąg Unicode połowy tej długości czy wygeneruje również tego błędu.  
  
 Jeśli masz ciąg zdefiniowane w następujący sposób generuje C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Możesz można podzielić go w następujący sposób:  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Warto przechowywać literałów ciągów wyjątkowo dużą (32 KB lub więcej) niestandardowego zasobu lub zewnętrznego pliku. Zobacz [Tworzenie nowej niestandardowej lub zasobów danych](../../windows/creating-a-new-custom-or-data-resource.md) Aby uzyskać więcej informacji.