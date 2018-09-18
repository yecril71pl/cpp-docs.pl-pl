---
title: Ostrzeżenie RW4004 kompilatora zasobów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33305f1f86c0cc1722e4a235ec27927f6e70675f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095992"
---
# <a name="resource-compiler-warning-rw4004"></a>Ostrzeżenie RW4004 kompilatora zasobów

Znak ASCII nie są równoważne kod klawisza wirtualnego

Literał ciągu użyto wirtualnego kod klucza w akceleratorze typu VIRTKEY.

To ostrzeżenie można kontynuować, ale należy pamiętać, klawisze skrótów generowane może nie odpowiadać ciągu, wskazane przez Ciebie. (VIRTKEYs używają różnych kody klawiszy niż akceleratory ASCII).

Literały ciągów są nieprawidłową składnię, należy można tylko mieć pewność, że akcelerator, za pomocą **VK_\* #define** wartości WINDOWS.h.