---
title: STUB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 385e073f877a938a3b73fa79036d27cf50c1e4ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375204"
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