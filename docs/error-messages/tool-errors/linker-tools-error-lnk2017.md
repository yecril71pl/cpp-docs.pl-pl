---
title: Błąd narzędzi konsolidatora LNK2017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022453"
---
# <a name="linker-tools-error-lnk2017"></a>Błąd narzędzi konsolidatora LNK2017

relokacja "symbol" do "segmentu" Nieprawidłowa bez pamięci

Chcesz utworzyć obraz 64-bitowym z 32-bitowymi adresami. Aby to zrobić, musisz mieć:

- Użyj adresu obciążenia stały.

- Obraz należy ograniczyć do 3 GB.

- Określ [pamięci](../../build/reference/largeaddressaware-handle-large-addresses.md).