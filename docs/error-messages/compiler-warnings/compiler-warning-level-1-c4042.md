---
title: Kompilatora (poziom 1) ostrzeżenie C4042 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc4123c18eb9765841a5f6b54446cd064407700
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4042"></a>Kompilator C4042 ostrzegawcze (poziom 1)
'Identyfikator': ma złą klasę magazynu  
  
 Klasa wybrany magazyn nie można używać z tego identyfikatora w tym kontekście. Kompilator używa zamiast tego domyślną klasę magazynu:  
  
-   `extern`, jeśli *identyfikator* jest funkcją.  
  
-   **automatycznie**, jeśli *identyfikator* jest formalny parametr lub zmienna lokalna.  
  
-   Brak magazynu klasy, jeśli *identyfikator* jest zmienną globalną.  
  
 To ostrzeżenie może być spowodowana przez określenie klasę magazynu innego niż **zarejestrować** w deklaracji parametru.  
  
 Poniższy przykład generuje C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```