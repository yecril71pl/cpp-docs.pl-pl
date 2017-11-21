---
title: "Błąd narzędzi konsolidatora LNK2033 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2033
dev_langs: C++
helpviewer_keywords: LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41bba79acaca7a83e4103d7d146831dc60c2c2ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2033"></a>Błąd narzędzi konsolidatora LNK2033
Nierozpoznany token typeref (token) dla 'type'  
  
 Typ nie ma definicji w metadanych MSIL.  
  
 LNK2033 mogą wystąpić podczas kompilowania za pomocą **/CLR: Safe** i ma tylko: deklaracja przekazująca dalej dla typu w moduł MSIL, w którym typ odwołuje się moduł MSIL.  
  
 Typ musi być zdefiniowane w obszarze **/CLR: Safe**.  
  
 Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje LNK2033.  
  
```  
// LNK2033.cpp  
// compile with: /clr:safe  
// LNK2033 expected  
ref class A;  
ref class B {};  
  
int main() {  
   A ^ aa = nullptr;  
   B ^ bb = nullptr;   // OK  
};  
```