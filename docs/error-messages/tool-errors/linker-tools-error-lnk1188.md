---
title: Błąd narzędzi konsolidatora LNK1188 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31943ae253a332576fba73102db410b103a0096
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302623"
---
# <a name="linker-tools-error-lnk1188"></a>Błąd narzędzi konsolidatora LNK1188
BADFIXUPSECTION:: nieprawidłowy element docelowy naprawy "symbol"; możliwe długość sekcji wynosi zero  
  
 Podczas łącze VxD element docelowy relokacji nie miał sekcji. Z LINK386 (starsza wersja), rekord grupy OMF (generowane przez dyrektywę grupy MASM) mogą zostać wykorzystane do łączenia długość sekcji wynosi 0 z innej sekcji o niezerowej długości. COFF format nie obsługuje dyrektywy grupy i sekcji o zerowej długości. Ten błąd może wystąpić, gdy łącze powoduje automatyczną konwersję tego typu obiektów OMF do formatu COFF.