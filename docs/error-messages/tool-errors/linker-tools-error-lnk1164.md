---
title: Błąd narzędzi konsolidatora LNK1164 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b07dcf360a58b07b84abe655641b758d6137d0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087443"
---
# <a name="linker-tools-error-lnk1164"></a>Błąd narzędzi konsolidatora LNK1164

sekcja wyrównanie sekcji (numer) większa niż wartość opcji/align

Rozmiar wyrównania sekcji podanej w pliku obiektu przekracza wartość określoną za pomocą [/ALIGN](../../build/reference/align-section-alignment.md) opcji. **/ALIGN** wartość musi być potęgą liczby 2 i musi być równa lub przekracza wyrównanie sekcji podany w pliku obiektu.

Albo Skompiluj ponownie z mniejszych wyrównanie sekcji lub zwiększ **/ALIGN** wartość.