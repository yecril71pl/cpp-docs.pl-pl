---
title: Błąd narzędzi konsolidatora LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299059"
---
# <a name="linker-tools-error-lnk2017"></a>Błąd narzędzi konsolidatora LNK2017

relokacja "symbol" do "segmentu" Nieprawidłowa bez pamięci

Chcesz utworzyć obraz 64-bitowym z 32-bitowymi adresami. Aby to zrobić, musisz mieć:

- Użyj adresu obciążenia stały.

- Obraz należy ograniczyć do 3 GB.

- Określ [pamięci](../../build/reference/largeaddressaware-handle-large-addresses.md).