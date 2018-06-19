---
title: C2220 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171496"
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