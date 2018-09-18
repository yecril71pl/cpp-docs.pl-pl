---
title: Kompilator ostrzeżenie (poziom 1) C4650 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d49b21452465f26d6e696f928c04c20dc0e33307
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052899"
---
# <a name="compiler-warning-level-1-c4650"></a>Kompilator ostrzeżenie (poziom 1) C4650

informacje o debugowaniu nie znajduje się w prekompilowanym nagłówkiem; tylko symbole globalne z nagłówka będą dostępne

Prekompilowanego pliku nagłówkowego nie został skompilowany przy użyciu Microsoft symboliczne informacje debugowania.

Jeśli połączone, wynikowy plik wykonywalny lub dołączana dynamicznie biblioteka nie będzie zawierać informacji debugowania dla zawartych w prekompilowany plik nagłówkowy symboli lokalnych.

To ostrzeżenie można uniknąć przez kompilację prekompilowanego pliku nagłówkowego z [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji wiersza polecenia.