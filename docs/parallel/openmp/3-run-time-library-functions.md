---
title: 3. Funkcje biblioteki czasu wykonywania
ms.date: 11/04/2016
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: e1d8d498be7f58bcf510025c67c539127f450824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484100"
---
# <a name="3-run-time-library-functions"></a>3. Funkcje biblioteki czasu wykonywania

Ten rozdział Opisuje funkcje biblioteki czasu wykonywania OpenMP C i C++. Nagłówek  **\<omp.h >** deklaruje dwa typy, kilka funkcji, które mogą służyć do kontrolowania i wysyłać zapytania do środowiska wykonywania równoległego oraz blokowanie funkcje, które mogą służyć do synchronizowania dostępu do danych.

Typ **omp_lock_t** jest typem obiektu może reprezentować, czy blokada jest dostępny, lub wątek posiada blokadę. Blokadami tymi są określane jako *proste blokad*.

Typ **omp_nest_lock_t** może reprezentować, że typ obiektu blokady jest dostępna lub tożsamość wątku, który jest właścicielem blokady i *zagnieżdżania liczba* (opisanych poniżej). Blokadami tymi są określane jako *zagnieżdżalnych blokad*.

Funkcje biblioteki są zewnętrzne funkcji z powiązaniem "C".

Opisy w tym rozdziale są podzielone na następujące tematy:

- Funkcje środowiska wykonawczego (zobacz [sekcji 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stronie 35).

- Zablokuj funkcji (zobacz [sekcji 3.2](../../parallel/openmp/3-2-lock-functions.md) na stronie 41).