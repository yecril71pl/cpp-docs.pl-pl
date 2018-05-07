---
title: C2447 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f0f72bc1278792853e1886e302f4410fdbe2d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2447"></a>C2447 błąd kompilatora
'{': brak nagłówka funkcji (stary styl listy formalnej)?  
  
 Kompilator napotkał nieoczekiwany otwierający nawias klamrowy w zakresie globalnym. W większości przypadków jest to spowodowane przez nieprawidłowo sformułowany nagłówek funkcji, deklarację umieszczoną w złym miejscu lub zabłąkany średnik. Aby rozwiązać ten problem, sprawdź, czy otwierający nawias klamrowy następuje po poprawnie sformułowanym nagłówku funkcji i nie jest poprzedzony przez deklarację lub zabłąkany średnik.  
  
 Ten błąd może być też spowodowany listą argumentów formalnych języka C w starym stylu. Aby rozwiązać ten problem, zreorganizuj listę argumentów, aby używała stylu nowoczesnego — to znaczy ujętego w nawiasy.  
  
 Poniższy przykład generuje C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```