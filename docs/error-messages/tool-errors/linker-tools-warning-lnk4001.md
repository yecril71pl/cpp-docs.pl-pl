---
title: "Ostrzeżenie LNK4001 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4001
dev_langs: C++
helpviewer_keywords: LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfb73e0c62a49fe5190103987277483d29af71fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4001"></a>Ostrzeżenie LNK4001 narzędzi konsolidatora
nie określono; plików obiektów użyto bibliotek  
  
 Konsolidator przekazano jeden lub więcej plików lib, ale żadne pliki .obj.  
  
 Ponieważ konsolidator nie będzie mógł uzyskać dostępu do informacji w pliku .lib, który jest w stanie uzyskać dostęp w pliku .obj, to ostrzeżenie oznacza, że zostaną jawnie określone inne opcje konsolidatora. Na przykład może być konieczne określenie [/maszyny](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), lub [/Entry](../../build/reference/entry-entry-point-symbol.md) opcje.