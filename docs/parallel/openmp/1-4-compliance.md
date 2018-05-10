---
title: 1.4 zgodności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1bde41491f456ff99b0cd0d1ccc8ab98508412
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="14-compliance"></a>1.4 Zgodność
Implementacja interfejsu API C/C++ OpenMP jest *OpenMP zgodne* Jeśli go rozpoznaje i zachowuje semantykę wszystkie elementy tej specyfikacji, tak jak w rozdziałach 1, 2, 3, 4, i dotyczą dodatek C. dodatki A, B, D, E i F informacje o tylko celów i nie są częścią specyfikacji. Implementacje, które obejmują tylko podzestaw interfejsu API nie są zgodne z OpenMP.  
  
 Openmpc i C++ interfejsu API jest rozszerzeniem języka podstawowego, która jest obsługiwana przez implementację. Jeśli podstawowy język nie obsługuje konstrukcji języka lub rozszerzenia, które pojawia się w tym dokumencie, implementacja OpenMP nie jest wymagane do jego obsługi.  
  
 Wszystkie funkcje biblioteki standardowe C i C++ i funkcji wbudowanych (to znaczy funkcji których kompilator ma określonych informacji na temat) musi być wątkowo. Niezsynchronizowane użycie funkcji obsługującej wielowątkowość przez inne wątki w ramach równoległego regionu dać niezdefiniowane zachowanie. Jednak to zachowanie nie może być taki sam jak region szeregowego. (Przykładem jest funkcja generowania liczb losowych.)  
  
 Interfejs API C/C++ OpenMP — Określa, że określone zachowanie *zdefiniowane w implementacji.* Zgodnych implementacja OpenMP jest wymagany do definiowania i jego zachowanie w tych przypadkach dokumentu. Zobacz [E dodatku](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), strony 97, aby uzyskać listę zachowania zdefiniowane w implementacji.