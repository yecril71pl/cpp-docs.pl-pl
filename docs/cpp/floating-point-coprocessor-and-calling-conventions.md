---
title: Koprocesor zmiennoprzecinkowy i Konwencje wywoływania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9f45f73e3cb1910bfc604c8a0fde871cef973a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075959"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor zmiennoprzecinkowy i konwencje wywoływania

Jeśli piszesz zestawu procedury dla zmiennoprzecinkowego punktu Koprocesor, należy zachować wartość zmiennoprzecinkowa punktem słowa sterującego i wyczyścić stosu Koprocesor, chyba że jest zwracany **float** lub **double** wartość (która funkcja powinna zwrócić w ST(0)).

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)