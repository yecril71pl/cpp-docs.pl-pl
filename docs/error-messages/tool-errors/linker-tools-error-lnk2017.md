---
title: Błąd narzędzi konsolidatora LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194736"
---
# <a name="linker-tools-error-lnk2017"></a>Błąd narzędzi konsolidatora LNK2017

przemieszczenie "symbol" do "segment" jest nieprawidłowe bez/LARGEADDRESSAWARE: NO

Próbujesz utworzyć obraz 64-bitowy z 32-bitowymi adresami. W tym celu należy wykonać następujące czynności:

- Użyj stałego adresu ładowania.

- Ogranicz obraz do 3 GB.

- Określ [/LARGEADDRESSAWARE: No](../../build/reference/largeaddressaware-handle-large-addresses.md).
