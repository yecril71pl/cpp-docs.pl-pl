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
ms.openlocfilehash: 36b31590d94d809c16ed64d16071db0919f60238
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098943"
---
# <a name="linker-tools-error-lnk1188"></a>Błąd narzędzi konsolidatora LNK1188

BADFIXUPSECTION:: nieprawidłowy element docelowy naprawy "symbol"; możliwa długość sekcji wynosi zero

Podczas łącze VxD celem przeniesienie nie ma sekcji. Za pomocą LINK386 (starsza wersja), rekord grupy OMF (generowany przez dyrektywę grupy MASM) były używane do łączenia długość sekcji wynosi 0 z innej sekcji o niezerowej długości. COFF format nie obsługuje dyrektywy grupy i sekcje o zerowej długości. Ten błąd może wystąpić, gdy łącze automatycznie konwertuje tego typu obiektów OMF do formatu COFF.