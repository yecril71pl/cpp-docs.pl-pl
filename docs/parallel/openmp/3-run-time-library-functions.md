---
title: 3. Funkcje biblioteki wykonawczej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688118"
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki wykonawczej
W tej sekcji opisano funkcje biblioteki czasu wykonywania Openmpc i C++. Nagłówek  **\<omp.h >** deklaruje dwa typy, niektóre funkcje, które mogą służyć do kontrolowania i środowiska równoległego wykonywania zapytań i zablokować funkcje, które mogą służyć do synchronizowania dostęp do danych.  
  
 Typ **omp_lock_t** typu obiektu jest w stanie reprezentującą, czy blokada jest dostępny, lub wątku jest właścicielem blokady. Te blokady są określane jako *proste blokad*.  
  
 Typ **omp_nest_lock_t** może reprezentować, że typ obiektu jest dostępny blokady lub tożsamość wątku, który jest właścicielem blokady i *zagnieżdżania liczba* (opisanych poniżej). Te blokady są określane jako *nestable blokad*.  
  
 Funkcje bibliotek są zewnętrzne funkcji z powiązaniem "C".  
  
 W tym rozdziale opisy są podzielone na następujące tematy:  
  
-   Funkcje środowiska wykonawczego (zobacz [sekcji 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stronie 35).  
  
-   Zablokowanie funkcji (zobacz [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41).