---
title: Biblioteki OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46bd287ff8a020a4d5d7775afdb12f5571d43294
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-libraries"></a>Biblioteki OpenMP
W tym artykule omówiono .lib — pliki wchodzące w skład biblioteki wykonawczej OpenMP w programie Visual C++.  
  
 Następujące biblioteki zawierają funkcje biblioteki wykonawczej programu Visual C++ OpenMP.  
  
|Biblioteki wykonawcze języka OpenMP|Właściwości|  
|------------------------------|---------------------|  
|VCOMP.LIB|Łącze wielowątkowe, dynamicznych (Importuj biblioteki VCOMP. LIB).|  
|VCOMPD.LIB|Łącze wielowątkowe, dynamicznych (Importuj biblioteki VCOMPD. POKRYWY) (debugowanie)|  
  
 Jeśli _DEBUG jest zdefiniowany w kompilacji i `#include omp.h` jest w kodzie źródłowym, VCOMPD. LIB będzie lib domyślne. W przeciwnym razie VCOMP. LIB będą używane.  
  
 Można użyć [/nodefaultlib (Ignoruj biblioteki)](../../../build/reference/nodefaultlib-ignore-libraries.md) Usuń lib domyślne, a jawnie połączenie z lib wybranych przez użytkownika.  
  
 Biblioteki DLL OpenMP znajdują się w katalogu pakietu redystrybucyjnego Visual C++ i muszą być dystrybuowane z aplikacjami, które używają OpenMP.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)