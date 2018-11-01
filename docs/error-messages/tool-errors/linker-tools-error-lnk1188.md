---
title: Błąd narzędzi konsolidatora LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461259"
---
# <a name="linker-tools-error-lnk1188"></a>Błąd narzędzi konsolidatora LNK1188

BADFIXUPSECTION:: nieprawidłowy element docelowy naprawy "symbol"; możliwa długość sekcji wynosi zero

Podczas łącze VxD celem przeniesienie nie ma sekcji. Za pomocą LINK386 (starsza wersja), rekord grupy OMF (generowany przez dyrektywę grupy MASM) były używane do łączenia długość sekcji wynosi 0 z innej sekcji o niezerowej długości. COFF format nie obsługuje dyrektywy grupy i sekcje o zerowej długości. Ten błąd może wystąpić, gdy łącze automatycznie konwertuje tego typu obiektów OMF do formatu COFF.