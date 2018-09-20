---
title: 3. Funkcje bibliotek wykonawczych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5c1a05df3b47c2bbf345bc0101f30ffb83b84967
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401852"
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki czasu wykonywania

Ten rozdział Opisuje funkcje biblioteki czasu wykonywania OpenMP C i C++. Nagłówek  **\<omp.h >** deklaruje dwa typy, kilka funkcji, które mogą służyć do kontrolowania i wysyłać zapytania do środowiska wykonywania równoległego oraz blokowanie funkcje, które mogą służyć do synchronizowania dostępu do danych.

Typ **omp_lock_t** jest typem obiektu może reprezentować, czy blokada jest dostępny, lub wątek posiada blokadę. Blokadami tymi są określane jako *proste blokad*.

Typ **omp_nest_lock_t** może reprezentować, że typ obiektu blokady jest dostępna lub tożsamość wątku, który jest właścicielem blokady i *zagnieżdżania liczba* (opisanych poniżej). Blokadami tymi są określane jako *zagnieżdżalnych blokad*.

Funkcje biblioteki są zewnętrzne funkcji z powiązaniem "C".

Opisy w tym rozdziale są podzielone na następujące tematy:

- Funkcje środowiska wykonawczego (zobacz [sekcji 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stronie 35).

- Zablokuj funkcji (zobacz [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41).