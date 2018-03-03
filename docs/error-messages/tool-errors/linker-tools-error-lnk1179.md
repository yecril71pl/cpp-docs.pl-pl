---
title: "Błąd narzędzi konsolidatora LNK1179 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93b042e928331e369d64a45aa27f5f613ce9fc31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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