---
title: Kolejność opcji CL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ffe9a440396df14823775db335e52bca6cacdb3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725026"
---
# <a name="order-of-cl-options"></a>Kolejność opcji CL

Opcje mogą występować w dowolnym miejscu w wierszu polecenia CL, z wyjątkiem opcji/Link musi występować jako ostatnia. Kompilator zaczyna się od opcji określonych w [zmiennej środowiskowej CL](../../build/reference/cl-environment-variables.md) , a następnie odczytuje wiersza polecenia od lewej do prawej — przetwarzanie plików polecenia w kolejności ich wystąpienia. Każda opcja ma zastosowanie do wszystkich plików w wierszu polecenia. Jeśli CL napotka opcje powodujące konflikt, zostanie użyta opcja po prawej stronie.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)