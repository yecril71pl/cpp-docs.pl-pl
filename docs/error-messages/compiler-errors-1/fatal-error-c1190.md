---
title: "Błąd krytyczny C1190 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1190
dev_langs: C++
helpviewer_keywords: C1190
ms.assetid: dee2266d-6c40-4f6e-91db-f01e65f8d2bc
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b04b08bd57a527145cafde1073430a78d68b89b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1190"></a>Błąd krytyczny C1190
docelowy kod zarządzany wymaga "/ clr" opcja  
  
 Używasz konstrukcje CLR, ale nie określono **/CLR**.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Poniższy przykład generuje C1190:  
  
```  
// C1190.cpp  
// compile with: /c  
__gc class A {};   // C1190  
ref class A {};  
```