---
title: Kolejność opcji CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: e5dd07f52f853b17bf663e2fbad7dbe66a3a1db7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633540"
---
# <a name="order-of-cl-options"></a>Kolejność opcji CL

Opcje mogą występować w dowolnym miejscu w wierszu polecenia CL, z wyjątkiem opcji/Link musi występować jako ostatnia. Kompilator zaczyna się od opcji określonych w [zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md) , a następnie odczytuje wiersza polecenia od lewej do prawej — przetwarzanie plików polecenia w kolejności ich wystąpienia. Każda opcja ma zastosowanie do wszystkich plików w wierszu polecenia. Jeśli CL napotka opcje powodujące konflikt, zostanie użyta opcja po prawej stronie.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)