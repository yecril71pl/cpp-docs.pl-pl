---
title: Kolejność opcji CL (C++) — program Visual Studio
ms.date: 12/14/2018
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 93907265bed8141b5c63edd5e75d632e060351fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320945"
---
# <a name="order-of-cl-options"></a>Kolejność opcji CL

Opcje mogą występować w dowolnym miejscu w wierszu polecenia CL, z wyjątkiem opcji/Link musi występować jako ostatnia. Kompilator zaczyna się od opcji określonych w [zmiennej środowiskowej CL](cl-environment-variables.md) , a następnie odczytuje wiersza polecenia od lewej do prawej — przetwarzanie plików polecenia w kolejności ich wystąpienia. Każda opcja ma zastosowanie do wszystkich plików w wierszu polecenia. Jeśli CL napotka opcje powodujące konflikt, zostanie użyta opcja po prawej stronie.

## <a name="see-also"></a>Zobacz także

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
