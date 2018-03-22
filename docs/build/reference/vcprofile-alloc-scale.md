---
title: "VCPROFILE_ALLOC_SCALE — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_ALLOC_SCALE
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7b441f41106544633bd691c409fa04c989146f0
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2018
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
Zmodyfikuj ilość pamięci przydzielonej do przechowywania danych profilu.  
  
## <a name="syntax"></a>Składnia  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>Parametry  
 `scale_value`  
 Wartość skali ilości pamięci, potrzebne do uruchomienia testu scenariuszy.  Domyślnym ustawieniem jest 1.  
  
## <a name="remarks"></a>Uwagi  
 W rzadkich przypadkach, nie będzie wystarczającej ilości pamięci do obsługi zbierania danych profilu podczas uruchamiania testu scenariuszy.  W takich przypadkach można zwiększyć ilość pamięci z `VCPROFILE_ALLOC_SCALE`.  
  
 Jeśli zostanie wyświetlony komunikat o błędzie podczas uruchomienia testu, który wskazuje, czy masz za mało pamięci, należy przypisać wartość większą do `VCPROFILE_ALLOC_SCALE`, dopóki test uruchomieniu ukończone bez błędów braku pamięci.  
  
## <a name="example"></a>Przykład  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)