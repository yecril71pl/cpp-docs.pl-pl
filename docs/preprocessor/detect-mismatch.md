---
title: detect_mismatch | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d99efe6bca27cdbefa73057f843adbcd01cd1fdf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="detectmismatch"></a>detect_mismatch
Umieszcza rekord w obiekcie. Te rekordy w przypadku niezgodności potencjalnych sprawdza, czy konsolidator.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Uwagi  
 Po połączeniu projektu konsolidator wygeneruje `LNK2038` błąd Jeśli projekt zawiera dwa obiekty, które mają taki sam `name` , ale różne `value`. Użyj tej pragmy, aby zapobiec konsolidacji plików obiektu niespójne.  
  
 Nazwy i wartości są literały ciągów i przestrzegać zasad literałów ciągów znaków ucieczki i łączenia. Jest rozróżniana wielkość liter i nie może zawierać przecinka, znaku równości, znaki cudzysłowu lub `null` znaków.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie powoduje utworzenie dwóch plików, które mają numery inną wersję dla etykiety tej samej wersji.  
  
```  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
 Jeśli oba te pliki skompilować przy użyciu wiersza polecenia `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, zostanie wyświetlony błąd `LNK2038`.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)