---
title: Ostrzeżenie LNK4086 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: f692f848825cd3d8e5e1fc042cb94d7cce8ea6bf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195814"
---
# <a name="linker-tools-warning-lnk4086"></a>Ostrzeżenie LNK4086 narzędzi konsolidatora

punkt wejścia "Function" nie jest __stdcall z "liczbą" bajtów argumentów; nie można uruchomić obrazu

Punkt wejścia dla biblioteki DLL musi być **`__stdcall`** . Należy ponownie skompilować funkcję przy użyciu opcji [/GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) lub określić **`__stdcall`** lub WINAPI podczas definiowania funkcji.
