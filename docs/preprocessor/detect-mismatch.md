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
ms.openlocfilehash: f165d24dc1a3044fb89474aef58a2992fa6feed9
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465580"
---
# <a name="detectmismatch"></a>detect_mismatch
Umieszcza rekord w obiekcie. Konsolidator sprawdza, czy te rekordy w potencjalnych niezgodności.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Uwagi  
 
Gdy łączysz projektu, konsolidator generuje `LNK2038` błąd, jeśli projekt zawiera dwa obiekty, które mają taki sam `name` , ale każde z nich ma inną `value`. Użyj tej pragmie, aby uniemożliwić konsolidacji plików obiektu niespójne.  
  
Nazwy i wartości są literały ciągów i przestrzegają zasad dla literałów ciągów znaków ucieczki i łączenia. Jest rozróżniana wielkość liter, a nie może zawierać przecinka, znaku równości, znaki cudzysłowu lub **null** znaków.  
  
## <a name="example"></a>Przykład  
 
Ten przykład tworzy dwa pliki, które mają numery wersji różne etykiety w tej samej wersji.  
  
```cpp  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
Jeśli kompilujesz oba te pliki przy użyciu wiersza polecenia `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, zostanie wyświetlony błąd `LNK2038`.  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)