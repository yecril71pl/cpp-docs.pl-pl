---
title: Ostrzeżenie LNK4086 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4086
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
ms.openlocfilehash: 6e012ceb5e20855353c69bbcde85fb78afad2011
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183426"
---
# <a name="linker-tools-warning-lnk4086"></a>Ostrzeżenie LNK4086 narzędzi konsolidatora

punkt wejścia "Function" nie jest __stdcall z "liczbą" bajtów argumentów; nie można uruchomić obrazu

Punkt wejścia dla biblioteki DLL musi być `__stdcall`. Należy ponownie skompilować funkcję przy użyciu opcji [/GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) lub określić `__stdcall` lub WINAPI podczas definiowania funkcji.
