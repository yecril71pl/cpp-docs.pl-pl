---
title: Wklejania tokenu (##) — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '##'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6e224c0327a7ba50c3e13ca78d749f41ad4641f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842234"
---
# <a name="token-pasting-operator-"></a>Operator wklejania tokenu (##)
Operator o podwójnej precyzji numer znaku lub "wklejania tokenu" (**##**), jest czasami nazywany "scalania" operator jest używany w makrach zarówno przypominającej obiekt i podobnych funkcji. Zezwala na oddzielnych tokeny mają zostać połączone w jeden token, a w związku z tym nie może być pierwszym lub ostatnim token w definicji makra.  
  
 Jeśli formalnego parametru w definicji makra jest przed lub po operator wklejania tokenu, formalny parametr zastępuje rzeczywisty argument nierozwiniętego natychmiast. Argument przed zamiany nie jest przeprowadzane rozwinięciu makra.  
  
 Następnie, każde wystąpienie operator wklejania tokenu w *ciąg tokenu* zostanie usunięty, i tokenów przed i po jego są połączone. Wynikowy token musi być prawidłowym tokenem. Jeśli tak jest, token jest skanowany w poszukiwaniu możliwe zastąpienie Jeśli termin reprezentuje nazwę makra. Identyfikator reprezentuje nazwę za pomocą którego będzie znany połączonych tokenów w programie przed zastąpienia. Każdy token reprezentuje token, który został zdefiniowany w innym miejscu, w programie lub z wiersza polecenia kompilatora. Biały znak poprzedzające lub następujące operator jest opcjonalna.  
  
 W tym przykładzie przedstawiono użycie oba operatory tworzenia ciągów i wklejania tokenu określania danych wyjściowych programu:  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 Jeśli makro jest wywoływana z argumentem liczbowym, takich jak  
  
```  
paster( 9 );  
```  
  
 wydajność — makro  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 które stają się  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## <a name="example"></a>Przykład  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
```Output  
token9 = 9  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory preprocesora](../preprocessor/preprocessor-operators.md)