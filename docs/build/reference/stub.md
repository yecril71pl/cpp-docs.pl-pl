---
title: STUB | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58430f8211f8859b65103b53d1f98a173c4635ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stub"></a>STUB
Gdy jest używany w pliku definicji modułu, która tworzy sterownik urządzenia wirtualnego (VxD), można określić nazwę pliku, która zawiera strukturę IMAGE_DOS_HEADER (zdefiniowany w Windows NT. H) do użycia w sterownik urządzenia wirtualnego (VxD), zamiast domyślnego nagłówka.  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>Uwagi  
 Odpowiednik sposobu na określenie *filename* z [/STUB](../../build/reference/stub-ms-dos-stub-file-name.md) — opcja konsolidatora.  
  
 STUB jest prawidłowy w pliku definicji modułu tylko wtedy, gdy tworzenie VxD.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)