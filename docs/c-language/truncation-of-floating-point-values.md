---
title: Obcięcie wartości zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, truncation
ms.assetid: 051a6e22-c636-4af8-9ac4-40160f4affca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b30700b52e7cbbbc295d6050b03283b4b45a0b08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103818"
---
# <a name="truncation-of-floating-point-values"></a>Obcięcie wartości zmiennoprzecinkowych

**ANSI 3.2.1.4** kierunek obcięcie lub zaokrąglania, gdy liczba zmiennoprzecinkowa jest konwertowana na mniejszą niż liczba zmiennoprzecinkowa

W przypadku niedopełnienie wartości zmiennoprzecinkowych zmiennej jest zaokrąglona w dół zero. Przepełnienie może spowodować błąd czasu wykonywania, lub może tworzyć, nieprzewidywalne wartość, w zależności od optymalizacji określony.

## <a name="see-also"></a>Zobacz też

[Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)