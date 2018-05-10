---
title: 1.1 zakres | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48d14ec722299a9ff72ad5bab0a68cde5e00d6ad
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="11-scope"></a>1.1 Zakres
Określenie tej wartości obejmuje tylko przekierowywany użytkownik paralelizacja, w którym użytkownik jawnie określa akcje podejmowane przez kompilator i środowiska wykonawczego systemu w celu wykonania programu równolegle. Implementacje Openmpc i C++ nie są wymagane do sprawdzenia zależności konflikty, zakleszczenie, wyścigu lub innych problemów, które powoduje wykonanie programu niepoprawne. Użytkownik jest odpowiedzialny za egzekwowanie poprawnie wykonuje aplikacji przy użyciu konstrukcji Openmpc i C++ interfejsu API. W tym dokumencie nie są objęte generowane przez kompilator automatyczna paralelizacja i dyrektywy kompilatora ułatwiających takich paralelizacja.