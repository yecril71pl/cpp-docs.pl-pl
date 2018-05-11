---
title: detect_mismatch | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f30afed5acdb9da433f7ce5f992df9bcb6dc8f5
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
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