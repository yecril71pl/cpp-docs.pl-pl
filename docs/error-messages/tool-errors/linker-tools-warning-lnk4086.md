---
title: Ostrzeżenie LNK4086 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: c6a5a0714e070e6cf3aee8efcdfbdfa07fa9ee69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427862"
---
# <a name="linker-tools-warning-lnk4086"></a>Ostrzeżenie LNK4086 narzędzi konsolidatora

punkt wejścia "function" jest inny niż __stdcall, za pomocą "number" bajtami argumentów; Obraz może nie działać.

Punkt wejścia dla biblioteki DLL muszą być `__stdcall`. Albo ponownie skompilować funkcję z [GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) opcji lub określić `__stdcall` lub WINAPI podczas definiowania funkcji.