---
title: Błąd narzędzi konsolidatora LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 8323fa234851ce3ba12083adb74d5ee0fba0ac69
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194931"
---
# <a name="linker-tools-error-lnk1302"></a>Błąd narzędzi konsolidatora LNK1302

Obsługiwane są tylko łączenie bezpiecznych modułów. nie można połączyć pliku. module

Moduł. (skompilowany za pomocą **/LN**) został przekazano do konsolidatora w próbie wywołania elementu MSIL.  C++ Moduł jest prawidłowy dla łączenia MSIL, jeśli jest kompilowany z **/CLR: Safe**.

Aby naprawić ten błąd, skompiluj z **/CLR: Safe** , aby włączyć łączenie MSIL, lub Przekaż plik **/CLR** lub **/CLR: Pure** . obj zamiast modułu.

Aby uzyskać więcej informacji, zobacz

- [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md)

- [Pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)
