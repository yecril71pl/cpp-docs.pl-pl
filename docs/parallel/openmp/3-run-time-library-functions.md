---
title: 3. Funkcje biblioteki wykonawczej | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1cbedf8782c9c5ccb25bda3f8b43df8a526f268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki wykonawczej
W tej sekcji opisano funkcje biblioteki czasu wykonywania Openmpc i C++. Nagłówek  **\<omp.h >** deklaruje dwa typy, niektóre funkcje, które mogą służyć do kontrolowania i środowiska równoległego wykonywania zapytań i zablokować funkcje, które mogą służyć do synchronizowania dostęp do danych.  
  
 Typ **omp_lock_t** typu obiektu jest w stanie reprezentującą, czy blokada jest dostępny, lub wątku jest właścicielem blokady. Te blokady są określane jako *proste blokad*.  
  
 Typ **omp_nest_lock_t** może reprezentować, że typ obiektu jest dostępny blokady lub tożsamość wątku, który jest właścicielem blokady i *zagnieżdżania liczba* (opisanych poniżej). Te blokady są określane jako *nestable blokad*.  
  
 Funkcje bibliotek są zewnętrzne funkcji z powiązaniem "C".  
  
 W tym rozdziale opisy są podzielone na następujące tematy:  
  
-   Funkcje środowiska wykonawczego (zobacz [sekcji 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stronie 35).  
  
-   Zablokowanie funkcji (zobacz [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41).