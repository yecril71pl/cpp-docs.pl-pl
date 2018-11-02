---
title: Błąd narzędzi konsolidatora LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: c3b1117b31db4759b385943323a581da7a58f0c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491081"
---
# <a name="linker-tools-error-lnk1302"></a>Błąd narzędzi konsolidatora LNK1302

obsługiwana jest konsolidacja bezpiecznych modułów .netmodule; tylko Nie można skonsolidować modułu .netmodule pliku

.Netmodule (skompilowany przy użyciu **/LN**) została przekazana do konsolidatora użytkownika próbę wywołania MSIL konsolidacji.  Modułu języka C++ jest prawidłowa dla Konsolidacja MSIL, jeśli został skompilowany z **/CLR: Safe**.

Aby rozwiązać ten problem, skompiluj z **/CLR: Safe** Włącz łączenie MSIL lub przekazać **/CLR** lub **/CLR: pure** pliku .obj do konsolidatora, zamiast modułu.

Aby uzyskać więcej informacji, zobacz artykuł

- [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md)

- [Pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)