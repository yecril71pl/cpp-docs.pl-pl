---
title: Biblioteki OpenMP | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c0f009c26789fd771d55dab5fcfe5f342aa03b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-libraries"></a>Biblioteki OpenMP
W tym artykule omówiono .lib — pliki wchodzące w skład biblioteki wykonawczej OpenMP w programie Visual C++.  
  
 Następujące biblioteki zawierają funkcje biblioteki wykonawczej programu Visual C++ OpenMP.  
  
|Biblioteki wykonawcze języka OpenMP|Właściwości|  
|------------------------------|---------------------|  
|VCOMP. LIB|Łącze wielowątkowe, dynamicznych (Importuj biblioteki VCOMP. LIB).|  
|VCOMPD. LIB|Łącze wielowątkowe, dynamicznych (Importuj biblioteki VCOMPD. POKRYWY) (debugowanie)|  
  
 Jeśli _DEBUG jest zdefiniowany w kompilacji i `#include omp.h` jest w kodzie źródłowym, VCOMPD. LIB będzie lib domyślne. W przeciwnym razie VCOMP. LIB będą używane.  
  
 Można użyć [/nodefaultlib (Ignoruj biblioteki)](../../../build/reference/nodefaultlib-ignore-libraries.md) Usuń lib domyślne, a jawnie połączenie z lib wybranych przez użytkownika.  
  
 Biblioteki DLL OpenMP znajdują się w katalogu pakietu redystrybucyjnego Visual C++ i muszą być dystrybuowane z aplikacjami, które używają OpenMP.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)