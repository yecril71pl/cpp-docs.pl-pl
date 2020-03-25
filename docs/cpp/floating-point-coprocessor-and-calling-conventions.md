---
title: Koprocesor zmiennoprzecinkowy i konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188626"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor zmiennoprzecinkowy i konwencje wywoływania

Jeśli piszesz procedury asemblera dla współprocesora zmiennoprzecinkowego, musisz zachować słowo kontrolne zmiennoprzecinkowe i wyczyścić stos współprocesora, chyba że zwracasz wartość **zmiennoprzecinkową** lub **podwójną** (którą funkcja powinna zwrócić w St (0)).

## <a name="see-also"></a>Zobacz też

[Konwencje wywoływania](../cpp/calling-conventions.md)
