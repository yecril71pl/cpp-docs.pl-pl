---
title: Ostrzeżenie LNK4086 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4086
dev_langs:
- C++
helpviewer_keywords:
- LNK4086
ms.assetid: ea1eecbb-ba2c-41bb-9a4f-fa0808a4b92d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7b3ad3a8ceebf97ccdcf7a1d8079886f54a3984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4086"></a>Ostrzeżenie LNK4086 narzędzi konsolidatora
punkt wejścia "function" nie jest __stdcall z "number" bajtami argumentów; Obraz może nie działać.  
  
 Punkt wejścia biblioteki DLL muszą być `__stdcall`. Albo ponownie skompilować funkcję z [GZ](../../build/reference/gd-gr-gv-gz-calling-convention.md) opcji lub określ `__stdcall` lub WINAPI podczas definiowania funkcji.