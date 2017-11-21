---
title: "Błąd narzędzi konsolidatora LNK1179 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1179
dev_langs: C++
helpviewer_keywords: LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f026ef33452525f9e26da621517cadaeb57621e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1179"></a>Błąd narzędzi konsolidatora LNK1179
nieprawidłowy lub uszkodzony plik: Zduplikowana sekcja COMDAT "filename"  
  
 Moduł obiektu zawiera co najmniej dwie sekcje Comdat o takiej samej nazwie.  
  
 Ten błąd może być spowodowany za pomocą [/H](../../build/reference/h-restrict-length-of-external-names.md), co ogranicza długość nazw zewnętrznych i [/Gy](../../build/reference/gy-enable-function-level-linking.md), które pakiety funkcji Comdat.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie `function1` i `function2` są takie same, w której pierwszych osiem znaków. Kompilowanie przy użyciu **/Gy** i **/H8** powoduje błąd łącza.  
  
```  
void function1(void);  
void function2(void);  
  
int main() {  
    function1();  
    function2();  
}  
  
void function1(void) {}  
void function2(void) {}  
```