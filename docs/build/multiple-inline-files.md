---
title: Wiele plików wbudowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9be15f029c0aaab3ca4bc47fb183e1499c2e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368216"
---
# <a name="multiple-inline-files"></a>Pliki wbudowane
Polecenie można utworzyć więcej niż jednego pliku wbudowanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>Uwagi  
 Dla każdego pliku określ jeden lub więcej wierszy tekstu wbudowanego znak zawierający ogranicznik wiersza zamknięcia. Rozpocznij tekst drugiego pliku w wierszu następującym rozdzielające wiersza dla pierwszego pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki wbudowane w pliku reguł programu Make](../build/inline-files-in-a-makefile.md)