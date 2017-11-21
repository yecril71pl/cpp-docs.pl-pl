---
title: "-Zc-: trigramów (podstawianie Trigramów) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56068f6cb630ac12b9c8417940411616cec65c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Podstawianie trigramów)
Gdy **/Zc: trigraphs** określono kompilator zastępuje sekwencja znaków — trigram przy użyciu odpowiedniego znak interpunkcyjny. Aby wyłączyć — trigram podstawienia, określ **/Zc:trigraphs-**. Domyślnie **/Zc: trigraphs** jest wyłączona.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zc:trigraphs[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 — Trigram składa się z dwóch następujących po sobie znaki zapytania ("?") następuje znak trzeci unikatowy. Na przykład kompilator zastępuje "? = "— trigram za pomocą znaku"#". Użyj trigramów w plikach źródłowych C, korzystających z zestawu znaków, która nie zawiera graficzne przedstawienie wygodny dla niektórych znaków interpunkcyjnych.  
  
 Aby uzyskać listę trigramów C/C++ oraz przykład przedstawia sposób użycia trigramów, zobacz [Trigramów](../../c-language/trigraphs.md).  
  
## <a name="see-also"></a>Zobacz też  
 [/Zc (zgodność)](../../build/reference/zc-conformance.md)   
 [Trigramów](../../c-language/trigraphs.md)