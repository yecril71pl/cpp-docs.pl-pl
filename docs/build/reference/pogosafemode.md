---
title: PogoSafeMode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- PogoSafeMode
ms.assetid: 2daeeff7-44cb-417f-90eb-6b9edf658533
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f40dad6feff9e49deeb495e8acbf2584dea3e41
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2018
---
# <a name="pogosafemode"></a>PogoSafeMode
Określ, czy użyć trybu szybkiego lub w trybie awaryjnym do profilowania aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
PogoSafeMode  
```  
  
## <a name="remarks"></a>Uwagi  
 Optymalizacja sterowana profilem — (PGO) ma dwa tryby możliwe podczas fazy profilowania: szybkie trybie i w trybie awaryjnym. Podczas profilowania jest w trybie szybkiego, używa **INC** instrukcji, aby zwiększyć danych liczników. **INC** instrukcji jest szybsze, ale nie jest bezpieczne wątkowo. Podczas profilowania jest w trybie awaryjnym, używa **INC blokady** instrukcji, aby zwiększyć danych liczników. **INC blokady** instrukcji ma te same funkcje co **INC** instrukcji ma i wątkowo, ale jest mniejsza niż **INC** instrukcji.  
  
 Domyślnie profilowania PGO działa w trybie Szybkie. `PogoSafeMode` jest wymagane tylko, jeśli chcesz użyć trybu awaryjnego.  
  
 Aby uruchomić PGO profilowania w trybie awaryjnym, należy użyć zmiennej środowiskowej `PogoSafeMode` lub przełącznik konsolidatora **- PogoSafeMode**, w zależności od systemu. Jeśli przeprowadzasz profilowanie na x64 komputera, należy użyć przełącznika konsolidatora. Jeśli przeprowadzasz profilowanie na x86 komputera, należy zdefiniować zmienną środowiskową wartości przed rozpoczęciem procesu optymalizacji.  
  
## <a name="example"></a>Przykład  
  
```  
set PogoSafeMode=1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)   
 [Optymalizacje sterowane profilem](../../build/reference/profile-guided-optimizations.md)