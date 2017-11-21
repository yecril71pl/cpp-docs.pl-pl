---
title: "C2220 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2220
dev_langs: C++
helpviewer_keywords: C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc31519b2153c66ea9bab42f536ba7c6be5b2a10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2220"></a>C2220 błąd kompilatora
Ostrzeżenie potraktowano jako błąd — nie wygenerowano pliku obiektu  
  
 [Wx](../../build/reference/compiler-option-warning-level.md) nakazuje kompilatorowi na traktowanie wszystkich ostrzeżeń jako błędy. Wystąpił błąd, nie obiektu lub plik wykonywalny nie wygenerowano.  
  
 Ten błąd pojawia się tylko w przypadku **wx** flagę i ostrzeżenie występuje podczas kompilacji. Aby naprawić ten błąd, można wyeliminować każdego ostrzeżenia w projekcie.  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>Aby rozwiązać problem, użyj jednej z następujących metod  
  
-   Rozwiąż problemy, które powodują ostrzeżenia w projekcie.  
  
-   Kompiluj na niższym poziomie ostrzeżenie — na przykład użyć **/W3** zamiast **/W4**.  
  
-   Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma pominąć określone ostrzeżenia lub wyłączyć.  
  
-   Nie używaj **wx** do skompilowania.