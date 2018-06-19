---
title: OMP_NESTED | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NESTED
dev_langs:
- C++
helpviewer_keywords:
- OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c6b51df88ae700f81cf84250cc06ae24c9131fec
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691225"
---
# <a name="ompnested"></a>OMP_NESTED
Określa, czy zagnieżdżonych równoległości jest włączone, chyba że zagnieżdżonych równoległości jest włączone lub wyłączone z `omp_set_nested`.  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Uwagi  
 `OMP_NESTED` Zmiennej środowiskowej może zostać przesłonięta przez [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) funkcji.  
  
 Wartość domyślna w implementacji Visual C++ standardu OpenMP to `OMP_DYNAMIC=FALSE`.  
  
 Aby uzyskać więcej informacji, zobacz [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia `OMP_NESTED` zmiennej środowiskowej na wartość TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie `OMP_NESTED` zmiennej środowiskowej:  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)