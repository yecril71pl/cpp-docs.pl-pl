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
ms.openlocfilehash: 1a332d8fb5de172c363c6f9c1bebba65d6fa0ff8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381819"
---
# <a name="14-compliance"></a>1.4 Zgodność

Implementacja OpenMP API języka C/C++ jest *CLS OpenMP* jeśli ją rozpoznaje i zachowuje semantykę wszystkie elementy tej specyfikacji, tak jak w rozdziałach 1, 2, 3, 4, i związanych z dodatek C. dodatki A, B, D, E i f. informacje o wyłącznie do celów i nie są częścią specyfikacji. Implementacji, które zawierają tylko podzestaw interfejsu API nie są zgodne z OpenMP.

OpenMP C i C++ interfejsu API jest rozszerzeniem języka podstawowego, która jest obsługiwana przez implementację. Jeśli język podstawowy nie obsługuje konstrukcją języka pierwszej klasy lub rozszerzenie, które pojawia się w tym dokumencie, implementacja OpenMP nie jest wymagane do jego obsługi.

Wszystkie standardowe funkcje biblioteki C i C++ i funkcji wbudowanych (oznacza to, że funkcje których kompilator zna określonych) musi być metodą o bezpiecznych wątkach. Niezsynchronizowane korzystania z funkcji metodą o bezpiecznych wątkach, przez inne wątki w ramach równoległego regionu nie generuje niezdefiniowane zachowanie. Jednak to zachowanie nie może być taki sam jak region szeregowe. (Funkcja generowania liczb losowych jest przykładem).

OpenMP C/C++ API Określa, że określone zachowanie jest *zdefiniowanych w implementacji.* Odpowiadające implementacja OpenMP jest wymagany do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach. Zobacz [dodatku E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), stronie 97, aby uzyskać listę zachowania zdefiniowane w implementacji.