---
title: Kompilatora (poziom 3) ostrzeżenie C4359 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4359
dev_langs:
- C++
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7ddc48294734e5a180014ea20cf98b9d7374f25
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292987"
---
# <a name="compiler-warning-level-3-c4359"></a>Kompilator C4359 ostrzegawcze (poziom 3)
'type': rzeczywiste wyrównanie (8) jest większa niż wartość określona w __declspec(align())  
  
 Wyrównanie określone dla typu jest mniejsza niż wyrównanie typ jednego z jego elementów członkowskich danych.  Aby uzyskać więcej informacji, zobacz [Dopasuj](../../cpp/align-cpp.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4359.  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```