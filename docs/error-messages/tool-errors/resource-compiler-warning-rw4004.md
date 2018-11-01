---
title: Ostrzeżenie RW4004 kompilatora zasobów
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485647"
---
# <a name="resource-compiler-warning-rw4004"></a>Ostrzeżenie RW4004 kompilatora zasobów

Znak ASCII nie są równoważne kod klawisza wirtualnego

Literał ciągu użyto wirtualnego kod klucza w akceleratorze typu VIRTKEY.

To ostrzeżenie można kontynuować, ale należy pamiętać, klawisze skrótów generowane może nie odpowiadać ciągu, wskazane przez Ciebie. (VIRTKEYs używają różnych kody klawiszy niż akceleratory ASCII).

Literały ciągów są nieprawidłową składnię, należy można tylko mieć pewność, że akcelerator, za pomocą **VK_\* #define** wartości WINDOWS.h.