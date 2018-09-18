---
title: Błąd narzędzi konsolidatora LNK1302 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc85b37d58e12602c02c2207c1f38bda9344e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045513"
---
# <a name="linker-tools-error-lnk1302"></a>Błąd narzędzi konsolidatora LNK1302

obsługiwana jest konsolidacja bezpiecznych modułów .netmodule; tylko Nie można skonsolidować modułu .netmodule pliku

.Netmodule (skompilowany przy użyciu **/LN**) została przekazana do konsolidatora użytkownika próbę wywołania MSIL konsolidacji.  Modułu języka C++ jest prawidłowa dla Konsolidacja MSIL, jeśli został skompilowany z **/CLR: Safe**.

Aby rozwiązać ten problem, skompiluj z **/CLR: Safe** Włącz łączenie MSIL lub przekazać **/CLR** lub **/CLR: pure** pliku .obj do konsolidatora, zamiast modułu.

Aby uzyskać więcej informacji, zobacz artykuł

- [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md)

- [Pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)