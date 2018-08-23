---
title: region, endregion | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9e6ec22be873dcec06f224913eb905a2779e4efd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466035"
---
# <a name="region-endregion"></a>region, endregion
`#pragma region` Pozwala określić bloku kodu, który można rozwinąć lub zwinąć, korzystając z [konspekt funkcji](/visualstudio/ide/outlining) Edytor kodu programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>Parametry  
*komentarz* (opcjonalnie)  
Komentarz, która będzie wyświetlana w edytorze kodu.  
  
*Nazwa* (opcjonalnie)  
Nazwa regionu.  Ta nazwa będzie wyświetlana w edytorze kodu.  
  
## <a name="remarks"></a>Uwagi  
 
`#pragma endregion` oznacza koniec `#pragma region` bloku.  
  
A `#region` musi się kończyć bloku `#pragma endregion`.  
  
## <a name="example"></a>Przykład  
  
```cpp  
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