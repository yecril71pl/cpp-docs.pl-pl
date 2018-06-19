---
title: region, endregion — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5590d2b251d86a9d20b62bfdb3d5bf929e3d92d4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839450"
---
# <a name="region-endregion"></a>region, endregion
**#pragma region** pozwala określić blok kodu, który można rozwinąć lub zwinąć przy użyciu [zwijania funkcji](/visualstudio/ide/outlining) edytora kodu programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### <a name="parameters"></a>Parametry  
 `comment`(opcjonalnie)  
 Komentarz, który będzie wyświetlana w edytorze kodu.  
  
 *Nazwa*(opcjonalnie)  
 Nazwa regionu.  Ta nazwa będzie wyświetlana w edytorze kodu.  
  
## <a name="remarks"></a>Uwagi  
 **endregion — #pragma** oznacza koniec **#pragma region** bloku.  
  
 A `#region` muszą kończyć bloku **endregion — #pragma**.  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)