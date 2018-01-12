---
title: "Błąd narzędzi konsolidatora LNK1188 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1188
dev_langs: C++
helpviewer_keywords: LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81d2988742eb9e8cd6aef134510ac8272d3dd27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1188"></a>Błąd narzędzi konsolidatora LNK1188
BADFIXUPSECTION:: nieprawidłowy element docelowy naprawy "symbol"; możliwe długość sekcji wynosi zero  
  
 Podczas łącze VxD element docelowy relokacji nie miał sekcji. Z LINK386 (starsza wersja), rekord grupy OMF (generowane przez dyrektywę grupy MASM) mogą zostać wykorzystane do łączenia długość sekcji wynosi 0 z innej sekcji o niezerowej długości. COFF format nie obsługuje dyrektywy grupy i sekcji o zerowej długości. Ten błąd może wystąpić, gdy łącze powoduje automatyczną konwersję tego typu obiektów OMF do formatu COFF.