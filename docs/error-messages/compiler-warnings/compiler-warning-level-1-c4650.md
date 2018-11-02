---
title: Kompilator ostrzeżenie (poziom 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: ea3f1b6e792239692960e74c8360c6c3a1323815
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536109"
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilator ostrzeżenie (poziom 1) C4650

informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne z nagłówka będą dostępne

Prekompilowanego pliku nagłówkowego nie został skompilowany przy użyciu Microsoft symboliczne informacje debugowania.

Jeśli połączone, wynikowy plik wykonywalny lub dołączana dynamicznie biblioteka nie będzie zawierać informacji debugowania dla zawartych w prekompilowany plik nagłówkowy symboli lokalnych.

To ostrzeżenie można uniknąć przez kompilację prekompilowanego pliku nagłówkowego z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji wiersza polecenia.