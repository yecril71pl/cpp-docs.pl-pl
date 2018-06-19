---
title: Błąd narzędzi konsolidatora LNK1179 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1179
dev_langs:
- C++
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72a531397c3c101fbff937f293f772c5f6778523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300218"
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